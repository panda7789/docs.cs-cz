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
# <a name="how-to-use-a-generic-class-visual-basic"></a><span data-ttu-id="9c0dd-102">Postupy: Použití obecné třídy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c0dd-102">How to: Use a Generic Class (Visual Basic)</span></span>
<span data-ttu-id="9c0dd-103">Třída, která přijímá *parametry typu* , se nazývá *Obecná třída*.</span><span class="sxs-lookup"><span data-stu-id="9c0dd-103">A class that takes *type parameters* is called a *generic class*.</span></span> <span data-ttu-id="9c0dd-104">Pokud používáte obecnou třídu, můžete z ní vytvořit *vytvořenou třídu* zadáním *argumentu typu* pro každý z těchto parametrů.</span><span class="sxs-lookup"><span data-stu-id="9c0dd-104">If you are using a generic class, you can generate a *constructed class* from it by supplying a *type argument* for each of these parameters.</span></span> <span data-ttu-id="9c0dd-105">Pak můžete deklarovat proměnnou typu konstruované třídy a vytvořit instanci konstruované třídy a přiřadit ji k této proměnné.</span><span class="sxs-lookup"><span data-stu-id="9c0dd-105">You can then declare a variable of the constructed class type, and you can create an instance of the constructed class and assign it to that variable.</span></span>  
  
 <span data-ttu-id="9c0dd-106">Kromě tříd můžete také definovat a používat obecné struktury, rozhraní, procedury a delegáty.</span><span class="sxs-lookup"><span data-stu-id="9c0dd-106">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
 <span data-ttu-id="9c0dd-107">Následující postup převezme obecnou třídu definovanou v .NET Framework a vytvoří z ní instanci.</span><span class="sxs-lookup"><span data-stu-id="9c0dd-107">The following procedure takes a generic class defined in the .NET Framework and creates an instance from it.</span></span>  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a><span data-ttu-id="9c0dd-108">Použití třídy, která přebírá parametr typu</span><span class="sxs-lookup"><span data-stu-id="9c0dd-108">To use a class that takes a type parameter</span></span>  
  
1. <span data-ttu-id="9c0dd-109">Na začátku zdrojového souboru zahrňte [příkaz Imports (obor názvů a typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pro import oboru názvů <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9c0dd-109">At the beginning of your source file, include an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to import the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="9c0dd-110">To vám umožňuje odkazovat na třídu <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, aniž by bylo nutné plně kvalifikovat jejich rozlišení od jiných tříd front, jako je například <xref:System.Collections.Queue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9c0dd-110">This allows you to refer to the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class without having to fully qualify it to differentiate it from other queue classes such as <xref:System.Collections.Queue?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="9c0dd-111">Vytvořte objekt normálním způsobem, ale přidejte `(Of type)` hned za název třídy.</span><span class="sxs-lookup"><span data-stu-id="9c0dd-111">Create the object in the normal way, but add `(Of type)` immediately after the class name.</span></span>  
  
     <span data-ttu-id="9c0dd-112">Následující příklad používá stejnou třídu (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) k vytvoření dvou objektů fronty, které obsahují položky různých datových typů.</span><span class="sxs-lookup"><span data-stu-id="9c0dd-112">The following example uses the same class (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) to create two queue objects that hold items of different data types.</span></span> <span data-ttu-id="9c0dd-113">Přidá položky na konec každé fronty a pak odebere a zobrazí položky z přední části každé fronty.</span><span class="sxs-lookup"><span data-stu-id="9c0dd-113">It adds items to the end of each queue and then removes and displays items from the front of each queue.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="9c0dd-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9c0dd-114">See also</span></span>

- [<span data-ttu-id="9c0dd-115">Datové typy</span><span class="sxs-lookup"><span data-stu-id="9c0dd-115">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="9c0dd-116">Obecné typy v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9c0dd-116">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="9c0dd-117">Jazyková nezávislost a jazykově nezávislé komponenty</span><span class="sxs-lookup"><span data-stu-id="9c0dd-117">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="9c0dd-118">Tohoto</span><span class="sxs-lookup"><span data-stu-id="9c0dd-118">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)
- [<span data-ttu-id="9c0dd-119">Příkaz Imports (obor názvů a typ .NET)</span><span class="sxs-lookup"><span data-stu-id="9c0dd-119">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="9c0dd-120">Postupy: Definice třídy, která poskytne identické funkce pro různé datové typy</span><span class="sxs-lookup"><span data-stu-id="9c0dd-120">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [<span data-ttu-id="9c0dd-121">Iterátory</span><span class="sxs-lookup"><span data-stu-id="9c0dd-121">Iterators</span></span>](../../../../visual-basic/programming-guide/concepts/iterators.md)
