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
# <a name="transactions"></a><span data-ttu-id="9ba06-103">Transakce</span><span class="sxs-lookup"><span data-stu-id="9ba06-103">Transactions</span></span>

<span data-ttu-id="9ba06-104">Transakce umožňují seskupit více příkazů SQL do jedné pracovní jednotky, která je potvrzena do databáze jako jedna atomická jednotka.</span><span class="sxs-lookup"><span data-stu-id="9ba06-104">Transactions let you group multiple SQL statements into a single unit of work that is committed to the database as one atomic unit.</span></span> <span data-ttu-id="9ba06-105">Pokud některý příkaz v transakci neuspěje, změny provedené v předchozích příkazech se dají vrátit zpátky.</span><span class="sxs-lookup"><span data-stu-id="9ba06-105">If any statement in the transaction fails, changes made by the previous statements can be rolled back.</span></span> <span data-ttu-id="9ba06-106">Počáteční stav databáze při spuštění transakce se zachová.</span><span class="sxs-lookup"><span data-stu-id="9ba06-106">The initial state of the database when the transaction was started is preserved.</span></span> <span data-ttu-id="9ba06-107">Použití transakce může také zvýšit výkon SQLite při provádění velkého množství změn databáze najednou.</span><span class="sxs-lookup"><span data-stu-id="9ba06-107">Using a transaction can also improve performance on SQLite when making numerous changes to the database at once.</span></span>

## <a name="concurrency"></a><span data-ttu-id="9ba06-108">Souběžnost</span><span class="sxs-lookup"><span data-stu-id="9ba06-108">Concurrency</span></span>

<span data-ttu-id="9ba06-109">V rámci SQLite může mít v databázi v okamžiku, že změny čekají na více než jednu transakci.</span><span class="sxs-lookup"><span data-stu-id="9ba06-109">In SQLite, only one transaction is allowed to have changes pending in the database at a time.</span></span> <span data-ttu-id="9ba06-110">Z tohoto důvodu volání <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> a `Execute` metody, které mohou být <xref:Microsoft.Data.Sqlite.SqliteCommand> vyvolány v případě, že dokončení jiné transakce trvá příliš dlouho.</span><span class="sxs-lookup"><span data-stu-id="9ba06-110">Because of this, calls to <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> and the `Execute` methods on <xref:Microsoft.Data.Sqlite.SqliteCommand> may time out if another transaction takes too long to complete.</span></span>

<span data-ttu-id="9ba06-111">Další informace o uzamykání, opakování a vypršení časových limitů najdete v tématu [chyby databáze](database-errors.md).</span><span class="sxs-lookup"><span data-stu-id="9ba06-111">For more information about locking, retries, and timeouts, see [Database errors](database-errors.md).</span></span>

## <a name="isolation-levels"></a><span data-ttu-id="9ba06-112">Úrovně izolace</span><span class="sxs-lookup"><span data-stu-id="9ba06-112">Isolation levels</span></span>

<span data-ttu-id="9ba06-113">Transakce jsou v SQLite ve výchozím nastavení **serializovatelné** .</span><span class="sxs-lookup"><span data-stu-id="9ba06-113">Transactions are **serializable** by default in SQLite.</span></span> <span data-ttu-id="9ba06-114">Tato úroveň izolace zaručuje, že všechny změny provedené v transakci jsou zcela izolované.</span><span class="sxs-lookup"><span data-stu-id="9ba06-114">This isolation level guarantees that any changes made within a transaction are completely isolated.</span></span> <span data-ttu-id="9ba06-115">Jiné příkazy provedené mimo transakci nejsou ovlivněny změnami transakce.</span><span class="sxs-lookup"><span data-stu-id="9ba06-115">Other statements executed outside of the transaction aren't affected by the transaction's changes.</span></span>

<span data-ttu-id="9ba06-116">SQLite také podporuje **čtení nepotvrzené** při použití sdílené mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="9ba06-116">SQLite also supports **read uncommitted** when using a shared cache.</span></span> <span data-ttu-id="9ba06-117">Tato úroveň umožňuje nečisté čtení, neopakující čtení a fiktivní:</span><span class="sxs-lookup"><span data-stu-id="9ba06-117">This level allows dirty reads, nonrepeatable reads, and phantoms:</span></span>

- <span data-ttu-id="9ba06-118">K nevyřešenému *čtení* dojde, pokud jsou změny, které čekají v jedné transakci, vráceny dotazem mimo transakci, ale změny v transakci jsou vráceny zpět.</span><span class="sxs-lookup"><span data-stu-id="9ba06-118">A *dirty read* occurs when changes pending in one transaction are returned by a query outside of the transaction, but the changes in the transaction are rolled back.</span></span> <span data-ttu-id="9ba06-119">Výsledky obsahují data, která se ve skutečnosti nikdy netvrdila do databáze.</span><span class="sxs-lookup"><span data-stu-id="9ba06-119">The results contain data that was never actually committed to the database.</span></span>

- <span data-ttu-id="9ba06-120">K *neopakovanému čtení* dojde, pokud transakce dotazuje stejný řádek dvakrát, ale výsledky se liší, protože došlo ke změně mezi dvěma dotazy jiné transakce.</span><span class="sxs-lookup"><span data-stu-id="9ba06-120">A *nonrepeatable read* occurs when a transaction queries same row twice, but the results are different because it was changed between the two queries by another transaction.</span></span>

- <span data-ttu-id="9ba06-121">*Fantom* jsou řádky, které se změní nebo přidají pro splnění klauzule WHERE dotazu během transakce.</span><span class="sxs-lookup"><span data-stu-id="9ba06-121">*Phantoms* are rows that get changed or added to meet the where clause of a query during a transaction.</span></span> <span data-ttu-id="9ba06-122">Pokud je povoleno, může stejný dotaz vracet jiné řádky při spuštění dvakrát ve stejné transakci.</span><span class="sxs-lookup"><span data-stu-id="9ba06-122">If allowed, the same query could return different rows when executed twice in the same transaction.</span></span>

<span data-ttu-id="9ba06-123">Microsoft. data. sqlite zpracovává IsolationLevel předaný do <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> jako minimální úroveň.</span><span class="sxs-lookup"><span data-stu-id="9ba06-123">Microsoft.Data.Sqlite treats the IsolationLevel passed to <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> as a minimum level.</span></span> <span data-ttu-id="9ba06-124">Skutečná úroveň izolace bude povýšena buď na hodnotu číst nepotvrzeno nebo serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="9ba06-124">The actual isolation level will be promoted to either read uncommitted or serializable.</span></span>

<span data-ttu-id="9ba06-125">Následující kód simuluje nepřečtené čtení.</span><span class="sxs-lookup"><span data-stu-id="9ba06-125">The following code simulates a dirty read.</span></span> <span data-ttu-id="9ba06-126">Všimněte si, že připojovací řetězec musí `Cache=Shared`obsahovat.</span><span class="sxs-lookup"><span data-stu-id="9ba06-126">Note, the connection string must include `Cache=Shared`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DirtyReadSample/Program.cs?name=snippet_DirtyRead)]
