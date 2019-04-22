---
title: Typy metod manipulace s řetězci v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: 44eb101ebdfeb316958a659107190ef1fc84df44
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58821150"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="488fd-102">Typy metod manipulace s řetězci v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="488fd-102">Types of String Manipulation Methods in Visual Basic</span></span>
<span data-ttu-id="488fd-103">Existuje několik různých způsobů, jak analyzovat a manipulaci s řetězci.</span><span class="sxs-lookup"><span data-stu-id="488fd-103">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="488fd-104">Některé metody jsou součástí jazyka Visual Basic a jiné jsou spojené `String` třídy.</span><span class="sxs-lookup"><span data-stu-id="488fd-104">Some of the methods are a part of the Visual Basic language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="488fd-105">Jazyk Visual Basic a rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="488fd-105">Visual Basic Language and the .NET Framework</span></span>  
 <span data-ttu-id="488fd-106">Metody jazyka Visual Basic se používají jako vlastní funkce jazyka.</span><span class="sxs-lookup"><span data-stu-id="488fd-106">Visual Basic methods are used as inherent functions of the language.</span></span> <span data-ttu-id="488fd-107">Může být použít bez kvalifikace v kódu.</span><span class="sxs-lookup"><span data-stu-id="488fd-107">They may be used without qualification in your code.</span></span> <span data-ttu-id="488fd-108">Následující příklad ukazuje typické použití příkazu zacházení s řetězci jazyka Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="488fd-108">The following example shows typical use of a Visual Basic string-manipulation command:</span></span>  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 <span data-ttu-id="488fd-109">V tomto příkladu `Mid` funkce provede operaci s přímým přístupem na `aString` a přiřadí hodnotu k `bString`.</span><span class="sxs-lookup"><span data-stu-id="488fd-109">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="488fd-110">Seznam metod manipulace s řetězci jazyka Visual Basic najdete v tématu [souhrn manipulace s řetězci](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span><span class="sxs-lookup"><span data-stu-id="488fd-110">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="488fd-111">Sdílené metody a Instance metody</span><span class="sxs-lookup"><span data-stu-id="488fd-111">Shared Methods and Instance Methods</span></span>  
 <span data-ttu-id="488fd-112">Můžete také manipulaci s řetězci s metodami `String` třídy.</span><span class="sxs-lookup"><span data-stu-id="488fd-112">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="488fd-113">Existují dva typy metod v `String`: *sdílené* metody a *instance* metody.</span><span class="sxs-lookup"><span data-stu-id="488fd-113">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="488fd-114">Sdílené metody</span><span class="sxs-lookup"><span data-stu-id="488fd-114">Shared Methods</span></span>  
 <span data-ttu-id="488fd-115">Sdílené metody je metoda, která vyplývá ze `String` třídu a nevyžaduje, aby instance této třídy pro práci.</span><span class="sxs-lookup"><span data-stu-id="488fd-115">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="488fd-116">Tyto metody mohou být kvalifikovány názvem třídy (`String`), nikoli s instancí `String` třídy.</span><span class="sxs-lookup"><span data-stu-id="488fd-116">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="488fd-117">Příklad:</span><span class="sxs-lookup"><span data-stu-id="488fd-117">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 <span data-ttu-id="488fd-118">V předchozím příkladu <xref:System.String.Copy%2A?displayProperty=nameWithType> metoda je statická metoda, která funguje na výraz ho dostane a přiřadí výslednou hodnotu pro `bString`.</span><span class="sxs-lookup"><span data-stu-id="488fd-118">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="488fd-119">Instance metody</span><span class="sxs-lookup"><span data-stu-id="488fd-119">Instance Methods</span></span>  
 <span data-ttu-id="488fd-120">Metody instance, naopak vyplývají z konkrétní instanci `String` a musí být kvalifikován s názvem instance.</span><span class="sxs-lookup"><span data-stu-id="488fd-120">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="488fd-121">Příklad:</span><span class="sxs-lookup"><span data-stu-id="488fd-121">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 <span data-ttu-id="488fd-122">V tomto příkladu <xref:System.String.Substring%2A?displayProperty=nameWithType> je metoda metodou instance `String` (to znamená `aString`).</span><span class="sxs-lookup"><span data-stu-id="488fd-122">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="488fd-123">Provádí operaci na `aString` a přiřadí tuto hodnotu `bString`.</span><span class="sxs-lookup"><span data-stu-id="488fd-123">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="488fd-124">Další informace najdete v tématu v dokumentaci <xref:System.String> třídy.</span><span class="sxs-lookup"><span data-stu-id="488fd-124">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="488fd-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="488fd-125">See also</span></span>

- [<span data-ttu-id="488fd-126">Úvod do řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="488fd-126">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
