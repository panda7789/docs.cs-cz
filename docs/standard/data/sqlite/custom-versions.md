---
title: Vlastní verze SQLite
ms.date: 12/13/2019
description: Naučte se používat vlastní verzi nativní knihovny SQLite.
ms.openlocfilehash: 8a2646138ea9dbecf412a2e8e0e347e2d71a5b0b
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447144"
---
# <a name="custom-sqlite-versions"></a>Vlastní verze SQLite

Microsoft. data. sqlite je postaven nad SQLitePCLRaw. Můžete použít vlastní verze nativní knihovny SQLite pomocí sady prostředků nebo konfigurací poskytovatele SQLitePCLRaw.

## <a name="bundles"></a>Sady

SQLitePCLRaw poskytuje balíčky sady prostředků, které usnadňují přenesení správných závislostí napříč různými platformami.

Hlavní balíček Microsoft. data. sqlite ve výchozím nastavení přináší SQLitePCLRaw. bundle_e_sqlite3.

Pokud chcete použít jinou sadu prostředků, nainstalujte místo toho balíček `Microsoft.Data.Sqlite.Core` společně s balíčkem sady, který chcete použít. Sady se automaticky inicializují pomocí Microsoft. data. sqlite.

| Nabídky | Popis |
| --- | --- |
| SQLitePCLRaw. bundle_e_sqlite3 | Poskytuje konzistentní verzi SQLite na všech platformách. Zahrnuje FTS4, FTS5, JSON1 a | Stromová rozšíření R *. Toto nastavení je výchozí. |
| SQLitePCLRaw. bundle_green | Stejné jako bundle_e_sqlite3, s výjimkou iOS, kde používá systémovou knihovnu SQLite. |
| SQLitePCLRaw. bundle_zetetic | Používá oficiální SQLCipher buildy z Zetetic (Nezahrnuto). |
| SQLitePCLRaw. bundle_winsqlite3 | Používá winsqlite3. dll, systémovou knihovnu SQLite ve Windows 10. |
| SQLitePCLRaw. bundle_e_sqlcipher | Poskytuje neoficiální a open source sestavení SQLCipher. |

Například pro použití neoficiálního Open Source sestavení SQLCipher použijte následující příkazy.

### <a name="net-core-clitabnetcore-cli"></a>[Rozhraní příkazového řádku .NET Core](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studiotabvisual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-providers"></a>SQLitePCLRaw poskytovatelé

Pomocí `SQLitePCLRaw.provider.dynamic_cdecl` balíčku můžete použít vlastní sestavení SQLite. V tomto případě zodpovídáte za nasazení nativní knihovny s vaší aplikací. Všimněte si, že podrobnosti o nasazení nativních knihoven s vaší aplikací se výrazně liší v závislosti na tom, kterou platformu .NET a modul runtime používáte.

Nejdřív budete muset implementovat IGetFunctionPointer. Implementace je poměrně triviální v .NET Core.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

Dále nakonfigurujte poskytovatele SQLitePCLRaw. Ujistěte se, že je to hotové předtím, než se v aplikaci použije Microsoft. data. sqlite. Nepoužívejte také balíček SQLitePCLRaw sady, který by mohl přepsat vašeho poskytovatele.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
