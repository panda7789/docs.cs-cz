---
title: 'Postupy: Zabránit řádku přidání a odstranění v ovládacím prvku Windows Forms DataGridView pomocí návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: f25461202ee807fc065a006b3bfe3f7c39a1c91d
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332569"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Zabránit řádku přidání a odstranění v ovládacím prvku Windows Forms DataGridView pomocí návrháře
Někdy budete chtít zabránit uživatelům v nové řádky dat zadávat nebo odstranění existující řádky v vaše <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Nové řádky jsou zadány ve speciální řádku pro nové záznamy v dolní části ovládacího prvku. Pokud zakážete přidání řádku, řádku pro nové záznamy se nezobrazí. Poté provedete ovládací prvek zcela jen pro čtení zakázáním odstranění řádku a editaci buňky.  
  
 Následující postup vyžaduje, **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Informace o nastavení takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [jak: Přidání ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-prevent-row-addition-and-deletion"></a>Abyste zabránili přidávání řádků a odstranění  
  
-   Klikněte na inteligentní označit piktogram (![piktogram inteligentní](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) v pravém horním rohu <xref:System.Windows.Forms.DataGridView> ovládací prvek a potom zrušte zaškrtnutí **povolit přidání** a **Povolit odstranění** zaškrtávací políčka.  
  
    > [!NOTE]
    >  Chcete-li ovládací prvek zcela jen pro čtení, zrušte **povolit úpravy** také políčko.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [Postupy: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
