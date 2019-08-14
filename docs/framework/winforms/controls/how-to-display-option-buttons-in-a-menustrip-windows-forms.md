---
title: 'Postupy: Zobrazit tlačítka možností v ovládacím prvku MenuStrip (model Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: 94d683369edd6583ad8b01c2ce3f393567a5ed75
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971927"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a>Postupy: Zobrazit tlačítka možností v ovládacím prvku MenuStrip (model Windows Forms)

Tlačítka možností, označovaná také jako přepínací tlačítko, jsou podobně jako zaškrtávací políčka s tím rozdílem, že uživatelé mohou vybírat pouze jeden z nich. I když ve výchozím <xref:System.Windows.Forms.ToolStripMenuItem> nastavení Třída neposkytuje chování přepínačů, třída poskytuje chování funkce zaškrtávací políčko, které lze přizpůsobit pro implementaci chování přepínačů pro položky nabídky <xref:System.Windows.Forms.MenuStrip> v ovládacím prvku.

Když je <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> `true`vlastnost položky nabídky, uživatelé můžou kliknout na položku a přepnout tak zobrazení značky zaškrtnutí. <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> Vlastnost označuje aktuální stav položky. Chcete-li implementovat základní chování přepínače, je nutné zajistit, aby se při výběru položky nastavila <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> vlastnost pro dříve vybranou položku na. `false`

Následující postupy popisují, jak implementovat tuto a další funkce ve třídě, která dědí <xref:System.Windows.Forms.ToolStripMenuItem> třídu. Třída Přepisuje členy <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> , jako jsou a <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> , aby poskytovaly chování výběru a vzhled tlačítek možností. `ToolStripRadioButtonMenuItem` Tato třída navíc Přepisuje <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnost tak, aby byly možnosti v podnabídce zakázané, pokud není vybraná nadřazená položka.

## <a name="to-implement-option-button-selection-behavior"></a>Implementace chování výběru přepínačů

1. Inicializujte `true` vlastnost pro povolení výběru položky. <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>

     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]

2. <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> Přepsat metodu pro vymazání výběru dříve vybrané položky, když je vybrána nová položka.

     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]

3. Přepište <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> metodu, aby se zajistilo, že kliknete na položku, která již byla vybrána, nevymaže výběr.

     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]

## <a name="to-modify-the-appearance-of-the-option-button-items"></a>Úprava vzhledu položek přepínačů

1. Přepište <xref:System.Windows.Forms.RadioButtonRenderer> metodu pro nahrazení výchozího kontrolního označení pomocí přepínače pomocí třídy. <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>

     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]

2. <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A> Přepište<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>metody ,,<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> a pro sledování stavu myši a zajistěte, že metodavykreslísprávnýstavtlačítkaMožnosti.<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>

     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]

## <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a>Zakázání možností v podnabídce, když není vybraná nadřazená položka

1. `false` <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> `true` <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> Přepsat vlastnost tak, že položka je zakázána, když má nadřazenou položku s hodnotou a hodnotou. <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>

     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]

2. Přepsat metodu pro přihlášení k odběru <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> události nadřazené položky. <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A>

     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]

3. V obslužné rutině pro událost nadřazené položky <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> zruší platnost položky, aby se zobrazila v novém povoleném stavu.

     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]

## <a name="example"></a>Příklad

Následující příklad kódu poskytuje úplnou `ToolStripRadioButtonMenuItem` třídu <xref:System.Windows.Forms.Form> a třídu a `Program` třídu pro předvedení chování možností tlačítek.

[!code-csharp[ToolStripRadioButtonMenuItem#000](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
[!code-vb[ToolStripRadioButtonMenuItem#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Tento příklad vyžaduje:

- Odkazy na sestavení System, System. Drawing a System. Windows. Forms.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RadioButtonRenderer>
- [Ovládací prvek MenuStrip](menustrip-control-windows-forms.md)
- [Postupy: Implementace vlastního ToolStripRenderer](how-to-implement-a-custom-toolstriprenderer.md)
