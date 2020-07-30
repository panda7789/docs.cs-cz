---
title: Používání indexovaných vlastností v programování zprostředkovatele komunikace s objekty COM – Průvodce programováním v C#
description: Přečtěte si, jak indexované vlastnosti zlepšují způsob, jakým se v tomto příkladu jazyka C# spotřebovávají vlastnosti modelu COM, které mají parametry.
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: abd785864bd79d455024cb4501c76a21b349aa91
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303007"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="b6c6e-103">Používání indexovaných vlastností v programování zprostředkovatele komunikace s objekty COM (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="b6c6e-103">How to use indexed properties in COM interop programming (C# Programming Guide)</span></span>
<span data-ttu-id="b6c6e-104">*Indexované vlastnosti* zlepšují způsob, jakým jsou vlastnosti modelu COM, které mají parametry spotřebované v programování v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="b6c6e-104">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="b6c6e-105">Indexované vlastnosti pracují společně s dalšími funkcemi v jazyce Visual C#, jako jsou [pojmenované a nepovinné argumenty](../classes-and-structs/named-and-optional-arguments.md), nový typ ([dynamický](../../language-reference/builtin-types/reference-types.md)) a [vložené informace o typu](../../../standard/assembly/embed-types-visual-studio.md), aby bylo možné vylepšit systém Microsoft Office programování.</span><span class="sxs-lookup"><span data-stu-id="b6c6e-105">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../language-reference/builtin-types/reference-types.md)), and [embedded type information](../../../standard/assembly/embed-types-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="b6c6e-106">V dřívějších verzích jazyka C# jsou metody přístupné jako vlastnosti pouze v případě, že `get` metoda nemá žádné parametry a `set` Metoda má jeden a pouze jeden parametr value.</span><span class="sxs-lookup"><span data-stu-id="b6c6e-106">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="b6c6e-107">Ale ne všechny vlastnosti modelu COM tyto omezení nesplňují.</span><span class="sxs-lookup"><span data-stu-id="b6c6e-107">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="b6c6e-108">Vlastnost aplikace Excel má například <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> `get` přistupující objekt, který vyžaduje parametr pro název rozsahu.</span><span class="sxs-lookup"><span data-stu-id="b6c6e-108">For example, the Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="b6c6e-109">Vzhledem k tomu, že nemůžete získat přístup k `Range` vlastnosti přímo, měli byste `get_Range` místo toho použít metodu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b6c6e-109">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 <span data-ttu-id="b6c6e-110">Indexované vlastnosti umožňují napsat následující místo:</span><span class="sxs-lookup"><span data-stu-id="b6c6e-110">Indexed properties enable you to write the following instead:</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> <span data-ttu-id="b6c6e-111">Předchozí příklad také používá funkci [volitelné argumenty](../classes-and-structs/named-and-optional-arguments.md) , která umožňuje vynechat `Type.Missing` .</span><span class="sxs-lookup"><span data-stu-id="b6c6e-111">The previous example also uses the [optional arguments](../classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="b6c6e-112">Podobně pro nastavení hodnoty `Value` vlastnosti <xref:Microsoft.Office.Interop.Excel.Range> objektu v C# 3,0 a starší jsou vyžadovány dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="b6c6e-112">Similarly to set the value of the `Value` property of a <xref:Microsoft.Office.Interop.Excel.Range> object in C# 3.0 and earlier, two arguments are required.</span></span> <span data-ttu-id="b6c6e-113">Jeden zadá argument pro volitelný parametr, který určuje typ hodnoty rozsahu.</span><span class="sxs-lookup"><span data-stu-id="b6c6e-113">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="b6c6e-114">Druhý zadá hodnotu `Value` Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b6c6e-114">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="b6c6e-115">Následující příklady ilustrují tyto techniky.</span><span class="sxs-lookup"><span data-stu-id="b6c6e-115">The following examples illustrate these techniques.</span></span> <span data-ttu-id="b6c6e-116">Nastavte hodnotu buňky a1 na `Name` .</span><span class="sxs-lookup"><span data-stu-id="b6c6e-116">Both set the value of the A1 cell to `Name`.</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 <span data-ttu-id="b6c6e-117">Indexované vlastnosti umožňují místo toho napsat následující kód.</span><span class="sxs-lookup"><span data-stu-id="b6c6e-117">Indexed properties enable you to write the following code instead.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 <span data-ttu-id="b6c6e-118">Nemůžete vytvořit indexované vlastnosti, které vlastníte.</span><span class="sxs-lookup"><span data-stu-id="b6c6e-118">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="b6c6e-119">Funkce podporuje jenom spotřebu stávajících indexovaných vlastností.</span><span class="sxs-lookup"><span data-stu-id="b6c6e-119">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6c6e-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="b6c6e-120">Example</span></span>  
 <span data-ttu-id="b6c6e-121">Následující kód ukazuje kompletní příklad.</span><span class="sxs-lookup"><span data-stu-id="b6c6e-121">The following code shows a complete example.</span></span> <span data-ttu-id="b6c6e-122">Další informace o tom, jak nastavit projekt, který přistupuje k rozhraní Office API, najdete v tématu [Jak získat přístup k objektům Interop sady Office pomocí funkcí jazyka C#](./how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="b6c6e-122">For more information about how to set up a project that accesses the Office API, see [How to access Office interop objects by using C# features](./how-to-access-office-onterop-objects.md).</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b6c6e-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6c6e-123">See also</span></span>

- [<span data-ttu-id="b6c6e-124">Pojmenované a nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="b6c6e-124">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="b6c6e-125">dynamické</span><span class="sxs-lookup"><span data-stu-id="b6c6e-125">dynamic</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="b6c6e-126">Použití typu dynamic</span><span class="sxs-lookup"><span data-stu-id="b6c6e-126">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="b6c6e-127">Jak použít pojmenované a nepovinné argumenty v programování pro sadu Office</span><span class="sxs-lookup"><span data-stu-id="b6c6e-127">How to use named and optional arguments in Office programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="b6c6e-128">Jak získat přístup k objektům interoperability Office pomocí funkcí jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b6c6e-128">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)
- [<span data-ttu-id="b6c6e-129">Návod: programování pro Office</span><span class="sxs-lookup"><span data-stu-id="b6c6e-129">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
