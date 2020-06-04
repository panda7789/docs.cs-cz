---
title: Výrazu '<expression>' nelze použít jako omezení typu.
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: e2ba411a5f0db21539a9cf99c7645b8c9309caab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409553"
---
# <a name="expression-cannot-be-used-as-a-type-constraint"></a><span data-ttu-id="01bb6-102">Výrazu '\<expression>' nelze použít jako omezení typu.</span><span class="sxs-lookup"><span data-stu-id="01bb6-102">'\<expression>' cannot be used as a type constraint</span></span>
<span data-ttu-id="01bb6-103">Seznam omezení obsahuje výraz, který nepředstavuje platné omezení parametru typu.</span><span class="sxs-lookup"><span data-stu-id="01bb6-103">A constraint list includes an expression that does not represent a valid constraint on a type parameter.</span></span>  
  
 <span data-ttu-id="01bb6-104">Seznam omezení ukládá požadavky na argument typu předaný parametru typu.</span><span class="sxs-lookup"><span data-stu-id="01bb6-104">A constraint list imposes requirements on the type argument passed to the type parameter.</span></span> <span data-ttu-id="01bb6-105">V libovolné kombinaci můžete zadat následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="01bb6-105">You can specify the following requirements in any combination:</span></span>  
  
- <span data-ttu-id="01bb6-106">Argument typu musí implementovat jedno nebo víc rozhraní.</span><span class="sxs-lookup"><span data-stu-id="01bb6-106">The type argument must implement one or more interfaces</span></span>  
  
- <span data-ttu-id="01bb6-107">Argument typu musí dědit od maximálně jedné třídy.</span><span class="sxs-lookup"><span data-stu-id="01bb6-107">The type argument must inherit from at most one class</span></span>  
  
- <span data-ttu-id="01bb6-108">Argument typu musí vystavit konstruktor bez parametrů, ke kterému může vytvořit kód (zahrnuje `New` omezení).</span><span class="sxs-lookup"><span data-stu-id="01bb6-108">The type argument must expose a parameterless constructor that the creating code can access (include the `New` constraint)</span></span>  
  
 <span data-ttu-id="01bb6-109">Pokud v seznamu omezení nezahrnete žádnou konkrétní třídu nebo rozhraní, můžete stanovit obecnější požadavek zadáním jednoho z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="01bb6-109">If you do not include any specific class or interface in the constraint list, you can impose a more general requirement by specifying one of the following:</span></span>  
  
- <span data-ttu-id="01bb6-110">Argument typu musí být typ hodnoty (zahrnuje `Structure` omezení).</span><span class="sxs-lookup"><span data-stu-id="01bb6-110">The type argument must be a value type (include the `Structure` constraint)</span></span>  
  
- <span data-ttu-id="01bb6-111">Argument typu musí být odkazový typ (zahrnuje `Class` omezení).</span><span class="sxs-lookup"><span data-stu-id="01bb6-111">The type argument must be a reference type (include the `Class` constraint)</span></span>  
  
 <span data-ttu-id="01bb6-112">Nemůžete zadat obojí `Structure` a `Class` pro stejný parametr typu a nemůžete zadat žádné z nich více než jednou.</span><span class="sxs-lookup"><span data-stu-id="01bb6-112">You cannot specify both `Structure` and `Class` for the same type parameter, and you cannot specify either one more than once.</span></span>  
  
 <span data-ttu-id="01bb6-113">**ID chyby:** BC32061</span><span class="sxs-lookup"><span data-stu-id="01bb6-113">**Error ID:** BC32061</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="01bb6-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="01bb6-114">To correct this error</span></span>  
  
- <span data-ttu-id="01bb6-115">Ověřte, zda je výraz a jeho prvky zadány správně.</span><span class="sxs-lookup"><span data-stu-id="01bb6-115">Verify that the expression and its elements are spelled correctly.</span></span>  
  
- <span data-ttu-id="01bb6-116">Pokud výraz nesplňuje podmínky pro předchozí seznam požadavků, odeberte ho ze seznamu omezení.</span><span class="sxs-lookup"><span data-stu-id="01bb6-116">If the expression does not qualify for the preceding list of requirements, remove it from the constraint list.</span></span>  
  
- <span data-ttu-id="01bb6-117">Pokud výraz odkazuje na rozhraní nebo třídu, ověřte, zda má kompilátor přístup k tomuto rozhraní nebo třídě.</span><span class="sxs-lookup"><span data-stu-id="01bb6-117">If the expression refers to an interface or class, verify that the compiler has access to that interface or class.</span></span> <span data-ttu-id="01bb6-118">Je možné, že budete muset kvalifikovat jeho název a může být nutné přidat odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="01bb6-118">You might need to qualify its name, and you might need to add a reference to your project.</span></span> <span data-ttu-id="01bb6-119">Další informace naleznete v části "odkazy na projekty" v tématu [odkazy na deklarované elementy](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="01bb6-119">For more information, see "References to Projects" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01bb6-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="01bb6-120">See also</span></span>

- [<span data-ttu-id="01bb6-121">Obecné typy v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="01bb6-121">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="01bb6-122">Typy hodnot a typy odkazu</span><span class="sxs-lookup"><span data-stu-id="01bb6-122">Value Types and Reference Types</span></span>](../../programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="01bb6-123">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="01bb6-123">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
