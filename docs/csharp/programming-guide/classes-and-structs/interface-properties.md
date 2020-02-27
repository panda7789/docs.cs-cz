---
title: Vlastnosti rozhraní – C# Průvodce programováním
ms.date: 01/31/2020
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: 5798b80526f34e923e2eaab43847b98f6c64e14b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626617"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="98a49-102">Vlastnosti rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="98a49-102">Interface Properties (C# Programming Guide)</span></span>

<span data-ttu-id="98a49-103">Vlastnosti lze deklarovat v [rozhraní](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="98a49-103">Properties can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="98a49-104">Následující příklad deklaruje přistupující objekt vlastnosti rozhraní:</span><span class="sxs-lookup"><span data-stu-id="98a49-104">The following example declares an interface property accessor:</span></span>

[!code-csharp[DeclareProperties](~/samples/snippets/csharp/interfaces/properties.cs#DeclareInterfaceProperties)]

<span data-ttu-id="98a49-105">Vlastnosti rozhraní obvykle nemají tělo.</span><span class="sxs-lookup"><span data-stu-id="98a49-105">Interface properties typically don't have a body.</span></span> <span data-ttu-id="98a49-106">Přistupující objekty označují, zda je vlastnost určena pro čtení i zápis, jen pro čtení nebo jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="98a49-106">The accessors indicate whether the property is read-write, read-only, or write-only.</span></span> <span data-ttu-id="98a49-107">Na rozdíl od tříd a struktur deklaruje přistupující objekty bez těla deklarace [automaticky implementované vlastnosti](auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="98a49-107">Unlike in classes and structs, declaring the accessors without a body doesn't declare an [auto-implemented property](auto-implemented-properties.md).</span></span> <span data-ttu-id="98a49-108">Počínaje C# 8,0 může rozhraní definovat výchozí implementaci pro členy, včetně vlastností.</span><span class="sxs-lookup"><span data-stu-id="98a49-108">Beginning with C# 8.0, an interface may define a default implementation for members, including properties.</span></span> <span data-ttu-id="98a49-109">Definice výchozí implementace pro vlastnost v rozhraní je vzácná, protože rozhraní nemůžou definovat datová pole instance.</span><span class="sxs-lookup"><span data-stu-id="98a49-109">Defining a default implementation for a property in an interface is rare because interfaces may not define instance data fields.</span></span>

## <a name="example"></a><span data-ttu-id="98a49-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="98a49-110">Example</span></span>

<span data-ttu-id="98a49-111">V tomto příkladu rozhraní `IEmployee` má vlastnost pro čtení i zápis, `Name`a vlastnost jen pro čtení `Counter`.</span><span class="sxs-lookup"><span data-stu-id="98a49-111">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="98a49-112">Třída `Employee` implementuje rozhraní `IEmployee` a používá tyto dvě vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="98a49-112">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="98a49-113">Program přečte název nového zaměstnance a aktuální počet zaměstnanců a zobrazí název zaměstnance a vypočtené číslo zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="98a49-113">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>

<span data-ttu-id="98a49-114">Můžete použít plně kvalifikovaný název vlastnosti, který odkazuje na rozhraní, ve kterém je člen deklarován.</span><span class="sxs-lookup"><span data-stu-id="98a49-114">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="98a49-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="98a49-115">For example:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="98a49-116">Předchozí příklad ukazuje [explicitní implementaci rozhraní](../interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="98a49-116">The preceding example demonstrates [Explicit Interface Implementation](../interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="98a49-117">Například pokud `Employee` třídy implementuje dvě rozhraní `ICitizen` a `IEmployee` a obě rozhraní mají vlastnost `Name`, bude nutná implementace explicitního člena rozhraní.</span><span class="sxs-lookup"><span data-stu-id="98a49-117">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="98a49-118">To znamená, že následující deklarace vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="98a49-118">That is, the following property declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="98a49-119">implementuje vlastnost `Name` v rozhraní `IEmployee`, zatímco následující deklarace:</span><span class="sxs-lookup"><span data-stu-id="98a49-119">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#CitizenImplementation)]

<span data-ttu-id="98a49-120">implementuje vlastnost `Name` v rozhraní `ICitizen`.</span><span class="sxs-lookup"><span data-stu-id="98a49-120">implements the `Name` property on the `ICitizen` interface.</span></span>

[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#PropertyExample)]
[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#UseProperty)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a><span data-ttu-id="98a49-121">Ukázkový výstup</span><span class="sxs-lookup"><span data-stu-id="98a49-121">Sample output</span></span>

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a><span data-ttu-id="98a49-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="98a49-122">See also</span></span>

- [<span data-ttu-id="98a49-123">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="98a49-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="98a49-124">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="98a49-124">Properties</span></span>](./properties.md)
- [<span data-ttu-id="98a49-125">Použití vlastností</span><span class="sxs-lookup"><span data-stu-id="98a49-125">Using Properties</span></span>](./using-properties.md)
- [<span data-ttu-id="98a49-126">Porovnání mezi vlastnostmi a indexery</span><span class="sxs-lookup"><span data-stu-id="98a49-126">Comparison Between Properties and Indexers</span></span>](../indexers/comparison-between-properties-and-indexers.md)
- [<span data-ttu-id="98a49-127">Indexery</span><span class="sxs-lookup"><span data-stu-id="98a49-127">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="98a49-128">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="98a49-128">Interfaces</span></span>](../interfaces/index.md)
