---
title: 'Postupy: Použití obecné třídy (Visual Basic)'
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
ms.openlocfilehash: 3bcf7b0556ef2c5d9b8f82442815672b2b3cde86
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43391052"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a><span data-ttu-id="09541-102">Postupy: Použití obecné třídy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09541-102">How to: Use a Generic Class (Visual Basic)</span></span>
<span data-ttu-id="09541-103">Třída, která přebírá *parametry typu* se volá *obecnou třídu*.</span><span class="sxs-lookup"><span data-stu-id="09541-103">A class that takes *type parameters* is called a *generic class*.</span></span> <span data-ttu-id="09541-104">Pokud používáte obecnou třídu, můžete vygenerovat *vytvořená třída* z něj zadáním *argument typu* pro každou z těchto parametrů.</span><span class="sxs-lookup"><span data-stu-id="09541-104">If you are using a generic class, you can generate a *constructed class* from it by supplying a *type argument* for each of these parameters.</span></span> <span data-ttu-id="09541-105">Pak může deklarovat proměnnou typu vytvořeného třídy, a můžete vytvořit instanci třídy konstruovaný a přiřaďte ho k proměnné.</span><span class="sxs-lookup"><span data-stu-id="09541-105">You can then declare a variable of the constructed class type, and you can create an instance of the constructed class and assign it to that variable.</span></span>  
  
 <span data-ttu-id="09541-106">Kromě tříd můžete také definovat a použijte obecné struktury, rozhraní, postupy a delegáti.</span><span class="sxs-lookup"><span data-stu-id="09541-106">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
 <span data-ttu-id="09541-107">Následující postup používá obecné třídy definované v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] a vytvoří instanci z něj.</span><span class="sxs-lookup"><span data-stu-id="09541-107">The following procedure takes a generic class defined in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] and creates an instance from it.</span></span>  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a><span data-ttu-id="09541-108">Použít třídu, která přebírá parametr typu</span><span class="sxs-lookup"><span data-stu-id="09541-108">To use a class that takes a type parameter</span></span>  
  
1.  <span data-ttu-id="09541-109">Na začátku zdrojového souboru, patří [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) import <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="09541-109">At the beginning of your source file, include an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to import the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="09541-110">To umožňuje odkazovat <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> třídy bez nutnosti k plnému určení ho, aby ho odlišil od jiných tříd fronty jako <xref:System.Collections.Queue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="09541-110">This allows you to refer to the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class without having to fully qualify it to differentiate it from other queue classes such as <xref:System.Collections.Queue?displayProperty=nameWithType>.</span></span>  
  
2.  <span data-ttu-id="09541-111">Vytvořte objekt běžným způsobem, ale přidat `(Of` `type``)` bezprostředně za název třídy.</span><span class="sxs-lookup"><span data-stu-id="09541-111">Create the object in the normal way, but add `(Of` `type``)` immediately after the class name.</span></span>  
  
     <span data-ttu-id="09541-112">Následující příklad používá stejnou třídu (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) vytvořte dva objekty fronty, které obsahují položky z různých datových typů.</span><span class="sxs-lookup"><span data-stu-id="09541-112">The following example uses the same class (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) to create two queue objects that hold items of different data types.</span></span> <span data-ttu-id="09541-113">Přidá položky do konce každou frontu a následně odebere a zobrazí položky z přední části každou frontu.</span><span class="sxs-lookup"><span data-stu-id="09541-113">It adds items to the end of each queue and then removes and displays items from the front of each queue.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#9](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-use-a-generic-class_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="09541-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="09541-114">See Also</span></span>  
 [<span data-ttu-id="09541-115">Datové typy</span><span class="sxs-lookup"><span data-stu-id="09541-115">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="09541-116">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="09541-116">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="09541-117">Jazyková nezávislost a jazykově nezávislé komponenty</span><span class="sxs-lookup"><span data-stu-id="09541-117">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)  
 [<span data-ttu-id="09541-118">z</span><span class="sxs-lookup"><span data-stu-id="09541-118">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)  
 [<span data-ttu-id="09541-119">Příkaz Imports (obor názvů a typ .NET)</span><span class="sxs-lookup"><span data-stu-id="09541-119">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="09541-120">Postupy: Definice třídy, která poskytne identické funkce pro různé datové typy</span><span class="sxs-lookup"><span data-stu-id="09541-120">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [<span data-ttu-id="09541-121">Iterátory</span><span class="sxs-lookup"><span data-stu-id="09541-121">Iterators</span></span>](https://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)
