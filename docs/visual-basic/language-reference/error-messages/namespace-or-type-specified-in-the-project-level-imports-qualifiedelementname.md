---
title: Obor názvů nebo typ zadaný v příkazu Imports '<qualifiedelementname>' na úrovni projektu neobsahuje žádného veřejného člena nebo nebyl nalezen.
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: 0ee235252d69e6f77ce53b048f45e73d0969e864
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409449"
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="31acd-102">Obor názvů nebo typ zadaný v příkazu Imports '\<qualifiedelementname>' na úrovni projektu neobsahuje žádného veřejného člena nebo nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="31acd-102">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>
<span data-ttu-id="31acd-103">Obor názvů nebo typ zadaný v importech na úrovni projektu neobsahuje \<qualifiedelementname> žádné veřejné členy nebo se nedá najít.</span><span class="sxs-lookup"><span data-stu-id="31acd-103">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="31acd-104">Ujistěte se, že je obor názvů nebo typ definován a obsahuje nejméně jeden veřejný člen.</span><span class="sxs-lookup"><span data-stu-id="31acd-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="31acd-105">Ujistěte se, že název aliasu neobsahuje další aliasy.</span><span class="sxs-lookup"><span data-stu-id="31acd-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="31acd-106">Vlastnost Import projektu určuje obsahující prvek, který buď nebyl nalezen, nebo nedefinuje žádné `Public` členy.</span><span class="sxs-lookup"><span data-stu-id="31acd-106">An import property of a project specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="31acd-107">*Obsahující element* může být obor názvů, třída, struktura, modul, rozhraní nebo výčet.</span><span class="sxs-lookup"><span data-stu-id="31acd-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="31acd-108">Obsahující element obsahuje členy, jako jsou proměnné, procedury nebo jiné obsahující prvky.</span><span class="sxs-lookup"><span data-stu-id="31acd-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="31acd-109">Účelem importu je dovolit vašemu kódu přístup k oboru názvů nebo členům typu bez nutnosti jejich zařazení.</span><span class="sxs-lookup"><span data-stu-id="31acd-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="31acd-110">Projekt může také potřebovat přidat odkaz na obor názvů nebo typ.</span><span class="sxs-lookup"><span data-stu-id="31acd-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="31acd-111">Další informace naleznete v tématu "Import obsahující prvky" v [odkazech na deklarované elementy](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="31acd-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="31acd-112">Pokud kompilátor nemůže najít zadaný element, který obsahuje, nemůže vyřešit odkazy, které ho používají.</span><span class="sxs-lookup"><span data-stu-id="31acd-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="31acd-113">Pokud prvek najde, ale nezveřejňuje žádné `Public` členy, nemůže být žádný odkaz úspěšný.</span><span class="sxs-lookup"><span data-stu-id="31acd-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="31acd-114">V obou případech je to pro import elementu nevýznamný.</span><span class="sxs-lookup"><span data-stu-id="31acd-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="31acd-115">K určení prvků pro import lze použít **Návrhář projektu** .</span><span class="sxs-lookup"><span data-stu-id="31acd-115">You use the **Project Designer** to specify elements to import.</span></span> <span data-ttu-id="31acd-116">Použijte část **importované obory názvů** na stránce **odkazy** .</span><span class="sxs-lookup"><span data-stu-id="31acd-116">Use the **Imported namespaces** section of the **References** page.</span></span> <span data-ttu-id="31acd-117">Můžete získat přístup k **Návrháři projektu** dvojitým kliknutím na ikonu **můj projekt** v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="31acd-117">You can get to the **Project Designer** by double-clicking the **My Project** icon in **Solution Explorer**.</span></span>  
  
 <span data-ttu-id="31acd-118">**ID chyby:** BC40057</span><span class="sxs-lookup"><span data-stu-id="31acd-118">**Error ID:** BC40057</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="31acd-119">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="31acd-119">To correct this error</span></span>  
  
1. <span data-ttu-id="31acd-120">Otevřete **Návrháře projektu** a přepněte na **referenční** stránku.</span><span class="sxs-lookup"><span data-stu-id="31acd-120">Open the **Project Designer** and switch to the **Reference** page.</span></span>  
  
2. <span data-ttu-id="31acd-121">V části **importované obory názvů** ověřte, zda je obsažený element přístupný z vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="31acd-121">In the **Imported namespaces** section, verify that the containing element is accessible from your project.</span></span>  
  
3. <span data-ttu-id="31acd-122">Ověřte, zda nadřazený element zveřejňuje alespoň jeden `Public` člen.</span><span class="sxs-lookup"><span data-stu-id="31acd-122">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31acd-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="31acd-123">See also</span></span>

- [<span data-ttu-id="31acd-124">Stránka Odkazy, návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31acd-124">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
- [<span data-ttu-id="31acd-125">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="31acd-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="31acd-126">Republik</span><span class="sxs-lookup"><span data-stu-id="31acd-126">Public</span></span>](../modifiers/public.md)
- [<span data-ttu-id="31acd-127">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="31acd-127">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="31acd-128">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="31acd-128">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
