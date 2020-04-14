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
# <a name="extensions"></a><span data-ttu-id="6a9e5-103">Rozšíření</span><span class="sxs-lookup"><span data-stu-id="6a9e5-103">Extensions</span></span>

<span data-ttu-id="6a9e5-104">SQLite podporuje načítání rozšíření za běhu.</span><span class="sxs-lookup"><span data-stu-id="6a9e5-104">SQLite supports loading extensions at run time.</span></span> <span data-ttu-id="6a9e5-105">Rozšíření zahrnují například další funkce SQL, kolace, virtuální tabulky a další.</span><span class="sxs-lookup"><span data-stu-id="6a9e5-105">Extensions include things like additional SQL functions, collations, virtual tables, and more.</span></span>

<span data-ttu-id="6a9e5-106">.NET Core obsahuje další logiku pro vyhledání nativních knihoven na dalších místech, jako jsou odkazované balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="6a9e5-106">.NET Core includes additional logic for locating native libraries in additional places like referenced NuGet packages.</span></span> <span data-ttu-id="6a9e5-107">Bohužel, SQLite nemůže využít tuto logiku; volá rozhraní API platformy přímo k načtení knihoven.</span><span class="sxs-lookup"><span data-stu-id="6a9e5-107">Unfortunately, SQLite can't leverage this logic; it calls the platform API directly to load libraries.</span></span> <span data-ttu-id="6a9e5-108">Z tohoto důvodu může být nutné upravit path, LD_LIBRARY_PATH nebo DYLD_LIBRARY_PATH proměnné prostředí před načtením rozšíření SQLite.</span><span class="sxs-lookup"><span data-stu-id="6a9e5-108">Because of this, you may need to modify the PATH, LD_LIBRARY_PATH, or DYLD_LIBRARY_PATH environment variables before loading SQLite extensions.</span></span> <span data-ttu-id="6a9e5-109">Existuje ukázka na [GitHubu,](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) která demonstruje hledání binárních souborů pro aktuální runtime uvnitř odkazované hobalíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="6a9e5-109">There's [a sample](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) on GitHub that demonstrates finding binaries for the current runtime inside a referenced NuGet package.</span></span>

<span data-ttu-id="6a9e5-110">Chcete-li načíst <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> rozšíření, zavolejte metodu.</span><span class="sxs-lookup"><span data-stu-id="6a9e5-110">To load an extension, call the <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> method.</span></span> <span data-ttu-id="6a9e5-111">Microsoft.Data.Sqlite zajistí, že rozšíření zůstane načteno i v případě, že je připojení uzavřeno a znovu otevřeno.</span><span class="sxs-lookup"><span data-stu-id="6a9e5-111">Microsoft.Data.Sqlite will ensure that the extension remains loaded even if the connection is closed and reopened.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

## <a name="see-also"></a><span data-ttu-id="6a9e5-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a9e5-112">See also</span></span>

* [<span data-ttu-id="6a9e5-113">Zaběhunatelná rozšíření</span><span class="sxs-lookup"><span data-stu-id="6a9e5-113">Run-Time Loadable Extensions</span></span>](https://www.sqlite.org/loadext.html)
