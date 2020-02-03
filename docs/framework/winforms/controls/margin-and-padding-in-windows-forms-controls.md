---
title: Okraj a odsazení v ovládacích prvcích
ms.date: 03/30/2017
helpviewer_keywords:
- Padding property [Windows Forms]
- layout [Windows Forms], margins and padding
- Windows Forms, layout
- Margin property [Windows Forms]
ms.assetid: 3781b5a1-3085-4072-bed0-44670c23ffdc
ms.openlocfilehash: 02cabccd0d51a3501a8aafb8733a5273deef6c49
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728572"
---
# <a name="margin-and-padding-in-windows-forms-controls"></a><span data-ttu-id="0532f-102">Okraj a odsazení v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0532f-102">Margin and Padding in Windows Forms Controls</span></span>
<span data-ttu-id="0532f-103">Přesné umístění ovládacích prvků ve formuláři je velmi prioritní pro mnoho aplikací.</span><span class="sxs-lookup"><span data-stu-id="0532f-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="0532f-104">Obor názvů <xref:System.Windows.Forms?displayProperty=nameWithType> poskytuje mnoho funkcí rozložení k tomu, aby to bylo možné.</span><span class="sxs-lookup"><span data-stu-id="0532f-104">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace gives you many layout features to accomplish this.</span></span> <span data-ttu-id="0532f-105">Dvěma nejdůležitějšími jsou vlastnosti <xref:System.Windows.Forms.Control.Margin%2A> a <xref:System.Windows.Forms.Control.Padding%2A>.</span><span class="sxs-lookup"><span data-stu-id="0532f-105">Two of the most important are the <xref:System.Windows.Forms.Control.Margin%2A> and <xref:System.Windows.Forms.Control.Padding%2A> properties.</span></span>  
  
 <span data-ttu-id="0532f-106">Vlastnost <xref:System.Windows.Forms.Control.Margin%2A> definuje prostor kolem ovládacího prvku, který uchovává jiné ovládací prvky o určenou vzdálenost od ohraničení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0532f-106">The <xref:System.Windows.Forms.Control.Margin%2A> property defines the space around the control that keeps other controls a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="0532f-107">Vlastnost <xref:System.Windows.Forms.Control.Padding%2A> definuje prostor uvnitř ovládacího prvku, který udržuje obsah ovládacího prvku (například hodnotu vlastnosti <xref:System.Windows.Forms.Control.Text%2A>) o určenou vzdálenost od ohraničení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0532f-107">The <xref:System.Windows.Forms.Control.Padding%2A> property defines the space in the interior of a control that keeps the control's content (for example, the value of its <xref:System.Windows.Forms.Control.Text%2A> property) a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="0532f-108">Následující obrázek ukazuje vlastnosti <xref:System.Windows.Forms.Control.Padding%2A> a <xref:System.Windows.Forms.Control.Margin%2A> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0532f-108">The following illustration shows the <xref:System.Windows.Forms.Control.Padding%2A> and <xref:System.Windows.Forms.Control.Margin%2A> properties on a control.</span></span>  
  
 <span data-ttu-id="0532f-109">![Odsazení a okraj pro ovládací prvky model Windows Forms](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span><span class="sxs-lookup"><span data-stu-id="0532f-109">![Padding And Margin for Windows Forms Controls](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span></span>  
  
 <span data-ttu-id="0532f-110">Pro tuto funkci v aplikaci Visual Studio je podporována podpora v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="0532f-110">There is design-time support for this feature in Visual Studio.</span></span> <span data-ttu-id="0532f-111">Viz také [Návod: rozvržení model Windows Forms ovládacích prvků s odsazením, okraji a vlastností AutoSize](windows-forms-controls-padding-autosize.md).</span><span class="sxs-lookup"><span data-stu-id="0532f-111">Also see [Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](windows-forms-controls-padding-autosize.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0532f-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="0532f-112">See also</span></span>

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- <xref:System.Windows.Forms.Control.LayoutEngine%2A>
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
