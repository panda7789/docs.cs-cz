---
title: "ToolTip – přehled komponenty (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ff2364b5c7223c265571257920a7c7e794b4921b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="tooltip-component-overview-windows-forms"></a><span data-ttu-id="7b578-102">ToolTip – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="7b578-102">ToolTip Component Overview (Windows Forms)</span></span>
<span data-ttu-id="7b578-103">Windows Forms <xref:System.Windows.Forms.ToolTip> součást zobrazí text, když uživatel odkazuje na ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="7b578-103">The Windows Forms <xref:System.Windows.Forms.ToolTip> component displays text when the user points at controls.</span></span> <span data-ttu-id="7b578-104">Popisek může být přidružen žádný ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="7b578-104">A ToolTip can be associated with any control.</span></span> <span data-ttu-id="7b578-105">Příklad použití této součásti: ušetřit místo na formuláři, můžete zobrazení malé ikony na tlačítku a pomocí popisek vysvětlit funkce tlačítka.</span><span class="sxs-lookup"><span data-stu-id="7b578-105">An example use of this component: to save space on a form, you can display a small icon on a button and use a ToolTip to explain the button's function.</span></span>  
  
## <a name="working-with-the-tooltip-component"></a><span data-ttu-id="7b578-106">Práce s komponentou ToolTip</span><span class="sxs-lookup"><span data-stu-id="7b578-106">Working with the ToolTip Component</span></span>  
 <span data-ttu-id="7b578-107">A <xref:System.Windows.Forms.ToolTip> poskytuje součásti `ToolTip` vlastnosti tak, aby více ovládacích prvků na formuláři Windows nebo jiné kontejneru.</span><span class="sxs-lookup"><span data-stu-id="7b578-107">A <xref:System.Windows.Forms.ToolTip> component provides a `ToolTip` property to multiple controls on a Windows Form or other container.</span></span> <span data-ttu-id="7b578-108">Například, pokud umístíte jedno <xref:System.Windows.Forms.ToolTip> součást ve formuláři, můžete zobrazit "Zadejte zde název" <xref:System.Windows.Forms.TextBox> řízení a "Kliknutím sem uložte změny" pro <xref:System.Windows.Forms.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7b578-108">For example, if you place one <xref:System.Windows.Forms.ToolTip> component on a form, you can display "Type your name here" for a <xref:System.Windows.Forms.TextBox> control and "Click here to save changes" for a <xref:System.Windows.Forms.Button> control.</span></span>  
  
 <span data-ttu-id="7b578-109">Klíče metody <xref:System.Windows.Forms.ToolTip> jsou součástí <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> a <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>.</span><span class="sxs-lookup"><span data-stu-id="7b578-109">The key methods of the <xref:System.Windows.Forms.ToolTip> component are <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> and <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>.</span></span> <span data-ttu-id="7b578-110">Můžete použít <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metodu pro nastavení ToolTips pro ovládací prvky zobrazen.</span><span class="sxs-lookup"><span data-stu-id="7b578-110">You can use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method to set the ToolTips displayed for controls.</span></span> <span data-ttu-id="7b578-111">Další informace najdete v tématu [postupy: nastavení ToolTips pro ovládací prvky na formuláři Windows v době návrhu](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="7b578-111">For more information, see [How to: Set ToolTips for Controls on a Windows Form at Design Time](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md).</span></span> <span data-ttu-id="7b578-112">Klíčové vlastnosti jsou <xref:System.Windows.Forms.ToolTip.Active%2A>, který musí být nastaven na `true` pro popisek, který se zobrazí, a <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, která nastaví dobu, která se zobrazí text popisu tlačítka, jak dlouho musí odkazovat uživatele v ovládacím prvku pro popisek, který se zobrazí a jak ho dlouhé potřebná pro následné popisku windows zobrazí.</span><span class="sxs-lookup"><span data-stu-id="7b578-112">The key properties are <xref:System.Windows.Forms.ToolTip.Active%2A>, which must be set to `true` for the ToolTip to appear, and <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, which sets the length of time that the ToolTip string is shown, how long the user must point at the control for the ToolTip to appear, and how long it takes for subsequent ToolTip windows to appear.</span></span> <span data-ttu-id="7b578-113">Další informace najdete v tématu [postupy: Změna zpoždění součásti Windows Forms ToolTip](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).</span><span class="sxs-lookup"><span data-stu-id="7b578-113">For more information, see [How to: Change the Delay of the Windows Forms ToolTip Component](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b578-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b578-114">See Also</span></span>  
 <xref:System.Windows.Forms.ToolTip>  
 [<span data-ttu-id="7b578-115">Postupy: nastavení ToolTips pro ovládací prvky na formuláři Windows v době návrhu</span><span class="sxs-lookup"><span data-stu-id="7b578-115">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)  
 [<span data-ttu-id="7b578-116">Postupy: Změna zpoždění součásti Windows Forms ToolTip</span><span class="sxs-lookup"><span data-stu-id="7b578-116">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
