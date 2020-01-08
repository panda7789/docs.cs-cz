---
title: Parametry
ms.date: 12/13/2019
description: Naučte se používat parametry SQL.
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447186"
---
# <a name="parameters"></a><span data-ttu-id="6a1ba-103">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a1ba-103">Parameters</span></span>

<span data-ttu-id="6a1ba-104">Parametry slouží k ochraně před útoky prostřednictvím injektáže SQL.</span><span class="sxs-lookup"><span data-stu-id="6a1ba-104">Parameters are used to protect against SQL injection attacks.</span></span> <span data-ttu-id="6a1ba-105">Namísto zřetězení vstupu uživatele s příkazy SQL použijte parametry pro zajištění, že vstup je někdy považován za hodnotu literálu a nikdy se neprovede.</span><span class="sxs-lookup"><span data-stu-id="6a1ba-105">Instead of concatenating user input with SQL statements, use parameters to ensure input is only ever treated as a literal value and never executed.</span></span> <span data-ttu-id="6a1ba-106">V SQLite jsou parametry obvykle povoleny všude, kde je v příkazech jazyka SQL povolen literál.</span><span class="sxs-lookup"><span data-stu-id="6a1ba-106">In SQLite, parameters are typically allowed anywhere a literal is allowed in SQL statements.</span></span>

<span data-ttu-id="6a1ba-107">Parametry mohou být uvozeny buď `:`, `@`nebo `$`.</span><span class="sxs-lookup"><span data-stu-id="6a1ba-107">Parameters can be prefixed with either `:`, `@`, or `$`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

<span data-ttu-id="6a1ba-108">Podrobnosti o tom, jak jsou hodnoty .NET mapovány na hodnoty SQLite, naleznete v tématu [datové typy](types.md) .</span><span class="sxs-lookup"><span data-stu-id="6a1ba-108">See [Data types](types.md) for details about how .NET values are mapped to SQLite values.</span></span>

## <a name="truncation"></a><span data-ttu-id="6a1ba-109">Zkrácení</span><span class="sxs-lookup"><span data-stu-id="6a1ba-109">Truncation</span></span>

<span data-ttu-id="6a1ba-110">Pro zkrácení textu a hodnot objektů BLOB použijte vlastnost <xref:Microsoft.Data.Sqlite.SqliteParameter.Size>.</span><span class="sxs-lookup"><span data-stu-id="6a1ba-110">Use the <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> property to truncate TEXT and BLOB values.</span></span>

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a><span data-ttu-id="6a1ba-111">Alternativní typy</span><span class="sxs-lookup"><span data-stu-id="6a1ba-111">Alternative types</span></span>

<span data-ttu-id="6a1ba-112">V některých případech může být vhodné použít jiný typ SQLite.</span><span class="sxs-lookup"><span data-stu-id="6a1ba-112">Sometimes, you may want to use an alternative SQLite type.</span></span> <span data-ttu-id="6a1ba-113">Provedete to nastavením vlastnosti <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType>.</span><span class="sxs-lookup"><span data-stu-id="6a1ba-113">Do this by setting the <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> property.</span></span>

<span data-ttu-id="6a1ba-114">Lze použít následující alternativní mapování typů.</span><span class="sxs-lookup"><span data-stu-id="6a1ba-114">The following alternative type mappings can be used.</span></span> <span data-ttu-id="6a1ba-115">Výchozí mapování najdete v tématu [datové typy](types.md).</span><span class="sxs-lookup"><span data-stu-id="6a1ba-115">For the default mappings, see [Data types](types.md).</span></span>

| <span data-ttu-id="6a1ba-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6a1ba-116">Value</span></span>          | <span data-ttu-id="6a1ba-117">SqliteType</span><span class="sxs-lookup"><span data-stu-id="6a1ba-117">SqliteType</span></span> | <span data-ttu-id="6a1ba-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a1ba-118">Remarks</span></span>          |
| -------------- | ---------- | ---------------- |
| <span data-ttu-id="6a1ba-119">Char</span><span class="sxs-lookup"><span data-stu-id="6a1ba-119">Char</span></span>           | <span data-ttu-id="6a1ba-120">Celé číslo</span><span class="sxs-lookup"><span data-stu-id="6a1ba-120">Integer</span></span>    | <span data-ttu-id="6a1ba-121">UTF-16</span><span class="sxs-lookup"><span data-stu-id="6a1ba-121">UTF-16</span></span>           |
| <span data-ttu-id="6a1ba-122">Datum a čas</span><span class="sxs-lookup"><span data-stu-id="6a1ba-122">DateTime</span></span>       | <span data-ttu-id="6a1ba-123">Skutečné</span><span class="sxs-lookup"><span data-stu-id="6a1ba-123">Real</span></span>       | <span data-ttu-id="6a1ba-124">Hodnota juliánského dne</span><span class="sxs-lookup"><span data-stu-id="6a1ba-124">Julian day value</span></span> |
| <span data-ttu-id="6a1ba-125">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="6a1ba-125">DateTimeOffset</span></span> | <span data-ttu-id="6a1ba-126">Skutečné</span><span class="sxs-lookup"><span data-stu-id="6a1ba-126">Real</span></span>       | <span data-ttu-id="6a1ba-127">Hodnota juliánského dne</span><span class="sxs-lookup"><span data-stu-id="6a1ba-127">Julian day value</span></span> |
| <span data-ttu-id="6a1ba-128">identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="6a1ba-128">Guid</span></span>           | <span data-ttu-id="6a1ba-129">Blob</span><span class="sxs-lookup"><span data-stu-id="6a1ba-129">Blob</span></span>       |                  |
| <span data-ttu-id="6a1ba-130">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="6a1ba-130">TimeSpan</span></span>       | <span data-ttu-id="6a1ba-131">Skutečné</span><span class="sxs-lookup"><span data-stu-id="6a1ba-131">Real</span></span>       | <span data-ttu-id="6a1ba-132">Ve dnech</span><span class="sxs-lookup"><span data-stu-id="6a1ba-132">In days</span></span>          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a><span data-ttu-id="6a1ba-133">Výstupní parametry</span><span class="sxs-lookup"><span data-stu-id="6a1ba-133">Output parameters</span></span>

<span data-ttu-id="6a1ba-134">SQLite nepodporuje výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="6a1ba-134">SQLite doesn't support output parameters.</span></span> <span data-ttu-id="6a1ba-135">Místo toho se vrátí hodnoty z výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="6a1ba-135">Return values in the query results instead.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a1ba-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a1ba-136">See also</span></span>

* [<span data-ttu-id="6a1ba-137">Datové typy</span><span class="sxs-lookup"><span data-stu-id="6a1ba-137">Data types</span></span>](types.md)
