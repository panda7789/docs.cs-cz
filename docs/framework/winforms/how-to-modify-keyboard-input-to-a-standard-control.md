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
ms.openlocfilehash: 1aa22501eb3d15b30be4ea4918473cf5a48cfe94
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964293"
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a>Postupy: Úprava vstupu klávesnice do standardního ovládacího prvku
Model Windows Forms poskytuje možnost využívat a upravovat vstup z klávesnice. Spotřebovávání klíče odkazuje na zpracování klíče v rámci metody nebo obslužné rutiny události, aby jiné metody a události v nižší části fronty zpráv neobdržely hodnotu klíče. Změna klíče odkazuje na úpravu hodnoty klíče tak, aby metody a obslužné rutiny událostí dále v dolní části fronty zpráv přijímaly jinou hodnotu klíče. V tomto tématu se dozvíte, jak tyto úlohy provést.  
  
### <a name="to-consume-a-key"></a>Využití klíče  
  
- V obslužné rutině <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> <xref:System.Windows.Forms.KeyPressEventArgs> události nastavte vlastnost třídy na `true`. <xref:System.Windows.Forms.Control.KeyPress>  
  
     -nebo-  
  
     V obslužné rutině <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> <xref:System.Windows.Forms.KeyEventArgs> události nastavte vlastnost třídy na `true`. <xref:System.Windows.Forms.Control.KeyDown>  
  
    > [!NOTE]
    > Nastavení vlastnosti v obslužné rutině události nebrání <xref:System.Windows.Forms.Control.KeyUp> vyvolání událostí aproaktuálníklávesovouzkratku.<xref:System.Windows.Forms.Control.KeyPress> <xref:System.Windows.Forms.Control.KeyDown> <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> Pro tento účel použijte vlastnost.<xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A>  
  
     Následující `switch` příklad je výpis z příkazu, který <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> prochází vlastnost <xref:System.Windows.Forms.KeyPressEventArgs> přijímanou <xref:System.Windows.Forms.Control.KeyPress> obslužnou rutinou události. Tento kód využívá klíče "A" a "a".  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a>Postup úpravy standardního znakového klíče  
  
- V obslužné rutině <xref:System.Windows.Forms.KeyPressEventArgs> <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> <xref:System.Windows.Forms.Control.KeyPress> události nastavte vlastnost třídy na hodnotu nového znakového klíče.  
  
     Následující příklad je výňatek z `switch` příkazu, který upravuje b ' a ' a ' b ' na ' a '. Všimněte si, <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> že vlastnost <xref:System.Windows.Forms.KeyPressEventArgs> parametru je nastavena na `false`hodnotu, takže nová hodnota klíče je šířena do jiných metod a událostí ve frontě zpráv.  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a>Postup úpravy neznakového klíče  
  
- Přepište <xref:System.Windows.Forms.Message.WParam%2A> <xref:System.Windows.Forms.Message> <xref:System.Windows.Forms.Keys> metodu, která zpracovává zprávy systému Windows, detekuje zprávu WM_KEYDOWN nebo WM_SYSKEYDOWN a nastavte vlastnost parametru na hodnotu, která představuje nový neznakový klíč. <xref:System.Windows.Forms.Control>  
  
     Následující příklad kódu ukazuje, jak přepsat <xref:System.Windows.Forms.Control.PreProcessMessage%2A> metodu ovládacího prvku pro detekci klíčů F1 po F9 a změnit všechny klávesy F3 stisknutím klávesy F1. Další informace o <xref:System.Windows.Forms.Control> metodách, které lze přepsat pro zachycení zpráv klávesnice, najdete [v tématu vstup uživatele v aplikaci model Windows Forms](user-input-in-a-windows-forms-application.md) a [Jak funguje vstup z klávesnice](how-keyboard-input-works.md).  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu je úplná aplikace pro příklady kódu v předchozích částech. Aplikace používá vlastní ovládací prvek odvozený od <xref:System.Windows.Forms.TextBox> třídy pro využívání a úpravy vstupu z klávesnice.  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. Drawing a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také:

- [Vstup z klávesnice v aplikaci Windows Forms](keyboard-input-in-a-windows-forms-application.md)
- [Uživatelský vstup v aplikaci Windows Forms](user-input-in-a-windows-forms-application.md)
- [Jak funguje vstup z klávesnice](how-keyboard-input-works.md)
