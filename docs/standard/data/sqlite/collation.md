---
title: Kolace
ms.date: 12/13/2019
description: Přečtěte si, jak vytvořit vlastní posloupnost řazení.
ms.openlocfilehash: 9879846cc191a62c4cb47a0fbaa47c59153ba61c
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242969"
---
# <a name="collation"></a><span data-ttu-id="224ef-103">Kolace</span><span class="sxs-lookup"><span data-stu-id="224ef-103">Collation</span></span>

<span data-ttu-id="224ef-104">Kompletování sekvence jsou používány SQLite při porovnávání text hodnoty k určení pořadí a rovnosti.</span><span class="sxs-lookup"><span data-stu-id="224ef-104">Collating sequences are used by SQLite when comparing TEXT values to determine order and equality.</span></span> <span data-ttu-id="224ef-105">Můžete určit, které řazení se má použít při vytváření sloupců nebo operací v dotazech SQL.</span><span class="sxs-lookup"><span data-stu-id="224ef-105">You can specify which collation to use when creating columns or per-operation in SQL queries.</span></span> <span data-ttu-id="224ef-106">SQLite obsahuje ve výchozím nastavení tři kompletační sekvence.</span><span class="sxs-lookup"><span data-stu-id="224ef-106">SQLite includes three collating sequences by default.</span></span>

| <span data-ttu-id="224ef-107">Kolace</span><span class="sxs-lookup"><span data-stu-id="224ef-107">Collation</span></span> | <span data-ttu-id="224ef-108">Popis</span><span class="sxs-lookup"><span data-stu-id="224ef-108">Description</span></span>                               |
| --------- | ----------------------------------------- |
| <span data-ttu-id="224ef-109">RTRIM</span><span class="sxs-lookup"><span data-stu-id="224ef-109">RTRIM</span></span>     | <span data-ttu-id="224ef-110">Ignoruje koncové prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="224ef-110">Ignores trailing whitespace</span></span>               |
| <span data-ttu-id="224ef-111">ŽÁDNÝ PŘÍPAD</span><span class="sxs-lookup"><span data-stu-id="224ef-111">NOCASE</span></span>    | <span data-ttu-id="224ef-112">Necitlivé malá a velká písmena pro znaky ASCII A-Z</span><span class="sxs-lookup"><span data-stu-id="224ef-112">Case-insensitive for ASCII characters A-Z</span></span> |
| <span data-ttu-id="224ef-113">Binární</span><span class="sxs-lookup"><span data-stu-id="224ef-113">BINARY</span></span>    | <span data-ttu-id="224ef-114">Case-sensitive.</span><span class="sxs-lookup"><span data-stu-id="224ef-114">Case-sensitive.</span></span> <span data-ttu-id="224ef-115">Porovnává přímo bajty</span><span class="sxs-lookup"><span data-stu-id="224ef-115">Compares bytes directly</span></span>   |

## <a name="custom-collation"></a><span data-ttu-id="224ef-116">Vlastní řazení</span><span class="sxs-lookup"><span data-stu-id="224ef-116">Custom collation</span></span>

<span data-ttu-id="224ef-117">Můžete také definovat vlastní řazení sekvence nebo přepsat vestavěné ty <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>pomocí .</span><span class="sxs-lookup"><span data-stu-id="224ef-117">You can also define your own collating sequences or override the built-in ones using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span></span> <span data-ttu-id="224ef-118">Následující příklad ukazuje přepsání nocase řazení pro podporu znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="224ef-118">The following example shows overriding the NOCASE collation to support Unicode characters.</span></span> <span data-ttu-id="224ef-119">[Úplný ukázkový kód](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) je k dispozici na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="224ef-119">The [full sample code](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) is available on GitHub.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a><span data-ttu-id="224ef-120">Stejně jako operátor</span><span class="sxs-lookup"><span data-stu-id="224ef-120">Like operator</span></span>

<span data-ttu-id="224ef-121">Operátor LIKE v SQLite nectí kolace.</span><span class="sxs-lookup"><span data-stu-id="224ef-121">The LIKE operator in SQLite doesn't honor collations.</span></span> <span data-ttu-id="224ef-122">Výchozí implementace má stejnou sémantiku jako kolace NOCASE.</span><span class="sxs-lookup"><span data-stu-id="224ef-122">The default implementation has the same semantics as the NOCASE collation.</span></span> <span data-ttu-id="224ef-123">Je pouze malá a velká písmena pro znaky ASCII A až Z.</span><span class="sxs-lookup"><span data-stu-id="224ef-123">It's only case-insensitive for the ASCII characters A through Z.</span></span>

<span data-ttu-id="224ef-124">Můžete snadno provést operátor like rozlišování velkých a malých písmen pomocí následujícího příkazu pragma:</span><span class="sxs-lookup"><span data-stu-id="224ef-124">You can easily make the LIKE operator case-sensitive by using the following pragma statement:</span></span>

```sql
PRAGMA case_sensitive_like = 1
```

<span data-ttu-id="224ef-125">Viz [Uživatelem definované funkce](user-defined-functions.md) podrobnosti o přepsání implementace operátoru LIKE.</span><span class="sxs-lookup"><span data-stu-id="224ef-125">See [User-defined functions](user-defined-functions.md) for details on overriding the implementation of the LIKE operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="224ef-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="224ef-126">See also</span></span>

* [<span data-ttu-id="224ef-127">Uživatelsky definované funkce</span><span class="sxs-lookup"><span data-stu-id="224ef-127">User-defined functions</span></span>](user-defined-functions.md)
* [<span data-ttu-id="224ef-128">Syntaxe SQL</span><span class="sxs-lookup"><span data-stu-id="224ef-128">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
