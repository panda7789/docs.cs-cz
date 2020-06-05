---
title: Typy metod pro manipulaci s řetězci
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: aba9af9c699cf8d07862c5d2967902bec1623500
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363756"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="4dcd0-102">Typy metod manipulace s řetězci v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4dcd0-102">Types of String Manipulation Methods in Visual Basic</span></span>
<span data-ttu-id="4dcd0-103">Existuje několik různých způsobů, jak analyzovat a manipulovat s řetězci.</span><span class="sxs-lookup"><span data-stu-id="4dcd0-103">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="4dcd0-104">Některé metody jsou součástí jazyka Visual Basic a další jsou podstatou `String` třídy.</span><span class="sxs-lookup"><span data-stu-id="4dcd0-104">Some of the methods are a part of the Visual Basic language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="4dcd0-105">Visual Basic jazyk a .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4dcd0-105">Visual Basic Language and the .NET Framework</span></span>  
 <span data-ttu-id="4dcd0-106">Metody Visual Basic jsou používány jako podstatné funkce jazyka.</span><span class="sxs-lookup"><span data-stu-id="4dcd0-106">Visual Basic methods are used as inherent functions of the language.</span></span> <span data-ttu-id="4dcd0-107">Je možné je použít bez kvalifikace ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="4dcd0-107">They may be used without qualification in your code.</span></span> <span data-ttu-id="4dcd0-108">Následující příklad ukazuje typické použití Visual Basic příkazu pro manipulaci s řetězci:</span><span class="sxs-lookup"><span data-stu-id="4dcd0-108">The following example shows typical use of a Visual Basic string-manipulation command:</span></span>  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 <span data-ttu-id="4dcd0-109">V tomto příkladu `Mid` funkce provede přímou operaci se zapnutou `aString` a přiřadí hodnotu `bString` .</span><span class="sxs-lookup"><span data-stu-id="4dcd0-109">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="4dcd0-110">Seznam metod manipulace s řetězci Visual Basic naleznete v tématu [Souhrn manipulace s řetězci](../../../language-reference/keywords/string-manipulation-summary.md).</span><span class="sxs-lookup"><span data-stu-id="4dcd0-110">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="4dcd0-111">Sdílené metody a metody instance</span><span class="sxs-lookup"><span data-stu-id="4dcd0-111">Shared Methods and Instance Methods</span></span>  
 <span data-ttu-id="4dcd0-112">Můžete také manipulovat s řetězci pomocí metod `String` třídy.</span><span class="sxs-lookup"><span data-stu-id="4dcd0-112">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="4dcd0-113">Existují dva typy metod v `String` : *sdílené* metody a metody *instance* .</span><span class="sxs-lookup"><span data-stu-id="4dcd0-113">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="4dcd0-114">Sdílené metody</span><span class="sxs-lookup"><span data-stu-id="4dcd0-114">Shared Methods</span></span>  
 <span data-ttu-id="4dcd0-115">Sdílená metoda je metoda, která vychází z `String` samotné třídy a nevyžaduje, aby instance této třídy fungovala.</span><span class="sxs-lookup"><span data-stu-id="4dcd0-115">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="4dcd0-116">Tyto metody mohou být kvalifikovány s názvem třídy ( `String` ) spíše než instancí `String` třídy.</span><span class="sxs-lookup"><span data-stu-id="4dcd0-116">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="4dcd0-117">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4dcd0-117">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 <span data-ttu-id="4dcd0-118">V předchozím příkladu <xref:System.String.Copy%2A?displayProperty=nameWithType> je metoda statickou metodou, která funguje na výrazu, který je dán, a přiřazuje výslednou hodnotu k `bString` .</span><span class="sxs-lookup"><span data-stu-id="4dcd0-118">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="4dcd0-119">Metody instance</span><span class="sxs-lookup"><span data-stu-id="4dcd0-119">Instance Methods</span></span>  
 <span data-ttu-id="4dcd0-120">Metody instance, naproti tomu stonk z konkrétní instance `String` a musí být kvalifikovány názvem instance.</span><span class="sxs-lookup"><span data-stu-id="4dcd0-120">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="4dcd0-121">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4dcd0-121">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 <span data-ttu-id="4dcd0-122">V tomto příkladu <xref:System.String.Substring%2A?displayProperty=nameWithType> je metoda metodou instance třídy `String` (to znamená, `aString` ).</span><span class="sxs-lookup"><span data-stu-id="4dcd0-122">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="4dcd0-123">Provede operaci na `aString` a přiřadí tuto hodnotu k `bString` .</span><span class="sxs-lookup"><span data-stu-id="4dcd0-123">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="4dcd0-124">Další informace naleznete v dokumentaci pro <xref:System.String> třídu.</span><span class="sxs-lookup"><span data-stu-id="4dcd0-124">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dcd0-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="4dcd0-125">See also</span></span>

- [<span data-ttu-id="4dcd0-126">Představení řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4dcd0-126">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
