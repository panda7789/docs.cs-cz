---
title: Namespace nebo typ zadaný v příkazu Imports &#39; &lt;qualifiedelementname&gt; &#39; kódu&#39;t obsahovat žádný veřejný člen nebo nebyl nalezen
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 21c0794fb4ed6104204fba5d49e37394eff24865
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552135"
---
# <a name="namespace-or-type-specified-in-the-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="340d4-102">Namespace nebo typ zadaný v příkazu Imports &#39; &lt;qualifiedelementname&gt; &#39; kódu&#39;t obsahovat žádný veřejný člen nebo nebyl nalezen</span><span class="sxs-lookup"><span data-stu-id="340d4-102">Namespace or type specified in the Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found</span></span>
<span data-ttu-id="340d4-103">Namespace nebo typ zadaný v příkazu Imports'\<qualifiedelementname >' neobsahuje žádný veřejný člen nebo nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="340d4-103">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="340d4-104">Ujistěte se, že obor názvů nebo typ definován a obsahuje nejméně jeden veřejný člen.</span><span class="sxs-lookup"><span data-stu-id="340d4-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="340d4-105">Ujistěte se, že název aliasu neobsahuje další aliasy.</span><span class="sxs-lookup"><span data-stu-id="340d4-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="340d4-106">`Imports` Příkaz určuje nadřazeného elementu, který nemůže být nalezen nebo nedefinuje žádné `Public` členy.</span><span class="sxs-lookup"><span data-stu-id="340d4-106">An `Imports` statement specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="340d4-107">A *obsahující element* může být obor názvů, třída, struktura, modul, rozhraní nebo výčet.</span><span class="sxs-lookup"><span data-stu-id="340d4-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="340d4-108">Obsahující element obsahuje členy, jako jsou proměnné, postupy a další obsahující prvky.</span><span class="sxs-lookup"><span data-stu-id="340d4-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="340d4-109">Účelem importu je umožnit váš kód získat přístup ke členům obor názvů nebo typ bez nutnosti je vyfiltrovat.</span><span class="sxs-lookup"><span data-stu-id="340d4-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="340d4-110">Váš projekt může být také nutné přidat odkaz na obor názvů nebo typ.</span><span class="sxs-lookup"><span data-stu-id="340d4-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="340d4-111">Další informace najdete v tématu "Import obsahující prvky" [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="340d4-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="340d4-112">Pokud kompilátor nemůže najít zadaný nadřazený prvek, nelze ho přeložit odkazy, které ji používají.</span><span class="sxs-lookup"><span data-stu-id="340d4-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="340d4-113">Vyhledá prvek ale elementu nevystavuje žádné `Public` členové, pak žádný odkaz může být úspěšné.</span><span class="sxs-lookup"><span data-stu-id="340d4-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="340d4-114">V obou případech je importovat element nemá význam.</span><span class="sxs-lookup"><span data-stu-id="340d4-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="340d4-115">Uvědomte si, že pokud provedete import nadřazeného elementu a přiřadit alias importu, nemůžete použít tento alias importu k importu jiný element.</span><span class="sxs-lookup"><span data-stu-id="340d4-115">Keep in mind that if you import a containing element and assign an import alias to it, then you cannot use that import alias to import another element.</span></span> <span data-ttu-id="340d4-116">Následující kód vygeneruje chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="340d4-116">The following code generates a compiler error.</span></span>  
  
 <span data-ttu-id="340d4-117">`Imports`   `winfrm`   `= System.Windows.Forms`</span><span class="sxs-lookup"><span data-stu-id="340d4-117">`Imports`   `winfrm`   `= System.Windows.Forms`</span></span>  
  
 <span data-ttu-id="340d4-118">`' The following statement is`   `INVALID`   `because it reuses an import alias.`</span><span class="sxs-lookup"><span data-stu-id="340d4-118">`' The following statement is`   `INVALID`   `because it reuses an import alias.`</span></span>  
  
 <span data-ttu-id="340d4-119">`Imports behav =`   `winfrm`  `.Design.Behavior`</span><span class="sxs-lookup"><span data-stu-id="340d4-119">`Imports behav =`   `winfrm`  `.Design.Behavior`</span></span>  
  
 <span data-ttu-id="340d4-120">**ID chyby:** BC40056</span><span class="sxs-lookup"><span data-stu-id="340d4-120">**Error ID:** BC40056</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="340d4-121">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="340d4-121">To correct this error</span></span>  
  
1.  <span data-ttu-id="340d4-122">Ověřte, že nadřazeného elementu je dostupná z projektu.</span><span class="sxs-lookup"><span data-stu-id="340d4-122">Verify that the containing element is accessible from your project.</span></span>  
  
2.  <span data-ttu-id="340d4-123">Ověřte, že specifikace nadřazeného elementu nezahrnuje jakýkoli alias import z jiného importu.</span><span class="sxs-lookup"><span data-stu-id="340d4-123">Verify that the specification of the containing element does not include any import alias from another import.</span></span>  
  
3.  <span data-ttu-id="340d4-124">Ověřte, že nadřazeného elementu zpřístupňuje alespoň jeden `Public` člena.</span><span class="sxs-lookup"><span data-stu-id="340d4-124">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="340d4-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="340d4-125">See also</span></span>
- [<span data-ttu-id="340d4-126">Příkaz Imports (obor názvů a typ .NET)</span><span class="sxs-lookup"><span data-stu-id="340d4-126">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="340d4-127">Příkaz Namespace</span><span class="sxs-lookup"><span data-stu-id="340d4-127">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="340d4-128">Public</span><span class="sxs-lookup"><span data-stu-id="340d4-128">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="340d4-129">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="340d4-129">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="340d4-130">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="340d4-130">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
