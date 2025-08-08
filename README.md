# 🧹 Cleanup Docker Completely

Dưới đây là các bước để xóa sạch mọi thứ trong Docker (containers, images, volumes, networks, caches) để có thể build lại từ đầu.

---

## 1. 🛑 Dừng toàn bộ containers

```bash
docker stop $(docker ps -aq)
```

---

## 2. 🗑 Xóa toàn bộ containers

```bash
docker rm $(docker ps -aq)
```

---

## 3. 🧨 Xóa toàn bộ images

```bash
docker rmi -f $(docker images -q)
```

---

## 4. 📦 Xóa toàn bộ volumes

```bash
docker volume rm $(docker volume ls -q)
```

---

## 5. 🌐 Xóa networks do Docker tạo (ngoại trừ mặc định)

```bash
docker network rm $(docker network ls | grep -v 'bridge\|host\|none' | awk '{print $1}')
```

---

## 6. 🧰 Xóa cache build

```bash
docker builder prune -a
```

---

## 7. 🧼 Dọn sạch toàn bộ hệ thống Docker (images, containers, volumes, networks)

```bash
docker system prune -a --volumes -f
```

---

## ✅ Kiểm tra dung lượng sau khi dọn

```bash
docker system df -v
```

---

> ⚠️ **Cảnh báo:** Hành động này sẽ xóa toàn bộ dữ liệu, bao gồm cả database trong volumes. Hãy sao lưu nếu cần giữ lại!
