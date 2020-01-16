---
title: Rozšíření
ms.date: 12/13/2019
description: Přečtěte si, jak načíst rozšíření SQLite.
ms.openlocfilehash: a85b1227be4274dd20156d2475d6d2d68e250f99
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901299"
---
# <a name="extensions"></a><span data-ttu-id="7a452-103">Rozšíření</span><span class="sxs-lookup"><span data-stu-id="7a452-103">Extensions</span></span>

<span data-ttu-id="7a452-104">SQLite podporuje načítání rozšíření v době běhu.</span><span class="sxs-lookup"><span data-stu-id="7a452-104">SQLite supports loading extensions at run time.</span></span> <span data-ttu-id="7a452-105">Mezi přípony patří například další funkce SQL, kolace, virtuální tabulky a další.</span><span class="sxs-lookup"><span data-stu-id="7a452-105">Extensions include things like additional SQL functions, collations, virtual tables, and more.</span></span>

<span data-ttu-id="7a452-106">.NET Core zahrnuje další logiku pro vyhledání nativních knihoven na dalších místech, jako jsou odkazované balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="7a452-106">.NET Core includes additional logic for locating native libraries in additional places like referenced NuGet packages.</span></span> <span data-ttu-id="7a452-107">Omlouváme se, ale SQLite nemůže tuto logiku využít; volá rozhraní API platformy přímo k načtení knihoven.</span><span class="sxs-lookup"><span data-stu-id="7a452-107">Unfortunately, SQLite can't leverage this logic; it calls the platform API directly to load libraries.</span></span> <span data-ttu-id="7a452-108">Z tohoto důvodu může být nutné před načtením rozšíření SQLite změnit cestu, LD_LIBRARY_PATH nebo DYLD_LIBRARY_PATH proměnných prostředí.</span><span class="sxs-lookup"><span data-stu-id="7a452-108">Because of this, you may need to modify the PATH, LD_LIBRARY_PATH, or DYLD_LIBRARY_PATH environment variables before loading SQLite extensions.</span></span> <span data-ttu-id="7a452-109">Na GitHubu je [Ukázka](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) , která ukazuje nalezení binárních souborů pro aktuální modul runtime v rámci odkazovaného balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="7a452-109">There's [a sample](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) on GitHub that demonstrates finding binaries for the current runtime inside a referenced NuGet package.</span></span>

<span data-ttu-id="7a452-110">Chcete-li načíst rozšíření, zavolejte metodu <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A>.</span><span class="sxs-lookup"><span data-stu-id="7a452-110">To load an extension, call the <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> method.</span></span> <span data-ttu-id="7a452-111">Microsoft. data. sqlite zajistí, že rozšíření zůstane načteno i v případě, že je připojení zavřeno a znovu otevřeno.</span><span class="sxs-lookup"><span data-stu-id="7a452-111">Microsoft.Data.Sqlite will ensure that the extension remains loaded even if the connection is closed and reopened.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

## <a name="see-also"></a><span data-ttu-id="7a452-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7a452-112">See also</span></span>

* [<span data-ttu-id="7a452-113">Spustitelný rozšíření běhu</span><span class="sxs-lookup"><span data-stu-id="7a452-113">Run-Time Loadable Extensions</span></span>](https://www.sqlite.org/loadext.html)