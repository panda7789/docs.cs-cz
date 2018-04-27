---
title: 'Postupy: Úprava vstupu klávesnice do standardního ovládacího prvku'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyboard input [Windows Forms], modifying
- modifying keyboard input
- Windows Forms, modifying keyboard input
- keyboards [Windows Forms], keyboard input
ms.assetid: 626d3712-d866-4988-bcda-a2d5b36ec0ba
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 13aa7ce515a60ae541559eaeff8037454bac6a41
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a>Postupy: Úprava vstupu klávesnice do standardního ovládacího prvku
Windows Forms poskytuje možnost využívat a úprava vstupu klávesnice. Využívání klíč odkazuje na zpracování klíč v rámci obslužnou rutinu metoda nebo událost, aby jiné metody a události, které dolů fronty zpráv neobdrží hodnota klíče. Úprava klíč odkazuje na změnou hodnoty klíče, aby metody a obslužné rutiny událostí další dolů fronty zpráv s jinou hodnotou klíče. Toto téma ukazuje, jak k těmto úkolům.  
  
### <a name="to-consume-a-key"></a>Používat klíč  
  
-   V <xref:System.Windows.Forms.Control.KeyPress> nastavit popisovač události <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> vlastnost <xref:System.Windows.Forms.KeyPressEventArgs> třídy k `true`.  
  
     -nebo-  
  
     V <xref:System.Windows.Forms.Control.KeyDown> nastavit popisovač události <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> vlastnost <xref:System.Windows.Forms.KeyEventArgs> třídy k `true`.  
  
    > [!NOTE]
    >  Nastavení <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> vlastnost <xref:System.Windows.Forms.Control.KeyDown> obslužné rutiny události nezabrání <xref:System.Windows.Forms.Control.KeyPress> a <xref:System.Windows.Forms.Control.KeyUp> vyvolána pro aktuální klávesu. Použití <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> vlastnost pro tento účel.  
  
     Následující příklad je výňatek ze `switch` příkaz, který ověřuje, zda <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> vlastnost <xref:System.Windows.Forms.KeyPressEventArgs> přijatých <xref:System.Windows.Forms.Control.KeyPress> obslužné rutiny události. Tento kód spotřebuje "A" a "a" znak klíče.  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a>Chcete-li upravit klíč standardní znak  
  
-   V <xref:System.Windows.Forms.Control.KeyPress> nastavit popisovač události <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> vlastnost <xref:System.Windows.Forms.KeyPressEventArgs> třídu na hodnotu nový klíč znak.  
  
     Následující příklad je výňatek ze `switch` příkaz, který upravuje "B" na "A" a "b" na "a". Všimněte si, že <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> vlastnost <xref:System.Windows.Forms.KeyPressEventArgs> parametr je nastaven na `false`tak, aby nová hodnota klíče se rozšíří do jiné metody a událostí ve frontě zpráv.  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a>Chcete-li upravit noncharacter klíč  
  
-   Přepsání <xref:System.Windows.Forms.Control> metoda, která zpracuje zprávy Windows zjistit WM_KEYDOWN nebo WM_SYSKEYDOWN zprávu a nastavte <xref:System.Windows.Forms.Message.WParam%2A> vlastnost <xref:System.Windows.Forms.Message> parametru <xref:System.Windows.Forms.Keys> hodnotu, která představuje nový noncharacter klíč.  
  
     Následující příklad kódu ukazuje, jak lze přepsat <xref:System.Windows.Forms.Control.PreProcessMessage%2A> metoda ovládacího prvku ke zjištění klávesy F1 až F9 a upravit F3 stisknutí klávesy F1. Další informace o <xref:System.Windows.Forms.Control> metody, které můžete přepsat zachytávat zprávy klávesnice, najdete v části [uživatelský vstup ve formulářové aplikaci Windows](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md) a [jak funguje vstup klávesnice](../../../docs/framework/winforms/how-keyboard-input-works.md).  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu je úplná žádost o příklady kódu v předchozích částech. Aplikace používá vlastní ovládací prvek odvozen od <xref:System.Windows.Forms.TextBox> třída spotřebovat a úprava vstupu klávesnice.  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Drawing a System.Windows.Forms sestavení.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 [Vstup z klávesnice v aplikaci Windows Forms](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [Uživatelský vstup v aplikaci Windows Forms](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md)  
 [Jak funguje vstup z klávesnice](../../../docs/framework/winforms/how-keyboard-input-works.md)
