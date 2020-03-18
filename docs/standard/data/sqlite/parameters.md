---
title: Parametry
ms.date: 12/13/2019
description: Přečtěte si, jak používat parametry SQL.
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400454"
---
# <a name="parameters"></a><span data-ttu-id="cf0f7-103">Parametry</span><span class="sxs-lookup"><span data-stu-id="cf0f7-103">Parameters</span></span>

<span data-ttu-id="cf0f7-104">Parametry se používají k ochraně proti útokům injektáže SQL.</span><span class="sxs-lookup"><span data-stu-id="cf0f7-104">Parameters are used to protect against SQL injection attacks.</span></span> <span data-ttu-id="cf0f7-105">Místo zřetězení vstupu uživatele s příkazy SQL použijte parametry, abyste zajistili, že vstup je vždy považován pouze za literálovou hodnotu a nikdy nebyl proveden.</span><span class="sxs-lookup"><span data-stu-id="cf0f7-105">Instead of concatenating user input with SQL statements, use parameters to ensure input is only ever treated as a literal value and never executed.</span></span> <span data-ttu-id="cf0f7-106">V SQLite parametry jsou obvykle povoleny kdekoli literál je povoleno v příkazech SQL.</span><span class="sxs-lookup"><span data-stu-id="cf0f7-106">In SQLite, parameters are typically allowed anywhere a literal is allowed in SQL statements.</span></span>

<span data-ttu-id="cf0f7-107">Parametry mohou být předponou buď `:`, `@`nebo `$`.</span><span class="sxs-lookup"><span data-stu-id="cf0f7-107">Parameters can be prefixed with either `:`, `@`, or `$`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

<span data-ttu-id="cf0f7-108">Podrobnosti o tom, jak jsou hodnoty .NET mapovány na hodnoty SQLite, najdete v tématu [Datové typy.](types.md)</span><span class="sxs-lookup"><span data-stu-id="cf0f7-108">See [Data types](types.md) for details about how .NET values are mapped to SQLite values.</span></span>

## <a name="truncation"></a><span data-ttu-id="cf0f7-109">Zkrácení</span><span class="sxs-lookup"><span data-stu-id="cf0f7-109">Truncation</span></span>

<span data-ttu-id="cf0f7-110">Pomocí <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> vlastnosti můžete zkrátit hodnoty TEXT a BLOB.</span><span class="sxs-lookup"><span data-stu-id="cf0f7-110">Use the <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> property to truncate TEXT and BLOB values.</span></span>

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a><span data-ttu-id="cf0f7-111">Alternativní typy</span><span class="sxs-lookup"><span data-stu-id="cf0f7-111">Alternative types</span></span>

<span data-ttu-id="cf0f7-112">Někdy můžete chtít použít alternativní typ SQLite.</span><span class="sxs-lookup"><span data-stu-id="cf0f7-112">Sometimes, you may want to use an alternative SQLite type.</span></span> <span data-ttu-id="cf0f7-113">To provést nastavením vlastnosti. <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType></span><span class="sxs-lookup"><span data-stu-id="cf0f7-113">Do this by setting the <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> property.</span></span>

<span data-ttu-id="cf0f7-114">Lze použít následující mapování alternativního typu.</span><span class="sxs-lookup"><span data-stu-id="cf0f7-114">The following alternative type mappings can be used.</span></span> <span data-ttu-id="cf0f7-115">Výchozí mapování naleznete v tématu [Datové typy](types.md).</span><span class="sxs-lookup"><span data-stu-id="cf0f7-115">For the default mappings, see [Data types](types.md).</span></span>

| <span data-ttu-id="cf0f7-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="cf0f7-116">Value</span></span>          | <span data-ttu-id="cf0f7-117">SqliteTyp</span><span class="sxs-lookup"><span data-stu-id="cf0f7-117">SqliteType</span></span> | <span data-ttu-id="cf0f7-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cf0f7-118">Remarks</span></span>          |
| -------------- | ---------- | ---------------- |
| <span data-ttu-id="cf0f7-119">Char</span><span class="sxs-lookup"><span data-stu-id="cf0f7-119">Char</span></span>           | <span data-ttu-id="cf0f7-120">Integer</span><span class="sxs-lookup"><span data-stu-id="cf0f7-120">Integer</span></span>    | <span data-ttu-id="cf0f7-121">UTF-16</span><span class="sxs-lookup"><span data-stu-id="cf0f7-121">UTF-16</span></span>           |
| <span data-ttu-id="cf0f7-122">DateTime</span><span class="sxs-lookup"><span data-stu-id="cf0f7-122">DateTime</span></span>       | <span data-ttu-id="cf0f7-123">Skutečné</span><span class="sxs-lookup"><span data-stu-id="cf0f7-123">Real</span></span>       | <span data-ttu-id="cf0f7-124">Hodnota juliánského dne</span><span class="sxs-lookup"><span data-stu-id="cf0f7-124">Julian day value</span></span> |
| <span data-ttu-id="cf0f7-125">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="cf0f7-125">DateTimeOffset</span></span> | <span data-ttu-id="cf0f7-126">Skutečné</span><span class="sxs-lookup"><span data-stu-id="cf0f7-126">Real</span></span>       | <span data-ttu-id="cf0f7-127">Hodnota juliánského dne</span><span class="sxs-lookup"><span data-stu-id="cf0f7-127">Julian day value</span></span> |
| <span data-ttu-id="cf0f7-128">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="cf0f7-128">Guid</span></span>           | <span data-ttu-id="cf0f7-129">Objekt blob</span><span class="sxs-lookup"><span data-stu-id="cf0f7-129">Blob</span></span>       |                  |
| <span data-ttu-id="cf0f7-130">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="cf0f7-130">TimeSpan</span></span>       | <span data-ttu-id="cf0f7-131">Skutečné</span><span class="sxs-lookup"><span data-stu-id="cf0f7-131">Real</span></span>       | <span data-ttu-id="cf0f7-132">Ve dnech</span><span class="sxs-lookup"><span data-stu-id="cf0f7-132">In days</span></span>          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a><span data-ttu-id="cf0f7-133">Výstupní parametry</span><span class="sxs-lookup"><span data-stu-id="cf0f7-133">Output parameters</span></span>

<span data-ttu-id="cf0f7-134">SQLite nepodporuje výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="cf0f7-134">SQLite doesn't support output parameters.</span></span> <span data-ttu-id="cf0f7-135">Místo toho vrátí tezauje hodnoty ve výsledcích dotazu.</span><span class="sxs-lookup"><span data-stu-id="cf0f7-135">Return values in the query results instead.</span></span>

## <a name="see-also"></a><span data-ttu-id="cf0f7-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf0f7-136">See also</span></span>

* [<span data-ttu-id="cf0f7-137">Datové typy</span><span class="sxs-lookup"><span data-stu-id="cf0f7-137">Data types</span></span>](types.md)
