---
title: 'Postupy: Použití obecné třídy'
ms.date: 07/20/2015
helpviewer_keywords:
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- generic parameters
- data type parameters
- generics [Visual Basic], about generics
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], creating generic types
- data type arguments
- parameters [Visual Basic], data type
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
ms.openlocfilehash: 87ca0da5095484615666cda505b4f7678d8160de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350063"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a><span data-ttu-id="bceb0-102">Postupy: Použití obecné třídy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bceb0-102">How to: Use a Generic Class (Visual Basic)</span></span>
<span data-ttu-id="bceb0-103">A class that takes *type parameters* is called a *generic class*.</span><span class="sxs-lookup"><span data-stu-id="bceb0-103">A class that takes *type parameters* is called a *generic class*.</span></span> <span data-ttu-id="bceb0-104">If you are using a generic class, you can generate a *constructed class* from it by supplying a *type argument* for each of these parameters.</span><span class="sxs-lookup"><span data-stu-id="bceb0-104">If you are using a generic class, you can generate a *constructed class* from it by supplying a *type argument* for each of these parameters.</span></span> <span data-ttu-id="bceb0-105">You can then declare a variable of the constructed class type, and you can create an instance of the constructed class and assign it to that variable.</span><span class="sxs-lookup"><span data-stu-id="bceb0-105">You can then declare a variable of the constructed class type, and you can create an instance of the constructed class and assign it to that variable.</span></span>  
  
 <span data-ttu-id="bceb0-106">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span><span class="sxs-lookup"><span data-stu-id="bceb0-106">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
 <span data-ttu-id="bceb0-107">The following procedure takes a generic class defined in the .NET Framework and creates an instance from it.</span><span class="sxs-lookup"><span data-stu-id="bceb0-107">The following procedure takes a generic class defined in the .NET Framework and creates an instance from it.</span></span>  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a><span data-ttu-id="bceb0-108">To use a class that takes a type parameter</span><span class="sxs-lookup"><span data-stu-id="bceb0-108">To use a class that takes a type parameter</span></span>  
  
1. <span data-ttu-id="bceb0-109">At the beginning of your source file, include an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to import the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="bceb0-109">At the beginning of your source file, include an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to import the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="bceb0-110">This allows you to refer to the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class without having to fully qualify it to differentiate it from other queue classes such as <xref:System.Collections.Queue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bceb0-110">This allows you to refer to the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class without having to fully qualify it to differentiate it from other queue classes such as <xref:System.Collections.Queue?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="bceb0-111">Create the object in the normal way, but add `(Of type)` immediately after the class name.</span><span class="sxs-lookup"><span data-stu-id="bceb0-111">Create the object in the normal way, but add `(Of type)` immediately after the class name.</span></span>  
  
     <span data-ttu-id="bceb0-112">The following example uses the same class (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) to create two queue objects that hold items of different data types.</span><span class="sxs-lookup"><span data-stu-id="bceb0-112">The following example uses the same class (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) to create two queue objects that hold items of different data types.</span></span> <span data-ttu-id="bceb0-113">It adds items to the end of each queue and then removes and displays items from the front of each queue.</span><span class="sxs-lookup"><span data-stu-id="bceb0-113">It adds items to the end of each queue and then removes and displays items from the front of each queue.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="bceb0-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bceb0-114">See also</span></span>

- [<span data-ttu-id="bceb0-115">Datové typy</span><span class="sxs-lookup"><span data-stu-id="bceb0-115">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="bceb0-116">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bceb0-116">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="bceb0-117">Jazyková nezávislost a jazykově nezávislé komponenty</span><span class="sxs-lookup"><span data-stu-id="bceb0-117">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="bceb0-118">Of</span><span class="sxs-lookup"><span data-stu-id="bceb0-118">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)
- [<span data-ttu-id="bceb0-119">Příkaz Imports (obor názvů a typ .NET)</span><span class="sxs-lookup"><span data-stu-id="bceb0-119">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="bceb0-120">Postupy: Definice třídy, která poskytne identické funkce pro různé datové typy</span><span class="sxs-lookup"><span data-stu-id="bceb0-120">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [<span data-ttu-id="bceb0-121">Iterátory</span><span class="sxs-lookup"><span data-stu-id="bceb0-121">Iterators</span></span>](../../../../visual-basic/programming-guide/concepts/iterators.md)
