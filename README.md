# DeepDive 发布仓

DeepDive（深潜）macOS 客户端的**发布产物**与**更新源**。源码仓 [CatSkys/DSH-deck](https://github.com/CatSkys/DSH-deck) 是私有的，而装好的应用要匿名读更新——所以 feed 落在这里。

每个 Release 带两项：

| 资产 | 是什么 |
|---|---|
| `appcast.xml` | Sparkle 更新源。已安装的 DeepDive 读它的永久链接 `…/releases/latest/download/appcast.xml`（应用 Info.plist 的 `SUFeedURL`） |
| `DeepDive-<版本>.dmg` | 该版本的安装包，appcast 的 enclosure 指向它 |

DMG 里的应用用 Developer ID 签名，并已装订公证票据（首启过 Gatekeeper）。更新是否可信由 appcast 里的 EdDSA 签名决定，公钥固化在应用 Info.plist 的 `SUPublicEDKey`——只有持有对应私钥的一方签出的包会被接受。

发布由源码仓的 `make publish`（`scripts/publish-release.sh`）完成，请勿手工上传资产。
