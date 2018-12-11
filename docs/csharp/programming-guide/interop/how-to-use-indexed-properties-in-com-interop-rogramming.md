---
title: 'Postupy: Použití indexovaných vlastností při programování vzájemné spolupráce COM - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 58b3b2646fec0284dc3e04c152b183ce05e05932
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245373"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="691b1-102">Postupy: Použití indexovaných vlastností při programování v modelu COM Interop (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="691b1-102">How to: Use Indexed Properties in COM Interop Programming (C# Programming Guide)</span></span>
<span data-ttu-id="691b1-103">*Indexované vlastnosti* zlepšit způsob, ve které modelu COM jsou vlastnosti, které mají parametry spotřebovány v programování v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="691b1-103">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="691b1-104">Indexované vlastnosti pracují společně pomocí dalších funkcí v jazyce Visual C#, jako například [pojmenované a nepovinné argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), nový typ ([dynamické](../../../csharp/language-reference/keywords/dynamic.md)), a [vložené informace o typu](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)do Vylepšete programování pro sadu Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="691b1-104">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../../csharp/language-reference/keywords/dynamic.md)), and [embedded type information](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="691b1-105">V dřívějších verzích jazyka C#, jsou dostupné jako vlastnosti pouze v případě metody `get` metoda nemá žádné parametry a `set` metoda má jeden a pouze jeden parametr hodnoty.</span><span class="sxs-lookup"><span data-stu-id="691b1-105">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="691b1-106">Ale ne všechny vlastnosti modelu COM splnění těchto omezení.</span><span class="sxs-lookup"><span data-stu-id="691b1-106">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="691b1-107">Například v aplikaci Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> má vlastnost `get` přístupový objekt, který vyžaduje parametr pro název oblasti.</span><span class="sxs-lookup"><span data-stu-id="691b1-107">For example, the Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="691b1-108">V minulosti protože nelze získat přístup k `Range` vlastnost přímo, musíte použít `get_Range` metoda místo toho, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="691b1-108">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]  
  
 <span data-ttu-id="691b1-109">Indexované vlastnosti umožňují také napsat následující místo:</span><span class="sxs-lookup"><span data-stu-id="691b1-109">Indexed properties enable you to write the following instead:</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]  
  
> [!NOTE]
>  <span data-ttu-id="691b1-110">V předchozím příkladu se používá také [volitelné argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) funkci, která umožňuje vynechat `Type.Missing`.</span><span class="sxs-lookup"><span data-stu-id="691b1-110">The previous example also uses the [optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="691b1-111">Podobně se nastavit hodnotu `Value` vlastnost <xref:Microsoft.Office.Interop.Excel.Range> objektu v aplikaci Visual C# 2008 a dřívějších verzí se vyžadují dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="691b1-111">Similarly to set the value of the `Value` property of a <xref:Microsoft.Office.Interop.Excel.Range> object in Visual C# 2008 and earlier, two arguments are required.</span></span> <span data-ttu-id="691b1-112">Poskytuje jeden argument pro volitelný parametr, který určuje typ hodnoty rozsahu.</span><span class="sxs-lookup"><span data-stu-id="691b1-112">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="691b1-113">Druhá hodnota poskytuje `Value` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="691b1-113">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="691b1-114">Následující příklady znázorňují těchto technik.</span><span class="sxs-lookup"><span data-stu-id="691b1-114">The following examples illustrate these techniques.</span></span> <span data-ttu-id="691b1-115">Obě hodnotu buňky A1 do `Name`.</span><span class="sxs-lookup"><span data-stu-id="691b1-115">Both set the value of the A1 cell to `Name`.</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]  
  
 <span data-ttu-id="691b1-116">Indexované vlastnosti umožňují místo toho zadejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="691b1-116">Indexed properties enable you to write the following code instead.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]  
  
 <span data-ttu-id="691b1-117">Nelze vytvořit indexované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="691b1-117">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="691b1-118">Tato funkce podporuje pouze využití stávající indexované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="691b1-118">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="691b1-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="691b1-119">Example</span></span>  
 <span data-ttu-id="691b1-120">Následující kód ukazuje kompletní příklad.</span><span class="sxs-lookup"><span data-stu-id="691b1-120">The following code shows a complete example.</span></span> <span data-ttu-id="691b1-121">Další informace o tom, jak nastavit projekt, který má přístup k rozhraní API pro Office naleznete v tématu [jak: Přístup k objektům Interop sady Office pomocí Vizuálu C# funkce](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="691b1-121">For more information about how to set up a project that accesses the Office API, see [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="691b1-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="691b1-122">See Also</span></span>

- [<span data-ttu-id="691b1-123">Pojmenované a nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="691b1-123">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
- [<span data-ttu-id="691b1-124">dynamic</span><span class="sxs-lookup"><span data-stu-id="691b1-124">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
- [<span data-ttu-id="691b1-125">Použití typu dynamic</span><span class="sxs-lookup"><span data-stu-id="691b1-125">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)  
- [<span data-ttu-id="691b1-126">Postupy: Použití pojmenovaných a nepovinných argumentů v programování pro Office</span><span class="sxs-lookup"><span data-stu-id="691b1-126">How to: Use Named and Optional Arguments in Office Programming</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)  
- [<span data-ttu-id="691b1-127">Postupy: Přístup k objektům Interop sady Office pomocí Vizuálu C# funkce</span><span class="sxs-lookup"><span data-stu-id="691b1-127">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
- [<span data-ttu-id="691b1-128">Návod: Programování pro systém Office</span><span class="sxs-lookup"><span data-stu-id="691b1-128">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
