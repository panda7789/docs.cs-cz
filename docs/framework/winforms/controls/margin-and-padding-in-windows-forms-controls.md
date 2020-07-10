---
title: Okraj a odsazení v ovládacích prvcích
description: Naučte se, jak přidat okraje a odsazení v ovládacích prvcích Windows Form s vlastnostmi okraj a výplň.
ms.date: 03/30/2017
helpviewer_keywords:
- Padding property [Windows Forms]
- layout [Windows Forms], margins and padding
- Windows Forms, layout
- Margin property [Windows Forms]
ms.assetid: 3781b5a1-3085-4072-bed0-44670c23ffdc
ms.openlocfilehash: 4279f39bb4f89fbda8be472f49c8e60853abcac6
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174481"
---
# <a name="margin-and-padding-in-windows-forms-controls"></a><span data-ttu-id="d7307-103">Okraj a odsazení v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d7307-103">Margin and Padding in Windows Forms Controls</span></span>
<span data-ttu-id="d7307-104">Přesné umístění ovládacích prvků ve formuláři je velmi prioritní pro mnoho aplikací.</span><span class="sxs-lookup"><span data-stu-id="d7307-104">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="d7307-105"><xref:System.Windows.Forms?displayProperty=nameWithType>Obor názvů poskytuje mnoho funkcí rozložení k tomu, aby to bylo možné.</span><span class="sxs-lookup"><span data-stu-id="d7307-105">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace gives you many layout features to accomplish this.</span></span> <span data-ttu-id="d7307-106">Dvěma nejdůležitějšími jsou <xref:System.Windows.Forms.Control.Margin%2A> <xref:System.Windows.Forms.Control.Padding%2A> vlastnosti a.</span><span class="sxs-lookup"><span data-stu-id="d7307-106">Two of the most important are the <xref:System.Windows.Forms.Control.Margin%2A> and <xref:System.Windows.Forms.Control.Padding%2A> properties.</span></span>  
  
 <span data-ttu-id="d7307-107"><xref:System.Windows.Forms.Control.Margin%2A>Vlastnost definuje prostor kolem ovládacího prvku, který uchovává jiné ovládací prvky o určenou vzdálenost od ohraničení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d7307-107">The <xref:System.Windows.Forms.Control.Margin%2A> property defines the space around the control that keeps other controls a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="d7307-108"><xref:System.Windows.Forms.Control.Padding%2A>Vlastnost definuje prostor uvnitř ovládacího prvku, který udržuje obsah ovládacího prvku (například hodnota jeho <xref:System.Windows.Forms.Control.Text%2A> Vlastnosti) o zadanou vzdálenost od ohraničení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d7307-108">The <xref:System.Windows.Forms.Control.Padding%2A> property defines the space in the interior of a control that keeps the control's content (for example, the value of its <xref:System.Windows.Forms.Control.Text%2A> property) a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="d7307-109">Následující ilustrace znázorňuje <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.Control.Margin%2A> vlastnosti a na ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="d7307-109">The following illustration shows the <xref:System.Windows.Forms.Control.Padding%2A> and <xref:System.Windows.Forms.Control.Margin%2A> properties on a control.</span></span>  
  
 <span data-ttu-id="d7307-110">![Odsazení a okraj pro ovládací prvky model Windows Forms](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span><span class="sxs-lookup"><span data-stu-id="d7307-110">![Padding And Margin for Windows Forms Controls](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span></span>  
  
 <span data-ttu-id="d7307-111">Pro tuto funkci v aplikaci Visual Studio je podporována podpora v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="d7307-111">There is design-time support for this feature in Visual Studio.</span></span> <span data-ttu-id="d7307-112">Viz také [Návod: rozvržení model Windows Forms ovládacích prvků s odsazením, okraji a vlastností AutoSize](windows-forms-controls-padding-autosize.md).</span><span class="sxs-lookup"><span data-stu-id="d7307-112">Also see [Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](windows-forms-controls-padding-autosize.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7307-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7307-113">See also</span></span>

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- <xref:System.Windows.Forms.Control.LayoutEngine%2A>
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
