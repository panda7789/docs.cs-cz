---
title: Používání indexovaných vlastností v programování zprostředkovatele komunikace s objekty C# com – Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: aa4dc6da520fc58a99a9691aa39e412468aa02b5
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635311"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="98609-102">Používání indexovaných vlastností v programování zprostředkovatele komunikace s objektyC# com (Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="98609-102">How to use indexed properties in COM interop programming (C# Programming Guide)</span></span>
<span data-ttu-id="98609-103">*Indexované vlastnosti* zlepšují způsob, jakým jsou vlastnosti modelu COM, které mají C# parametry spotřebované při programování.</span><span class="sxs-lookup"><span data-stu-id="98609-103">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="98609-104">Indexované vlastnosti pracují společně s dalšími funkcemi v vizuálu C#, jako jsou [pojmenované a nepovinné argumenty](../classes-and-structs/named-and-optional-arguments.md), nový typ ([dynamický](../../language-reference/builtin-types/reference-types.md)) a [vložené informace o typu](../../../standard/assembly/embed-types-visual-studio.md), aby bylo možné vylepšit systém Microsoft Office programování.</span><span class="sxs-lookup"><span data-stu-id="98609-104">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../language-reference/builtin-types/reference-types.md)), and [embedded type information](../../../standard/assembly/embed-types-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="98609-105">V dřívějších verzích nástroje C#jsou metody přístupné jako vlastnosti pouze v případě, že metoda `get` nemá žádné parametry a metoda `set` má jeden a pouze jeden parametr value.</span><span class="sxs-lookup"><span data-stu-id="98609-105">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="98609-106">Ale ne všechny vlastnosti modelu COM tyto omezení nesplňují.</span><span class="sxs-lookup"><span data-stu-id="98609-106">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="98609-107">Například vlastnost Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> má přistupující objekt `get`, který vyžaduje parametr pro název rozsahu.</span><span class="sxs-lookup"><span data-stu-id="98609-107">For example, the Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="98609-108">Vzhledem k tomu, že v minulosti jste nezískali přístup k vlastnosti `Range` přímo, museli byste místo toho použít metodu `get_Range`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="98609-108">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 <span data-ttu-id="98609-109">Indexované vlastnosti umožňují napsat následující místo:</span><span class="sxs-lookup"><span data-stu-id="98609-109">Indexed properties enable you to write the following instead:</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> <span data-ttu-id="98609-110">Předchozí příklad také používá funkci [volitelné argumenty](../classes-and-structs/named-and-optional-arguments.md) , která umožňuje vynechat `Type.Missing`.</span><span class="sxs-lookup"><span data-stu-id="98609-110">The previous example also uses the [optional arguments](../classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="98609-111">Podobně pro nastavení hodnoty vlastnosti `Value` objektu <xref:Microsoft.Office.Interop.Excel.Range> v C# 3,0 a starších verzích jsou vyžadovány dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="98609-111">Similarly to set the value of the `Value` property of a <xref:Microsoft.Office.Interop.Excel.Range> object in C# 3.0 and earlier, two arguments are required.</span></span> <span data-ttu-id="98609-112">Jeden zadá argument pro volitelný parametr, který určuje typ hodnoty rozsahu.</span><span class="sxs-lookup"><span data-stu-id="98609-112">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="98609-113">Druhý zadá hodnotu vlastnosti `Value`.</span><span class="sxs-lookup"><span data-stu-id="98609-113">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="98609-114">Následující příklady ilustrují tyto techniky.</span><span class="sxs-lookup"><span data-stu-id="98609-114">The following examples illustrate these techniques.</span></span> <span data-ttu-id="98609-115">Nastavte hodnotu buňky a1 na `Name`.</span><span class="sxs-lookup"><span data-stu-id="98609-115">Both set the value of the A1 cell to `Name`.</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 <span data-ttu-id="98609-116">Indexované vlastnosti umožňují místo toho napsat následující kód.</span><span class="sxs-lookup"><span data-stu-id="98609-116">Indexed properties enable you to write the following code instead.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 <span data-ttu-id="98609-117">Nemůžete vytvořit indexované vlastnosti, které vlastníte.</span><span class="sxs-lookup"><span data-stu-id="98609-117">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="98609-118">Funkce podporuje jenom spotřebu stávajících indexovaných vlastností.</span><span class="sxs-lookup"><span data-stu-id="98609-118">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98609-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="98609-119">Example</span></span>  
 <span data-ttu-id="98609-120">Následující kód ukazuje kompletní příklad.</span><span class="sxs-lookup"><span data-stu-id="98609-120">The following code shows a complete example.</span></span> <span data-ttu-id="98609-121">Další informace o tom, jak nastavit projekt, který přistupuje k rozhraní Office API, najdete v tématu [Jak získat přístup k objektům Interop C# sady Office pomocí funkcí](./how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="98609-121">For more information about how to set up a project that accesses the Office API, see [How to access Office interop objects by using C# features](./how-to-access-office-onterop-objects.md).</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="98609-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98609-122">See also</span></span>

- [<span data-ttu-id="98609-123">Pojmenované a nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="98609-123">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="98609-124">dynamic</span><span class="sxs-lookup"><span data-stu-id="98609-124">dynamic</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="98609-125">Použití typu dynamic</span><span class="sxs-lookup"><span data-stu-id="98609-125">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="98609-126">Použití pojmenovaných a nepovinných argumentů v programování pro Office</span><span class="sxs-lookup"><span data-stu-id="98609-126">How to use named and optional arguments in Office programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="98609-127">Přístup k objektům Interop sady Office pomocí C# funkcí</span><span class="sxs-lookup"><span data-stu-id="98609-127">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)
- [<span data-ttu-id="98609-128">Návod: programování pro Office</span><span class="sxs-lookup"><span data-stu-id="98609-128">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
