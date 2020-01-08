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
# <a name="encryption"></a><span data-ttu-id="fd971-103">Šifrování</span><span class="sxs-lookup"><span data-stu-id="fd971-103">Encryption</span></span>

<span data-ttu-id="fd971-104">SQLite nepodporuje ve výchozím nastavení šifrování souborů databáze.</span><span class="sxs-lookup"><span data-stu-id="fd971-104">SQLite doesn't support encrypting database files by default.</span></span> <span data-ttu-id="fd971-105">Místo toho musíte použít upravenou verzi SQLite, jako je například [See](https://www.hwaci.com/sw/sqlite/see.html), [SQLCipher](https://www.zetetic.net/sqlcipher/), [SQLiteCrypt](http://www.sqlite-crypt.com/)nebo [wxSQLite3](https://utelle.github.io/wxsqlite3).</span><span class="sxs-lookup"><span data-stu-id="fd971-105">Instead, you need to use a modified version of SQLite like [SEE](https://www.hwaci.com/sw/sqlite/see.html), [SQLCipher](https://www.zetetic.net/sqlcipher/), [SQLiteCrypt](http://www.sqlite-crypt.com/), or [wxSQLite3](https://utelle.github.io/wxsqlite3).</span></span> <span data-ttu-id="fd971-106">Tento článek ukazuje použití nepodporovaného Open Source sestavení SQLCipher, ale tyto informace platí i pro další řešení, protože obvykle řídí stejný vzor.</span><span class="sxs-lookup"><span data-stu-id="fd971-106">This article demonstrates using an unsupported, open-source build of SQLCipher, but the information also applies to other solutions since they generally follow the same pattern.</span></span>

## <a name="installation"></a><span data-ttu-id="fd971-107">Instalace služby</span><span class="sxs-lookup"><span data-stu-id="fd971-107">Installation</span></span>

### <a name="net-core-clitabnetcore-cli"></a>[<span data-ttu-id="fd971-108">Rozhraní příkazového řádku .NET Core</span><span class="sxs-lookup"><span data-stu-id="fd971-108">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet remove package Microsoft.Data.Sqlite
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studiotabvisual-studio"></a>[<span data-ttu-id="fd971-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fd971-109">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Remove-Package Microsoft.Data.Sqlite
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

<span data-ttu-id="fd971-110">Další informace o použití jiné nativní knihovny pro šifrování naleznete v tématu [Custom SQLite Versions](custom-versions.md).</span><span class="sxs-lookup"><span data-stu-id="fd971-110">For more information about using a different native library for encryption, see [Custom SQLite versions](custom-versions.md).</span></span>

## <a name="specify-the-key"></a><span data-ttu-id="fd971-111">Zadat klíč</span><span class="sxs-lookup"><span data-stu-id="fd971-111">Specify the key</span></span>

<span data-ttu-id="fd971-112">Pokud chcete povolit šifrování, zadejte klíč pomocí klíčového slova `Password` připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="fd971-112">To enable encryption, specify the key using the `Password` connection string keyword.</span></span> <span data-ttu-id="fd971-113">Pomocí <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> můžete přidat nebo aktualizovat hodnotu ze vstupu uživatele a vyhnout se útokům prostřednictvím injektáže připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="fd971-113">Use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> to add or update the value from user input and avoid connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="rekeying-the-database"></a><span data-ttu-id="fd971-114">Opětovné vytvoření klíče databáze</span><span class="sxs-lookup"><span data-stu-id="fd971-114">Rekeying the database</span></span>

<span data-ttu-id="fd971-115">Pokud chcete změnit šifrovací klíč databáze, vydejte příkaz `PRAGMA rekey`.</span><span class="sxs-lookup"><span data-stu-id="fd971-115">If you want to change the encryption key of a database, issue a `PRAGMA rekey` statement.</span></span> <span data-ttu-id="fd971-116">Chcete-li dešifrovat databázi, zadejte `NULL`.</span><span class="sxs-lookup"><span data-stu-id="fd971-116">To decrypt the database, specify `NULL`.</span></span>

<span data-ttu-id="fd971-117">SQLite nepodporuje parametry v příkazech `PRAGMA`.</span><span class="sxs-lookup"><span data-stu-id="fd971-117">Unfortunately, SQLite doesn't support parameters in `PRAGMA` statements.</span></span> <span data-ttu-id="fd971-118">Místo toho použijte funkci `quote()`, abyste zabránili injektáže SQL.</span><span class="sxs-lookup"><span data-stu-id="fd971-118">Instead, use the `quote()` function to prevent SQL injection.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_Rekey)]
