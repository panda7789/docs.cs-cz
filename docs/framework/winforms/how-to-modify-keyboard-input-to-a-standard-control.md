---
title: 'Postupy: Úprava vstupu klávesnice do standardního ovládacího prvku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyboard input [Windows Forms], modifying
- modifying keyboard input
- Windows Forms, modifying keyboard input
- keyboards [Windows Forms], keyboard input
ms.assetid: 626d3712-d866-4988-bcda-a2d5b36ec0ba
ms.openlocfilehash: c109615b9a0eb61d18f7f44e3248d2b24934ee5f
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45742966"
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a>Postupy: Úprava vstupu klávesnice do standardního ovládacího prvku
Windows Forms poskytuje možnost využívat a úprava vstupu klávesnice. Využívání klíč odkazuje na zpracování klíč v rámci obslužnou rutinu metody nebo události tak, aby jiné metody a události, které dolů fronty zpráv neobdrží hodnotu klíče. Úprava klíč odkazuje na úpravy hodnoty vlastnosti klíč tak, aby metody a obslužné rutiny událostí další dolů fronty zpráv dostávat na jinou hodnotu klíče. Toto téma ukazuje, jak provádět tyto úlohy.  
  
### <a name="to-consume-a-key"></a>Používat klíče  
  
-   V <xref:System.Windows.Forms.Control.KeyPress> nastavena obslužná rutina události, <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> vlastnost <xref:System.Windows.Forms.KeyPressEventArgs> třídu `true`.  
  
     -nebo-  
  
     V <xref:System.Windows.Forms.Control.KeyDown> nastavena obslužná rutina události, <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> vlastnost <xref:System.Windows.Forms.KeyEventArgs> třídu `true`.  
  
    > [!NOTE]
    >  Nastavení <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> vlastnost <xref:System.Windows.Forms.Control.KeyDown> obslužná rutina události byste nezabránili <xref:System.Windows.Forms.Control.KeyPress> a <xref:System.Windows.Forms.Control.KeyUp> událostí vyvolaných pro aktuální stisknutí klávesy. Použití <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> vlastnost pro tento účel.  
  
     Následující příklad je výpisem z `switch` příkaz, který prověří <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> vlastnost <xref:System.Windows.Forms.KeyPressEventArgs> přijatých <xref:System.Windows.Forms.Control.KeyPress> obslužné rutiny události. Tento kód využívá "A" a "a" klávesy znaku.  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a>Chcete-li změnit klíč standardnímu znaku  
  
-   V <xref:System.Windows.Forms.Control.KeyPress> nastavena obslužná rutina události, <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> vlastnost <xref:System.Windows.Forms.KeyPressEventArgs> třídy k hodnotě nový klíč znak.  
  
     Následující příklad je výpisem z `switch` příkaz, který upravuje "B" do "A" a "b" do "a". Všimněte si, že <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> vlastnost <xref:System.Windows.Forms.KeyPressEventArgs> parametr je nastaven na `false`, aby se nová hodnota klíče je postoupena do jiné metody a události do fronty zpráv.  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a>Chcete-li změnit neznakové klávesy  
  
-   Přepsat <xref:System.Windows.Forms.Control> metodu, která zpracovává zprávy Windows detekovat zpráva WM_KEYDOWN nebo WM_SYSKEYDOWN a nastavit <xref:System.Windows.Forms.Message.WParam%2A> vlastnost <xref:System.Windows.Forms.Message> parametr <xref:System.Windows.Forms.Keys> hodnotu, která představuje nový neznakové klíč.  
  
     Následující příklad kódu ukazuje, jak přepsat <xref:System.Windows.Forms.Control.PreProcessMessage%2A> metoda ovládacího prvku na detekci klávesy F1 až F9 a upravit F3 stisknutí klávesy F1. Další informace o <xref:System.Windows.Forms.Control> metody, které můžete přepsat, aby se zachytily zprávy týkající se klávesnice, naleznete v tématu [uživatelský vstup ve formulářové aplikaci Windows](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md) a [jak funguje vstup klávesnice](../../../docs/framework/winforms/how-keyboard-input-works.md).  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu je je aplikace dokončena a příklady kódu v předchozích částech. Aplikace používá vlastní ovládací prvek odvozen od <xref:System.Windows.Forms.TextBox> třídy využívat a úprava vstupu klávesnice.  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 [Vstup z klávesnice v aplikaci Windows Forms](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [Uživatelský vstup v aplikaci Windows Forms](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md)  
 [Jak funguje vstup z klávesnice](../../../docs/framework/winforms/how-keyboard-input-works.md)
