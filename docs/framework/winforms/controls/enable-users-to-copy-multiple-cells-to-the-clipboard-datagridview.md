---
title: Povolit uživatelům kopírovat více buněk do schránky z ovládacího prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], copying to Clipboard
- DataGridView control [Windows Forms], copying multiple cells
- data grids [Windows Forms], copying multiple cells
- Clipboard [Windows Forms], copying multiple cells
ms.assetid: fd0403b2-d0e3-4ae0-839c-0f737e1eb4a9
ms.openlocfilehash: 2bb74a1f0c59b28ab496ce9c89c1c1b5f9d8147b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745784"
---
# <a name="how-to-enable-users-to-copy-multiple-cells-to-the-clipboard-from-the-windows-forms-datagridview-control"></a>Postupy: Povolení kopírování více buněk do schránky z ovládacího prvku Windows Forms DataGridView
Když povolíte kopírování buněk, zpřístupníte data v ovládacím prvku <xref:System.Windows.Forms.DataGridView> k ostatním aplikacím prostřednictvím <xref:System.Windows.Forms.Clipboard>. Hodnoty vybraných buněk jsou převedeny na řetězce a přidány do schránky jako textové hodnoty s oddělovači pro vložení do aplikací, jako je například Poznámkový blok a Excel, a jako tabulka ve formátu HTML pro vložení do aplikací, jako je Word.  
  
 Můžete nakonfigurovat kopírování buňky pouze pro kopírování hodnot buňky, pro zahrnutí textu záhlaví řádku a sloupce do dat schránky nebo pro zahrnutí textu záhlaví, pokud uživatelé vyberou celé řádky nebo sloupce.  
  
 V závislosti na režimu výběru můžou uživatelé vybrat několik odpojených skupin buněk. Když uživatel zkopíruje buňky do schránky, řádky a sloupce, které neobsahují vybrané buňky, se nezkopírují. Všechny ostatní řádky nebo sloupce se stanou řádky a sloupci v tabulce dat zkopírovaných do schránky. Nevybrané buňky na těchto řádcích nebo sloupcích se zkopírují jako prázdná zástupné symboly do schránky.  
  
### <a name="to-enable-cell-copying"></a>Povolení kopírování buněk  
  
- Nastavte vlastnost <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#15)]
     [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#15)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kompletního kódu ukazuje, jak se buňky zkopírují do schránky. Tento příklad obsahuje tlačítko, které zkopíruje vybrané buňky do schránky pomocí metody <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> a zobrazí obsah schránky v textovém poli.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento kód vyžaduje:  
  
- Odkazy na sestavení N:System a N:System.Windows.Forms.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>
- <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A>
- [Výběr a používání schránky s ovládacím prvkem Windows Forms DataGridView](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
