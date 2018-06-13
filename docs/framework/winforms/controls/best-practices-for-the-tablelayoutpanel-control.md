---
title: Doporučené postupy pro ovládací prvek TableLayoutPanel
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms]
- TableLayoutPanel control [Windows Forms], best practices
- forms [Windows Forms], best practices
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- layout [Windows Forms], AutoSize
- layout [Windows Forms], best practices
- best practices [Windows Forms], tableLayoutPanel control
- sizing [Windows Forms], automatic
- automatic sizing
ms.assetid: b6706efb-d7a4-45ec-8cf4-08fa993e3afb
ms.openlocfilehash: 40322dc6c5facd4167a4c9ac5c12fdf2a8831b7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526449"
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a><span data-ttu-id="eb2f5-102">Doporučené postupy pro ovládací prvek TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="eb2f5-102">Best Practices for the TableLayoutPanel Control</span></span>
<span data-ttu-id="eb2f5-103"><xref:System.Windows.Forms.TableLayoutPanel> Rozložení výkonné funkce, které byste měli pečlivě zvážit před použitím v aplikaci Windows Forms poskytuje ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="eb2f5-103">The <xref:System.Windows.Forms.TableLayoutPanel> control provides powerful layout features that you should consider carefully before using on your Windows Forms.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="eb2f5-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="eb2f5-104">Recommendations</span></span>  
 <span data-ttu-id="eb2f5-105">Následující doporučení vám pomůže používat <xref:System.Windows.Forms.TableLayoutPanel> řízení k jeho nejlepší výhodou.</span><span class="sxs-lookup"><span data-stu-id="eb2f5-105">The following recommendations will help you use the <xref:System.Windows.Forms.TableLayoutPanel> control to its best advantage.</span></span>  
  
### <a name="targeted-use"></a><span data-ttu-id="eb2f5-106">Cílové použití</span><span class="sxs-lookup"><span data-stu-id="eb2f5-106">Targeted Use</span></span>  
 <span data-ttu-id="eb2f5-107">Použití <xref:System.Windows.Forms.TableLayoutPanel> řízení opatrně.</span><span class="sxs-lookup"><span data-stu-id="eb2f5-107">Use the <xref:System.Windows.Forms.TableLayoutPanel> control sparingly.</span></span> <span data-ttu-id="eb2f5-108">Byste neměli používat ve všech situacích, které vyžadují s možností změny velikosti rozložení.</span><span class="sxs-lookup"><span data-stu-id="eb2f5-108">You should not use it in all situations that require a resizable layout.</span></span> <span data-ttu-id="eb2f5-109">Následující seznam popisuje rozložení využívající většinu z použití <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="eb2f5-109">The following list describes layouts that benefit most from the use of the <xref:System.Windows.Forms.TableLayoutPanel> control:</span></span>  
  
-   <span data-ttu-id="eb2f5-110">Rozložení, ve kterých existuje více částí formuláře, které proporcionálně navzájem.</span><span class="sxs-lookup"><span data-stu-id="eb2f5-110">Layouts in which there are multiple parts of the form that resize proportionally to each other.</span></span>  
  
-   <span data-ttu-id="eb2f5-111">Rozložení, které bude upravena nebo generována dynamicky za běhu, jako jsou formuláře položku dat, které mají uživatele přizpůsobitelné pole přidány nebo odečítat podle preferencí.</span><span class="sxs-lookup"><span data-stu-id="eb2f5-111">Layouts that will be modified or generated dynamically at run time, such as data entry forms that have user-customizable fields added or subtracted based on preferences.</span></span>  
  
-   <span data-ttu-id="eb2f5-112">Rozložení, které by měla zůstat na celkové pevné velikosti.</span><span class="sxs-lookup"><span data-stu-id="eb2f5-112">Layouts that should remain at an overall fixed size.</span></span> <span data-ttu-id="eb2f5-113">Například můžete mít dialogu, který by měla zůstat menší než 800 × 600, ale budete potřebovat k podpoře lokalizovaných řetězců.</span><span class="sxs-lookup"><span data-stu-id="eb2f5-113">For example, you may have a dialog box that should remain smaller than 800 x 600, but you need to support localized strings.</span></span>  
  
 <span data-ttu-id="eb2f5-114">Následující seznam popisuje rozložení, které nejsou výrazně nijak přínosné pomocí <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="eb2f5-114">The following list describes layouts that do not benefit greatly from using the <xref:System.Windows.Forms.TableLayoutPanel> control:</span></span>  
  
-   <span data-ttu-id="eb2f5-115">Jednoduché formuláře pro zadávání dat s jedním sloupcem popisků a zadání textu oblastí jeden sloupec.</span><span class="sxs-lookup"><span data-stu-id="eb2f5-115">Simple data entry forms with a single column of labels and a single column of text-entry areas.</span></span>  
  
-   <span data-ttu-id="eb2f5-116">Zobrazení formulářů s jedním velké oblasti, která by měl vyplnit veškeré dostupné místo v případě změny velikosti.</span><span class="sxs-lookup"><span data-stu-id="eb2f5-116">Forms with a single large display area that should fill all the available space when a resize occurs.</span></span> <span data-ttu-id="eb2f5-117">Příkladem je formulář, který zobrazuje jeden <xref:System.Windows.Forms.PropertyGrid> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="eb2f5-117">An example of this is a form that displays a single <xref:System.Windows.Forms.PropertyGrid> control.</span></span> <span data-ttu-id="eb2f5-118">V takovém případě použijte ukotvení, protože nic jiného by měl rozbalit, pokud se změnila velikost formuláře.</span><span class="sxs-lookup"><span data-stu-id="eb2f5-118">In this case, use anchoring, because nothing else should expand when the form is resized.</span></span>  
  
 <span data-ttu-id="eb2f5-119">Pečlivě zvolte ovládacích prvků, které musí být v <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="eb2f5-119">Choose carefully which controls need to be in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="eb2f5-120">Pokud máte místo pro text růst o 30 % pomocí ukotvení, zvažte použití <xref:System.Windows.Forms.Control.Anchor%2A> pouze vlastnost.</span><span class="sxs-lookup"><span data-stu-id="eb2f5-120">If you have room for your text to grow by 30% using anchoring, consider using the <xref:System.Windows.Forms.Control.Anchor%2A> property only.</span></span> <span data-ttu-id="eb2f5-121">Pokud chcete-li odhadnout místo vyžadované vaší rozložení, použití <xref:System.Windows.Forms.Control.Dock%2A> a <xref:System.Windows.Forms.Control.Anchor%2A> je jednodušší než odhadnout podrobnosti zbývajícího místa a <xref:System.Windows.Forms.Control.AutoSize%2A> chování.</span><span class="sxs-lookup"><span data-stu-id="eb2f5-121">If you can estimate the space required by your layout, use of <xref:System.Windows.Forms.Control.Dock%2A> and <xref:System.Windows.Forms.Control.Anchor%2A> is easier than estimating the details of remaining space and <xref:System.Windows.Forms.Control.AutoSize%2A> behavior.</span></span>  
  
 <span data-ttu-id="eb2f5-122">Obecně platí, že při navrhování vaší rozložení s <xref:System.Windows.Forms.TableLayoutPanel> řídit, zachovat návrh co nejjednodušší.</span><span class="sxs-lookup"><span data-stu-id="eb2f5-122">In general, when designing your layout with the <xref:System.Windows.Forms.TableLayoutPanel> control, keep the design as simple as possible.</span></span>  
  
### <a name="use-the-document-outline-window"></a><span data-ttu-id="eb2f5-123">Použití Osnova dokumentu – okno</span><span class="sxs-lookup"><span data-stu-id="eb2f5-123">Use the Document Outline Window</span></span>  
 <span data-ttu-id="eb2f5-124">Okno Osnova dokumentu vám rozložení, který můžete použít k manipulaci s pořadí z-order a nadřazený podřízený vztahy pro vaše ovládací prvky zobrazení stromu.</span><span class="sxs-lookup"><span data-stu-id="eb2f5-124">The Document Outline window gives you a tree view of your layout, which you can use to manipulate the z-order and parent-child relationships of your controls.</span></span> <span data-ttu-id="eb2f5-125">Z **nabídka Zobrazit**, vyberte **ostatní okna**, pak vyberte **Osnova dokumentu**.</span><span class="sxs-lookup"><span data-stu-id="eb2f5-125">From the **View menu**, select **Other Windows**, then select **Document Outline**.</span></span>  
  
### <a name="avoid-nesting"></a><span data-ttu-id="eb2f5-126">Vyhněte se vnoření</span><span class="sxs-lookup"><span data-stu-id="eb2f5-126">Avoid Nesting</span></span>  
 <span data-ttu-id="eb2f5-127">Vyhněte se vnoření jiných <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvky v rámci <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="eb2f5-127">Avoid nesting other <xref:System.Windows.Forms.TableLayoutPanel> controls within a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="eb2f5-128">Ladění rozložení vnořené může být obtížné.</span><span class="sxs-lookup"><span data-stu-id="eb2f5-128">Debugging nested layouts can be difficult.</span></span>  
  
### <a name="avoid-visual-inheritance"></a><span data-ttu-id="eb2f5-129">Vyhněte se dědičnost vizuálních prvků</span><span class="sxs-lookup"><span data-stu-id="eb2f5-129">Avoid Visual Inheritance</span></span>  
 <span data-ttu-id="eb2f5-130"><xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek nepodporuje dědičnost vizuálních prvků v Návrháři formulářů.</span><span class="sxs-lookup"><span data-stu-id="eb2f5-130">The <xref:System.Windows.Forms.TableLayoutPanel> control does not support visual inheritance in the Windows Forms Designer.</span></span> <span data-ttu-id="eb2f5-131">A <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek v odvozené třídě se zobrazí jako "vyřazené" v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="eb2f5-131">A <xref:System.Windows.Forms.TableLayoutPanel> control in a derived class appears as "locked" at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb2f5-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb2f5-132">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>
