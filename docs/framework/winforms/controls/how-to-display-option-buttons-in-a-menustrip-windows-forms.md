---
title: 'Postupy: Zobrazení tlačítek možností v MenuStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: f3010e71396ce562e9dbdefd4b75b36f3a81ffb3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735523"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a>Postupy: Zobrazení tlačítek možností v MenuStrip (Windows Forms)

Tlačítka možností, označovaná také jako přepínací tlačítko, jsou podobně jako zaškrtávací políčka s tím rozdílem, že uživatelé mohou vybírat pouze jeden z nich. I když ve výchozím nastavení třída <xref:System.Windows.Forms.ToolStripMenuItem> neposkytuje chování přepínače, třída poskytuje chování funkce zaškrtávací políčko, které lze přizpůsobit, aby implementovala chování možností tlačítek pro položky nabídky v ovládacím prvku <xref:System.Windows.Forms.MenuStrip>.

Když je `true`vlastnost <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> položky nabídky, uživatelé můžou kliknout na položku a přepnout tak zobrazení zaškrtnutí. Vlastnost <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> označuje aktuální stav položky. Chcete-li implementovat základní chování přepínače, je nutné zajistit, aby při výběru položky byla vlastnost <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> pro dříve vybranou položku nastavena na hodnotu `false`.

Následující postupy popisují, jak implementovat tuto a další funkce ve třídě, která dědí třídu <xref:System.Windows.Forms.ToolStripMenuItem>. Třída `ToolStripRadioButtonMenuItem` Přepisuje členy, jako je například <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> a <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>, k poskytnutí chování výběr a vzhled tlačítek možností. Kromě toho tato třída Přepisuje vlastnost <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> tak, aby byly možnosti v podnabídce zakázané, pokud není vybraná nadřazená položka.

## <a name="to-implement-option-button-selection-behavior"></a>Implementace chování výběru přepínačů

1. Chcete-li povolit výběr položky, inicializujte vlastnost <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> na `true`.

     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]

2. Přepsat metodu <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> pro vymazání výběru dříve vybrané položky, když je vybrána nová položka.

     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]

3. Přepište metodu <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A>, aby se zajistilo, že kliknete na položku, která již byla vybrána, nebude výběr vymazán.

     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]

## <a name="to-modify-the-appearance-of-the-option-button-items"></a>Úprava vzhledu položek přepínačů

1. Přepište metodu <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> pro nahrazení výchozího kontrolního panelu pomocí přepínače pomocí <xref:System.Windows.Forms.RadioButtonRenderer> třídy.

     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]

2. Přepište metody <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>a <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> pro sledování stavu myši a zajistěte, že metoda <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> vykreslí správný stav tlačítka Možnosti.

     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]

## <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a>Zakázání možností v podnabídce, když není vybraná nadřazená položka

1. Přepište vlastnost <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>, aby byla položka neaktivní, když má nadřazenou položku s hodnotou <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> `true` a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> hodnotou `false`.

     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]

2. Přepište metodu <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> pro přihlášení k odběru události <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> nadřazené položky.

     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]

3. V obslužné rutině události <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> nadřazených položek zruší platnost položky pro zobrazení aktualizace s novým stavem Enabled.

     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]

## <a name="example"></a>Příklad

Následující příklad kódu poskytuje úplnou třídu `ToolStripRadioButtonMenuItem` a třídu <xref:System.Windows.Forms.Form> a třídu `Program` k předvedení chování možností tlačítek.

[!code-csharp[ToolStripRadioButtonMenuItem#000](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
[!code-vb[ToolStripRadioButtonMenuItem#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Tento příklad vyžaduje:

- Odkazy na sestavení System, System. Drawing a System. Windows. Forms.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RadioButtonRenderer>
- [Ovládací prvek MenuStrip](menustrip-control-windows-forms.md)
- [Postupy: Implementace vlastního prvku ToolStripRenderer](how-to-implement-a-custom-toolstriprenderer.md)
