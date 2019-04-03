---
title: Výrazu '<expression>' nelze použít jako omezení typu.
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: 8dbf510d7c6ee80e2dcd2f9d2552bc870413cbab
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838102"
---
# <a name="expression-cannot-be-used-as-a-type-constraint"></a><span data-ttu-id="66348-102">"\<výrazu >' nelze použít jako omezení typu</span><span class="sxs-lookup"><span data-stu-id="66348-102">'\<expression>' cannot be used as a type constraint</span></span>
<span data-ttu-id="66348-103">Seznam omezení obsahuje výraz, který nepředstavuje platné omezení pro parametr typu.</span><span class="sxs-lookup"><span data-stu-id="66348-103">A constraint list includes an expression that does not represent a valid constraint on a type parameter.</span></span>  
  
 <span data-ttu-id="66348-104">Seznam omezení žáků argument typu předaný do parametru typu.</span><span class="sxs-lookup"><span data-stu-id="66348-104">A constraint list imposes requirements on the type argument passed to the type parameter.</span></span> <span data-ttu-id="66348-105">V jakékoli kombinace můžete určit následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="66348-105">You can specify the following requirements in any combination:</span></span>  
  
-   <span data-ttu-id="66348-106">Argument typu musí implementovat jedno nebo více rozhraní</span><span class="sxs-lookup"><span data-stu-id="66348-106">The type argument must implement one or more interfaces</span></span>  
  
-   <span data-ttu-id="66348-107">Argument typu musí dědit z nejvýše jednu třídu</span><span class="sxs-lookup"><span data-stu-id="66348-107">The type argument must inherit from at most one class</span></span>  
  
-   <span data-ttu-id="66348-108">Argument typu musí vystavit konstruktor bez parametrů, s přístupem k vytváření kódu (patří `New` omezení)</span><span class="sxs-lookup"><span data-stu-id="66348-108">The type argument must expose a parameterless constructor that the creating code can access (include the `New` constraint)</span></span>  
  
 <span data-ttu-id="66348-109">Pokud jste neobsahují žádné konkrétní třídu nebo rozhraní v seznamu omezení, je možné nastavit obecnější požadavek zadáním jedné z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="66348-109">If you do not include any specific class or interface in the constraint list, you can impose a more general requirement by specifying one of the following:</span></span>  
  
-   <span data-ttu-id="66348-110">Argument typu musí být typ hodnoty (patří `Structure` omezení)</span><span class="sxs-lookup"><span data-stu-id="66348-110">The type argument must be a value type (include the `Structure` constraint)</span></span>  
  
-   <span data-ttu-id="66348-111">Argument typu musí být typ odkazu (patří `Class` omezení)</span><span class="sxs-lookup"><span data-stu-id="66348-111">The type argument must be a reference type (include the `Class` constraint)</span></span>  
  
 <span data-ttu-id="66348-112">Nelze zadat současně `Structure` a `Class` pro stejný typ parametru a nelze zadat jednu více než jednou.</span><span class="sxs-lookup"><span data-stu-id="66348-112">You cannot specify both `Structure` and `Class` for the same type parameter, and you cannot specify either one more than once.</span></span>  
  
 <span data-ttu-id="66348-113">**ID chyby:** BC32061</span><span class="sxs-lookup"><span data-stu-id="66348-113">**Error ID:** BC32061</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="66348-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="66348-114">To correct this error</span></span>  
  
-   <span data-ttu-id="66348-115">Ověřte, že výraz a jeho prvky jsou zadány správně.</span><span class="sxs-lookup"><span data-stu-id="66348-115">Verify that the expression and its elements are spelled correctly.</span></span>  
  
-   <span data-ttu-id="66348-116">Pokud výraz nesplňuje požadavky uvedené v předchozím seznamu, odeberte ji ze seznamu omezení.</span><span class="sxs-lookup"><span data-stu-id="66348-116">If the expression does not qualify for the preceding list of requirements, remove it from the constraint list.</span></span>  
  
-   <span data-ttu-id="66348-117">Pokud výraz odkazuje na rozhraní nebo tříd, ověřte, že kompilátor má přístup k tomuto rozhraní nebo tříd.</span><span class="sxs-lookup"><span data-stu-id="66348-117">If the expression refers to an interface or class, verify that the compiler has access to that interface or class.</span></span> <span data-ttu-id="66348-118">Možná budete muset kvalifikovat její název a může být nutné přidat odkaz na svůj projekt.</span><span class="sxs-lookup"><span data-stu-id="66348-118">You might need to qualify its name, and you might need to add a reference to your project.</span></span> <span data-ttu-id="66348-119">Další informace najdete v tématu "Odkazy na projekty" [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="66348-119">For more information, see "References to Projects" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66348-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66348-120">See also</span></span>

- [<span data-ttu-id="66348-121">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="66348-121">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="66348-122">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="66348-122">Value Types and Reference Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="66348-123">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="66348-123">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
