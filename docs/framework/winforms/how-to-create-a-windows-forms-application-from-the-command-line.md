---
title: 'Postupy: Vytvoření aplikace model Windows Forms z příkazového řádku'
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
ms.openlocfilehash: af1548602ece8ea0f5720a836ec05648854e198f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127250"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a>Postupy: Vytvoření aplikace model Windows Forms z příkazového řádku

Následující postupy popisují základní kroky, které je nutné provést, chcete-li vytvořit a spustit aplikaci model Windows Forms z příkazového řádku. Existuje Rozsáhlá podpora těchto postupů v aplikaci Visual Studio.  Viz také [Návod: hostování ovládacího prvku model Windows Forms v](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)subsystému WPF.
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-create-the-form"></a>Vytvoření formuláře  
  
1. V prázdném souboru kódu zadejte následující `Imports` nebo `using` příkazy:  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. Deklarovat třídu s názvem `Form1`, která dědí z třídy Form:
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. Vytvořte konstruktor bez parametrů pro `Form1`.
  
     V následné proceduře přidáte do konstruktoru více kódu.
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. Přidejte do třídy metodu `Main`.
  
    1. Použijte <xref:System.STAThreadAttribute> k metodě C# `Main` a určete tak, že aplikace pro model Windows Forms je objekt Apartment s jedním vláknem. (Atribut není v Visual Basic potřebný, protože aplikace Windows Forms vyvinuté pomocí Visual Basic ve výchozím nastavení používají model Apartment s jedním vláknem.)  
  
    2. Zavolejte <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> pro použití stylů operačního systému pro vaši aplikaci.  
  
    3. Vytvořte instanci formuláře a spusťte ji.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a>Kompilace a spuštění aplikace  
  
1. Na příkazovém řádku .NET Framework přejděte do adresáře, který jste vytvořili `Form1` třídy.  
  
2. Zkompilujte formulář.  
  
    - Pokud používáte C#, zadejte: `csc form1.cs`  
  
         `-or-`  
  
    - Pokud používáte Visual Basic, zadejte: `vbc form1.vb`  
  
3. Do příkazového řádku zadejte: `Form1.exe`  
  
## <a name="adding-a-control-and-handling-an-event"></a>Přidání ovládacího prvku a zpracování události

Předchozí kroky postupu ukázaly, jak vytvořit základní formulář Windows, který se zkompiluje a spustí. Další postup vám ukáže, jak vytvořit a přidat ovládací prvek do formuláře a zpracovat událost pro ovládací prvek. Další informace o ovládacích prvcích, které lze přidat do model Windows Forms, naleznete v tématu [model Windows Forms Controls](./controls/index.md).
  
 Kromě pochopení způsobu vytváření model Windows Formsch aplikací byste měli pochopit programování založené na událostech a postup zpracování vstupu uživatele. Další informace naleznete v tématu [vytváření obslužných rutin událostí v model Windows Forms](creating-event-handlers-in-windows-forms.md)a [zpracování vstupu uživatele](./controls/handling-user-input.md) .  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a>Deklarace ovládacího prvku tlačítko a zpracování jeho události Click  
  
1. Deklarujte ovládací prvek tlačítko s názvem `button1`.  
  
2. V konstruktoru vytvořte tlačítko a nastavte jeho <xref:System.Windows.Forms.Control.Size%2A>, vlastnosti <xref:System.Windows.Forms.Control.Location%2A> a <xref:System.Windows.Forms.Control.Text%2A>.  
  
3. Přidejte tlačítko do formuláře.  
  
     Následující příklad kódu ukazuje, jak deklarovat ovládací prvek tlačítko:
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. Vytvořte metodu pro zpracování události <xref:System.Windows.Forms.Control.Click> pro tlačítko.  
  
5. V obslužné rutině události Click Zobrazte <xref:System.Windows.Forms.MessageBox> se zprávou "Hello World".  
  
     Následující příklad kódu ukazuje, jak zpracovat událost kliknutí ovládacího prvku tlačítko:
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. Přidružte událost <xref:System.Windows.Forms.Control.Click> k metodě, kterou jste vytvořili.  
  
     Následující příklad kódu ukazuje, jak přidružit událost k metodě.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. Zkompilujte a spusťte aplikaci, jak je popsáno v předchozím postupu.  
  
## <a name="example"></a>Příklad  
 
Následující příklad kódu je kompletní příklad z předchozích postupů:
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [Změna vzhledu Windows Forms](changing-the-appearance-of-windows-forms.md)
- [Rozšiřování formulářových aplikací Windows](./advanced/index.md)
- [Začínáme s Windows Forms](getting-started-with-windows-forms.md)
