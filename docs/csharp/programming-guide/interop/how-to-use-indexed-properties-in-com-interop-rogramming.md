---
title: 'Postupy: Použití indexovaných vlastností při programování vzájemné spolupráce COM - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: d2b992131bb5722b8a10ec4a71fc42602c98a12c
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347628"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="f0eac-102">Postupy: Použití indexovaných vlastností při programování v modelu COM Interop (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="f0eac-102">How to: Use Indexed Properties in COM Interop Programming (C# Programming Guide)</span></span>
<span data-ttu-id="f0eac-103">*Indexované vlastnosti* zlepšit způsob, ve které modelu COM jsou vlastnosti, které mají parametry spotřebovány v programování v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="f0eac-103">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="f0eac-104">Indexované vlastnosti pracují společně pomocí dalších funkcí v jazyce Visual C#, jako například [pojmenované a nepovinné argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), nový typ ([dynamické](../../../csharp/language-reference/keywords/dynamic.md)), a [vložené informace o typu](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)do Vylepšete programování pro sadu Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="f0eac-104">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../../csharp/language-reference/keywords/dynamic.md)), and [embedded type information](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="f0eac-105">V dřívějších verzích jazyka C#, jsou dostupné jako vlastnosti pouze v případě metody `get` metoda nemá žádné parametry a `set` metoda má jeden a pouze jeden parametr hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f0eac-105">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="f0eac-106">Ale ne všechny vlastnosti modelu COM splnění těchto omezení.</span><span class="sxs-lookup"><span data-stu-id="f0eac-106">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="f0eac-107">Například v aplikaci Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> má vlastnost `get` přístupový objekt, který vyžaduje parametr pro název oblasti.</span><span class="sxs-lookup"><span data-stu-id="f0eac-107">For example, the Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="f0eac-108">V minulosti protože nelze získat přístup k `Range` vlastnost přímo, musíte použít `get_Range` metoda místo toho, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f0eac-108">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 <span data-ttu-id="f0eac-109">Indexované vlastnosti umožňují také napsat následující místo:</span><span class="sxs-lookup"><span data-stu-id="f0eac-109">Indexed properties enable you to write the following instead:</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
>  <span data-ttu-id="f0eac-110">V předchozím příkladu se používá také [volitelné argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) funkci, která umožňuje vynechat `Type.Missing`.</span><span class="sxs-lookup"><span data-stu-id="f0eac-110">The previous example also uses the [optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="f0eac-111">Podobně se nastavit hodnotu `Value` vlastnost <xref:Microsoft.Office.Interop.Excel.Range> objekt C# 3.0 a starší, se vyžadují dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="f0eac-111">Similarly to set the value of the `Value` property of a <xref:Microsoft.Office.Interop.Excel.Range> object in C# 3.0 and earlier, two arguments are required.</span></span> <span data-ttu-id="f0eac-112">Poskytuje jeden argument pro volitelný parametr, který určuje typ hodnoty rozsahu.</span><span class="sxs-lookup"><span data-stu-id="f0eac-112">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="f0eac-113">Druhá hodnota poskytuje `Value` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f0eac-113">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="f0eac-114">Následující příklady znázorňují těchto technik.</span><span class="sxs-lookup"><span data-stu-id="f0eac-114">The following examples illustrate these techniques.</span></span> <span data-ttu-id="f0eac-115">Obě hodnotu buňky A1 do `Name`.</span><span class="sxs-lookup"><span data-stu-id="f0eac-115">Both set the value of the A1 cell to `Name`.</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 <span data-ttu-id="f0eac-116">Indexované vlastnosti umožňují místo toho zadejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="f0eac-116">Indexed properties enable you to write the following code instead.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 <span data-ttu-id="f0eac-117">Nelze vytvořit indexované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f0eac-117">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="f0eac-118">Tato funkce podporuje pouze využití stávající indexované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f0eac-118">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0eac-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="f0eac-119">Example</span></span>  
 <span data-ttu-id="f0eac-120">Následující kód ukazuje kompletní příklad.</span><span class="sxs-lookup"><span data-stu-id="f0eac-120">The following code shows a complete example.</span></span> <span data-ttu-id="f0eac-121">Další informace o tom, jak nastavit projekt, který má přístup k rozhraní API pro Office naleznete v tématu [jak: Přístup k objektům Interop sady Office pomocí Vizuálu C# funkce](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="f0eac-121">For more information about how to set up a project that accesses the Office API, see [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="f0eac-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f0eac-122">See also</span></span>

- [<span data-ttu-id="f0eac-123">Pojmenované a nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="f0eac-123">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="f0eac-124">dynamic</span><span class="sxs-lookup"><span data-stu-id="f0eac-124">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)
- [<span data-ttu-id="f0eac-125">Použití typu dynamic</span><span class="sxs-lookup"><span data-stu-id="f0eac-125">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="f0eac-126">Postupy: Použití pojmenovaných a nepovinných argumentů v programování pro Office</span><span class="sxs-lookup"><span data-stu-id="f0eac-126">How to: Use Named and Optional Arguments in Office Programming</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="f0eac-127">Postupy: Přístup k objektům Interop sady Office pomocí Vizuálu C# funkce</span><span class="sxs-lookup"><span data-stu-id="f0eac-127">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)
- [<span data-ttu-id="f0eac-128">Návod: Programování pro systém Office</span><span class="sxs-lookup"><span data-stu-id="f0eac-128">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
