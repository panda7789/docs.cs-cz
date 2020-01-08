---
title: Hromadné vložení
ms.date: 12/13/2019
description: Tipy ke zvýšení výkonu, které můžete použít při provádění mnoha změn v databázi.
ms.openlocfilehash: 9d87d5c8d70f8e70479f9aa02b7802f73b88de9e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447039"
---
# <a name="bulk-insert"></a><span data-ttu-id="3ce6a-103">Hromadné vložení</span><span class="sxs-lookup"><span data-stu-id="3ce6a-103">Bulk insert</span></span>

<span data-ttu-id="3ce6a-104">SQLite nemá žádný zvláštní způsob, jak hromadně vkládat data.</span><span class="sxs-lookup"><span data-stu-id="3ce6a-104">SQLite doesn't have any special way to bulk insert data.</span></span> <span data-ttu-id="3ce6a-105">Chcete-li dosáhnout optimálního výkonu při vkládání nebo aktualizaci dat, ujistěte se, že jste provedete následující akce:</span><span class="sxs-lookup"><span data-stu-id="3ce6a-105">To get optimal performance when inserting or updating data, ensure that you do the following:</span></span>

- <span data-ttu-id="3ce6a-106">Použijte transakci.</span><span class="sxs-lookup"><span data-stu-id="3ce6a-106">Use a transaction.</span></span>
- <span data-ttu-id="3ce6a-107">Opakované použití stejného parametrizovaného příkazu.</span><span class="sxs-lookup"><span data-stu-id="3ce6a-107">Reuse the same parameterized command.</span></span> <span data-ttu-id="3ce6a-108">Následná spuštění znovu použijí kompilaci prvního z nich.</span><span class="sxs-lookup"><span data-stu-id="3ce6a-108">Subsequent executions will reuse the compilation of the first one.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BulkInsertSample/Program.cs?name=snippet_BulkInsert)]
