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
ms.openlocfilehash: 788addee7c024577d029626da4aeb86d0ca9076a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300525"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>Postupy: Dědění ze stávajících ovládacích prvků Windows Forms
Pokud chcete rozšířit funkce pro existující ovládací prvek, můžete vytvořit ovládací prvek odvozený z existujícího ovládacího prvku prostřednictvím dědičnosti. Při dědění z existujícího ovládacího prvku, zdědí všechny funkce a vlastností ovládacího prvku visual. Například, pokud vytváříte ovládací prvek, který dědí z <xref:System.Windows.Forms.Button>, by vypadalo nového ovládacího prvku a act stejně jako standardní <xref:System.Windows.Forms.Button> ovládacího prvku. Pak můžete rozšířit nebo upravit funkce nasazovaných nového ovládacího prvku prostřednictvím implementace vlastních metod a vlastností. V některých ovládacích prvků, můžete také změnit vzhled zděděný ovládací prvek tak, že přepíšete její <xref:System.Windows.Forms.Control.OnPaint%2A> metody.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-an-inherited-control"></a>Chcete-li vytvořit zděděný ovládací prvek  
  
1. Vytvořte nový **formulářová aplikace Windows** projektu.  
  
2. Z **projektu** nabídce zvolte **přidat novou položku**.  
  
     Zobrazí se dialogové okno **Přidat novou položku**.  
  
3. V **přidat novou položku** dialogové okno, klikněte dvakrát na **vlastní ovládací prvek**.  
  
     Nový vlastní ovládací prvek se přidá do vašeho projektu.  
  
4. Pokud používáte Visual Basic, v horní části **Průzkumníka řešení**, klikněte na tlačítko **zobrazit všechny soubory**. Rozbalte CustomControl1.vb a poté otevřete CustomControl1.Designer.vb v editoru kódu.  
  
5. Pokud používáte C#, otevřete CustomControl1.cs v editoru kódu.  
  
6. Vyhledejte deklaraci třídy, která dědí z <xref:System.Windows.Forms.Control>.  
  
7. Změňte základní třídu pro ovládací prvek, který se má Zdědit z.  
  
     Například, pokud chcete dědit z <xref:System.Windows.Forms.Button>, změňte deklaraci třídy na následující:  
  
    ```vb  
    Partial Class CustomControl1  
        Inherits System.Windows.Forms.Button  
    ```  
  
    ```csharp  
    public partial class CustomControl1 : System.Windows.Forms.Button  
    ```  
  
8. Pokud používáte Visual Basic, uložte a zavřete CustomControl1.Designer.vb. Otevřete CustomControl1.vb v editoru kódu.  
  
9. Implementujte všechny vlastní metody nebo vlastnosti, které bude obsahovat váš ovládací prvek.  
  
10. Pokud chcete upravit vzhled grafického ovládacího prvku, má přednost před <xref:System.Windows.Forms.Control.OnPaint%2A> metody.  
  
    > [!NOTE]
    >  Přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> nebude možné změnit vzhled všech ovládacích prvků. Tyto ovládací prvky, které mají všechny jejich Malování provádí Windows (například <xref:System.Windows.Forms.TextBox>) nikdy neměl volat jejich <xref:System.Windows.Forms.Control.OnPaint%2A> metoda a proto se nikdy použít vlastní kód. Přečtěte si dokumentaci nápovědy pro konkrétní ovládací prvek, kterou chcete upravit a zjistěte, jestli <xref:System.Windows.Forms.Control.OnPaint%2A> metoda je k dispozici. Seznam všechny ovládací prvky formuláře Windows najdete v tématu [ovládací prvky používané ve formulářích Windows](controls-to-use-on-windows-forms.md). Pokud ovládací prvek nemá žádné <xref:System.Windows.Forms.Control.OnPaint%2A> uvedená jako člena metody, není možné pozměnit jeho vzhled přepsáním této metody. Další informace o vlastních Malování, naleznete v tématu [vlastní ovládací prvek Malování a vykreslování](custom-control-painting-and-rendering.md).  
  
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
  
11. Uložit a testování ovládacího prvku.  
  
## <a name="see-also"></a>Viz také:

- [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)
- [Postupy: Dědit ze třídy Control](how-to-inherit-from-the-control-class.md)
- [Postupy: Dědit ze třídy UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Postupy: Autor ovládacích prvků Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basic](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
