---
title: 'Postupy: Umisťování ovládacích prvků ve formulářích Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Location
- Location.Y
- Location.X
helpviewer_keywords:
- controls [Windows Forms]
- controls [Windows Forms], moving
- snaplines
- controls [Windows Forms], positioning
ms.assetid: 4693977e-34a4-4f19-8221-68c3120c2b2b
ms.openlocfilehash: 6843c22fec964de92c41760f1108d1c83e1f5bf8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871173"
---
# <a name="how-to-position-controls-on-windows-forms"></a>Postupy: Umisťování ovládacích prvků ve formulářích Windows
Umístit ovládací prvky, použijte Návrhář formulářů Windows nebo zadat <xref:System.Windows.Forms.Control.Location%2A> vlastnost.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a>Pokud chcete umístit ovládací prvek na návrhové ploše Návrháře formulářů Windows  
  
-   Přetáhněte ovládací prvek pomocí myši do příslušného umístění.  
  
    > [!NOTE]
    >  Vyberte ovládací prvek a přesunout že ho s šipkou klíče na pozici přesněji. Navíc *zarovnávacích čar* vám pomohou při uvádění ovládací prvky měly ve správnou chvíli na formuláři. Další informace najdete v tématu [návod: uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
### <a name="to-position-a-control-using-the-properties-window"></a>Na pozici ovládacího prvku pomocí okna Vlastnosti  
  
1.  Klikněte na ovládací prvek, který chcete umístit.  
  
2.  V **vlastnosti** okno, zadejte hodnoty <xref:System.Windows.Forms.Control.Location%2A> vlastnost oddělené čárkou, pokud chcete umístit ovládací prvek v rámci jeho kontejneru.  
  
     První číslo (X) je vzdálenost od levého ohraničení kontejneru; druhé číslo (Y) je vzdálenost mezi horním okrajem oblasti kontejnerů, měřeno v pixelech.  
  
    > [!NOTE]
    >  Můžete rozšířit <xref:System.Windows.Forms.Control.Location%2A> vlastnosti na typ **X** a **Y** hodnoty jednotlivě.  
  
### <a name="to-position-a-control-programmatically"></a>Pokud chcete umístit ovládací prvek prostřednictvím kódu programu  
  
1.  Nastavte <xref:System.Windows.Forms.Control.Location%2A> vlastnost ovládacího prvku <xref:System.Drawing.Point>.  
  
    ```vb  
    Button1.Location = New Point(100, 100)  
    ```  
  
    ```csharp  
    button1.Location = new Point(100, 100);  
    ```  
  
    ```cpp  
    button1->Location = Point(100, 100);  
    ```  
  
2.  Změnit souřadnici X polohy ovládacího prvku pomocí <xref:System.Windows.Forms.Control.Left%2A> podvlastností.  
  
    ```vb  
    Button1.Left = 300  
    ```  
  
    ```csharp  
    button1.Left = 300;  
    ```  
  
    ```cpp  
    button1->Left = 300;  
    ```  
  
### <a name="to-increment-a-controls-location-programmatically"></a>Umístění ovládacího prvku postupně prostřednictvím kódu programu  
  
1.  Nastavte <xref:System.Windows.Forms.Control.Left%2A> podvlastností postupně souřadnici X ovládacího prvku.  
  
    ```vb  
    Button1.Left += 200  
    ```  
  
    ```csharp  
    button1.Left += 200;  
    ```  
  
    ```cpp  
    button1->Left += 200;  
    ```  
  
    > [!NOTE]
    >  Použití <xref:System.Windows.Forms.Control.Location%2A> vlastnosti chcete nastavit ovládací prvek X a Y pozice současně. Chcete-li nastavení pozice jednotlivě, použijte ovládací prvek <xref:System.Windows.Forms.Control.Left%2A> (**X**) nebo <xref:System.Windows.Forms.Control.Top%2A> (**Y**) podvlastností. Nepokoušejte se implicitně nastavena souřadnice X a Y <xref:System.Drawing.Point> strukturu, která představuje tlačítka umístění, protože tato struktura obsahuje kopii souřadnice na tlačítko.  
  
## <a name="see-also"></a>Viz také  
 [Windows Forms – ovládací prvky](../../../../docs/framework/winforms/controls/index.md)  
 [Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Postupy: Uspořádání ovládacích prvků na Windows Forms s použitím ovládacího prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Postupy: Uspořádání ovládacích prvků na formuláři Windows Forms s použitím ovládacího prvku FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Uspořádávání ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Ovládací prvky používané ve Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Ovládací prvky Windows Forms podle funkce](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [Postupy: nastavit polohu na obrazovce formulářů Windows](https://msdn.microsoft.com/library/cb023ab7-dea7-4284-9aa6-8c03c59b60c6)
