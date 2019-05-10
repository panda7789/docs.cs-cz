---
title: 'Postupy: Umístit více než jednu hodnotu proměnné (Visual Basic)'
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
ms.openlocfilehash: 2c3df9873d184ead2de3f82b89a081955ade93b3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64601125"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="f81ee-102">Postupy: Umístit více než jednu hodnotu proměnné (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f81ee-102">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>
<span data-ttu-id="f81ee-103">Proměnná obsahuje více než jednu hodnotu, pokud deklarujete jej bude *složené datový typ*.</span><span class="sxs-lookup"><span data-stu-id="f81ee-103">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>  
  
 <span data-ttu-id="f81ee-104">[Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) zahrnují třídy, struktury a pole.</span><span class="sxs-lookup"><span data-stu-id="f81ee-104">[Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="f81ee-105">Proměnné typu složených dat může obsahovat kombinaci základní datové typy a dalších složené typy.</span><span class="sxs-lookup"><span data-stu-id="f81ee-105">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="f81ee-106">Struktury a třídy může obsahovat kód, jakož i data.</span><span class="sxs-lookup"><span data-stu-id="f81ee-106">Structures and classes can hold code as well as data.</span></span>  
  
### <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="f81ee-107">Chcete-li do proměnné umístit více než jednu hodnotu</span><span class="sxs-lookup"><span data-stu-id="f81ee-107">To hold more than one value in a variable</span></span>  
  
1. <span data-ttu-id="f81ee-108">Určete, jaký složené datový typ, který chcete použít pro proměnné.</span><span class="sxs-lookup"><span data-stu-id="f81ee-108">Determine what composite data type you want to use for your variable.</span></span>  
  
2. <span data-ttu-id="f81ee-109">Pokud již není definován typ. složených dat, definujte ho tak, aby ho může použít vaše proměnná.</span><span class="sxs-lookup"><span data-stu-id="f81ee-109">If the composite data type is not already defined, define it so that your variable can use it.</span></span>  
  
    - <span data-ttu-id="f81ee-110">Definovat strukturu s [Structure – příkaz](../../../../visual-basic/language-reference/statements/structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f81ee-110">Define a structure with a [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md).</span></span>  
  
    - <span data-ttu-id="f81ee-111">Definování pole [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f81ee-111">Define an array with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
    - <span data-ttu-id="f81ee-112">Definovat třídu pomocí [Class – příkaz](../../../../visual-basic/language-reference/statements/class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f81ee-112">Define a class with a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md).</span></span>  
  
3. <span data-ttu-id="f81ee-113">Deklarujte proměnné s `Dim` příkazu.</span><span class="sxs-lookup"><span data-stu-id="f81ee-113">Declare your variable with a `Dim` statement.</span></span>  
  
4. <span data-ttu-id="f81ee-114">Použijte název proměnné pomocí `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="f81ee-114">Follow the variable name with an `As` clause.</span></span>  
  
5. <span data-ttu-id="f81ee-115">Postupujte podle `As` – klíčové slovo s názvem odpovídající složené datového typu.</span><span class="sxs-lookup"><span data-stu-id="f81ee-115">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f81ee-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f81ee-116">See also</span></span>

- [<span data-ttu-id="f81ee-117">Datové typy</span><span class="sxs-lookup"><span data-stu-id="f81ee-117">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="f81ee-118">Znaky typu</span><span class="sxs-lookup"><span data-stu-id="f81ee-118">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [<span data-ttu-id="f81ee-119">Složené datové typy</span><span class="sxs-lookup"><span data-stu-id="f81ee-119">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="f81ee-120">Struktury</span><span class="sxs-lookup"><span data-stu-id="f81ee-120">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="f81ee-121">Pole</span><span class="sxs-lookup"><span data-stu-id="f81ee-121">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="f81ee-122">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="f81ee-122">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="f81ee-123">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="f81ee-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
