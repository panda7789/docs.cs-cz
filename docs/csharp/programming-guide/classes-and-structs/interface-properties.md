---
title: Vlastnosti rozhraní – průvodce programováním jazyka C#
ms.date: 01/31/2020
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: 5798b80526f34e923e2eaab43847b98f6c64e14b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626617"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="b6ab7-102">Vlastnosti rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="b6ab7-102">Interface Properties (C# Programming Guide)</span></span>

<span data-ttu-id="b6ab7-103">Vlastnosti lze deklarovat na [rozhraní](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="b6ab7-103">Properties can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="b6ab7-104">Následující příklad deklaruje přistupující objekt vlastnosti rozhraní:</span><span class="sxs-lookup"><span data-stu-id="b6ab7-104">The following example declares an interface property accessor:</span></span>

[!code-csharp[DeclareProperties](~/samples/snippets/csharp/interfaces/properties.cs#DeclareInterfaceProperties)]

<span data-ttu-id="b6ab7-105">Vlastnosti rozhraní obvykle nemají tělo.</span><span class="sxs-lookup"><span data-stu-id="b6ab7-105">Interface properties typically don't have a body.</span></span> <span data-ttu-id="b6ab7-106">Přistupující objekty označují, zda je vlastnost jen pro čtení, jen pro čtení nebo jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="b6ab7-106">The accessors indicate whether the property is read-write, read-only, or write-only.</span></span> <span data-ttu-id="b6ab7-107">Na rozdíl od tříd a struktur deklarování přístupových objektů bez těla nedeklaruje [automaticky implementovanou vlastnost](auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="b6ab7-107">Unlike in classes and structs, declaring the accessors without a body doesn't declare an [auto-implemented property](auto-implemented-properties.md).</span></span> <span data-ttu-id="b6ab7-108">Počínaje C# 8.0 rozhraní může definovat výchozí implementaci pro členy, včetně vlastností.</span><span class="sxs-lookup"><span data-stu-id="b6ab7-108">Beginning with C# 8.0, an interface may define a default implementation for members, including properties.</span></span> <span data-ttu-id="b6ab7-109">Definování výchozí implementace vlastnosti v rozhraní je vzácné, protože rozhraní nemusí definovat datová pole instancí.</span><span class="sxs-lookup"><span data-stu-id="b6ab7-109">Defining a default implementation for a property in an interface is rare because interfaces may not define instance data fields.</span></span>

## <a name="example"></a><span data-ttu-id="b6ab7-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="b6ab7-110">Example</span></span>

<span data-ttu-id="b6ab7-111">V tomto příkladu `IEmployee` rozhraní má vlastnost `Name`pro čtení a zápis `Counter`a vlastnost jen pro čtení .</span><span class="sxs-lookup"><span data-stu-id="b6ab7-111">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="b6ab7-112">Třída `Employee` implementuje `IEmployee` rozhraní a používá tyto dvě vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b6ab7-112">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="b6ab7-113">Program přečte jméno nového zaměstnance a aktuální počet zaměstnanců a zobrazí jméno zaměstnance a číslo vypočítaného zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="b6ab7-113">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>

<span data-ttu-id="b6ab7-114">Můžete použít plně kvalifikovaný název vlastnosti, která odkazuje na rozhraní, ve kterém je deklarován člen.</span><span class="sxs-lookup"><span data-stu-id="b6ab7-114">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="b6ab7-115">Například:</span><span class="sxs-lookup"><span data-stu-id="b6ab7-115">For example:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="b6ab7-116">Předchozí příklad ukazuje [explicitní implementace rozhraní](../interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="b6ab7-116">The preceding example demonstrates [Explicit Interface Implementation](../interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="b6ab7-117">Například pokud třída `Employee` implementuje dvě `ICitizen` `IEmployee` rozhraní a obě `Name` rozhraní mají vlastnost, bude nutné explicitní implementace člena rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b6ab7-117">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="b6ab7-118">To znamená následující prohlášení o vlastnostech:</span><span class="sxs-lookup"><span data-stu-id="b6ab7-118">That is, the following property declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="b6ab7-119">implementuje `Name` vlastnost `IEmployee` na rozhraní, zatímco následující prohlášení:</span><span class="sxs-lookup"><span data-stu-id="b6ab7-119">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#CitizenImplementation)]

<span data-ttu-id="b6ab7-120">implementuje `Name` vlastnost `ICitizen` na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b6ab7-120">implements the `Name` property on the `ICitizen` interface.</span></span>

[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#PropertyExample)]
[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#UseProperty)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a><span data-ttu-id="b6ab7-121">Ukázkový výstup</span><span class="sxs-lookup"><span data-stu-id="b6ab7-121">Sample output</span></span>

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a><span data-ttu-id="b6ab7-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6ab7-122">See also</span></span>

- [<span data-ttu-id="b6ab7-123">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b6ab7-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b6ab7-124">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b6ab7-124">Properties</span></span>](./properties.md)
- [<span data-ttu-id="b6ab7-125">Použití vlastností</span><span class="sxs-lookup"><span data-stu-id="b6ab7-125">Using Properties</span></span>](./using-properties.md)
- [<span data-ttu-id="b6ab7-126">Porovnání vlastností a indexerů</span><span class="sxs-lookup"><span data-stu-id="b6ab7-126">Comparison Between Properties and Indexers</span></span>](../indexers/comparison-between-properties-and-indexers.md)
- [<span data-ttu-id="b6ab7-127">Indexery</span><span class="sxs-lookup"><span data-stu-id="b6ab7-127">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="b6ab7-128">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6ab7-128">Interfaces</span></span>](../interfaces/index.md)
