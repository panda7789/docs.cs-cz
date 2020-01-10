---
title: Kolace
ms.date: 12/13/2019
description: Naučte se vytvořit vlastní sekvenci seřazení.
ms.openlocfilehash: 9cc574a75c8f5347dd9bb44e36af72e50afa57b4
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777386"
---
# <a name="collation"></a><span data-ttu-id="7ef64-103">Kolace</span><span class="sxs-lookup"><span data-stu-id="7ef64-103">Collation</span></span>

<span data-ttu-id="7ef64-104">Při porovnávání textových hodnot s určením pořadí a rovnosti používá SQLite sekvence.</span><span class="sxs-lookup"><span data-stu-id="7ef64-104">Collating sequences are used by SQLite when comparing TEXT values to determine order and equality.</span></span> <span data-ttu-id="7ef64-105">Můžete určit, kterou kolaci použít při vytváření sloupců nebo operací v dotazech SQL.</span><span class="sxs-lookup"><span data-stu-id="7ef64-105">You can specify which collation to use when creating columns or per-operation in SQL queries.</span></span> <span data-ttu-id="7ef64-106">SQLite obsahuje tři sekvence řazení ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="7ef64-106">SQLite includes three collating sequences by default.</span></span>

| <span data-ttu-id="7ef64-107">Kolace</span><span class="sxs-lookup"><span data-stu-id="7ef64-107">Collation</span></span> | <span data-ttu-id="7ef64-108">Popis</span><span class="sxs-lookup"><span data-stu-id="7ef64-108">Description</span></span>                               |
| --------- | ----------------------------------------- |
| <span data-ttu-id="7ef64-109">RTRIM</span><span class="sxs-lookup"><span data-stu-id="7ef64-109">RTRIM</span></span>     | <span data-ttu-id="7ef64-110">Ignoruje koncovou mezeru.</span><span class="sxs-lookup"><span data-stu-id="7ef64-110">Ignores trailing whitespace</span></span>               |
| <span data-ttu-id="7ef64-111">BEZPŘÍPADU</span><span class="sxs-lookup"><span data-stu-id="7ef64-111">NOCASE</span></span>    | <span data-ttu-id="7ef64-112">Nerozlišuje velká a malá písmena pro znaky ASCII A – Z</span><span class="sxs-lookup"><span data-stu-id="7ef64-112">Case-insensitive for ASCII characters A-Z</span></span> |
| <span data-ttu-id="7ef64-113">TVARU</span><span class="sxs-lookup"><span data-stu-id="7ef64-113">BINARY</span></span>    | <span data-ttu-id="7ef64-114">Rozlišuje velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="7ef64-114">Case-sensitive.</span></span> <span data-ttu-id="7ef64-115">Porovná bajty přímo</span><span class="sxs-lookup"><span data-stu-id="7ef64-115">Compares bytes directly</span></span>   |

## <a name="custom-collation"></a><span data-ttu-id="7ef64-116">Vlastní kolace</span><span class="sxs-lookup"><span data-stu-id="7ef64-116">Custom collation</span></span>

<span data-ttu-id="7ef64-117">Můžete také definovat vlastní řadicí sekvence nebo přepsat vestavěné objekty pomocí <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span><span class="sxs-lookup"><span data-stu-id="7ef64-117">You can also define your own collating sequences or override the built-in ones using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span></span> <span data-ttu-id="7ef64-118">Následující příklad ukazuje, jak přepsat kolaci případu pro podporu znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="7ef64-118">The following example shows overriding the NOCASE collation to support Unicode characters.</span></span> <span data-ttu-id="7ef64-119">[Úplný ukázkový kód](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/CollationSample/Program.cs) je k dispozici na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="7ef64-119">The [full sample code](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/CollationSample/Program.cs) is available on GitHub.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a><span data-ttu-id="7ef64-120">Like – operátor</span><span class="sxs-lookup"><span data-stu-id="7ef64-120">Like operator</span></span>

<span data-ttu-id="7ef64-121">Operátor LIKE v SQLite nedodržuje kolace.</span><span class="sxs-lookup"><span data-stu-id="7ef64-121">The LIKE operator in SQLite doesn't honor collations.</span></span> <span data-ttu-id="7ef64-122">Výchozí implementace má stejnou sémantiku jako řazení v případě případu.</span><span class="sxs-lookup"><span data-stu-id="7ef64-122">The default implementation has the same semantics as the NOCASE collation.</span></span> <span data-ttu-id="7ef64-123">Rozlišuje velká a malá písmena pro znaky ASCII A až Z.</span><span class="sxs-lookup"><span data-stu-id="7ef64-123">It's only case-insensitive for the ASCII characters A through Z.</span></span>

<span data-ttu-id="7ef64-124">Pomocí následujícího příkazu pragma můžete snadno vytvořit rozlišování velkých a malých písmen jako operátor:</span><span class="sxs-lookup"><span data-stu-id="7ef64-124">You can easily make the LIKE operator case-sensitive by using the following pragma statement:</span></span>

```sql
PRAGMA case_sensitive_like = 0
```

<span data-ttu-id="7ef64-125">Podrobnosti o přepsání implementace operátoru LIKE najdete v tématu [uživatelsky definované funkce](user-defined-functions.md) .</span><span class="sxs-lookup"><span data-stu-id="7ef64-125">See [User-defined functions](user-defined-functions.md) for details on overriding the implementation of the LIKE operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ef64-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ef64-126">See also</span></span>

* [<span data-ttu-id="7ef64-127">Uživatelsky definované funkce</span><span class="sxs-lookup"><span data-stu-id="7ef64-127">User-defined functions</span></span>](user-defined-functions.md)
* [<span data-ttu-id="7ef64-128">Syntaxe SQL</span><span class="sxs-lookup"><span data-stu-id="7ef64-128">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
