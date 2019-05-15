---
title: 'Postupy: Vytvoření aplikace Windows Forms z příkazového řádku'
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
ms.openlocfilehash: 72195dd49c163b26a5bcfa739768718f2a32f346
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588976"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a>Postupy: Vytvoření aplikace Windows Forms z příkazového řádku
Následující postupy popisují základní kroky, které je třeba provést k vytvoření a spuštění aplikace modelu Windows Forms z příkazového řádku. Není k dispozici rozsáhlou podporu pro tyto postupy v sadě Visual Studio.  Viz také [názorný postup: Ovládací prvek hostování Windows Forms v subsystému WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-create-the-form"></a>Vytvoření formuláře  
  
1. Prázdný soubor kódu zadejte následující import nebo příkazy using:  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. Deklarovat třídu s názvem `Form1` , která dědí z třídy formuláře.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. Výchozí konstruktor pro vytvoření `Form1`.  
  
     Přidejte další kód do konstruktoru v následujícím postupu.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. Přidat `Main` metodu do třídy.  
  
    1. Použít <xref:System.STAThreadAttribute> jazyka C# `Main` metoda k určení aplikace Windows Forms je jednovláknový apartment. (Atribut není nutné v jazyce Visual Basic, protože aplikace Windows forms vyvinutých s využitím jazyka Visual Basic jednovláknový apartment modelu ve výchozím nastavení.)  
  
    2. Volání <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> pro používání stylů pro operační systém pro vaše aplikace.  
  
    3. Vytvoření instance formuláře a spustíme ji.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a>Kompilace a spuštění aplikace  
  
1. Na příkazovém řádku rozhraní .NET Framework, přejděte do adresáře, který jste vytvořili `Form1` třídy.  
  
2. Zkompilujte formuláře.  
  
    - Pokud používáte C#, zadejte: `csc form1.cs`  
  
         `-or-`  
  
    - Pokud používáte Visual Basic, zadejte: `vbc form1.vb`  
  
3. Na příkazovém řádku zadejte: `Form1.exe`  
  
## <a name="adding-a-control-and-handling-an-event"></a>Přidání ovládacího prvku a zpracování událostí  
 Předchozí kroky postupu jsme vám ukázali jen vytvoření základního formuláře Windows, který zkompiluje a spustí. Následující postup obsahuje pokyny k vytvoření a přidání ovládacího prvku na formuláři a zpracovat události pro ovládací prvek. Další informace o ovládacích prvků můžete přidat do formulářů Windows, naleznete v tématu [ovládacích prvků Windows Forms](./controls/index.md).  
  
 Kromě pochopení způsobu, jak vytvořit aplikace Windows Forms, měli byste porozumět programování založené na událostech a způsob zpracování vstupu uživatele. Další informace najdete v tématu [vytváření obslužných rutin událostí ve Windows Forms](creating-event-handlers-in-windows-forms.md), a [zpracování uživatelského vstupu](./controls/handling-user-input.md)  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a>Deklarovat ovládací prvek button a zpracovat jeho událost click  
  
1. Deklarovat ovládacího prvku tlačítko s názvem `button1`.  
  
2. V konstruktoru, vytvořit tlačítko a nastavte jeho <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> a <xref:System.Windows.Forms.Control.Text%2A> vlastnosti.  
  
3. Přidání tlačítka do formuláře.  
  
     Následující příklad kódu ukazuje, jak deklarovat ovládací prvek tlačítko.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. Vytvořit metodu ke zpracování <xref:System.Windows.Forms.Control.Click> události pro tlačítko.  
  
5. V obslužné rutině události kliknutí, zobrazení <xref:System.Windows.Forms.MessageBox> zprávou "Hello World".  
  
     Následující příklad kódu ukazuje, jak zpracovat tlačítko ovládacího prvku klikněte na událost.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. Přidružit <xref:System.Windows.Forms.Control.Click> událostí pomocí metody, které jste vytvořili.  
  
     Následující příklad kódu ukazuje, jak přidružit metodu události.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. Kompilace a spuštění aplikace, jak je popsáno v předchozím postupu.  
  
## <a name="example"></a>Příklad  
 Následující ukázka kódu je kompletní příklad z předchozích kroků.  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [Změna vzhledu Windows Forms](changing-the-appearance-of-windows-forms.md)
- [Rozšiřování aplikací Windows Forms](./advanced/index.md)
- [Začínáme s Windows Forms](getting-started-with-windows-forms.md)
