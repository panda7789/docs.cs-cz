---
title: Dávkování
ms.date: 12/13/2019
description: Naučte se, jak spustit dávku příkazů SQL v jednom příkazu.
ms.openlocfilehash: 0799784471520bb279db6a4b5879ad30945bdebb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447053"
---
# <a name="batching"></a><span data-ttu-id="c64cc-103">Dávkování</span><span class="sxs-lookup"><span data-stu-id="c64cc-103">Batching</span></span>

<span data-ttu-id="c64cc-104">SQLite nativně nepodporuje dávkování příkazů SQL společně do jednoho příkazu.</span><span class="sxs-lookup"><span data-stu-id="c64cc-104">SQLite doesn't natively support batching SQL statements together into a single command.</span></span> <span data-ttu-id="c64cc-105">Ale vzhledem k tomu, že není k dispozici žádná síť, by ve skutečnosti nedocházelo k jejich výkonu.</span><span class="sxs-lookup"><span data-stu-id="c64cc-105">But because there's no network involved, it wouldn't really help performance anyway.</span></span> <span data-ttu-id="c64cc-106">Microsoft. data. sqlite ale implementují dávkování příkazů jako pohodlí, aby se chovala podobně jako ostatní poskytovatelé ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="c64cc-106">Microsoft.Data.Sqlite does, however, implement statement batching as a convenience to make it behave more like other ADO.NET providers.</span></span>

<span data-ttu-id="c64cc-107">Při volání <xref:System.Data.Common.DbCommand.ExecuteReader%2A?displayProperty=nameWithType>jsou příkazy spouštěny až do prvního, který vrací výsledky.</span><span class="sxs-lookup"><span data-stu-id="c64cc-107">When calling <xref:System.Data.Common.DbCommand.ExecuteReader%2A?displayProperty=nameWithType>, statements are executed up to the first one that returns results.</span></span> <span data-ttu-id="c64cc-108">Volání <xref:System.Data.Common.DbDataReader.NextResult%2A?displayProperty=nameWithType> pokračuje ve spouštění příkazů až do další, který vrátí výsledky, nebo dokud nedosáhne konce dávky.</span><span class="sxs-lookup"><span data-stu-id="c64cc-108">Calling <xref:System.Data.Common.DbDataReader.NextResult%2A?displayProperty=nameWithType> continues executing statements until the next one that returns results or until it reaches the end of the batch.</span></span> <span data-ttu-id="c64cc-109">Volání <xref:System.Data.Common.DbDataReader.Dispose%2A?displayProperty=nameWithType> nebo <xref:System.Data.Common.DbDataReader.Close%2A> provádění všech zbývajících příkazů, které nebyly spotřebovány `NextResult()`.</span><span class="sxs-lookup"><span data-stu-id="c64cc-109">Calling <xref:System.Data.Common.DbDataReader.Dispose%2A?displayProperty=nameWithType> or <xref:System.Data.Common.DbDataReader.Close%2A> executes any remaining statements that haven't been consumed by `NextResult()`.</span></span> <span data-ttu-id="c64cc-110">Pokud neuvolníte čtečku dat, pokusí se finalizační metoda spustit zbývající příkazy, ale všechny chyby, které se vyskytnou, se ignorují.</span><span class="sxs-lookup"><span data-stu-id="c64cc-110">If you don't dispose a data reader, the finalizer tries to execute the remaining statements, but any errors it encounters are ignored.</span></span> <span data-ttu-id="c64cc-111">Z tohoto důvodu je důležité při použití dávek vyřadit `DbDataReader` objekty.</span><span class="sxs-lookup"><span data-stu-id="c64cc-111">Because of this, it's important to dispose `DbDataReader` objects when using batches.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BatchingSample/Program.cs?name=snippet_Batching)]

## <a name="see-also"></a><span data-ttu-id="c64cc-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="c64cc-112">See also</span></span>

* [<span data-ttu-id="c64cc-113">Hromadné vložení</span><span class="sxs-lookup"><span data-stu-id="c64cc-113">Bulk Insert</span></span>](bulk-insert.md)
