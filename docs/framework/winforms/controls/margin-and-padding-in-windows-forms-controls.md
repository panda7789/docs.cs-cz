---
title: "Okraj a odsazení v ovládacích prvcích Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Padding property [Windows Forms]
- layout [Windows Forms], margins and padding
- Windows Forms, layout
- Margin property [Windows Forms]
ms.assetid: 3781b5a1-3085-4072-bed0-44670c23ffdc
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28092704d3c7eaa4820bf6dcbc1678f806ac213e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="margin-and-padding-in-windows-forms-controls"></a><span data-ttu-id="76814-102">Okraj a odsazení v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="76814-102">Margin and Padding in Windows Forms Controls</span></span>
<span data-ttu-id="76814-103">Přesné umístění ovládacích prvků ve formuláři je důležitá pro mnoho aplikací.</span><span class="sxs-lookup"><span data-stu-id="76814-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="76814-104"><xref:System.Windows.Forms?displayProperty=nameWithType> Obor názvů poskytuje mnoho funkcí rozložení toho chcete dosáhnout.</span><span class="sxs-lookup"><span data-stu-id="76814-104">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace gives you many layout features to accomplish this.</span></span> <span data-ttu-id="76814-105">Dva nejdůležitějších jsou <xref:System.Windows.Forms.Control.Margin%2A> a <xref:System.Windows.Forms.Control.Padding%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="76814-105">Two of the most important are the <xref:System.Windows.Forms.Control.Margin%2A> and <xref:System.Windows.Forms.Control.Padding%2A> properties.</span></span>  
  
 <span data-ttu-id="76814-106"><xref:System.Windows.Forms.Control.Margin%2A> Vlastnost definuje prostor okolo ovládacího prvku, který udržuje další ovládací prvky zadaná vzdálenost od ohraničení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="76814-106">The <xref:System.Windows.Forms.Control.Margin%2A> property defines the space around the control that keeps other controls a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="76814-107"><xref:System.Windows.Forms.Control.Padding%2A> Vlastnost definuje místo uvnitř ovládacího prvku, který uchovává obsah ovládacího prvku (například hodnota jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost) zadaná vzdálenost od ohraničení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="76814-107">The <xref:System.Windows.Forms.Control.Padding%2A> property defines the space in the interior of a control that keeps the control's content (for example, the value of its <xref:System.Windows.Forms.Control.Text%2A> property) a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="76814-108">Následující obrázek ukazuje <xref:System.Windows.Forms.Control.Padding%2A> a <xref:System.Windows.Forms.Control.Margin%2A> vlastnosti ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="76814-108">The following illustration shows the <xref:System.Windows.Forms.Control.Padding%2A> and <xref:System.Windows.Forms.Control.Margin%2A> properties on a control.</span></span>  
  
 <span data-ttu-id="76814-109">![Odsazení a okrajů pro Windows Forms – ovládací prvky](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span><span class="sxs-lookup"><span data-stu-id="76814-109">![Padding And Margin for Windows Forms Controls](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span></span>  
  
 <span data-ttu-id="76814-110">Není poskytována podpora návrhu pro tuto funkci v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="76814-110">There is design-time support for this feature in Visual Studio.</span></span>  <span data-ttu-id="76814-111">Viz také [návod:, kterým se ovládacích prvků Windows Forms s odsazením, okraji a s vlastností AutoSize](http://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="76814-111">Also see [Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](http://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76814-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="76814-112">See Also</span></span>  
 <xref:System.Windows.Forms.Control.AutoSize%2A>  
 <xref:System.Windows.Forms.Control.Margin%2A>  
 <xref:System.Windows.Forms.Control.Padding%2A>  
 <xref:System.Windows.Forms.Control.LayoutEngine%2A>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>
