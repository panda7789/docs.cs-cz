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
# <a name="batching"></a>Dávkování

SQLite nativně nepodporuje dávkování příkazů SQL společně do jednoho příkazu. Ale vzhledem k tomu, že není k dispozici žádná síť, by ve skutečnosti nedocházelo k jejich výkonu. Microsoft. data. sqlite ale implementují dávkování příkazů jako pohodlí, aby se chovala podobně jako ostatní poskytovatelé ADO.NET.

Při volání <xref:System.Data.Common.DbCommand.ExecuteReader%2A?displayProperty=nameWithType>jsou příkazy spouštěny až do prvního, který vrací výsledky. Volání <xref:System.Data.Common.DbDataReader.NextResult%2A?displayProperty=nameWithType> pokračuje ve spouštění příkazů až do další, který vrátí výsledky, nebo dokud nedosáhne konce dávky. Volání <xref:System.Data.Common.DbDataReader.Dispose%2A?displayProperty=nameWithType> nebo <xref:System.Data.Common.DbDataReader.Close%2A> provádí všechny zbývající příkazy, které nebyly využívány `NextResult()`. Pokud neuvolníte čtečku dat, pokusí se finalizační metoda spustit zbývající příkazy, ale všechny chyby, které se vyskytnou, se ignorují. Z tohoto důvodu je důležité při použití dávek vyřadit `DbDataReader` objekty.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BatchingSample/Program.cs?name=snippet_Batching)]

## <a name="see-also"></a>Viz také:

* [Hromadné vložení](bulk-insert.md)
