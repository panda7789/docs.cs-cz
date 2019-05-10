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
ms.openlocfilehash: e46d0fe6913bec61bd56199b7cb56a9b24d15bd0
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211347"
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a><span data-ttu-id="b559f-102">Doporučené postupy pro ovládací prvek TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="b559f-102">Best Practices for the TableLayoutPanel Control</span></span>
<span data-ttu-id="b559f-103"><xref:System.Windows.Forms.TableLayoutPanel> Ovládacího prvku poskytuje výkonné rozložení funkce, které byste měli pečlivě zvážit před použitím ve formulářích Windows.</span><span class="sxs-lookup"><span data-stu-id="b559f-103">The <xref:System.Windows.Forms.TableLayoutPanel> control provides powerful layout features that you should consider carefully before using on your Windows Forms.</span></span>

## <a name="recommendations"></a><span data-ttu-id="b559f-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="b559f-104">Recommendations</span></span>
 <span data-ttu-id="b559f-105">Následující doporučení vám pomůže s použitím <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek na jeho přinášelo maximální výhody.</span><span class="sxs-lookup"><span data-stu-id="b559f-105">The following recommendations will help you use the <xref:System.Windows.Forms.TableLayoutPanel> control to its best advantage.</span></span>

### <a name="targeted-use"></a><span data-ttu-id="b559f-106">Cílové použití</span><span class="sxs-lookup"><span data-stu-id="b559f-106">Targeted Use</span></span>
 <span data-ttu-id="b559f-107">Použití <xref:System.Windows.Forms.TableLayoutPanel> řídit opatrně.</span><span class="sxs-lookup"><span data-stu-id="b559f-107">Use the <xref:System.Windows.Forms.TableLayoutPanel> control sparingly.</span></span> <span data-ttu-id="b559f-108">Nepoužívejte ho ve všech situacích, které vyžadují umožňující změnu velikosti rozložení.</span><span class="sxs-lookup"><span data-stu-id="b559f-108">You should not use it in all situations that require a resizable layout.</span></span> <span data-ttu-id="b559f-109">Následující seznam popisuje rozložení, která je nejužitečnější u použití <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="b559f-109">The following list describes layouts that benefit most from the use of the <xref:System.Windows.Forms.TableLayoutPanel> control:</span></span>

- <span data-ttu-id="b559f-110">Rozložení, ve kterém se více částí formuláře, které proporcionálně k sobě navzájem.</span><span class="sxs-lookup"><span data-stu-id="b559f-110">Layouts in which there are multiple parts of the form that resize proportionally to each other.</span></span>

- <span data-ttu-id="b559f-111">Rozložení, které budou změněny nebo dynamicky generované v době běhu, jako je například formulářích pro zadávání dat, které mají uživatelsky přizpůsobitelnými pole přičíst nebo odečíst podle preferencí.</span><span class="sxs-lookup"><span data-stu-id="b559f-111">Layouts that will be modified or generated dynamically at run time, such as data entry forms that have user-customizable fields added or subtracted based on preferences.</span></span>

- <span data-ttu-id="b559f-112">Rozložení, které by měla zůstat na celkové pevné velikosti.</span><span class="sxs-lookup"><span data-stu-id="b559f-112">Layouts that should remain at an overall fixed size.</span></span> <span data-ttu-id="b559f-113">Například můžete mít dialogové okno, které by měla zůstat menší než 800 × 600, ale budete potřebovat k podpoře lokalizovaných řetězců.</span><span class="sxs-lookup"><span data-stu-id="b559f-113">For example, you may have a dialog box that should remain smaller than 800 x 600, but you need to support localized strings.</span></span>

 <span data-ttu-id="b559f-114">Následující seznam popisuje rozložení, které nejsou nijak přínosné výrazně pomocí <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="b559f-114">The following list describes layouts that do not benefit greatly from using the <xref:System.Windows.Forms.TableLayoutPanel> control:</span></span>

- <span data-ttu-id="b559f-115">Jednoduchá datová položka formy s jedním sloupcem popisky a jedním sloupcem textového vstupu oblastí.</span><span class="sxs-lookup"><span data-stu-id="b559f-115">Simple data entry forms with a single column of labels and a single column of text-entry areas.</span></span>

- <span data-ttu-id="b559f-116">Formuláře pomocí jediného velké zobrazit oblast, která by měla zaplnit veškeré dostupné místo, když dojde k Změna velikosti.</span><span class="sxs-lookup"><span data-stu-id="b559f-116">Forms with a single large display area that should fill all the available space when a resize occurs.</span></span> <span data-ttu-id="b559f-117">Příkladem je formulář, který se zobrazí jedna <xref:System.Windows.Forms.PropertyGrid> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b559f-117">An example of this is a form that displays a single <xref:System.Windows.Forms.PropertyGrid> control.</span></span> <span data-ttu-id="b559f-118">V takovém případě použijte ukotvení, protože nic jiného by měli rozbalit při změně velikosti formuláře.</span><span class="sxs-lookup"><span data-stu-id="b559f-118">In this case, use anchoring, because nothing else should expand when the form is resized.</span></span>

 <span data-ttu-id="b559f-119">Pečlivě zvolit, jaké ovládací prvky musí být v <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b559f-119">Choose carefully which controls need to be in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="b559f-120">Pokud máte místo pro text zvětší o 30 % pomocí ukotvení, zvažte použití <xref:System.Windows.Forms.Control.Anchor%2A> pouze vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b559f-120">If you have room for your text to grow by 30% using anchoring, consider using the <xref:System.Windows.Forms.Control.Anchor%2A> property only.</span></span> <span data-ttu-id="b559f-121">Pokud chcete-li odhadnout místo vyžadované rozložení, použijte <xref:System.Windows.Forms.Control.Dock%2A> a <xref:System.Windows.Forms.Control.Anchor%2A> je snazší než odhad podrobnosti zbývajícího místa a <xref:System.Windows.Forms.Control.AutoSize%2A> chování.</span><span class="sxs-lookup"><span data-stu-id="b559f-121">If you can estimate the space required by your layout, use of <xref:System.Windows.Forms.Control.Dock%2A> and <xref:System.Windows.Forms.Control.Anchor%2A> is easier than estimating the details of remaining space and <xref:System.Windows.Forms.Control.AutoSize%2A> behavior.</span></span>

 <span data-ttu-id="b559f-122">Obecně platí, že při návrhu rozložení s <xref:System.Windows.Forms.TableLayoutPanel> řídit, zachovat návrhu co nejjednodušší.</span><span class="sxs-lookup"><span data-stu-id="b559f-122">In general, when designing your layout with the <xref:System.Windows.Forms.TableLayoutPanel> control, keep the design as simple as possible.</span></span>

### <a name="use-the-document-outline-window"></a><span data-ttu-id="b559f-123">Použijte okno osnovy dokumentu</span><span class="sxs-lookup"><span data-stu-id="b559f-123">Use the Document Outline Window</span></span>
 <span data-ttu-id="b559f-124">Osnova dokumentu – okno nabízí stromového zobrazení rozložení, který můžete použít k manipulaci s pořadí vykreslování a hierarchické vztahy své ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="b559f-124">The Document Outline window gives you a tree view of your layout, which you can use to manipulate the z-order and parent-child relationships of your controls.</span></span> <span data-ttu-id="b559f-125">Z **nabídka zobrazení**vyberte **ostatní Windows**a pak vyberte **Osnova dokumentu**.</span><span class="sxs-lookup"><span data-stu-id="b559f-125">From the **View menu**, select **Other Windows**, then select **Document Outline**.</span></span>

### <a name="avoid-nesting"></a><span data-ttu-id="b559f-126">Avoid Nesting</span><span class="sxs-lookup"><span data-stu-id="b559f-126">Avoid Nesting</span></span>
 <span data-ttu-id="b559f-127">Vyhnout se vnoření jiných <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvky v rámci <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b559f-127">Avoid nesting other <xref:System.Windows.Forms.TableLayoutPanel> controls within a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="b559f-128">Ladění rozložení vnořeného může být obtížné.</span><span class="sxs-lookup"><span data-stu-id="b559f-128">Debugging nested layouts can be difficult.</span></span>

### <a name="avoid-visual-inheritance"></a><span data-ttu-id="b559f-129">Vyhněte se vizuálního dědění</span><span class="sxs-lookup"><span data-stu-id="b559f-129">Avoid Visual Inheritance</span></span>
 <span data-ttu-id="b559f-130"><xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek nepodporuje vizuálního dědění v Návrháři formulářů Windows v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b559f-130">The <xref:System.Windows.Forms.TableLayoutPanel> control does not support visual inheritance in the Windows Forms Designer in Visual Studio.</span></span> <span data-ttu-id="b559f-131">A <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek v odvozené třídě se zobrazí jako "uzamčená" v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="b559f-131">A <xref:System.Windows.Forms.TableLayoutPanel> control in a derived class appears as "locked" at design time.</span></span>

## <a name="see-also"></a><span data-ttu-id="b559f-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b559f-132">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
