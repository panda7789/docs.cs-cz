---
title: Vlastní verze SQLite
ms.date: 05/14/2020
description: Naučte se používat vlastní verzi nativní knihovny SQLite.
ms.openlocfilehash: 15db10db26bc7c5017313ca020a0e1e528ba207a
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83440834"
---
# <a name="custom-sqlite-versions"></a>Vlastní verze SQLite

`Microsoft.Data.Sqlite`je postaven na začátku `SQLitePCLRaw` . Můžete použít vlastní verze nativní knihovny SQLite pomocí sady prostředků nebo konfigurací `SQLitePCLRaw` poskytovatele.

## <a name="bundles"></a>Sady

`SQLitePCLRaw`poskytuje balíčky na bázi pohodlí, které usnadňují přenesení správných závislostí napříč různými platformami. Hlavní `Microsoft.Data.Sqlite` balíček ve `SQLitePCLRaw.bundle_e_sqlite3` výchozím nastavení přinese. Pokud chcete použít jinou sadu prostředků, nainstalujte `Microsoft.Data.Sqlite.Core` balíček místo toho společně s balíčkem sady, který chcete použít. Sady jsou automaticky inicializovány nástrojem `Microsoft.Data.Sqlite` .

| Nabídky | Popis |
|--|--|
| [SQLitePCLRaw. bundle_e_sqlite3](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlite3) | Poskytuje konzistentní verzi SQLite na všech platformách. Zahrnuje rozšíření stromu FTS4, FTS5, JSON1 a R *. Toto nastavení je výchozí. |
| [SQLitePCLRaw. bundle_e_sqlcipher](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlcipher) | Poskytuje neoficiální sestavení open source `SQLCipher` . |
| [SQLitePCLRaw. bundle_green](https://www.nuget.org/packages/SQLitePCLRaw.bundle_green) | Stejné jako `bundle_e_sqlite3` , s výjimkou iOS, kde používá systémovou knihovnu sqlite. |
| [SQLitePCLRaw. bundle_winsqlite3](https://www.nuget.org/packages/SQLitePCLRaw.bundle_winsqlite3) | Používá `winsqlite3.dll` , systémová knihovna SQLite ve Windows 10. |
| [SQLitePCLRaw. bundle_zetetic](https://www.nuget.org/packages/SQLitePCLRaw.bundle_zetetic) | Používá oficiální `SQLCipher` buildy z Zetetic (Nezahrnuto). |

Například pro použití neoficiálního Open Source sestavení `SQLCipher` použijte následující příkazy.

### <a name="net-core-cli"></a>[.NET Core CLI](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-available-providers"></a>SQLitePCLRaw poskytovatelé k dispozici

Pokud se nespoléháte na sadu prostředků, můžete použít dostupné poskytovatele SQLite se základním sestavením.

| Poskytovatel | Popis |
|--|--|
| [SQLitePCLRaw. Provider. Dynamic](https://www.nuget.org/packages/SQLitePCLRaw.provider.dynamic) | `dynamic`Zprostředkovatel načte nativní knihovnu namísto použití <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType> atributů. Další informace o použití tohoto poskytovatele najdete v tématu [použití dynamického poskytovatele](#use-the-dynamic-provider). |
| [SQLitePCLRaw. Provider. e_sqlite3](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlite3) | `e_sqlite3`Je výchozím zprostředkovatelem. |
| [SQLitePCLRaw. Provider. e_sqlcipher](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlcipher) | `e_sqlcipher`Poskytovatel je neoficiální a nepodporovaný `SQLCipher` . |
| [SQLitePCLRaw. Provider. sqlite3](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlite3) | `sqlite3`Poskytovatel se poskytuje systémem `SQLite` pro iOS, MacOS a Linux. |
| [SQLitePCLRaw. Provider. SQLCIPHER](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlcipher) | `sqlcipher`Poskytovatel je pro oficiální `SQLCipher` sestavení z `Zetetic` . |
| [SQLitePCLRaw. Provider. winsqlite3](https://www.nuget.org/packages/SQLitePCLRaw.provider.winsqlite3) | `winsqlite3`Zprostředkovatel je pro prostředí Windows 10. |

Chcete-li použít `sqlite3` zprostředkovatele, použijte následující příkazy:

### <a name="net-core-cli"></a>[.NET Core CLI](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.core
dotnet add package SQLitePCLRaw.provider.sqlite3
```

### <a name="visual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.core
Install-Package SQLitePCLRaw.provider.sqlite3
```

---

S nainstalovanými balíčky pak nastavte poskytovatele na `sqlite3` instanci.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SqliteProviderSample/Program.cs)]

## <a name="use-the-dynamic-provider"></a>Použití dynamického poskytovatele

Můžete použít vlastní sestavení SQLite využitím `SQLitePCLRaw.provider.dynamic_cdecl` balíčku. V tomto případě zodpovídáte za nasazení nativní knihovny s vaší aplikací. Všimněte si, že podrobnosti o nasazení nativních knihoven s vaší aplikací se výrazně liší v závislosti na tom, kterou platformu .NET a modul runtime používáte.

Nejdřív budete muset implementovat `IGetFunctionPointer` . Implementace rozhraní .NET Core je následující:

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

Dále nakonfigurujte `SQLitePCLRaw` poskytovatele. Zajistěte, aby se to dokončilo předtím, než `Microsoft.Data.Sqlite` se ve vaší aplikaci použije. Nepoužívejte také `SQLitePCLRaw` balíček sady prostředků, který by mohl přepsat vašeho poskytovatele.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
