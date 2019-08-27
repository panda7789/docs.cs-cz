---
title: 'Postupy: Přidávání ovládacích prvků do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: bfe9449ecc862c361719d27dba2f5ed9af563957
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046055"
---
# <a name="how-to-add-controls-to-windows-forms"></a>Postupy: Přidávání ovládacích prvků do Windows Forms

Většina formulářů je navržena přidáním ovládacích prvků na plochu formuláře k definování uživatelského rozhraní (UI). *Ovládací prvek* je komponenta na formuláři sloužící k zobrazení informací nebo přijetí vstupu uživatele. Další informace o ovládacích prvcích naleznete v tématu [model Windows Forms Controls](index.md).

## <a name="to-draw-a-control-on-a-form"></a>Nakreslení ovládacího prvku na formuláři

1. Otevřete formulář. Další informace najdete v tématu [jak: Zobrazit model Windows Forms v Návrháři](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))

2. V sadě **nástrojů**klikněte na ovládací prvek, který chcete přidat do formuláře.

3. Ve formuláři klikněte na místo, kde chcete umístit levý horní roh ovládacího prvku, a přetáhněte jej na místo, kde chcete umístit pravý dolní roh ovládacího prvku.

    Ovládací prvek je přidán do formuláře se zadaným umístěním a velikostí.

    > [!NOTE]
    > U každého ovládacího prvku je definována výchozí velikost. Ovládací prvek lze přidat do formuláře ve výchozí velikosti ovládacího prvku přetažením z **panelu nástrojů** do formuláře.

## <a name="to-drag-a-control-to-a-form"></a>Přetažení ovládacího prvku do formuláře

1. Otevřete formulář. Další informace najdete v tématu [jak: Zobrazit model Windows Forms v Návrháři](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))

2. V sadě **nástrojů**klikněte na požadovaný ovládací prvek a přetáhněte ho do formuláře.

    Ovládací prvek je přidán do formuláře v zadaném umístění ve výchozí velikosti.

    > [!NOTE]
    > Můžete dvakrát kliknout na ovládací prvek v **sadě nástrojů** a přidat ho do levého horního rohu formuláře ve výchozí velikosti.

    Ovládací prvky lze také dynamicky přidávat do formuláře za běhu. V následujícím příkladu <xref:System.Windows.Forms.TextBox> kódu bude ovládací prvek přidán do formuláře <xref:System.Windows.Forms.Button> při kliknutí na ovládací prvek.

    > [!NOTE]
    > Následující postup vyžaduje existenci formuláře s ovládacím prvkem `Button1` **tlačítko** , na kterém je již umístěn.

## <a name="to-add-a-control-to-a-form-programmatically"></a>Postup pro přidání ovládacího prvku do formuláře prostřednictvím kódu programu

1. V metodě, která zpracovává `Click` událost tlačítka v rámci třídy formuláře, vložte kód podobný následujícímu pro přidání odkazu na proměnnou ovládacího prvku, nastavení `Location`ovládacího prvku a přidání ovládacího prvku.

    ```vb
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
       Dim MyText As New TextBox()
       MyText.Location = New Point(25, 25)
       Me.Controls.Add(MyText)
    End Sub
    ```

    ```csharp
    private void button1_Click(object sender, System.EventArgs e)
    {
       TextBox myText = new TextBox();
       myText.Location = new Point(25,25);
       this.Controls.Add (myText);
    }
    ```

    ```cpp
    private:
      System::Void button1_Click(System::Object ^  sender,
        System::EventArgs ^  e)
      {
        TextBox ^ myText = gcnew TextBox();
        myText->Location = Point(25,25);
        this->Controls->Add(myText);
      }
    ```

    > [!NOTE]
    > Můžete také přidat kód pro inicializaci dalších vlastností ovládacího prvku.

    > [!IMPORTANT]
    > Místní počítač můžete vystavit bezpečnostnímu riziku prostřednictvím sítě, a to tak, že `UserControl`se na něj odkazuje škodlivá aktivita. To by mělo být obavy jenom v případě, že by škodlivá osoba vytvořila škodlivý vlastní ovládací prvek, a pak ji nepřidali do projektu omylem.

## <a name="see-also"></a>Viz také:

- [Windows Forms – ovládací prvky](index.md)
- [Postupy: Změnit velikost ovládacích prvků na model Windows Forms](how-to-resize-controls-on-windows-forms.md)
- [Postupy: Nastavení textu zobrazovaného ovládacím prvkem model Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
