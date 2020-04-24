---
title: Rozšíření
ms.date: 12/13/2019
description: Přečtěte si, jak načíst rozšíření SQLite.
ms.openlocfilehash: 51c705349c25240fe42e0edda8004a3e3b013ca3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242956"
---
# <a name="extensions"></a><span data-ttu-id="00735-103">Rozšíření</span><span class="sxs-lookup"><span data-stu-id="00735-103">Extensions</span></span>

<span data-ttu-id="00735-104">SQLite podporuje načítání rozšíření v době běhu.</span><span class="sxs-lookup"><span data-stu-id="00735-104">SQLite supports loading extensions at run time.</span></span> <span data-ttu-id="00735-105">Mezi přípony patří například další funkce SQL, kolace, virtuální tabulky a další.</span><span class="sxs-lookup"><span data-stu-id="00735-105">Extensions include things like additional SQL functions, collations, virtual tables, and more.</span></span>

<span data-ttu-id="00735-106">.NET Core zahrnuje další logiku pro vyhledání nativních knihoven na dalších místech, jako jsou odkazované balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="00735-106">.NET Core includes additional logic for locating native libraries in additional places like referenced NuGet packages.</span></span> <span data-ttu-id="00735-107">Omlouváme se, ale SQLite nemůže tuto logiku využít; volá rozhraní API platformy přímo k načtení knihoven.</span><span class="sxs-lookup"><span data-stu-id="00735-107">Unfortunately, SQLite can't leverage this logic; it calls the platform API directly to load libraries.</span></span> <span data-ttu-id="00735-108">Z tohoto důvodu může být nutné před načtením rozšíření SQLite změnit cestu, LD_LIBRARY_PATH nebo DYLD_LIBRARY_PATH proměnných prostředí.</span><span class="sxs-lookup"><span data-stu-id="00735-108">Because of this, you may need to modify the PATH, LD_LIBRARY_PATH, or DYLD_LIBRARY_PATH environment variables before loading SQLite extensions.</span></span> <span data-ttu-id="00735-109">Na GitHubu je [Ukázka](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) , která ukazuje nalezení binárních souborů pro aktuální modul runtime v rámci odkazovaného balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="00735-109">There's [a sample](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) on GitHub that demonstrates finding binaries for the current runtime inside a referenced NuGet package.</span></span>

<span data-ttu-id="00735-110">Chcete-li načíst rozšíření, zavolejte <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="00735-110">To load an extension, call the <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> method.</span></span> <span data-ttu-id="00735-111">Microsoft. data. sqlite zajistí, že rozšíření zůstane načteno i v případě, že je připojení zavřeno a znovu otevřeno.</span><span class="sxs-lookup"><span data-stu-id="00735-111">Microsoft.Data.Sqlite will ensure that the extension remains loaded even if the connection is closed and reopened.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

## <a name="see-also"></a><span data-ttu-id="00735-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="00735-112">See also</span></span>

* [<span data-ttu-id="00735-113">Spustitelný rozšíření běhu</span><span class="sxs-lookup"><span data-stu-id="00735-113">Run-Time Loadable Extensions</span></span>](https://www.sqlite.org/loadext.html)
