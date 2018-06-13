---
title: '&#39;&lt;výraz&gt; &#39; nelze použít jako omezení typu.'
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: 8e9aad2ec65e037b15e19ca2e624fdc8f28bc94e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588171"
---
# <a name="39ltexpressiongt39-cannot-be-used-as-a-type-constraint"></a><span data-ttu-id="ffcb9-102">&#39;&lt;výraz&gt; &#39; nelze použít jako omezení typu.</span><span class="sxs-lookup"><span data-stu-id="ffcb9-102">&#39;&lt;expression&gt;&#39; cannot be used as a type constraint</span></span>
<span data-ttu-id="ffcb9-103">Seznam omezení obsahuje výraz, který nepředstavuje platný parametr typu omezení.</span><span class="sxs-lookup"><span data-stu-id="ffcb9-103">A constraint list includes an expression that does not represent a valid constraint on a type parameter.</span></span>  
  
 <span data-ttu-id="ffcb9-104">Seznam omezení ukládá požadavky na typ argument předaný parametr typu.</span><span class="sxs-lookup"><span data-stu-id="ffcb9-104">A constraint list imposes requirements on the type argument passed to the type parameter.</span></span> <span data-ttu-id="ffcb9-105">V libovolné kombinace můžete určit následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="ffcb9-105">You can specify the following requirements in any combination:</span></span>  
  
-   <span data-ttu-id="ffcb9-106">Argument typu musí implementovat jednu nebo více rozhraní</span><span class="sxs-lookup"><span data-stu-id="ffcb9-106">The type argument must implement one or more interfaces</span></span>  
  
-   <span data-ttu-id="ffcb9-107">Argument typu musí dědit z maximálně jednu třídu</span><span class="sxs-lookup"><span data-stu-id="ffcb9-107">The type argument must inherit from at most one class</span></span>  
  
-   <span data-ttu-id="ffcb9-108">Argument typu musí vystavit konstruktor bez parametrů, kterým může přistupovat vytváření kódu (zahrnout `New` omezení)</span><span class="sxs-lookup"><span data-stu-id="ffcb9-108">The type argument must expose a parameterless constructor that the creating code can access (include the `New` constraint)</span></span>  
  
 <span data-ttu-id="ffcb9-109">Pokud neuvedete žádné konkrétní třídy nebo rozhraní v seznamu omezení, můžete použít obecnější požadavek zadáním jednoho z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="ffcb9-109">If you do not include any specific class or interface in the constraint list, you can impose a more general requirement by specifying one of the following:</span></span>  
  
-   <span data-ttu-id="ffcb9-110">Argument typu musí být typu hodnoty (zahrnout `Structure` omezení)</span><span class="sxs-lookup"><span data-stu-id="ffcb9-110">The type argument must be a value type (include the `Structure` constraint)</span></span>  
  
-   <span data-ttu-id="ffcb9-111">Argument typu musí být typu odkazu (zahrnout `Class` omezení)</span><span class="sxs-lookup"><span data-stu-id="ffcb9-111">The type argument must be a reference type (include the `Class` constraint)</span></span>  
  
 <span data-ttu-id="ffcb9-112">Nelze zadat současně `Structure` a `Class` pro stejný typ parametru a nelze zadat buď jednu více než jednou.</span><span class="sxs-lookup"><span data-stu-id="ffcb9-112">You cannot specify both `Structure` and `Class` for the same type parameter, and you cannot specify either one more than once.</span></span>  
  
 <span data-ttu-id="ffcb9-113">**ID chyby:** BC32061</span><span class="sxs-lookup"><span data-stu-id="ffcb9-113">**Error ID:** BC32061</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ffcb9-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ffcb9-114">To correct this error</span></span>  
  
-   <span data-ttu-id="ffcb9-115">Ověřte, jestli jsou správně zadané ve výrazu a jejích elementů.</span><span class="sxs-lookup"><span data-stu-id="ffcb9-115">Verify that the expression and its elements are spelled correctly.</span></span>  
  
-   <span data-ttu-id="ffcb9-116">Výraz není způsobilá pro předchozí seznam požadavků, odeberte ji ze seznamu omezení.</span><span class="sxs-lookup"><span data-stu-id="ffcb9-116">If the expression does not qualify for the preceding list of requirements, remove it from the constraint list.</span></span>  
  
-   <span data-ttu-id="ffcb9-117">Pokud výraz odkazuje na rozhraní nebo třídy, ověřte, zda kompilátor má přístup k tomuto rozhraní nebo třídy.</span><span class="sxs-lookup"><span data-stu-id="ffcb9-117">If the expression refers to an interface or class, verify that the compiler has access to that interface or class.</span></span> <span data-ttu-id="ffcb9-118">Možná budete muset kvalifikovat jeho název a možná budete muset přidat odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="ffcb9-118">You might need to qualify its name, and you might need to add a reference to your project.</span></span> <span data-ttu-id="ffcb9-119">Další informace najdete v tématu "Odkazy na projekty" v [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="ffcb9-119">For more information, see "References to Projects" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffcb9-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="ffcb9-120">See Also</span></span>  
 [<span data-ttu-id="ffcb9-121">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ffcb9-121">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="ffcb9-122">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="ffcb9-122">Value Types and Reference Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="ffcb9-123">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="ffcb9-123">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 
