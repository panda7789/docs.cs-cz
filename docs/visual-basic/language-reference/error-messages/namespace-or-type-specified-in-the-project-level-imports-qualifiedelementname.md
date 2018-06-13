---
title: Namespace nebo typ zadaný v importech úrovni projektu &#39; &lt;qualifiedelementname&gt; &#39; nemá&#39;t obsahovat všechny veřejné člen nebo nebyla nalezena
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: d6d0c931262d892ec3e65888a76f25218b23d868
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595810"
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="7cb9a-102">Namespace nebo typ zadaný v importech úrovni projektu &#39; &lt;qualifiedelementname&gt; &#39; nemá&#39;t obsahovat všechny veřejné člen nebo nebyla nalezena</span><span class="sxs-lookup"><span data-stu-id="7cb9a-102">Namespace or type specified in the project-level Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found</span></span>
<span data-ttu-id="7cb9a-103">Namespace nebo typ zadaný v úrovni projektu Imports\<qualifiedelementname >' neobsahuje žádný veřejný člen nebo nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="7cb9a-103">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="7cb9a-104">Zajistěte, aby obor názvů nebo typ je definovaný a obsahuje nejméně jeden člen veřejné.</span><span class="sxs-lookup"><span data-stu-id="7cb9a-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="7cb9a-105">Ujistěte se, že název aliasu neobsahuje jiné aliasy.</span><span class="sxs-lookup"><span data-stu-id="7cb9a-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="7cb9a-106">Importu vlastnost projektu určuje obsahující element, který nelze nalézt nebo nejsou definovány žádné `Public` členy.</span><span class="sxs-lookup"><span data-stu-id="7cb9a-106">An import property of a project specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="7cb9a-107">A *obsahující element* můžou být obor názvů, třída, struktura, modulu, rozhraní nebo výčet.</span><span class="sxs-lookup"><span data-stu-id="7cb9a-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="7cb9a-108">Element obsahující obsahuje členy, jako jsou proměnné, postupy nebo jiné obsahující prvky.</span><span class="sxs-lookup"><span data-stu-id="7cb9a-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="7cb9a-109">Účelem importu je umožnit kódu členům přístup k oboru názvů nebo typ bez nutnosti jejich kvalifikaci.</span><span class="sxs-lookup"><span data-stu-id="7cb9a-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="7cb9a-110">Projekt může být také nutné přidat odkaz na obor názvů nebo typu.</span><span class="sxs-lookup"><span data-stu-id="7cb9a-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="7cb9a-111">Další informace najdete v tématu "Import obsahující prvků" v [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="7cb9a-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="7cb9a-112">Pokud kompilátor nemůže najít zadaný element obsahující, nelze ho přeložit odkazy, které ho používají.</span><span class="sxs-lookup"><span data-stu-id="7cb9a-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="7cb9a-113">Pokud najde elementu, ale element nevystavuje žádné `Public` členy, pak žádný odkaz může být úspěšné.</span><span class="sxs-lookup"><span data-stu-id="7cb9a-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="7cb9a-114">V obou případech je smysl pro import elementu.</span><span class="sxs-lookup"><span data-stu-id="7cb9a-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="7cb9a-115">Můžete použít **Návrhář projektu** k určení elementy pro import.</span><span class="sxs-lookup"><span data-stu-id="7cb9a-115">You use the **Project Designer** to specify elements to import.</span></span> <span data-ttu-id="7cb9a-116">Použití **importovat obory názvů** části **odkazy** stránky.</span><span class="sxs-lookup"><span data-stu-id="7cb9a-116">Use the **Imported namespaces** section of the **References** page.</span></span> <span data-ttu-id="7cb9a-117">Můžete získat **Návrhář projektu** dvojitým kliknutím **Můj projekt** ikonu v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="7cb9a-117">You can get to the **Project Designer** by double-clicking the **My Project** icon in **Solution Explorer**.</span></span>  
  
 <span data-ttu-id="7cb9a-118">**ID chyby:** BC40057</span><span class="sxs-lookup"><span data-stu-id="7cb9a-118">**Error ID:** BC40057</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7cb9a-119">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="7cb9a-119">To correct this error</span></span>  
  
1.  <span data-ttu-id="7cb9a-120">Otevřete **Návrhář projektu** a přepněte do **odkaz** stránky.</span><span class="sxs-lookup"><span data-stu-id="7cb9a-120">Open the **Project Designer** and switch to the **Reference** page.</span></span>  
  
2.  <span data-ttu-id="7cb9a-121">V **importovat obory názvů** části, ověřte, zda je přístupný z projektu obsahující element.</span><span class="sxs-lookup"><span data-stu-id="7cb9a-121">In the **Imported namespaces** section, verify that the containing element is accessible from your project.</span></span>  
  
3.  <span data-ttu-id="7cb9a-122">Ověřte, zda obsahující element zpřístupňuje alespoň jeden `Public` člen.</span><span class="sxs-lookup"><span data-stu-id="7cb9a-122">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cb9a-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="7cb9a-123">See Also</span></span>  
 [<span data-ttu-id="7cb9a-124">Stránka Odkazy, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7cb9a-124">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)  
 [<span data-ttu-id="7cb9a-125">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="7cb9a-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="7cb9a-126">Public</span><span class="sxs-lookup"><span data-stu-id="7cb9a-126">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="7cb9a-127">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7cb9a-127">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="7cb9a-128">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="7cb9a-128">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
