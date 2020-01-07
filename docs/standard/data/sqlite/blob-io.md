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
# <a name="blob-io"></a>I/O objektů BLOB

Můžete snížit využití paměti při čtení a psaní velkých objektů streamování dat do databáze a z ní. To může být obzvláště užitečné při analýze nebo transformaci dat.

Začněte vložením řádku jako normálního. Použijte funkci `zeroblob()` SQL k přidělení místa v databázi pro uložení velkého objektu. Funkce `last_insert_rowid()` poskytuje pohodlný způsob, jak získat své ROWID.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Insert)]

Po vložení řádku otevřete datový proud, který zapíše velký objekt pomocí <xref:Microsoft.Data.Sqlite.SqliteBlob>.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Write)]

Chcete-li datový proud z databáze streamovat, musíte vybrat ROWID nebo jeden z jeho aliasů, jak je znázorněno zde vedle sloupce rozsáhlých objektů. Pokud nevyberete ROWID, celý objekt se načte do paměti. Objekt vrácený `GetStream()` bude `SqliteBlob` v případě správného provedení.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Read)]
