---
title: Vytvoření aplikace pro Windows Forms z příkazového řádku
titleSuffix: ''
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
ms.openlocfilehash: 7bd3add526a6b60d628b05d46eca22ce407c36b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181990"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a>Postup: Vytvoření aplikace pro Windows Forms z příkazového řádku

Následující postupy popisují základní kroky, které je nutné provést k vytvoření a spuštění aplikace windows forms z příkazového řádku. Existuje rozsáhlá podpora pro tyto postupy v sadě Visual Studio.  Viz [také návod: Hostování ovládacího prvku Windows Forms Ve wpf](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-create-the-form"></a>Vytvoření formuláře  
  
1. Do prázdného souboru kódu `Imports` `using` zadejte následující příkazy nebo příkazy:  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. Deklarujte `Form1` třídu s názvem, která dědí z třídy Form:
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. Vytvořte konstruktor bez `Form1`parametrů pro .
  
     Přidáte další kód konstruktoru v následném postupu.
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. Přidejte `Main` metodu do třídy.
  
    1. Použijte <xref:System.STAThreadAttribute> metodu C# `Main` k určení aplikace Windows Forms je apartment s jedním podprocesem. (Atribut není nutné v jazyce Visual Basic, protože formuláře systému Windows aplikace vyvinuté v jazyce Visual Basic použít model apartment s jedním podprocesem ve výchozím nastavení.)  
  
    2. Volání <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> použít styly operačního systému pro vaši aplikaci.  
  
    3. Vytvořte instanci formuláře a spusťte ji.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a>Kompilace a spuštění aplikace  
  
1. Na příkazovém řádku rozhraní .NET Framework `Form1` přejděte do adresáře, který jste vytvořili.  
  
2. Zkompilujte formulář.  
  
    - Pokud používáte C#, zadejte:`csc form1.cs`  
  
         `-or-`  
  
    - Pokud používáte jazyk Visual Basic, zadejte:`vbc form1.vb`  
  
3. Na příkazovém řádku zadejte:`Form1.exe`  
  
## <a name="adding-a-control-and-handling-an-event"></a>Přidání ovládacího prvku a zpracování události

Předchozí kroky postupu ukázaly, jak pouze vytvořit základní formulář systému Windows, který kompiluje a spouští. Další postup vám ukáže, jak vytvořit a přidat ovládací prvek do formuláře a zpracovat událost pro ovládací prvek. Další informace o ovládacích prvcích, které lze přidat do systému Windows Forms, naleznete v [tématu Ovládací prvky forem systému Windows](./controls/index.md).
  
 Kromě pochopení, jak vytvářet aplikace windows forms, měli byste pochopit programování založené na událostech a jak zpracovat vstup uživatele. Další informace naleznete [v tématech Vytváření obslužných rutin událostí ve formulářích systému Windows](creating-event-handlers-in-windows-forms.md)a Zpracování vstupu [uživatele.](./controls/handling-user-input.md)  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a>Deklarování ovládacího prvku tlačítka a zpracování události kliknutí  
  
1. Deklarujte `button1`ovládací prvek tlačítka s názvem .  
  
2. V konstruktoru vytvořte tlačítko <xref:System.Windows.Forms.Control.Size%2A>a <xref:System.Windows.Forms.Control.Location%2A> <xref:System.Windows.Forms.Control.Text%2A> nastavte jeho vlastnosti a vlastnosti .  
  
3. Přidejte tlačítko do formuláře.  
  
     Následující příklad kódu ukazuje, jak deklarovat ovládací prvek tlačítka:
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. Vytvořte metodu <xref:System.Windows.Forms.Control.Click> pro zpracování události pro tlačítko.  
  
5. V obslužné <xref:System.Windows.Forms.MessageBox> rutině události kliknutí zobrazte a se zprávou "Hello World".  
  
     Následující příklad kódu ukazuje, jak zpracovat událost kliknutí ovládacího prvku tlačítka:
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. Přidružte <xref:System.Windows.Forms.Control.Click> událost k metodě, kterou jste vytvořili.  
  
     Následující příklad kódu ukazuje, jak přidružit událost k metodě.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. Zkompilujte a spusťte aplikaci, jak je popsáno v předchozím postupu.  
  
## <a name="example"></a>Příklad  

Následující příklad kódu je úplný příklad z předchozích postupů:
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [Změna vzhledu Windows Forms](changing-the-appearance-of-windows-forms.md)
- [Rozšiřování formulářových aplikací Windows](./advanced/index.md)
- [Začínáme s Windows Forms](getting-started-with-windows-forms.md)
