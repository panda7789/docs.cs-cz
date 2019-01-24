---
title: 'Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 706a020bfb007250b9a1b708da25704aacd755e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601532"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a>Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí návrháře
Windows Forms <xref:System.Windows.Forms.Panel> ovládací prvky se používají k seskupování další ovládací prvky. Existují tři hlavní důvody k seskupování ovládacích prvků. Jeden je vizuální seskupení elementů související formuláře pro jasné uživatelské rozhraní; Další je programový seskupování, přepínačů. poslední slouží k přesunutí ovládacích prvků jako jednotka v době návrhu.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-a-group-of-controls"></a>Chcete-li vytvořit skupinu ovládacích prvků  
  
1.  Přetáhněte <xref:System.Windows.Forms.Panel> ovládacího prvku **Windows Forms** kartu na panelu nástrojů do formuláře.  
  
2.  Přidejte další ovládací prvky panel, kreslení každý uvnitř panelu.  
  
     Pokud máte existující ovládací prvky, které chcete uvést v panelu, můžete vybrat všechny ovládací prvky, vyjmout data do schránky, vyberte <xref:System.Windows.Forms.Panel> ovládací prvek a pak je vložte do panelu. Můžete také přetáhnout do panelu.  
  
3.  (Volitelné) Pokud chcete doplnit o ohraničení panelu, nastavte jeho <xref:System.Windows.Forms.BorderStyle> vlastnost. Existují tři možnosti: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, a <xref:System.Windows.Forms.BorderStyle.None>.  
  
## <a name="see-also"></a>Viz také:
- [Ovládací prvek Panel](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)
- [Přehled ovládacího prvku Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)
- [Postupy: Nastavení pozadí panelu](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md)
