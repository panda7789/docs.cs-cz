---
title: Kolace
ms.date: 12/13/2019
description: Naučte se vytvořit vlastní sekvenci seřazení.
ms.openlocfilehash: 9879846cc191a62c4cb47a0fbaa47c59153ba61c
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242969"
---
# <a name="collation"></a><span data-ttu-id="17074-103">Kolace</span><span class="sxs-lookup"><span data-stu-id="17074-103">Collation</span></span>

<span data-ttu-id="17074-104">Při porovnávání textových hodnot s určením pořadí a rovnosti používá SQLite sekvence.</span><span class="sxs-lookup"><span data-stu-id="17074-104">Collating sequences are used by SQLite when comparing TEXT values to determine order and equality.</span></span> <span data-ttu-id="17074-105">Můžete určit, kterou kolaci použít při vytváření sloupců nebo operací v dotazech SQL.</span><span class="sxs-lookup"><span data-stu-id="17074-105">You can specify which collation to use when creating columns or per-operation in SQL queries.</span></span> <span data-ttu-id="17074-106">SQLite obsahuje tři sekvence řazení ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="17074-106">SQLite includes three collating sequences by default.</span></span>

| <span data-ttu-id="17074-107">Kolace</span><span class="sxs-lookup"><span data-stu-id="17074-107">Collation</span></span> | <span data-ttu-id="17074-108">Popis</span><span class="sxs-lookup"><span data-stu-id="17074-108">Description</span></span>                               |
| --------- | ----------------------------------------- |
| <span data-ttu-id="17074-109">RTRIM</span><span class="sxs-lookup"><span data-stu-id="17074-109">RTRIM</span></span>     | <span data-ttu-id="17074-110">Ignoruje koncovou mezeru.</span><span class="sxs-lookup"><span data-stu-id="17074-110">Ignores trailing whitespace</span></span>               |
| <span data-ttu-id="17074-111">BEZPŘÍPADU</span><span class="sxs-lookup"><span data-stu-id="17074-111">NOCASE</span></span>    | <span data-ttu-id="17074-112">Nerozlišuje velká a malá písmena pro znaky ASCII A – Z</span><span class="sxs-lookup"><span data-stu-id="17074-112">Case-insensitive for ASCII characters A-Z</span></span> |
| <span data-ttu-id="17074-113">TVARU</span><span class="sxs-lookup"><span data-stu-id="17074-113">BINARY</span></span>    | <span data-ttu-id="17074-114">Rozlišuje velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="17074-114">Case-sensitive.</span></span> <span data-ttu-id="17074-115">Porovná bajty přímo</span><span class="sxs-lookup"><span data-stu-id="17074-115">Compares bytes directly</span></span>   |

## <a name="custom-collation"></a><span data-ttu-id="17074-116">Vlastní kolace</span><span class="sxs-lookup"><span data-stu-id="17074-116">Custom collation</span></span>

<span data-ttu-id="17074-117">Můžete také definovat vlastní pořadí kompletování nebo přepsat předdefinované pomocí <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span><span class="sxs-lookup"><span data-stu-id="17074-117">You can also define your own collating sequences or override the built-in ones using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span></span> <span data-ttu-id="17074-118">Následující příklad ukazuje, jak přepsat kolaci případu pro podporu znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="17074-118">The following example shows overriding the NOCASE collation to support Unicode characters.</span></span> <span data-ttu-id="17074-119">[Úplný ukázkový kód](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) je k dispozici na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="17074-119">The [full sample code](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) is available on GitHub.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a><span data-ttu-id="17074-120">Like – operátor</span><span class="sxs-lookup"><span data-stu-id="17074-120">Like operator</span></span>

<span data-ttu-id="17074-121">Operátor LIKE v SQLite nedodržuje kolace.</span><span class="sxs-lookup"><span data-stu-id="17074-121">The LIKE operator in SQLite doesn't honor collations.</span></span> <span data-ttu-id="17074-122">Výchozí implementace má stejnou sémantiku jako řazení v případě případu.</span><span class="sxs-lookup"><span data-stu-id="17074-122">The default implementation has the same semantics as the NOCASE collation.</span></span> <span data-ttu-id="17074-123">Rozlišuje velká a malá písmena pro znaky ASCII A až Z.</span><span class="sxs-lookup"><span data-stu-id="17074-123">It's only case-insensitive for the ASCII characters A through Z.</span></span>

<span data-ttu-id="17074-124">Pomocí následujícího příkazu pragma můžete snadno vytvořit rozlišování velkých a malých písmen jako operátor:</span><span class="sxs-lookup"><span data-stu-id="17074-124">You can easily make the LIKE operator case-sensitive by using the following pragma statement:</span></span>

```sql
PRAGMA case_sensitive_like = 1
```

<span data-ttu-id="17074-125">Podrobnosti o přepsání implementace operátoru LIKE najdete v tématu [uživatelsky definované funkce](user-defined-functions.md) .</span><span class="sxs-lookup"><span data-stu-id="17074-125">See [User-defined functions](user-defined-functions.md) for details on overriding the implementation of the LIKE operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="17074-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="17074-126">See also</span></span>

* [<span data-ttu-id="17074-127">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="17074-127">User-defined functions</span></span>](user-defined-functions.md)
* [<span data-ttu-id="17074-128">Syntaxe SQL</span><span class="sxs-lookup"><span data-stu-id="17074-128">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
