---
title: 'Postupy: Do proměnné umístit více než jednu hodnotu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- arrays [Visual Basic], compilation errors
- types [Visual Basic], composite
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
ms.openlocfilehash: 783c75ed4577831b7ca444870c97063e8a057346
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646668"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="e5201-102">Postupy: Do proměnné umístit více než jednu hodnotu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5201-102">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>
<span data-ttu-id="e5201-103">Proměnné obsahuje více než jednu hodnotu, pokud je deklarovat mohla být *složeného datového typu*.</span><span class="sxs-lookup"><span data-stu-id="e5201-103">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>  
  
 <span data-ttu-id="e5201-104">[Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) zahrnují struktury, pole a třídy.</span><span class="sxs-lookup"><span data-stu-id="e5201-104">[Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="e5201-105">Proměnná složeného datového typu mohou být uloženy kombinaci základní datové typy a dalších složené typy.</span><span class="sxs-lookup"><span data-stu-id="e5201-105">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="e5201-106">Struktury a třídy může obsahovat kód, jakož i data.</span><span class="sxs-lookup"><span data-stu-id="e5201-106">Structures and classes can hold code as well as data.</span></span>  
  
### <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="e5201-107">Chcete-li do proměnné umístit více než jednu hodnotu</span><span class="sxs-lookup"><span data-stu-id="e5201-107">To hold more than one value in a variable</span></span>  
  
1.  <span data-ttu-id="e5201-108">Určete, jaký typ složené datové, kterou chcete použít pro vaše proměnná.</span><span class="sxs-lookup"><span data-stu-id="e5201-108">Determine what composite data type you want to use for your variable.</span></span>  
  
2.  <span data-ttu-id="e5201-109">Pokud již není definován složený datový typ, definujte ho tak, aby vaše proměnná může používat.</span><span class="sxs-lookup"><span data-stu-id="e5201-109">If the composite data type is not already defined, define it so that your variable can use it.</span></span>  
  
    -   <span data-ttu-id="e5201-110">Definovat strukturu s [Structure – příkaz](../../../../visual-basic/language-reference/statements/structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e5201-110">Define a structure with a [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md).</span></span>  
  
    -   <span data-ttu-id="e5201-111">Zadejte pole s [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e5201-111">Define an array with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
    -   <span data-ttu-id="e5201-112">Definice třídy, se [Class – příkaz](../../../../visual-basic/language-reference/statements/class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e5201-112">Define a class with a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md).</span></span>  
  
3.  <span data-ttu-id="e5201-113">Deklarovat vaše proměnná s `Dim` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e5201-113">Declare your variable with a `Dim` statement.</span></span>  
  
4.  <span data-ttu-id="e5201-114">Postupujte podle názvu proměnné s `As` klauzule.</span><span class="sxs-lookup"><span data-stu-id="e5201-114">Follow the variable name with an `As` clause.</span></span>  
  
5.  <span data-ttu-id="e5201-115">Postupujte podle `As` – klíčové slovo s názvem odpovídající složené datového typu.</span><span class="sxs-lookup"><span data-stu-id="e5201-115">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5201-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5201-116">See Also</span></span>  
 [<span data-ttu-id="e5201-117">Datové typy</span><span class="sxs-lookup"><span data-stu-id="e5201-117">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="e5201-118">Znaky typu</span><span class="sxs-lookup"><span data-stu-id="e5201-118">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [<span data-ttu-id="e5201-119">Složené datové typy</span><span class="sxs-lookup"><span data-stu-id="e5201-119">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="e5201-120">Struktury</span><span class="sxs-lookup"><span data-stu-id="e5201-120">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="e5201-121">Pole</span><span class="sxs-lookup"><span data-stu-id="e5201-121">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="e5201-122">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="e5201-122">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="e5201-123">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="e5201-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
