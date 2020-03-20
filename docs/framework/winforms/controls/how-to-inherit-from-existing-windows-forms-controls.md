---
title: Dědění ze stávajících ovládacích prvků
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b0e0053816efde349c7e4d13d03bef5f8801c667
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78849377"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>Postupy: Dědění ze stávajících ovládacích prvků Windows Forms

Pokud chcete rozšířit funkce existujícího ovládacího prvku, můžete vytvořit ovládací prvek odvozený z existujícího ovládacího prvku prostřednictvím dědičnosti. Při dědění z existujícího ovládacího prvku zdědíte všechny funkce a vizuální vlastnosti tohoto ovládacího prvku. Například pokud jste vytvářeli ovládací prvek, který zdědil z <xref:System.Windows.Forms.Button>, nový <xref:System.Windows.Forms.Button> ovládací prvek bude vypadat a chovat přesně jako standardní ovládací prvek. Potom můžete rozšířit nebo upravit funkce nového ovládacího prvku prostřednictvím implementace vlastních metod a vlastností. V některých ovládacích prvcích můžete také změnit vizuální <xref:System.Windows.Forms.Control.OnPaint%2A> vzhled zděděného ovládacího prvku přepsáním jeho metody.

## <a name="to-create-an-inherited-control"></a>Vytvoření zděděného ovládacího prvku

1. V sadě Visual Studio vytvořte nový projekt **aplikace Windows Forms.**

1. V nabídce **Projekt** zvolte **Přidat novou položku**.

    Zobrazí se dialogové okno **Přidat novou položku**.

1. V dialogovém okně **Přidat novou položku** poklepejte na **položku Vlastní ovládací prvek**.

    Do projektu je přidán nový vlastní ovládací prvek.

1. Pokud používáte:

    - Visual Basic v horní části **Průzkumníka řešení**klikněte na **Zobrazit všechny soubory**. Rozbalte soubor CustomControl1.vb a v Editoru kódu otevřete soubor CustomControl1.Designer.vb.
    - C#, otevřete CustomControl1.cs v Editoru kódu.

1. Vyhledejte deklaraci třídy, <xref:System.Windows.Forms.Control>která dědí z .

1. Změňte základní třídu na ovládací prvek, ze kterého chcete dědit.

     Chcete-li například dědit <xref:System.Windows.Forms.Button>z , změňte deklaraci třídy na následující:

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

1. Pokud používáte visual basic, uložte a zavřete CustomControl1.Designer.vb. V Editoru kódu otevřete soubor CustomControl1.vb.

1. Implementujte všechny vlastní metody nebo vlastnosti, které bude váš ovládací prvek zahrnovat.

1. Pokud chcete změnit grafický vzhled ovládacího prvku, <xref:System.Windows.Forms.Control.OnPaint%2A> přepište metodu.

    > [!NOTE]
    > Přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> neumožňuje změnit vzhled všech ovládacích prvků. Tyto ovládací prvky, které mají všechny jejich <xref:System.Windows.Forms.TextBox>malování provádí <xref:System.Windows.Forms.Control.OnPaint%2A> systém Windows (například ) nikdy volat jejich metodu, a proto nikdy nebude používat vlastní kód. Naleznete v dokumentaci nápovědy pro konkrétní ovládací prvek, který chcete upravit, abyste zjistili, <xref:System.Windows.Forms.Control.OnPaint%2A> zda je metoda k dispozici. Seznam všech ovládacích prvků formuláře systému Windows naleznete v tématu [Ovládací prvky pro použití ve formulářích systému Windows](controls-to-use-on-windows-forms.md). Pokud ovládací prvek <xref:System.Windows.Forms.Control.OnPaint%2A> nemá uvedeny jako členské metody, nelze změnit jeho vzhled přepsáním této metody. Další informace o vlastním malování naleznete v [tématu Vlastní řídicí malba a vykreslování](custom-control-painting-and-rendering.md).

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

1. Uložte a otestujte ovládací prvek.

## <a name="see-also"></a>Viz také

- [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)
- [Postupy: Dědění ze třídy Control](how-to-inherit-from-the-control-class.md)
- [Postupy: Dědění ze třídy UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Postupy: Vytváření ovládacích prvků pro Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Návod: Dědění z ovládacího prvku formulářů systému Windows](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
