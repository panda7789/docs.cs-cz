---
title: Šifrování
ms.date: 12/13/2019
description: Naučte se šifrovat soubor databáze.
ms.openlocfilehash: ccdd4b6b8642b3cde1c2667c9ca432a9b0ef21f2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447263"
---
# <a name="encryption"></a>Šifrování

SQLite nepodporuje ve výchozím nastavení šifrování souborů databáze. Místo toho musíte použít upravenou verzi SQLite, jako je například [See](https://www.hwaci.com/sw/sqlite/see.html), [SQLCipher](https://www.zetetic.net/sqlcipher/), [SQLiteCrypt](http://www.sqlite-crypt.com/)nebo [wxSQLite3](https://utelle.github.io/wxsqlite3). Tento článek ukazuje použití nepodporovaného Open Source sestavení SQLCipher, ale tyto informace platí i pro další řešení, protože obvykle řídí stejný vzor.

## <a name="installation"></a>Instalace služby

### <a name="net-core-clitabnetcore-cli"></a>[Rozhraní příkazového řádku .NET Core](#tab/netcore-cli)

```dotnetcli
dotnet remove package Microsoft.Data.Sqlite
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studiotabvisual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Remove-Package Microsoft.Data.Sqlite
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

Další informace o použití jiné nativní knihovny pro šifrování naleznete v tématu [Custom SQLite Versions](custom-versions.md).

## <a name="specify-the-key"></a>Zadat klíč

Pokud chcete povolit šifrování, zadejte klíč pomocí klíčového slova `Password` připojovacího řetězce. Pomocí <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> můžete přidat nebo aktualizovat hodnotu ze vstupu uživatele a vyhnout se útokům prostřednictvím injektáže připojovacího řetězce.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="rekeying-the-database"></a>Opětovné vytvoření klíče databáze

Pokud chcete změnit šifrovací klíč databáze, vydejte příkaz `PRAGMA rekey`. Chcete-li dešifrovat databázi, zadejte `NULL`.

SQLite nepodporuje parametry v příkazech `PRAGMA`. Místo toho použijte funkci `quote()`, abyste zabránili injektáže SQL.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_Rekey)]
