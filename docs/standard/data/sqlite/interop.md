---
title: Interoperabilita
ms.date: 12/13/2019
description: Naučte se pracovat s ostatními knihovnami SQLite.
ms.openlocfilehash: 486e2a8e00999b8ebe9c85a5fcc1539c514676d3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447235"
---
# <a name="interoperability"></a><span data-ttu-id="e3a6d-103">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="e3a6d-103">Interoperability</span></span>

<span data-ttu-id="e3a6d-104">Microsoft. data. sqlite používá SQLitePCLRaw k interakci s nativní knihovnou SQLite.</span><span class="sxs-lookup"><span data-stu-id="e3a6d-104">Microsoft.Data.Sqlite uses SQLitePCLRaw to interact with the native SQLite library.</span></span> <span data-ttu-id="e3a6d-105">SQLitePCLRaw poskytuje dynamicky rozhraní .NET API přes nativní rozhraní API pro SQLite.</span><span class="sxs-lookup"><span data-stu-id="e3a6d-105">SQLitePCLRaw provides a thin .NET API over the native SQLite API.</span></span> <span data-ttu-id="e3a6d-106">SqliteConnection a SqliteDataReader poskytují přístup k podkladovým objektům SQLitePCLRaw, které vám umožní volat tato rozhraní API přímo.</span><span class="sxs-lookup"><span data-stu-id="e3a6d-106">SqliteConnection and SqliteDataReader provide access to the underlying SQLitePCLRaw objects letting you call these APIs directly.</span></span>

<span data-ttu-id="e3a6d-107">Následující příklad ukazuje, jak zavolat `sqlite3_trace` k zápisu provedených příkazů SQL do konzoly:</span><span class="sxs-lookup"><span data-stu-id="e3a6d-107">The following example shows how to call `sqlite3_trace` to write executed SQL statements to the console:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/InteropSample/Program.cs?name=snippet_Trace)]

<span data-ttu-id="e3a6d-108">A následující příklad ukazuje volání `sqlite3_stmt_status` pro zjištění, kolik kroků virtuálního počítače SQLite je ZKOMPILOVÁN příkaz SQL:</span><span class="sxs-lookup"><span data-stu-id="e3a6d-108">And the following example shows calling `sqlite3_stmt_status` to see how many SQLite virtual machine steps a SQL statement compiled into:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/InteropSample/Program.cs?name=snippet_StatementStatus)]

<span data-ttu-id="e3a6d-109">Objekty SQLitePCLRaw dokonce zveřejňují ukazatel na nativní objekty, které vám umožní P/Invoke dalších nativních rozhraních API SQLite.</span><span class="sxs-lookup"><span data-stu-id="e3a6d-109">The SQLitePCLRaw objects even expose a pointer to the native objects letting you P/Invoke additional native SQLite APIs.</span></span>
