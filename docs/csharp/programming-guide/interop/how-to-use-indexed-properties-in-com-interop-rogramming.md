---
title: Použití indexovaných vlastností v programování mezi opcemi com - Průvodce programováním c#
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 864e2274f0e0e79b4843e0bb67b5c4384eac8588
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712062"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="e41e5-102">Použití indexovaných vlastností v programování interop com (C# Programovací průvodce)</span><span class="sxs-lookup"><span data-stu-id="e41e5-102">How to use indexed properties in COM interop programming (C# Programming Guide)</span></span>
<span data-ttu-id="e41e5-103">*Indexované vlastnosti* zlepšují způsob, jakým jsou vlastnosti COM, které mají parametry, spotřebovány v programování jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="e41e5-103">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="e41e5-104">Indexované vlastnosti spolupracují s dalšími funkcemi v jazyce Visual C#, jako jsou [pojmenované a volitelné argumenty](../classes-and-structs/named-and-optional-arguments.md), nový typ ([dynamický](../../language-reference/builtin-types/reference-types.md)a [vložené informace o typu](../../../standard/assembly/embed-types-visual-studio.md), a vylepšují tak programování sady Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="e41e5-104">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../language-reference/builtin-types/reference-types.md)), and [embedded type information](../../../standard/assembly/embed-types-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="e41e5-105">V dřívějších verzích jazyka C# jsou metody `get` přístupné jako vlastnosti `set` pouze v případě, že metoda nemá žádné parametry a metoda má jeden a pouze jeden parametr hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e41e5-105">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="e41e5-106">Však ne všechny vlastnosti COM splňují tato omezení.</span><span class="sxs-lookup"><span data-stu-id="e41e5-106">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="e41e5-107">Například vlastnost <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> aplikace Excel `get` má přistupující objekt, který vyžaduje parametr pro název rozsahu.</span><span class="sxs-lookup"><span data-stu-id="e41e5-107">For example, the Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="e41e5-108">V minulosti, protože jste `Range` nemohli přistupovat přímo k `get_Range` vlastnosti, jste museli použít metodu místo, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e41e5-108">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 <span data-ttu-id="e41e5-109">Indexované vlastnosti umožňují místo toho napsat následující:</span><span class="sxs-lookup"><span data-stu-id="e41e5-109">Indexed properties enable you to write the following instead:</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> <span data-ttu-id="e41e5-110">Předchozí příklad také používá funkci [volitelné argumenty,](../classes-and-structs/named-and-optional-arguments.md) která `Type.Missing`umožňuje vynechat .</span><span class="sxs-lookup"><span data-stu-id="e41e5-110">The previous example also uses the [optional arguments](../classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="e41e5-111">Podobně nastavit hodnotu `Value` vlastnosti objektu <xref:Microsoft.Office.Interop.Excel.Range> v C# 3.0 a starší, jsou požadovány dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="e41e5-111">Similarly to set the value of the `Value` property of a <xref:Microsoft.Office.Interop.Excel.Range> object in C# 3.0 and earlier, two arguments are required.</span></span> <span data-ttu-id="e41e5-112">Jeden poskytuje argument pro volitelný parametr, který určuje typ hodnoty rozsahu.</span><span class="sxs-lookup"><span data-stu-id="e41e5-112">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="e41e5-113">Druhý poskytuje hodnotu vlastnosti. `Value`</span><span class="sxs-lookup"><span data-stu-id="e41e5-113">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="e41e5-114">Následující příklady ilustrují tyto techniky.</span><span class="sxs-lookup"><span data-stu-id="e41e5-114">The following examples illustrate these techniques.</span></span> <span data-ttu-id="e41e5-115">Obě nastaví hodnotu buňky `Name`A1 na hodnotu .</span><span class="sxs-lookup"><span data-stu-id="e41e5-115">Both set the value of the A1 cell to `Name`.</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 <span data-ttu-id="e41e5-116">Indexované vlastnosti umožňují místo toho napsat následující kód.</span><span class="sxs-lookup"><span data-stu-id="e41e5-116">Indexed properties enable you to write the following code instead.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 <span data-ttu-id="e41e5-117">Vlastní indexované vlastnosti nelze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="e41e5-117">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="e41e5-118">Funkce podporuje pouze spotřebu existujících indexovaných vlastností.</span><span class="sxs-lookup"><span data-stu-id="e41e5-118">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e41e5-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="e41e5-119">Example</span></span>  
 <span data-ttu-id="e41e5-120">Následující kód ukazuje úplný příklad.</span><span class="sxs-lookup"><span data-stu-id="e41e5-120">The following code shows a complete example.</span></span> <span data-ttu-id="e41e5-121">Další informace o nastavení projektu, který přistupuje k rozhraní API sady Office, naleznete v tématu [Přístup k objektům interop sady Office pomocí funkcí jazyka C#](./how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="e41e5-121">For more information about how to set up a project that accesses the Office API, see [How to access Office interop objects by using C# features](./how-to-access-office-onterop-objects.md).</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="e41e5-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="e41e5-122">See also</span></span>

- [<span data-ttu-id="e41e5-123">Pojmenované a nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="e41e5-123">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="e41e5-124">Dynamické</span><span class="sxs-lookup"><span data-stu-id="e41e5-124">dynamic</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="e41e5-125">Použití typu dynamic</span><span class="sxs-lookup"><span data-stu-id="e41e5-125">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="e41e5-126">Použití pojmenovaných a volitelných argumentů v programování sady Office</span><span class="sxs-lookup"><span data-stu-id="e41e5-126">How to use named and optional arguments in Office programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="e41e5-127">Jak získat přístup k objektům interoperability Office pomocí funkcí jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e41e5-127">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)
- [<span data-ttu-id="e41e5-128">Návod: Programování v Office</span><span class="sxs-lookup"><span data-stu-id="e41e5-128">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
