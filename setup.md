Here’s the information organized into a **clear format with tables**:

---

## 🐧 **Setup Linux Environment on Windows & macOS using Docker**

### ✅ **Steps for Windows Host**

1. Install **Docker Desktop** on Windows.
2. Create a folder named **ubuntu-data** in your Downloads folder.
3. Run the following command in **PowerShell** (update your username in the path):

```powershell
docker run -dit `
  --name ubuntu-container `
  --hostname ubuntu-dev `
  --restart unless-stopped `
  --cpus="2" `
  --memory="4g" `
  --mount type=bind,source="C:/Users/<Your-Username>/Downloads/ubuntu-data",target=/data `
  -v /var/run/docker.sock:/var/run/docker.sock `
  -p 2222:22 `
  -p 8080:80 `
  --env TZ=Asia/Kolkata `
  --env LANG=en_US.UTF-8 `
  ubuntu:latest /bin/bash
```

---

### ✅ **Steps for macOS or Linux Host**

1. Install **Docker Desktop** on macOS/Linux.
2. Create a folder named **ubuntu-data** in `/tmp`.
3. Run this command in **Terminal**:

```bash
docker run -dit \
  --name ubuntu-container \
  --hostname ubuntu-dev \
  --restart unless-stopped \
  --cpus="2" \
  --memory="4g" \
  --mount type=bind,source=/tmp/ubuntu-data,target=/data \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -p 2222:22 \
  -p 8080:80 \
  --env TZ=Asia/Kolkata \
  --env LANG=en_US.UTF-8 \
  ubuntu:latest /bin/bash
```

---

## 📋 **Explanation of Each Parameter**

| **Parameter**                                  | **Description**                                                                            |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------ |
| `-dit`                                         | Runs the container in **detached (-d)**, **interactive (-i)**, and **terminal (-t)** mode. |
| `--name ubuntu-container`                      | Assigns a **name** to the container for easy management.                                   |
| `--hostname ubuntu-dev`                        | Sets the container’s **hostname**.                                                         |
| `--restart unless-stopped`                     | Ensures the container **restarts automatically** unless manually stopped.                  |
| `--cpus="2"`                                   | Limits the container to **2 CPU cores**.                                                   |
| `--memory="4g"`                                | Allocates **4 GB RAM** to the container.                                                   |
| `--mount type=bind,source=...,target=/data`    | Mounts a **folder from host** into the container to persist data.                          |
| `-v /var/run/docker.sock:/var/run/docker.sock` | Allows **running Docker commands inside** the container (optional).                        |
| `-p 2222:22`                                   | Maps port **2222 on host** → **22 (SSH)** inside the container.                            |
| `-p 8080:80`                                   | Maps port **8080 on host** → **80 (web services)** inside the container.                   |
| `--env TZ=Asia/Kolkata`                        | Sets the **timezone** (modify based on your location).                                     |
| `--env LANG=en_US.UTF-8`                       | Sets the **language settings** inside the container.                                       |
| `ubuntu:latest /bin/bash`                      | Uses the **latest Ubuntu image** and runs **Bash shell**.                                  |

---

This format makes it easy to **copy-paste** and understand both the commands and their explanations.
