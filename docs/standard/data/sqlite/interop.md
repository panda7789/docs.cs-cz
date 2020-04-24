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
# <a name="interoperability"></a>Interoperabilita

Microsoft. data. sqlite používá SQLitePCLRaw k interakci s nativní knihovnou SQLite. SQLitePCLRaw poskytuje dynamicky rozhraní .NET API přes nativní rozhraní API pro SQLite. SqliteConnection a SqliteDataReader poskytují přístup k podkladovým objektům SQLitePCLRaw, které vám umožní volat tato rozhraní API přímo.

Následující příklad ukazuje, jak zavolat `sqlite3_trace` k zápisu provedených příkazů SQL do konzoly:

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/InteropSample/Program.cs?name=snippet_Trace)]

A následující příklad ukazuje volání `sqlite3_stmt_status` pro zjištění, kolik kroků virtuálního počítače SQLite je ZKOMPILOVÁN příkaz SQL:

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/InteropSample/Program.cs?name=snippet_StatementStatus)]

Objekty SQLitePCLRaw dokonce zveřejňují ukazatel na nativní objekty, které vám umožní P/Invoke dalších nativních rozhraních API SQLite.
