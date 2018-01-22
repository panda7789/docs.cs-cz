---
title: "Postupy: Přidávání ovládacích prvků do formulářů Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ab92f7a56173ec71642d0cc09f3f81e9859533b4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-controls-to-windows-forms"></a>Postupy: Přidávání ovládacích prvků do formulářů Windows
Většina formulářů jsou navrženy přidáním ovládacích prvků na povrch ve formátu pro definování uživatelského rozhraní (UI). A *řízení* je komponenta ve formuláři použít k zobrazení informací nebo přijímají vstup uživatele. Další informace o ovládacích prvcích najdete v tématu [ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/index.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-draw-a-control-on-a-form"></a>K vykreslení ovládacího prvku ve formuláři  
  
1.  Otevřete formulář. Další informace najdete v tématu [postupy: zobrazení Windows Forms v návrháři](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).  
  
2.  V **sada nástrojů**, klikněte na ovládací prvek, který chcete přidat do svého formuláře.  
  
3.  Ve formuláři klikněte na levý horní roh ovládacího prvku na nalezen a přetáhněte ji na místo, kde pravém dolním rohu ovládacího prvku na nalezen.  
  
     Ovládací prvek je přidán do formuláře s zadané umístění a velikost.  
  
    > [!NOTE]
    >  Každý ovládací prvek má výchozí velikost definované. Ovládacího prvku do svého formuláře ovládacího prvku výchozí velikost můžete přidat přetažením z **sada nástrojů** do formuláře.  
  
### <a name="to-drag-a-control-to-a-form"></a>Přetáhněte ovládacího prvku na formulář  
  
1.  Otevřete formulář. Další informace najdete v tématu [postupy: zobrazení Windows Forms v návrháři](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).  
  
2.  V **sada nástrojů**, klikněte na ovládací prvek a přetáhněte ji do svého formuláře.  
  
     Ovládací prvek je přidán do formuláře v zadaném umístění v jeho výchozí velikost.  
  
    > [!NOTE]
    >  Poklepáním na ovládací prvek v **sada nástrojů** ho přidejte do levého horního rohu formuláře v jeho výchozí velikost.  
  
     Můžete také přidat ovládací prvky dynamicky do formuláře za běhu. V následujícím příkladu kódu <xref:System.Windows.Forms.TextBox> ovládací prvek bude přidán do formuláře při <xref:System.Windows.Forms.Button> po kliknutí na ovládací prvek.  
  
    > [!NOTE]
    >  Následující postup vyžaduje existenci formulář s **tlačítko** řízení, `Button1`, již umístěné na něm.  
  
### <a name="to-add-a-control-to-a-form-programmatically"></a>Přidání ovládacího prvku na formulář prostřednictvím kódu programu  
  
1.  V metodě, která zpracovává na tlačítko `Click` události v rámci svého formuláře třídy, vložení kódu podobný následujícímu se přidat odkaz na řídicí proměnná, nastavte ovládacího prvku `Location`a přidejte ovládacího prvku.  
  
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
    >  Můžete také přidat kód pro inicializaci jiných vlastností ovládacího prvku.  
  
    > [!IMPORTANT]
    >  Mohou být vystaveny místního počítače k ohrožení zabezpečení přes síť odkazem škodlivý `UserControl`. To může být pouze o problém v případě osoba se zlými úmysly vytváření škodlivé vlastního ovládacího prvku, za nímž následuje jste omylem ho přidáte do projektu.  
  
## <a name="see-also"></a>Viz také  
 [Windows Forms – ovládací prvky](../../../../docs/framework/winforms/controls/index.md)  
 [Uspořádávání ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Postupy: Změna velikosti ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)  
 [Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [Ovládací prvky používané ve Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
