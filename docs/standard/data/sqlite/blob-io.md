---
title: I/O objektů BLOB
ms.date: 12/13/2019
description: Přečtěte si, jak používat funkci v/v objektu dataBlob SQLite.
ms.openlocfilehash: 0c133deacdc19684eca3a6724fb398dc01fda558
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447046"
---
# <a name="blob-io"></a><span data-ttu-id="354a8-103">I/O objektů BLOB</span><span class="sxs-lookup"><span data-stu-id="354a8-103">Blob I/O</span></span>

<span data-ttu-id="354a8-104">Můžete snížit využití paměti při čtení a psaní velkých objektů streamování dat do databáze a z ní.</span><span class="sxs-lookup"><span data-stu-id="354a8-104">You can reduce memory usage while reading and writing large objects by streaming the data into and out of the database.</span></span> <span data-ttu-id="354a8-105">To může být obzvláště užitečné při analýze nebo transformaci dat.</span><span class="sxs-lookup"><span data-stu-id="354a8-105">This can be especially useful when parsing or transforming the data.</span></span>

<span data-ttu-id="354a8-106">Začněte vložením řádku jako normálního.</span><span class="sxs-lookup"><span data-stu-id="354a8-106">Start by inserting a row as normal.</span></span> <span data-ttu-id="354a8-107">Použijte funkci `zeroblob()` SQL k přidělení místa v databázi pro uložení velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="354a8-107">Use the `zeroblob()` SQL function to allocate space in the database to hold the large object.</span></span> <span data-ttu-id="354a8-108">Funkce `last_insert_rowid()` poskytuje pohodlný způsob, jak získat své ROWID.</span><span class="sxs-lookup"><span data-stu-id="354a8-108">The `last_insert_rowid()` function provides a convenient way to get its rowid.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Insert)]

<span data-ttu-id="354a8-109">Po vložení řádku otevřete datový proud, který zapíše velký objekt pomocí <xref:Microsoft.Data.Sqlite.SqliteBlob>.</span><span class="sxs-lookup"><span data-stu-id="354a8-109">After inserting the row, open a stream to write the large object using <xref:Microsoft.Data.Sqlite.SqliteBlob>.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Write)]

<span data-ttu-id="354a8-110">Chcete-li datový proud z databáze streamovat, musíte vybrat ROWID nebo jeden z jeho aliasů, jak je znázorněno zde vedle sloupce rozsáhlých objektů.</span><span class="sxs-lookup"><span data-stu-id="354a8-110">To stream the large object out of the database, you must select the rowid or one of its aliases as show here in addition to the large object's column.</span></span> <span data-ttu-id="354a8-111">Pokud nevyberete ROWID, celý objekt se načte do paměti.</span><span class="sxs-lookup"><span data-stu-id="354a8-111">If you don't select the rowid, the entire object will be loaded into memory.</span></span> <span data-ttu-id="354a8-112">Objekt vrácený `GetStream()` bude `SqliteBlob` v případě správného provedení.</span><span class="sxs-lookup"><span data-stu-id="354a8-112">The object returned by `GetStream()` will be a `SqliteBlob` when done correctly.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Read)]
