---
title: 'Postupy: Přidání ovládacích prvků do formulářů Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: 31820775d4f7fb981599e806aa5e27655039e6ac
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720771"
---
# <a name="how-to-add-controls-to-windows-forms"></a>Postupy: Přidání ovládacích prvků do formulářů Windows
Většinou forem jsou navržené tak, že přidáte ovládací prvky na plochu formuláře k definování uživatelského rozhraní (UI). A *ovládací prvek* je součást na formulář pro zobrazení informací ani nebude přijímat uživatelský vstup. Další informace o ovládacích prvcích najdete v tématu [ovládacích prvků Windows Forms](index.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-draw-a-control-on-a-form"></a>K nakreslení ovládacího prvku ve formuláři  
  
1.  Otevřete formulář. Další informace najdete v tématu [jak: Zobrazení formulářů Windows v návrháři](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).  
  
2.  V **nástrojů**, klepněte na ovládací prvek, který chcete přidat do formuláře.  
  
3.  Ve formuláři klikněte na požadované levého horního rohu ovládacího prvku, který má být umístěná a přetáhněte ji na požadované místo pravého dolního rohu ovládacího prvku, který má být umístěná.  
  
     Ovládací prvek je přidán do formuláře pomocí zadaného umístění a velikost.  
  
    > [!NOTE]
    >  Každý ovládací prvek má definovaný výchozí velikost. Můžete přidat ovládací prvek do formuláře ve výchozí velikost ovládacího prvku přetažením z **nástrojů** do formuláře.  
  
### <a name="to-drag-a-control-to-a-form"></a>Přetáhněte ovládací prvek do formuláře  
  
1.  Otevřete formulář. Další informace najdete v tématu [jak: Zobrazení formulářů Windows v návrháři](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).  
  
2.  V **nástrojů**, klepněte na ovládací prvek a přetáhněte ji do svého formuláře.  
  
     Ovládací prvek je přidán do formuláře v zadaném umístění v její výchozí velikost.  
  
    > [!NOTE]
    >  Dvakrát kliknete na ovládací prvek v **nástrojů** se přidá do levého horního rohu formuláře v její výchozí velikost.  
  
     Můžete také přidat ovládací prvky dynamicky do formuláře v době běhu. V následujícím příkladu kódu <xref:System.Windows.Forms.TextBox> ovládací prvek bude přidán do formuláře při <xref:System.Windows.Forms.Button> dojde ke kliknutí na ovládací prvek.  
  
    > [!NOTE]
    >  Následující postup vyžaduje existenci formulář s **tlačítko** ovládacího prvku, `Button1`, již umístěné na něj.  
  
### <a name="to-add-a-control-to-a-form-programmatically"></a>Přidání ovládacího prvku na formulář prostřednictvím kódu programu  
  
1.  V metodě, která zpracovává tlačítka `Click` událostí v rámci třídy formuláře, vložit kód podobný následujícímu se přidat odkaz na řídicí proměnná nastavit u tohoto prvku `Location`a přidejte ovládací prvek.  
  
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
    >  Můžete také přidat kód pro inicializaci jiné vlastnosti ovládacího prvku.  
  
    > [!IMPORTANT]
    >  Místního počítače k ohrožení zabezpečení prostřednictvím sítě může být odkazem škodlivý `UserControl`. To může být pouze v případě nežádoucí osoba vytváření škodlivé vlastního ovládacího prvku, za nímž následuje omylem přidání do projektu žádný problém.  
  
## <a name="see-also"></a>Viz také:
- [Windows Forms – ovládací prvky](index.md)
- [Uspořádávání ovládacích prvků ve Windows Forms](arranging-controls-on-windows-forms.md)
- [Postupy: Změna velikosti ovládacích prvků ve formulářích Windows](how-to-resize-controls-on-windows-forms.md)
- [Postupy: Nastavit Text, zobrazený ovládacím prvkem Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
