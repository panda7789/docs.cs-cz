---
title: Transakce
ms.date: 12/13/2019
description: Naučte se používat transakce.
ms.openlocfilehash: 4b72a1573a560ffd1bfd0f54d46ab3b135280976
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447137"
---
# <a name="transactions"></a>Transakce

Transakce umožňují seskupit více příkazů SQL do jedné pracovní jednotky, která je potvrzena do databáze jako jedna atomická jednotka. Pokud některý příkaz v transakci neuspěje, změny provedené v předchozích příkazech se dají vrátit zpátky. Počáteční stav databáze při spuštění transakce se zachová. Použití transakce může také zvýšit výkon SQLite při provádění velkého množství změn databáze najednou.

## <a name="concurrency"></a>Souběžnost

V rámci SQLite může mít v databázi v okamžiku, že změny čekají na více než jednu transakci. Z tohoto důvodu volání <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> a `Execute` metody na <xref:Microsoft.Data.Sqlite.SqliteCommand> mohou vyprší časový limit, pokud dokončení jiné transakce trvá příliš dlouho.

Další informace o uzamykání, opakování a vypršení časových limitů najdete v tématu [chyby databáze](database-errors.md).

## <a name="isolation-levels"></a>Úrovně izolace

Transakce jsou v SQLite ve výchozím nastavení **serializovatelné** . Tato úroveň izolace zaručuje, že všechny změny provedené v transakci jsou zcela izolované. Jiné příkazy provedené mimo transakci nejsou ovlivněny změnami transakce.

SQLite také podporuje **čtení nepotvrzené** při použití sdílené mezipaměti. Tato úroveň umožňuje nečisté čtení, neopakující čtení a fiktivní:

- K nevyřešenému *čtení* dojde, pokud jsou změny, které čekají v jedné transakci, vráceny dotazem mimo transakci, ale změny v transakci jsou vráceny zpět. Výsledky obsahují data, která se ve skutečnosti nikdy netvrdila do databáze.

- K *neopakovanému čtení* dojde, pokud transakce dotazuje stejný řádek dvakrát, ale výsledky se liší, protože došlo ke změně mezi dvěma dotazy jiné transakce.

- *Fantom* jsou řádky, které se změní nebo přidají pro splnění klauzule WHERE dotazu během transakce. Pokud je povoleno, může stejný dotaz vracet jiné řádky při spuštění dvakrát ve stejné transakci.

Microsoft. data. sqlite zpracovává IsolationLevel předaný do <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> jako minimální úroveň. Skutečná úroveň izolace bude povýšena buď na hodnotu číst nepotvrzeno nebo serializovatelný.

Následující kód simuluje nepřečtené čtení. Všimněte si, že připojovací řetězec musí zahrnovat `Cache=Shared`.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DirtyReadSample/Program.cs?name=snippet_DirtyRead)]
