---
title: Namespace nebo typ zadaný v importech &#39; &lt;qualifiedelementname&gt; &#39; nemá&#39;t obsahovat všechny veřejné člen nebo nebyla nalezena
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 8be0df5cbe4b8d4a640c9b6c2e126b3828254fd6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595102"
---
# <a name="namespace-or-type-specified-in-the-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="40041-102">Namespace nebo typ zadaný v importech &#39; &lt;qualifiedelementname&gt; &#39; nemá&#39;t obsahovat všechny veřejné člen nebo nebyla nalezena</span><span class="sxs-lookup"><span data-stu-id="40041-102">Namespace or type specified in the Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found</span></span>
<span data-ttu-id="40041-103">Namespace nebo typ zadaný v importech\<qualifiedelementname >' neobsahuje žádný veřejný člen nebo nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="40041-103">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="40041-104">Zajistěte, aby obor názvů nebo typ je definovaný a obsahuje nejméně jeden člen veřejné.</span><span class="sxs-lookup"><span data-stu-id="40041-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="40041-105">Ujistěte se, že název aliasu neobsahuje jiné aliasy.</span><span class="sxs-lookup"><span data-stu-id="40041-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="40041-106">`Imports` Příkaz určuje obsahující element, který nelze nalézt nebo nejsou definovány žádné `Public` členy.</span><span class="sxs-lookup"><span data-stu-id="40041-106">An `Imports` statement specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="40041-107">A *obsahující element* můžou být obor názvů, třída, struktura, modulu, rozhraní nebo výčet.</span><span class="sxs-lookup"><span data-stu-id="40041-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="40041-108">Element obsahující obsahuje členy, jako jsou proměnné, postupy nebo jiné obsahující prvky.</span><span class="sxs-lookup"><span data-stu-id="40041-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="40041-109">Účelem importu je umožnit kódu členům přístup k oboru názvů nebo typ bez nutnosti jejich kvalifikaci.</span><span class="sxs-lookup"><span data-stu-id="40041-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="40041-110">Projekt může být také nutné přidat odkaz na obor názvů nebo typu.</span><span class="sxs-lookup"><span data-stu-id="40041-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="40041-111">Další informace najdete v tématu "Import obsahující prvků" v [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="40041-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="40041-112">Pokud kompilátor nemůže najít zadaný element obsahující, nelze ho přeložit odkazy, které ho používají.</span><span class="sxs-lookup"><span data-stu-id="40041-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="40041-113">Pokud najde elementu, ale element nevystavuje žádné `Public` členy, pak žádný odkaz může být úspěšné.</span><span class="sxs-lookup"><span data-stu-id="40041-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="40041-114">V obou případech je smysl pro import elementu.</span><span class="sxs-lookup"><span data-stu-id="40041-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="40041-115">Uvědomte si, že pokud provedete import elementu s obsahem a přiřadit import alias, nemůžete použít tento alias import k importu jiný element.</span><span class="sxs-lookup"><span data-stu-id="40041-115">Keep in mind that if you import a containing element and assign an import alias to it, then you cannot use that import alias to import another element.</span></span> <span data-ttu-id="40041-116">Následující kód generuje chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="40041-116">The following code generates a compiler error.</span></span>  
  
 <span data-ttu-id="40041-117">`Imports`   `winfrm`   `= System.Windows.Forms`</span><span class="sxs-lookup"><span data-stu-id="40041-117">`Imports`   `winfrm`   `= System.Windows.Forms`</span></span>  
  
 <span data-ttu-id="40041-118">`' The following statement is`   `INVALID`   `because it reuses an import alias.`</span><span class="sxs-lookup"><span data-stu-id="40041-118">`' The following statement is`   `INVALID`   `because it reuses an import alias.`</span></span>  
  
 <span data-ttu-id="40041-119">`Imports behav =`   `winfrm`  `.Design.Behavior`</span><span class="sxs-lookup"><span data-stu-id="40041-119">`Imports behav =`   `winfrm`  `.Design.Behavior`</span></span>  
  
 <span data-ttu-id="40041-120">**ID chyby:** BC40056</span><span class="sxs-lookup"><span data-stu-id="40041-120">**Error ID:** BC40056</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="40041-121">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="40041-121">To correct this error</span></span>  
  
1.  <span data-ttu-id="40041-122">Ověřte, zda je přístupný z projektu obsahující element.</span><span class="sxs-lookup"><span data-stu-id="40041-122">Verify that the containing element is accessible from your project.</span></span>  
  
2.  <span data-ttu-id="40041-123">Ověřte, že specifikace obsahující element neobsahuje libovolným aliasem import z jiného importu.</span><span class="sxs-lookup"><span data-stu-id="40041-123">Verify that the specification of the containing element does not include any import alias from another import.</span></span>  
  
3.  <span data-ttu-id="40041-124">Ověřte, zda obsahující element zpřístupňuje alespoň jeden `Public` člen.</span><span class="sxs-lookup"><span data-stu-id="40041-124">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40041-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="40041-125">See Also</span></span>  
 [<span data-ttu-id="40041-126">Příkaz Imports (obor názvů a typ .NET)</span><span class="sxs-lookup"><span data-stu-id="40041-126">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="40041-127">Příkaz Namespace</span><span class="sxs-lookup"><span data-stu-id="40041-127">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [<span data-ttu-id="40041-128">Public</span><span class="sxs-lookup"><span data-stu-id="40041-128">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="40041-129">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="40041-129">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="40041-130">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="40041-130">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
