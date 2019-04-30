---
title: Obor názvů nebo typ zadaný v příkazu Imports '<qualifiedelementname>' na úrovni projektu neobsahuje žádného veřejného člena nebo nebyl nalezen.
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: 105fa8da838938d13022c210c1f65cdafd251003
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918304"
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="9d620-102">Namespace nebo typ zadaný v příkazu Imports na úrovni projektu'\<qualifiedelementname >' neobsahuje žádný veřejný člen nebo nebyl nalezen</span><span class="sxs-lookup"><span data-stu-id="9d620-102">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>
<span data-ttu-id="9d620-103">Namespace nebo typ zadaný v příkazu Imports na úrovni projektu'\<qualifiedelementname >' neobsahuje žádný veřejný člen nebo nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="9d620-103">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="9d620-104">Ujistěte se, že obor názvů nebo typ definován a obsahuje nejméně jeden veřejný člen.</span><span class="sxs-lookup"><span data-stu-id="9d620-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="9d620-105">Ujistěte se, že název aliasu neobsahuje další aliasy.</span><span class="sxs-lookup"><span data-stu-id="9d620-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="9d620-106">Vlastnost importu projektu určuje nadřazeného elementu, který nemůže být nalezen nebo nedefinuje žádné `Public` členy.</span><span class="sxs-lookup"><span data-stu-id="9d620-106">An import property of a project specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="9d620-107">A *obsahující element* může být obor názvů, třída, struktura, modul, rozhraní nebo výčet.</span><span class="sxs-lookup"><span data-stu-id="9d620-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="9d620-108">Obsahující element obsahuje členy, jako jsou proměnné, postupy a další obsahující prvky.</span><span class="sxs-lookup"><span data-stu-id="9d620-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="9d620-109">Účelem importu je umožnit váš kód získat přístup ke členům obor názvů nebo typ bez nutnosti je vyfiltrovat.</span><span class="sxs-lookup"><span data-stu-id="9d620-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="9d620-110">Váš projekt může být také nutné přidat odkaz na obor názvů nebo typ.</span><span class="sxs-lookup"><span data-stu-id="9d620-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="9d620-111">Další informace najdete v tématu "Import obsahující prvky" [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="9d620-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="9d620-112">Pokud kompilátor nemůže najít zadaný nadřazený prvek, nelze ho přeložit odkazy, které ji používají.</span><span class="sxs-lookup"><span data-stu-id="9d620-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="9d620-113">Vyhledá prvek ale elementu nevystavuje žádné `Public` členové, pak žádný odkaz může být úspěšné.</span><span class="sxs-lookup"><span data-stu-id="9d620-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="9d620-114">V obou případech je importovat element nemá význam.</span><span class="sxs-lookup"><span data-stu-id="9d620-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="9d620-115">Můžete použít **Návrháře projektu** k určení prvků k importu.</span><span class="sxs-lookup"><span data-stu-id="9d620-115">You use the **Project Designer** to specify elements to import.</span></span> <span data-ttu-id="9d620-116">Použití **importovat obory názvů** část **odkazy** stránky.</span><span class="sxs-lookup"><span data-stu-id="9d620-116">Use the **Imported namespaces** section of the **References** page.</span></span> <span data-ttu-id="9d620-117">Můžete získat **Návrháře projektu** dvojitým kliknutím **Můj projekt** ikonu **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="9d620-117">You can get to the **Project Designer** by double-clicking the **My Project** icon in **Solution Explorer**.</span></span>  
  
 <span data-ttu-id="9d620-118">**ID chyby:** BC40057</span><span class="sxs-lookup"><span data-stu-id="9d620-118">**Error ID:** BC40057</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9d620-119">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="9d620-119">To correct this error</span></span>  
  
1. <span data-ttu-id="9d620-120">Otevřít **Návrháře projektu** a přepněte se na **odkaz** stránky.</span><span class="sxs-lookup"><span data-stu-id="9d620-120">Open the **Project Designer** and switch to the **Reference** page.</span></span>  
  
2. <span data-ttu-id="9d620-121">V **importovat obory názvů** části, ověřte, zda je přístupný z projektu nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="9d620-121">In the **Imported namespaces** section, verify that the containing element is accessible from your project.</span></span>  
  
3. <span data-ttu-id="9d620-122">Ověřte, že nadřazeného elementu zpřístupňuje alespoň jeden `Public` člena.</span><span class="sxs-lookup"><span data-stu-id="9d620-122">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d620-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d620-123">See also</span></span>

- [<span data-ttu-id="9d620-124">Stránka Odkazy, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d620-124">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
- [<span data-ttu-id="9d620-125">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="9d620-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="9d620-126">Public</span><span class="sxs-lookup"><span data-stu-id="9d620-126">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="9d620-127">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9d620-127">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="9d620-128">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="9d620-128">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
