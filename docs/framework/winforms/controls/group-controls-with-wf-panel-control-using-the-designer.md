---
title: 'Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 1cf4519a9aaaa1c4f0df321ab38c3f543c87b2a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525620"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a>Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí Návrháře
Windows Forms <xref:System.Windows.Forms.Panel> ovládací prvky slouží k seskupení další ovládací prvky. Existují tři důvodů, proč seskupování ovládacích prvků. Jedna je visual seskupování elementů související formuláře pro zrušte uživatelské rozhraní; jiné se programový seskupení, přepínačů například; poslední je přesouvání ovládacích prvků jako jednotku v době návrhu.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-a-group-of-controls"></a>Chcete-li vytvořit skupinu ovládacích prvků  
  
1.  Přetáhněte <xref:System.Windows.Forms.Panel> řídit z **Windows Forms** kartě nástrojů do formuláře.  
  
2.  Přidáte další ovládací prvky panelu Kreslení každý uvnitř panelu.  
  
     Pokud máte stávající ovládací prvky, které chcete uzavřete panelu, můžete vybrat všechny ovládací prvky, je vyjmout data do schránky, vyberte <xref:System.Windows.Forms.Panel> řízení a vložte je do panelu. Můžete také přetáhněte je do panelu.  
  
3.  (Volitelné) Pokud chcete přidat k panelu ohraničení, nastavte jeho <xref:System.Windows.Forms.BorderStyle> vlastnost. Existují tři možnosti: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, a <xref:System.Windows.Forms.BorderStyle.None>.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvek Panel](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [Přehled ovládacího prvku Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [Postupy: Nastavení pozadí panelu](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md)
