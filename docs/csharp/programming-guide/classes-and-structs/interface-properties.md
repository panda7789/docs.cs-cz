---
title: Vlastnosti rozhraní – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: fad674c6d56011afcccbe9ce2a88e7af411fe0a2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579158"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="f9624-102">Vlastnosti rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="f9624-102">Interface Properties (C# Programming Guide)</span></span>

<span data-ttu-id="f9624-103">Vlastnosti lze deklarovat v [rozhraní](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="f9624-103">Properties can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="f9624-104">Následuje příklad přistupujícího objektu vlastnosti rozhraní:</span><span class="sxs-lookup"><span data-stu-id="f9624-104">The following is an example of an interface property accessor:</span></span>

[!code-csharp[csProgGuideProperties#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#14)]

<span data-ttu-id="f9624-105">Přistupující objekt vlastnosti rozhraní nemá tělo.</span><span class="sxs-lookup"><span data-stu-id="f9624-105">The accessor of an interface property does not have a body.</span></span> <span data-ttu-id="f9624-106">Proto je účel přístupových objektů indikován, zda je vlastnost určena pro čtení i zápis, jen pro čtení nebo jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="f9624-106">Thus, the purpose of the accessors is to indicate whether the property is read-write, read-only, or write-only.</span></span>

## <a name="example"></a><span data-ttu-id="f9624-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9624-107">Example</span></span>

<span data-ttu-id="f9624-108">V tomto příkladu rozhraní `IEmployee` má vlastnost pro čtení i zápis, `Name` a vlastnost jen pro čtení `Counter`.</span><span class="sxs-lookup"><span data-stu-id="f9624-108">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="f9624-109">Třída `Employee` implementuje rozhraní `IEmployee` a používá tyto dvě vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f9624-109">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="f9624-110">Program přečte název nového zaměstnance a aktuální počet zaměstnanců a zobrazí název zaměstnance a vypočtené číslo zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="f9624-110">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>

<span data-ttu-id="f9624-111">Můžete použít plně kvalifikovaný název vlastnosti, který odkazuje na rozhraní, ve kterém je člen deklarován.</span><span class="sxs-lookup"><span data-stu-id="f9624-111">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="f9624-112">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f9624-112">For example:</span></span>

[!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]

<span data-ttu-id="f9624-113">To se označuje jako [explicitní implementace rozhraní](../interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="f9624-113">This is called [Explicit Interface Implementation](../interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="f9624-114">Například pokud `Employee` třídy implementuje dvě rozhraní `ICitizen` a `IEmployee` a obě rozhraní mají vlastnost `Name`, bude nutná implementace explicitního člena rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f9624-114">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="f9624-115">To znamená, že následující deklarace vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="f9624-115">That is, the following property declaration:</span></span>

[!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]

<span data-ttu-id="f9624-116">implementuje vlastnost `Name` v rozhraní `IEmployee`, zatímco následující deklarace:</span><span class="sxs-lookup"><span data-stu-id="f9624-116">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>

[!code-csharp[csProgGuideProperties#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#17)]

<span data-ttu-id="f9624-117">implementuje vlastnost `Name` v rozhraní `ICitizen`.</span><span class="sxs-lookup"><span data-stu-id="f9624-117">implements the `Name` property on the `ICitizen` interface.</span></span>

[!code-csharp[csProgGuideProperties#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#15)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a><span data-ttu-id="f9624-118">Ukázkový výstup</span><span class="sxs-lookup"><span data-stu-id="f9624-118">Sample output</span></span>

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a><span data-ttu-id="f9624-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9624-119">See also</span></span>

- [<span data-ttu-id="f9624-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f9624-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f9624-121">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f9624-121">Properties</span></span>](./properties.md)
- [<span data-ttu-id="f9624-122">Použití vlastností</span><span class="sxs-lookup"><span data-stu-id="f9624-122">Using Properties</span></span>](./using-properties.md)
- [<span data-ttu-id="f9624-123">Porovnání mezi vlastnostmi a indexery</span><span class="sxs-lookup"><span data-stu-id="f9624-123">Comparison Between Properties and Indexers</span></span>](../indexers/comparison-between-properties-and-indexers.md)
- [<span data-ttu-id="f9624-124">Indexery</span><span class="sxs-lookup"><span data-stu-id="f9624-124">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="f9624-125">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9624-125">Interfaces</span></span>](../interfaces/index.md)
