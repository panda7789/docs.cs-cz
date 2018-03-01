---
title: "CheckBox – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 39645a02cd66d37d61df72028ab129677edb757e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="checkbox-control-overview-windows-forms"></a><span data-ttu-id="e11f1-102">CheckBox – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e11f1-102">CheckBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="e11f1-103">Windows Forms <xref:System.Windows.Forms.CheckBox> řízení Určuje, zda je určitá podmínka zapnout nebo vypnout.</span><span class="sxs-lookup"><span data-stu-id="e11f1-103">The Windows Forms <xref:System.Windows.Forms.CheckBox> control indicates whether a particular condition is on or off.</span></span> <span data-ttu-id="e11f1-104">Běžně se používá k dispozici Ano/Ne nebo hodnotu True nebo False výběru uživatele.</span><span class="sxs-lookup"><span data-stu-id="e11f1-104">It is commonly used to present a Yes/No or True/False selection to the user.</span></span> <span data-ttu-id="e11f1-105">Ovládací prvky zaškrtávacích políček ve skupinách, můžete použít k zobrazení více možností, ze kterých uživatel může vybrat jednu nebo více.</span><span class="sxs-lookup"><span data-stu-id="e11f1-105">You can use check box controls in groups to display multiple choices from which the user can select one or more.</span></span>  
  
 <span data-ttu-id="e11f1-106">Ovládací prvek zaškrtávací políčko je podobná ovládací prvek přepínač, v tom, že každý slouží k označení výběru, která je vytvořená uživatelem.</span><span class="sxs-lookup"><span data-stu-id="e11f1-106">The check box control is similar to the radio button control in that each is used to indicate a selection that is made by the user.</span></span> <span data-ttu-id="e11f1-107">Se liší, ve které lze vybrat pouze jeden přepínač ve skupině najednou.</span><span class="sxs-lookup"><span data-stu-id="e11f1-107">They differ in that only one radio button in a group can be selected at a time.</span></span> <span data-ttu-id="e11f1-108">S ovládací prvek zaškrtávací políčko však může být libovolný počet zaškrtávací políčka vybraný.</span><span class="sxs-lookup"><span data-stu-id="e11f1-108">With the check box control, however, any number of check boxes may be selected.</span></span>  
  
 <span data-ttu-id="e11f1-109">Zaškrtávací políčko může být připojena k prvkům v databázi pomocí jednoduché datové vazby.</span><span class="sxs-lookup"><span data-stu-id="e11f1-109">A check box may be connected to elements in a database using simple data binding.</span></span> <span data-ttu-id="e11f1-110">Více zaškrtávacích políček může být seskupené pomocí <xref:System.Windows.Forms.GroupBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e11f1-110">Multiple check boxes may be grouped using the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="e11f1-111">To je užitečné pro vzhled a také pro návrh uživatelského rozhraní, protože skupina ovládacích prvků lze přesunout společně v návrháři formuláře.</span><span class="sxs-lookup"><span data-stu-id="e11f1-111">This is useful for visual appearance and also for user interface design, since grouped controls can be moved around together on the form designer.</span></span> <span data-ttu-id="e11f1-112">Další informace najdete v tématu [Windows Forms datové vazby](../../../../docs/framework/winforms/windows-forms-data-binding.md) a [groupbox – ovládací prvek](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e11f1-112">For more information, see [Windows Forms Data Binding](../../../../docs/framework/winforms/windows-forms-data-binding.md) and [GroupBox Control](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md).</span></span>  
  
 <span data-ttu-id="e11f1-113"><xref:System.Windows.Forms.CheckBox> Ovládací prvek má dvě důležité vlastnosti <xref:System.Windows.Forms.CheckBox.Checked%2A> a <xref:System.Windows.Forms.CheckBox.CheckState%2A>.</span><span class="sxs-lookup"><span data-stu-id="e11f1-113">The <xref:System.Windows.Forms.CheckBox> control has two important properties, <xref:System.Windows.Forms.CheckBox.Checked%2A> and <xref:System.Windows.Forms.CheckBox.CheckState%2A>.</span></span> <span data-ttu-id="e11f1-114"><xref:System.Windows.Forms.CheckBox.Checked%2A> Vlastnost vrací buď `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="e11f1-114">The <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns either `true` or `false`.</span></span> <span data-ttu-id="e11f1-115"><xref:System.Windows.Forms.CheckBox.CheckState%2A> Vlastnost vrací buď <xref:System.Windows.Forms.CheckState.Checked> nebo <xref:System.Windows.Forms.CheckState.Unchecked>; nebo, pokud <xref:System.Windows.Forms.CheckBox.ThreeState%2A> je nastavena na `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> může také vrátit <xref:System.Windows.Forms.CheckState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="e11f1-115">The <xref:System.Windows.Forms.CheckBox.CheckState%2A> property returns either <xref:System.Windows.Forms.CheckState.Checked> or <xref:System.Windows.Forms.CheckState.Unchecked>; or, if the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> may also return <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span> <span data-ttu-id="e11f1-116">V neurčitém stavu zobrazí se pole s neaktivní vzhled se indikovat, že možnost není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="e11f1-116">In the indeterminate state, the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e11f1-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="e11f1-117">See Also</span></span>  
 <xref:System.Windows.Forms.CheckBox>  
 [<span data-ttu-id="e11f1-118">Postupy: Nastavení možností pomocí ovládacích prvků Windows Forms CheckBox</span><span class="sxs-lookup"><span data-stu-id="e11f1-118">How to: Set Options with Windows Forms CheckBox Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)  
 [<span data-ttu-id="e11f1-119">Postupy: Reakce na kliknutí na prvek Windows Forms CheckBox</span><span class="sxs-lookup"><span data-stu-id="e11f1-119">How to: Respond to Windows Forms CheckBox Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)  
 [<span data-ttu-id="e11f1-120">Ovládací prvek CheckBox</span><span class="sxs-lookup"><span data-stu-id="e11f1-120">CheckBox Control</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
