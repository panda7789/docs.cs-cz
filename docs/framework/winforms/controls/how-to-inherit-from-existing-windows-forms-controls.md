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
ms.openlocfilehash: d0025ba136698c0a74a73e64a83fa4f526e44843
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736481"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>Postupy: Dědění ze stávajících ovládacích prvků Windows Forms

Chcete-li zvětšit funkce stávajícího ovládacího prvku, můžete vytvořit ovládací prvek odvozený z existujícího ovládacího prvku prostřednictvím dědičnosti. Při dědění z existujícího ovládacího prvku zdědíte všechny funkce a vizuální vlastnosti daného ovládacího prvku. Například pokud jste vytvořili ovládací prvek, který zdědil z <xref:System.Windows.Forms.Button>, bude nový ovládací prvek vypadat a fungovat přesně jako standardní ovládací prvek <xref:System.Windows.Forms.Button>. Můžete následně roztáhnout nebo změnit funkce nového ovládacího prvku prostřednictvím implementace vlastních metod a vlastností. V některých ovládacích prvcích můžete také změnit vizuální vzhled zděděného ovládacího prvku přepsáním jeho <xref:System.Windows.Forms.Control.OnPaint%2A> metody.

## <a name="to-create-an-inherited-control"></a>Vytvoření zděděného ovládacího prvku

1. V aplikaci Visual Studio vytvořte nový projekt **aplikace model Windows Forms** .

1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

    Zobrazí se dialogové okno **Přidat novou položku**.

1. V dialogovém okně **Přidat novou položku** dvakrát klikněte na možnost **vlastní ovládací prvek**.

    Do projektu se přidá nový vlastní ovládací prvek.

1. Pokud používáte:

    - Visual Basic, v horní části **Průzkumník řešení**klikněte na možnost **Zobrazit všechny soubory**. Rozbalte CustomControl1. vb a potom v editoru kódu otevřete CustomControl1. Designer. vb.
    - C#Otevřete CustomControl1.cs v editoru kódu.

1. Vyhledejte deklaraci třídy, která dědí z <xref:System.Windows.Forms.Control>.

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

1. Chcete-li upravit grafický vzhled ovládacího prvku, přepište metodu <xref:System.Windows.Forms.Control.OnPaint%2A>.

    > [!NOTE]
    > Přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> neumožní měnit vzhled všech ovládacích prvků. Tyto ovládací prvky, které mají všechny kresby provedené systémem Windows (například <xref:System.Windows.Forms.TextBox>), nikdy nevolají svou <xref:System.Windows.Forms.Control.OnPaint%2A> metodu, a proto nikdy nepoužijí vlastní kód. Chcete-li zjistit, zda je k dispozici metoda <xref:System.Windows.Forms.Control.OnPaint%2A>, přečtěte si dokumentaci k příslušnému ovládacímu prvku, který chcete upravit. Seznam všech ovládacích prvků Windows Form naleznete v tématu [ovládací prvky pro použití v model Windows Forms](controls-to-use-on-windows-forms.md). Pokud ovládací prvek nemá <xref:System.Windows.Forms.Control.OnPaint%2A> uveden jako metoda člena, nelze změnit jeho vzhled přepsáním této metody. Další informace o vlastním Malování naleznete v tématu [Malování a vykreslování vlastního ovládacího prvku](custom-control-painting-and-rendering.md).

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

## <a name="see-also"></a>Viz také

- [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)
- [Postupy: Dědění ze třídy Control](how-to-inherit-from-the-control-class.md)
- [Postupy: Dědění ze třídy UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Postupy: Vytváření ovládacích prvků pro Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Řešení potíží se zděděnými obslužnými rutinami událostí v Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Návod: dědění z ovládacího prvku model Windows Forms](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
