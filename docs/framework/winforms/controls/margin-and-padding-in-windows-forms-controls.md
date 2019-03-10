---
title: Okraj a odsazení v ovládacích prvcích Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Padding property [Windows Forms]
- layout [Windows Forms], margins and padding
- Windows Forms, layout
- Margin property [Windows Forms]
ms.assetid: 3781b5a1-3085-4072-bed0-44670c23ffdc
ms.openlocfilehash: 60c808138436b947ef78b61863fc353b731b4a8f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702812"
---
# <a name="margin-and-padding-in-windows-forms-controls"></a><span data-ttu-id="8d3f5-102">Okraj a odsazení v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8d3f5-102">Margin and Padding in Windows Forms Controls</span></span>
<span data-ttu-id="8d3f5-103">Přesné umístění ovládacích prvků na formuláři je důležitá pro mnoho aplikací.</span><span class="sxs-lookup"><span data-stu-id="8d3f5-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="8d3f5-104"><xref:System.Windows.Forms?displayProperty=nameWithType> Obor názvů poskytuje mnoho funkcí rozložení, jak toho dosáhnout.</span><span class="sxs-lookup"><span data-stu-id="8d3f5-104">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace gives you many layout features to accomplish this.</span></span> <span data-ttu-id="8d3f5-105">Dva nejdůležitější jsou <xref:System.Windows.Forms.Control.Margin%2A> a <xref:System.Windows.Forms.Control.Padding%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8d3f5-105">Two of the most important are the <xref:System.Windows.Forms.Control.Margin%2A> and <xref:System.Windows.Forms.Control.Padding%2A> properties.</span></span>  
  
 <span data-ttu-id="8d3f5-106"><xref:System.Windows.Forms.Control.Margin%2A> Vlastnost definuje místa kolem ovládacího prvku, který udržuje další ovládací prvky určené vzdálenosti od ohraničení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8d3f5-106">The <xref:System.Windows.Forms.Control.Margin%2A> property defines the space around the control that keeps other controls a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="8d3f5-107"><xref:System.Windows.Forms.Control.Padding%2A> Vlastnost definuje pole uvnitř ovládacího prvku, který uchovává obsah ovládacího prvku (například, hodnota jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnosti) určené vzdálenosti od ohraničení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8d3f5-107">The <xref:System.Windows.Forms.Control.Padding%2A> property defines the space in the interior of a control that keeps the control's content (for example, the value of its <xref:System.Windows.Forms.Control.Text%2A> property) a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="8d3f5-108">Je vidět na následujícím obrázku <xref:System.Windows.Forms.Control.Padding%2A> a <xref:System.Windows.Forms.Control.Margin%2A> vlastnosti na ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="8d3f5-108">The following illustration shows the <xref:System.Windows.Forms.Control.Padding%2A> and <xref:System.Windows.Forms.Control.Margin%2A> properties on a control.</span></span>  
  
 <span data-ttu-id="8d3f5-109">![Odsazení a okraj Windows Forms ovládací prvky](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span><span class="sxs-lookup"><span data-stu-id="8d3f5-109">![Padding And Margin for Windows Forms Controls](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span></span>  
  
 <span data-ttu-id="8d3f5-110">Není poskytována podpora návrhu pro tuto funkci v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8d3f5-110">There is design-time support for this feature in Visual Studio.</span></span> <span data-ttu-id="8d3f5-111">Viz také [názorný postup: Vytváření rozložení Windows Forms ovládací prvky s odsazením, okraji a s vlastností AutoSize](windows-forms-controls-padding-autosize.md).</span><span class="sxs-lookup"><span data-stu-id="8d3f5-111">Also see [Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](windows-forms-controls-padding-autosize.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d3f5-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d3f5-112">See also</span></span>
- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- <xref:System.Windows.Forms.Control.LayoutEngine%2A>
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
