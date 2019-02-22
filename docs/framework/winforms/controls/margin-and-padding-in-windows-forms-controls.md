---
title: Okraj a odsazení v ovládacích prvcích Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Padding property [Windows Forms]
- layout [Windows Forms], margins and padding
- Windows Forms, layout
- Margin property [Windows Forms]
ms.assetid: 3781b5a1-3085-4072-bed0-44670c23ffdc
ms.openlocfilehash: a3218ad029735f4a5d70b3166951dcd93e061c26
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2019
ms.locfileid: "56665222"
---
# <a name="margin-and-padding-in-windows-forms-controls"></a>Okraj a odsazení v ovládacích prvcích Windows Forms
Přesné umístění ovládacích prvků na formuláři je důležitá pro mnoho aplikací. <xref:System.Windows.Forms?displayProperty=nameWithType> Obor názvů poskytuje mnoho funkcí rozložení, jak toho dosáhnout. Dva nejdůležitější jsou <xref:System.Windows.Forms.Control.Margin%2A> a <xref:System.Windows.Forms.Control.Padding%2A> vlastnosti.  
  
 <xref:System.Windows.Forms.Control.Margin%2A> Vlastnost definuje místa kolem ovládacího prvku, který udržuje další ovládací prvky určené vzdálenosti od ohraničení ovládacího prvku.  
  
 <xref:System.Windows.Forms.Control.Padding%2A> Vlastnost definuje pole uvnitř ovládacího prvku, který uchovává obsah ovládacího prvku (například, hodnota jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnosti) určené vzdálenosti od ohraničení ovládacího prvku.  
  
 Je vidět na následujícím obrázku <xref:System.Windows.Forms.Control.Padding%2A> a <xref:System.Windows.Forms.Control.Margin%2A> vlastnosti na ovládacím prvku.  
  
 ![Odsazení a okraj Windows Forms ovládací prvky](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")  
  
 Není poskytována podpora návrhu pro tuto funkci v sadě Visual Studio. Viz také [názorný postup: Vytváření rozložení Windows Forms ovládací prvky s odsazením, okraji a s vlastností AutoSize](windows-forms-controls-padding-autosize.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- <xref:System.Windows.Forms.Control.LayoutEngine%2A>
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
