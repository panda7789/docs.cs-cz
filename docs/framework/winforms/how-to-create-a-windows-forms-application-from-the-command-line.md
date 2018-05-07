---
title: 'Postupy: vytvoření aplikace Windows Forms z příkazového řádku'
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe7c1eddd67e678e7086d948efb854a6b4b52f6e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a>Postupy: vytvoření aplikace Windows Forms z příkazového řádku
Následující postupy popisují základní kroky, které je třeba provést k vytvoření a spuštění aplikace Windows Forms z příkazového řádku. Rozsáhlá podpora pro tyto postupy v sadě Visual Studio není k dispozici.  Viz také [návod: vytvoření jednoduché formuláře Windows](http://msdn.microsoft.com/library/z9w2f38k\(v=vs.100\)).  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-create-the-form"></a>Vytvoření formuláře  
  
1.  V souboru prázdný kód zadejte následující importu nebo pomocí příkazů:  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2.  Deklarace třídy s názvem `Form1` , dědí z třídy formuláře.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3.  Výchozí konstruktor pro vytvoření `Form1`.  
  
     Další kód přidá do konstruktoru v následujícím postupu.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4.  Přidat `Main` metody pro třídu.  
  
    1.  Použít <xref:System.STAThreadAttribute> do jazyka C# `Main` je metoda k určení aplikace Windows Forms single-threaded apartment. (Atribut není nutné v jazyce Visual Basic, protože aplikace Windows forms vyvinuté s použitím jazyka Visual Basic model single-threaded apartment ve výchozím nastavení.)  
  
    2.  Volání <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> použít styly operačního systému do vaší aplikace.  
  
    3.  Vytvoření instance formuláře a potom ho spusťte.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a>Pro zkompilování a spuštění aplikace  
  
1.  Na příkazovém řádku rozhraní .NET Framework přejděte do adresáře, který jste vytvořili `Form1` třídy.  
  
2.  Zkompilujte formuláře.  
  
    -   Pokud používáte C#, zadejte: `csc form1.cs`  
  
         `-or-`  
  
    -   Pokud používáte Visual Basic, zadejte: `vbc form1.vb`  
  
3.  Na příkazovém řádku zadejte: `Form1.exe`  
  
## <a name="adding-a-control-and-handling-an-event"></a>Přidání ovládacího prvku a zpracování události  
 Předchozí kroky postupu ukázal, jak lze pouze vytvořit základní formuláře systému Windows, který se zkompiluje a spustí. Následující postup vám ukáže, jak vytvořit a přidání ovládacího prvku formuláře a zpracovat události pro ovládací prvek. Další informace o ovládacích prvcích můžete přidat do formulářů Windows najdete v tématu [ovládacích prvků Windows Forms](../../../docs/framework/winforms/controls/index.md).  
  
 Kromě vědět, jak vytvářet aplikace Windows Forms, byste měli vědět programování na základě událostí a jak se zpracovat vstup uživatele. Další informace najdete v tématu [vytváření obslužných rutin událostí v systému Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md), a [zpracování uživatelského vstupu](../../../docs/framework/winforms/controls/handling-user-input.md)  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a>Deklarovat ovládacího prvku tlačítko a zpracování události jeho klikněte na  
  
1.  Deklarace tlačítko – ovládací prvek s názvem `button1`.  
  
2.  V konstruktoru, vytvořte na tlačítko a nastavit jeho <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> a <xref:System.Windows.Forms.Control.Text%2A> vlastnosti.  
  
3.  Přidání tlačítka do formuláře.  
  
     Následující příklad kódu ukazuje, jak deklarovat ovládacího prvku tlačítko.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4.  Vytvoření metody pro zpracování <xref:System.Windows.Forms.Control.Click> události pro tlačítko.  
  
5.  V obslužné rutiny události kliknutí zobrazí <xref:System.Windows.Forms.MessageBox> se zprávou "Hello World".  
  
     Následující příklad kódu ukazuje, jak zpracovat tlačítko ovládacího prvku klikněte na události.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6.  Přidružení <xref:System.Windows.Forms.Control.Click> událostí pomocí metody, které jste vytvořili.  
  
     Následující příklad kódu ukazuje, jak přiřadit událost metodu.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7.  Zkompilování a spuštění aplikace, jak je popsáno v předchozím postupu.  
  
## <a name="example"></a>Příklad  
 Následující ukázka kódu je kompletní příklad z předchozích postupech.  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Kompilace kódu, postupujte podle pokynů v postupu budete pokračovat, které popisují, jak zkompilování a spuštění aplikace.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Control>  
 [Změna vzhledu Windows Forms](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)  
 [Rozšiřování aplikací Windows Forms](../../../docs/framework/winforms/advanced/index.md)  
 [Začínáme s Windows Forms](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
