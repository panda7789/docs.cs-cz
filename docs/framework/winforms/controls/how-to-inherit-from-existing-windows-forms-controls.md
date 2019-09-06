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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fcf95e08296f5a8ec5a386ac614482c034e72c8b
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373240"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>Postupy: Dědění ze stávajících ovládacích prvků Windows Forms

Chcete-li zvětšit funkce stávajícího ovládacího prvku, můžete vytvořit ovládací prvek odvozený z existujícího ovládacího prvku prostřednictvím dědičnosti. Při dědění z existujícího ovládacího prvku zdědíte všechny funkce a vizuální vlastnosti daného ovládacího prvku. Například pokud jste vytvořili ovládací prvek, který zdědil z <xref:System.Windows.Forms.Button>, váš nový ovládací prvek by vypadal a fungoval přesně jako standardní <xref:System.Windows.Forms.Button> ovládací prvek. Můžete následně roztáhnout nebo změnit funkce nového ovládacího prvku prostřednictvím implementace vlastních metod a vlastností. V některých ovládacích prvcích můžete také změnit vizuální vzhled zděděného ovládacího prvku přepsáním jeho <xref:System.Windows.Forms.Control.OnPaint%2A> metody.

## <a name="to-create-an-inherited-control"></a>Vytvoření zděděného ovládacího prvku

1. V aplikaci Visual Studio vytvořte nový projekt **aplikace model Windows Forms** .

1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

    Zobrazí se dialogové okno **Přidat novou položku**.

1. V dialogovém okně **Přidat novou položku** dvakrát klikněte na možnost **vlastní ovládací prvek**.

    Do projektu se přidá nový vlastní ovládací prvek.

1. Pokud používáte:

    - Visual Basic, v horní části **Průzkumník řešení**klikněte na možnost **Zobrazit všechny soubory**. Rozbalte CustomControl1. vb a potom v editoru kódu otevřete CustomControl1. Designer. vb.
    - C#Otevřete CustomControl1.cs v editoru kódu.

1. Vyhledejte deklaraci třídy, ze <xref:System.Windows.Forms.Control>které dědí.

1. Změňte základní třídu na ovládací prvek, ze kterého chcete dědit.

     Například pokud chcete dědit z <xref:System.Windows.Forms.Button>, změňte deklaraci třídy na následující:

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

1. Pokud používáte Visual Basic, uložte a zavřete CustomControl1. Designer. vb. Otevřete CustomControl1. vb v editoru kódu.

1. Implementujte všechny vlastní metody nebo vlastnosti, které bude váš ovládací prvek obsahovat.

1. Chcete-li upravit grafický vzhled ovládacího prvku, přepište <xref:System.Windows.Forms.Control.OnPaint%2A> metodu.

    > [!NOTE]
    > Přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> nebude umožňovat úpravu vzhledu všech ovládacích prvků. Tyto ovládací prvky, které mají všechny kresby provedené systémem Windows (například <xref:System.Windows.Forms.TextBox>), nikdy nevolají svou <xref:System.Windows.Forms.Control.OnPaint%2A> metodu, a proto nikdy nepoužijí vlastní kód. Chcete-li zjistit, zda <xref:System.Windows.Forms.Control.OnPaint%2A> je metoda k dispozici, přečtěte si dokumentaci k příslušnému ovládacímu prvku, který chcete upravit. Seznam všech ovládacích prvků Windows Form naleznete v tématu [ovládací prvky pro použití v model Windows Forms](controls-to-use-on-windows-forms.md). Pokud ovládací prvek není <xref:System.Windows.Forms.Control.OnPaint%2A> uveden jako metoda člena, nelze změnit jeho vzhled přepsáním této metody. Další informace o vlastním Malování naleznete v tématu [Malování a vykreslování vlastního ovládacího prvku](custom-control-painting-and-rendering.md).

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

1. Uložte a otestujte svůj ovládací prvek.

## <a name="see-also"></a>Viz také:

- [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)
- [Postupy: Zdědit z třídy ovládacího prvku](how-to-inherit-from-the-control-class.md)
- [Postupy: Zdědit z třídy UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Postupy: Vytváření ovládacích prvků pro model Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Řešení potíží se zděděnými obslužnými rutinami událostí v Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Návod: Dědění z ovládacího prvku model Windows Forms](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
