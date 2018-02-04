---
title: "Postupy: Použití indexovaných vlastností při programování zprostředkovatele komunikace s objekty COM (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2538dae8f02b17a77cc1eb2798b8b38a7f1d7db2
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="93f4b-102">Postupy: Použití indexovaných vlastností při programování zprostředkovatele komunikace s objekty COM (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="93f4b-102">How to: Use Indexed Properties in COM Interop Programming (C# Programming Guide)</span></span>
<span data-ttu-id="93f4b-103">*Indexované vlastnosti* zlepšit způsob v COM, které se spotřebovávají vlastnosti, které mají parametry v C# – programování.</span><span class="sxs-lookup"><span data-stu-id="93f4b-103">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="93f4b-104">Indexované vlastnosti pracovních společně s další funkce v jazyce Visual C#, jako [pojmenované a nepovinné argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), nový typ ([dynamické](../../../csharp/language-reference/keywords/dynamic.md)), a [vložených informací o typu](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)do vylepšení programování pro Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="93f4b-104">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../../csharp/language-reference/keywords/dynamic.md)), and [embedded type information](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="93f4b-105">V dřívějších verzích jazyka C#, jsou dostupné jako vlastnosti jenom v případě metody `get` metoda nemá žádné parametry a `set` metoda má jeden parametr hodnoty.</span><span class="sxs-lookup"><span data-stu-id="93f4b-105">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="93f4b-106">Ne všechny vlastnosti modelu COM však splňovat tato omezení.</span><span class="sxs-lookup"><span data-stu-id="93f4b-106">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="93f4b-107">Například aplikace Excel [rozsah](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.range.aspx) vlastnost má `get` přistupujícího objektu, který vyžaduje parametr pro název oblasti.</span><span class="sxs-lookup"><span data-stu-id="93f4b-107">For example, the Excel [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.range.aspx) property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="93f4b-108">V minulosti protože nelze získat přístup k `Range` vlastnost přímo, jste museli používat `get_Range` metoda místo toho, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="93f4b-108">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]  
  
 <span data-ttu-id="93f4b-109">Indexované vlastnosti umožňují zápisu následující místo:</span><span class="sxs-lookup"><span data-stu-id="93f4b-109">Indexed properties enable you to write the following instead:</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]  
  
> [!NOTE]
>  <span data-ttu-id="93f4b-110">Předchozí příklad používá také [volitelné argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) funkci, která umožňuje vynechat `Type.Missing`.</span><span class="sxs-lookup"><span data-stu-id="93f4b-110">The previous example also uses the [optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="93f4b-111">Podobně se nastavit hodnotu `Value` vlastnost [rozsah](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) objektů v aplikaci Visual C# 2008 a starší, dva argumenty jsou povinné.</span><span class="sxs-lookup"><span data-stu-id="93f4b-111">Similarly to set the value of the `Value` property of a [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) object in Visual C# 2008 and earlier, two arguments are required.</span></span> <span data-ttu-id="93f4b-112">Poskytuje jeden argument volitelný parametr, který určuje typ hodnoty rozsahu.</span><span class="sxs-lookup"><span data-stu-id="93f4b-112">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="93f4b-113">Druhá hodnota poskytuje `Value` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="93f4b-113">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="93f4b-114">Následující příklady znázorňují těchto postupů.</span><span class="sxs-lookup"><span data-stu-id="93f4b-114">The following examples illustrate these techniques.</span></span> <span data-ttu-id="93f4b-115">Jak nastavit hodnotu buňky A1 do `Name`.</span><span class="sxs-lookup"><span data-stu-id="93f4b-115">Both set the value of the A1 cell to `Name`.</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]  
  
 <span data-ttu-id="93f4b-116">Indexované vlastnosti umožňují místo zápisu následující kód.</span><span class="sxs-lookup"><span data-stu-id="93f4b-116">Indexed properties enable you to write the following code instead.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]  
  
 <span data-ttu-id="93f4b-117">Nelze vytvořit indexované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="93f4b-117">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="93f4b-118">Tato funkce podporuje jenom spotřeba existující indexované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="93f4b-118">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93f4b-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="93f4b-119">Example</span></span>  
 <span data-ttu-id="93f4b-120">Následující kód ukazuje kompletní příklad.</span><span class="sxs-lookup"><span data-stu-id="93f4b-120">The following code shows a complete example.</span></span> <span data-ttu-id="93f4b-121">Další informace o tom, jak nastavit projekt, který má přístup k rozhraní API Office najdete v tématu [postupy: přístup k objektům zprostředkovatel komunikace s objekty Office pomocí Visual C# funkce](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="93f4b-121">For more information about how to set up a project that accesses the Office API, see [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="93f4b-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="93f4b-122">See Also</span></span>  
 [<span data-ttu-id="93f4b-123">Pojmenované a nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="93f4b-123">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
 [<span data-ttu-id="93f4b-124">dynamic</span><span class="sxs-lookup"><span data-stu-id="93f4b-124">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
 [<span data-ttu-id="93f4b-125">Použití typu dynamic</span><span class="sxs-lookup"><span data-stu-id="93f4b-125">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [<span data-ttu-id="93f4b-126">Postupy: Použití pojmenovaných a nepovinných argumentů v programování pro sadu Office</span><span class="sxs-lookup"><span data-stu-id="93f4b-126">How to: Use Named and Optional Arguments in Office Programming</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)  
 [<span data-ttu-id="93f4b-127">Postupy: Přístup k objektům Interop sady Office pomocí funkcí Visual C#</span><span class="sxs-lookup"><span data-stu-id="93f4b-127">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 [<span data-ttu-id="93f4b-128">Návod: Programování pro Office</span><span class="sxs-lookup"><span data-stu-id="93f4b-128">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
