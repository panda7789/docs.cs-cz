---
title: Vlastnosti rozhraní – Průvodce programováním v C#
description: Vlastnosti lze deklarovat v rozhraní v jazyce C#. Tento příklad deklaruje přistupující objekt vlastnosti rozhraní.
ms.date: 01/31/2020
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: 920381ae804a6a968bfd667171269377f3d7e448
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864966"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="1e939-104">Vlastnosti rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="1e939-104">Interface Properties (C# Programming Guide)</span></span>

<span data-ttu-id="1e939-105">Vlastnosti lze deklarovat v [rozhraní](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="1e939-105">Properties can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="1e939-106">Následující příklad deklaruje přistupující objekt vlastnosti rozhraní:</span><span class="sxs-lookup"><span data-stu-id="1e939-106">The following example declares an interface property accessor:</span></span>

[!code-csharp[DeclareProperties](~/samples/snippets/csharp/interfaces/properties.cs#DeclareInterfaceProperties)]

<span data-ttu-id="1e939-107">Vlastnosti rozhraní obvykle nemají tělo.</span><span class="sxs-lookup"><span data-stu-id="1e939-107">Interface properties typically don't have a body.</span></span> <span data-ttu-id="1e939-108">Přistupující objekty označují, zda je vlastnost určena pro čtení i zápis, jen pro čtení nebo jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="1e939-108">The accessors indicate whether the property is read-write, read-only, or write-only.</span></span> <span data-ttu-id="1e939-109">Na rozdíl od tříd a struktur deklaruje přistupující objekty bez těla deklarace [automaticky implementované vlastnosti](auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="1e939-109">Unlike in classes and structs, declaring the accessors without a body doesn't declare an [auto-implemented property](auto-implemented-properties.md).</span></span> <span data-ttu-id="1e939-110">Počínaje jazykem C# 8,0 může rozhraní definovat výchozí implementaci pro členy, včetně vlastností.</span><span class="sxs-lookup"><span data-stu-id="1e939-110">Beginning with C# 8.0, an interface may define a default implementation for members, including properties.</span></span> <span data-ttu-id="1e939-111">Definice výchozí implementace pro vlastnost v rozhraní je vzácná, protože rozhraní nemůžou definovat datová pole instance.</span><span class="sxs-lookup"><span data-stu-id="1e939-111">Defining a default implementation for a property in an interface is rare because interfaces may not define instance data fields.</span></span>

## <a name="example"></a><span data-ttu-id="1e939-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="1e939-112">Example</span></span>

<span data-ttu-id="1e939-113">V tomto příkladu `IEmployee` má rozhraní vlastnost pro čtení i zápis, `Name` a vlastnost určenou jen pro čtení `Counter` .</span><span class="sxs-lookup"><span data-stu-id="1e939-113">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="1e939-114">Třída `Employee` implementuje `IEmployee` rozhraní a používá tyto dvě vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1e939-114">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="1e939-115">Program přečte název nového zaměstnance a aktuální počet zaměstnanců a zobrazí název zaměstnance a vypočtené číslo zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="1e939-115">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>

<span data-ttu-id="1e939-116">Můžete použít plně kvalifikovaný název vlastnosti, který odkazuje na rozhraní, ve kterém je člen deklarován.</span><span class="sxs-lookup"><span data-stu-id="1e939-116">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="1e939-117">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1e939-117">For example:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="1e939-118">Předchozí příklad ukazuje [explicitní implementaci rozhraní](../interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="1e939-118">The preceding example demonstrates [Explicit Interface Implementation](../interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="1e939-119">Například pokud třída `Employee` implementuje dvě rozhraní `ICitizen` a `IEmployee` a obě rozhraní mají `Name` vlastnost, bude nutná implementace explicitního člena rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1e939-119">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="1e939-120">To znamená, že následující deklarace vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="1e939-120">That is, the following property declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="1e939-121">implementuje `Name` vlastnost na `IEmployee` rozhraní a následující deklaraci:</span><span class="sxs-lookup"><span data-stu-id="1e939-121">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#CitizenImplementation)]

<span data-ttu-id="1e939-122">implementuje `Name` vlastnost na `ICitizen` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1e939-122">implements the `Name` property on the `ICitizen` interface.</span></span>

[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#PropertyExample)]
[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#UseProperty)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a><span data-ttu-id="1e939-123">Ukázkový výstup</span><span class="sxs-lookup"><span data-stu-id="1e939-123">Sample output</span></span>

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a><span data-ttu-id="1e939-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e939-124">See also</span></span>

- [<span data-ttu-id="1e939-125">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="1e939-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1e939-126">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1e939-126">Properties</span></span>](./properties.md)
- [<span data-ttu-id="1e939-127">Použití vlastností</span><span class="sxs-lookup"><span data-stu-id="1e939-127">Using Properties</span></span>](./using-properties.md)
- [<span data-ttu-id="1e939-128">Porovnání mezi vlastnostmi a indexery</span><span class="sxs-lookup"><span data-stu-id="1e939-128">Comparison Between Properties and Indexers</span></span>](../indexers/comparison-between-properties-and-indexers.md)
- [<span data-ttu-id="1e939-129">Indexery</span><span class="sxs-lookup"><span data-stu-id="1e939-129">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="1e939-130">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="1e939-130">Interfaces</span></span>](../interfaces/index.md)
