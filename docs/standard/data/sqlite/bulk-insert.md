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
# <a name="bulk-insert"></a>Hromadné vložení

SQLite nemá žádný zvláštní způsob, jak hromadně vkládat data. Chcete-li dosáhnout optimálního výkonu při vkládání nebo aktualizaci dat, ujistěte se, že jste provedete následující akce:

- Použijte transakci.
- Opakované použití stejného parametrizovaného příkazu. Následná spuštění znovu použijí kompilaci prvního z nich.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BulkInsertSample/Program.cs?name=snippet_BulkInsert)]
