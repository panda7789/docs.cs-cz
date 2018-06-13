---
title: 'Postupy: Dědění ze stávajících ovládacích prvků Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
ms.openlocfilehash: 6f35881bdb7a781d817c9f671962d0445bfd8e27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538738"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>Postupy: Dědění ze stávajících ovládacích prvků Windows Forms
Pokud chcete rozšířit funkce existujícího ovládacího prvku, můžete vytvořit ovládacího prvku odvozenou z ovládacího prvku existující prostřednictvím dědičnosti. Při dědění z ovládacího prvku existující, dědí všechny funkce a vizuálních vlastností tohoto ovládacího prvku. Například při vytváření ovládacího prvku, který dědí z <xref:System.Windows.Forms.Button>, nový ovládací prvek vypadat a act přesně standardní <xref:System.Windows.Forms.Button> ovládacího prvku. Pak můžete rozšířit nebo změnit funkce nový ovládací prvek prostřednictvím implementace vlastních metod a vlastností. V některé ovládací prvky, můžete také změnit vzhled ovládacího prvku zděděné přepsáním jeho <xref:System.Windows.Forms.Control.OnPaint%2A> metoda.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-an-inherited-control"></a>Vytvoření ovládacího prvku zděděné  
  
1.  Vytvořte novou **formulářové aplikace Windows** projektu.  
  
2.  Z **projektu** nabídce zvolte **přidat novou položku**.  
  
     **Přidat novou položku** zobrazí se dialogové okno.  
  
3.  V **přidat novou položku** dialogové okno, dvakrát klikněte na **vlastní ovládací prvek**.  
  
     Nové vlastní ovládací prvek se přidá do projektu.  
  
4.  Pokud používáte Visual Basic, v horní části **Průzkumníku řešení**, klikněte na tlačítko **zobrazit všechny soubory**. Rozbalte CustomControl1.vb a pak otevřete CustomControl1.Designer.vb v editoru kódu.  
  
5.  Pokud používáte C#, otevřete v editoru kódu CustomControl1.cs.  
  
6.  Vyhledejte deklaraci třídy, která dědí z <xref:System.Windows.Forms.Control>.  
  
7.  Změňte základní třídu pro ovládací prvek, který chcete použít dědění z.  
  
     Například, pokud chcete použít dědění z <xref:System.Windows.Forms.Button>, změňte deklaraci třídy na následující:  
  
    ```vb  
    Partial Class CustomControl1  
        Inherits System.Windows.Forms.Button  
    ```  
  
    ```csharp  
    public partial class CustomControl1 : System.Windows.Forms.Button  
    ```  
  
8.  Pokud používáte Visual Basic, uložte a zavřete CustomControl1.Designer.vb. Otevřete CustomControl1.vb v editoru kódu.  
  
9. Implementujte jakékoliv vlastní metody nebo vlastnosti, které bude obsahovat vlastní ovládací prvek.  
  
10. Pokud chcete upravit grafický vzhled ovládacího prvku, mají přednost před <xref:System.Windows.Forms.Control.OnPaint%2A> metoda.  
  
    > [!NOTE]
    >  Přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> nebude možné změnit vzhled všech ovládacích prvků. Kontrolní mechanismy, které mají všechny jejich Malování provádí systému Windows (například <xref:System.Windows.Forms.TextBox>) nikdy volat jejich <xref:System.Windows.Forms.Control.OnPaint%2A> metoda a proto se nikdy použít vlastní kód. V dokumentaci nápovědy pro konkrétní ovládací prvek, kterou chcete upravit a zjistěte, zda <xref:System.Windows.Forms.Control.OnPaint%2A> metoda je k dispozici. Seznam všechny požadované ovládací prvky Windows najdete v tématu [ovládací prvky používané ve formulářích Windows](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md). Pokud ovládací prvek nemá <xref:System.Windows.Forms.Control.OnPaint%2A> uvedené jako člen metodu, nelze změnit její vzhled přepsáním této metody. Další informace o vlastních Malování najdete v tématu [vlastní ovládací prvek Malování a vykreslování](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).  
  
    ```vb  
    Protected Overrides Sub OnPaint(ByVal e As _  
       System.Windows.Forms.PaintEventArgs)  
       MyBase.OnPaint(e)  
       ' Insert code to do custom painting.   
       ' If you want to completely change the appearance of your control,  
       ' do not call MyBase.OnPaint(e).  
    End Sub  
    ```  
  
    ```csharp  
    protected override void OnPaint(PaintEventArgs pe)  
    {  
       base.OnPaint(pe);  
       // Insert code to do custom painting.  
       // If you want to completely change the appearance of your control,  
       // do not call base.OnPaint(pe).  
    }  
    ```  
  
11. Uložte a otestování ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 [Typy vlastních ovládacích prvků](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [Postupy: Dědění ze třídy Control](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [Postupy: Dědění ze třídy UserControl](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [Postupy: Vytváření ovládacích prvků pro Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basicu](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
