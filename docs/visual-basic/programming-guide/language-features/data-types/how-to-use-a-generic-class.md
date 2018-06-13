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
ms.openlocfilehash: adea9f7e7dbbc2317e5b857a5153e3ec67d63344
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647914"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a><span data-ttu-id="22bcb-102">Postupy: Použití obecné třídy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22bcb-102">How to: Use a Generic Class (Visual Basic)</span></span>
<span data-ttu-id="22bcb-103">Třída, která přebírá *parametry typu* nazývá *– obecná třída*.</span><span class="sxs-lookup"><span data-stu-id="22bcb-103">A class that takes *type parameters* is called a *generic class*.</span></span> <span data-ttu-id="22bcb-104">Pokud používáte obecné třídy, můžete vygenerovat *sestavený třída* z něj zadáním *argument typu* pro každou z těchto parametrů.</span><span class="sxs-lookup"><span data-stu-id="22bcb-104">If you are using a generic class, you can generate a *constructed class* from it by supplying a *type argument* for each of these parameters.</span></span> <span data-ttu-id="22bcb-105">Potom můžete deklarovat proměnnou typu sestavené třídy a můžete vytvořit instance třídy vytvořený a přiřadit ji k této proměnné.</span><span class="sxs-lookup"><span data-stu-id="22bcb-105">You can then declare a variable of the constructed class type, and you can create an instance of the constructed class and assign it to that variable.</span></span>  
  
 <span data-ttu-id="22bcb-106">Kromě třídy můžete také definovat a použít obecné struktury, rozhraní, postupy a delegáti.</span><span class="sxs-lookup"><span data-stu-id="22bcb-106">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
 <span data-ttu-id="22bcb-107">Následující postup trvá obecné třídy definované v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] a vytvoří instanci z něj.</span><span class="sxs-lookup"><span data-stu-id="22bcb-107">The following procedure takes a generic class defined in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] and creates an instance from it.</span></span>  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a><span data-ttu-id="22bcb-108">Použití třídy, která přebírá parametr typu</span><span class="sxs-lookup"><span data-stu-id="22bcb-108">To use a class that takes a type parameter</span></span>  
  
1.  <span data-ttu-id="22bcb-109">Na začátku zdrojový soubor, patří [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) k importu <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="22bcb-109">At the beginning of your source file, include an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to import the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="22bcb-110">To umožňuje odkazovat <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> třída bez nutnosti k plnému určení ho k odlišení certifikátu od jiné třídy fronty, jako <xref:System.Collections.Queue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="22bcb-110">This allows you to refer to the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class without having to fully qualify it to differentiate it from other queue classes such as <xref:System.Collections.Queue?displayProperty=nameWithType>.</span></span>  
  
2.  <span data-ttu-id="22bcb-111">Vytvořit objekt běžným způsobem, ale přidat `(Of` `type``)` ihned po název třídy.</span><span class="sxs-lookup"><span data-stu-id="22bcb-111">Create the object in the normal way, but add `(Of` `type``)` immediately after the class name.</span></span>  
  
     <span data-ttu-id="22bcb-112">Následující příklad používá stejnou třídu (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) k vytvoření dvou objektů fronty, které mají různé datové typy položky.</span><span class="sxs-lookup"><span data-stu-id="22bcb-112">The following example uses the same class (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) to create two queue objects that hold items of different data types.</span></span> <span data-ttu-id="22bcb-113">Přidá na konec každé fronty položky a poté odstraní a zobrazí položky z před každou frontu.</span><span class="sxs-lookup"><span data-stu-id="22bcb-113">It adds items to the end of each queue and then removes and displays items from the front of each queue.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#9](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-use-a-generic-class_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="22bcb-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="22bcb-114">See Also</span></span>  
 [<span data-ttu-id="22bcb-115">Datové typy</span><span class="sxs-lookup"><span data-stu-id="22bcb-115">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="22bcb-116">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="22bcb-116">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="22bcb-117">Jazyková nezávislost a jazykově nezávislé komponenty</span><span class="sxs-lookup"><span data-stu-id="22bcb-117">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)  
 [<span data-ttu-id="22bcb-118">z</span><span class="sxs-lookup"><span data-stu-id="22bcb-118">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)  
 [<span data-ttu-id="22bcb-119">Příkaz Imports (obor názvů a typ .NET)</span><span class="sxs-lookup"><span data-stu-id="22bcb-119">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="22bcb-120">Postupy: Definice třídy, která poskytne identické funkce pro různé datové typy</span><span class="sxs-lookup"><span data-stu-id="22bcb-120">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [<span data-ttu-id="22bcb-121">Iterátory</span><span class="sxs-lookup"><span data-stu-id="22bcb-121">Iterators</span></span>](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)
