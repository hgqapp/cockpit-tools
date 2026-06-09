# Qoder 身份重置文件路径清单

> 对应 `reset_qoder_identity()` 实现，参考 Qoder-Free `qoder_reset_gui.py`。
> 代码位置：`src-tauri/src/modules/qoder_account.rs`
>
> 基准路径 `$USER_DATA_DIR` 来自 `qoder_instance::get_default_qoder_user_data_dir()`：

| 平台 | `$USER_DATA_DIR` |
|------|------------------|
| Linux | `${HOME}/.config/Qoder` |
| macOS | `${HOME}/Library/Application Support/Qoder` |
| Windows | `%APPDATA%\Qoder` |

---

## 写入/重置的文件

```
$USER_DATA_DIR/machineid
$USER_DATA_DIR/deviceid
$USER_DATA_DIR/hardware_uuid
$USER_DATA_DIR/system_uuid
$USER_DATA_DIR/platform_id
$USER_DATA_DIR/installation_id
$USER_DATA_DIR/User/globalStorage/storage.json
```

### storage.json 覆写的 Key

| Key | 值 |
|-----|-----|
| `telemetry.machineId` | MD5(新 UUID) |
| `telemetry.devDeviceId` | 新 UUID |
| `telemetry.sqmId` | 新 UUID |
| `telemetry.sessionId` | 新 UUID |
| `telemetry.installationId` | 新 UUID |
| `telemetry.clientId` | 新 UUID |
| `telemetry.userId` | 新 UUID |
| `telemetry.anonymousId` | 新 UUID |
| `machineId` | MD5(新 UUID) |
| `deviceId` | 新 UUID |
| `installationId` | 新 UUID |
| `hardwareId` | 新 UUID |
| `platformId` | 新 UUID |

---

## 删除的缓存目录

```
$USER_DATA_DIR/Cache
$USER_DATA_DIR/Code Cache
$USER_DATA_DIR/GPUCache
$USER_DATA_DIR/DawnGraphiteCache
$USER_DATA_DIR/DawnWebGPUCache
$USER_DATA_DIR/ShaderCache
$USER_DATA_DIR/DawnCache
$USER_DATA_DIR/blob_storage
$USER_DATA_DIR/SharedClientCache
$USER_DATA_DIR/CachedData
$USER_DATA_DIR/CachedProfilesData
$USER_DATA_DIR/CachedExtensions
$USER_DATA_DIR/IndexedDB
$USER_DATA_DIR/CacheStorage
$USER_DATA_DIR/Service Worker
$USER_DATA_DIR/File System
```

---

## 删除的身份跟踪文件

```
$USER_DATA_DIR/Network Persistent State
$USER_DATA_DIR/TransportSecurity
$USER_DATA_DIR/Trust Tokens
$USER_DATA_DIR/Trust Tokens-journal
$USER_DATA_DIR/Cookies
$USER_DATA_DIR/Cookies-journal
$USER_DATA_DIR/Login Data
$USER_DATA_DIR/Login Data-journal
$USER_DATA_DIR/Web Data
$USER_DATA_DIR/Web Data-journal
$USER_DATA_DIR/Local State
$USER_DATA_DIR/Preferences
$USER_DATA_DIR/Secure Preferences
$USER_DATA_DIR/Bookmarks
$USER_DATA_DIR/Shortcuts
$USER_DATA_DIR/Shortcuts-journal
$USER_DATA_DIR/Top Sites
$USER_DATA_DIR/Top Sites-journal
$USER_DATA_DIR/Favicons
$USER_DATA_DIR/Favicons-journal
$USER_DATA_DIR/History
$USER_DATA_DIR/History-journal
$USER_DATA_DIR/Visited Links
$USER_DATA_DIR/QuotaManager
$USER_DATA_DIR/QuotaManager-journal
$USER_DATA_DIR/NetworkDataMigrated
$USER_DATA_DIR/cert_transparency_reporter_state.json
```

---

## 删除的存储目录

```
$USER_DATA_DIR/databases
$USER_DATA_DIR/Session Storage  ← 可通过 UI 切换控制是否删除
$USER_DATA_DIR/Local Storage
$USER_DATA_DIR/WebStorage
```

> **Session Storage 开关**：Qoder 账号页面工具栏有一个数据库图标按钮(`Database`)，点击可切换是否在切换账号时清理 `Session Storage`。默认清理，设置保存在 `localStorage` 的 `qoder.cleanSessionStorage` key 中。
