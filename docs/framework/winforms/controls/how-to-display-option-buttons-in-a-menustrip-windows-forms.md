---
title: 'Postupy: Zobrazení tlačítek možností v MenuStrip (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: 07dd6a93e88119fa8a729747e0cb716170072cd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643712"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a>Postupy: Zobrazení tlačítek možností v MenuStrip (Windows Forms)
Přepínače, označované také jako přepínačů, jsou podobné zaškrtněte políčka s tím rozdílem, že uživatelé mohou vybrat pouze jeden po druhém. I když se ve výchozím nastavení <xref:System.Windows.Forms.ToolStripMenuItem> třída neposkytuje přepínač chování, třída poskytuje chování zaškrtávací políčko, které si můžete přizpůsobit pro implementaci přepínač chování pro položky nabídky v <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.  
  
 Když <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> vlastnost položky nabídky `true`, uživatelů můžete kliknutím na položku přepínat zobrazení zaškrtávací políčko. <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> Vlastnost označuje aktuální stav položky. K implementaci chování základní přepínač, musíte zajistit, že při výběru položky, je nastavit <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> vlastnost dříve vybrané položky do `false`.  
  
 Následující postupy popisují, jak implementovat tato a další funkce do třídy, která dědí <xref:System.Windows.Forms.ToolStripMenuItem> třídy. `ToolStripRadioButtonMenuItem` Třídy nahradí členy jako <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> a <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> poskytnout výběr chování a vzhled tlačítek možností. Kromě toho tato třída přepíše <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnost tak, která podnabídky možnosti jsou zakázáno, pokud vybrané nadřazené položky.  
  
### <a name="to-implement-option-button-selection-behavior"></a>K implementaci chování výběru – přepínač  
  
1.  Inicializovat <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> vlastnost `true` umožňující výběr položek.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]  
  
2.  Přepsat <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> metoda při výběru nové položky, zrušte zaškrtnutí políčka dříve vybrané položky.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]  
  
3.  Přepsat <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> metodou, jak zajistit, že kliknete na položku, která již byla vybrána nebude zrušte zaškrtnutí políčka.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]  
  
### <a name="to-modify-the-appearance-of-the-option-button-items"></a>K úpravě vzhledu položky – přepínač  
  
1.  Přepsat <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> metoda nahradit výchozí zaškrtnutí přepínač pomocí <xref:System.Windows.Forms.RadioButtonRenderer> třídy.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]  
  
2.  Přepsat <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, a <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> metody pro sledování stavu myší a ujistěte se, že <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> metody jsou vykreslovány stavu správné přepínač.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]  
  
### <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a>Zakázání možností na podnabídky, pokud není vybraná nadřazená položka  
  
1.  Přepsat <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnost tak, že položka je zakázaná, pokud má nadřazená položka s oběma <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> hodnotu `true` a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> hodnotu `false`.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]  
  
2.  Přepsat <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> metodu pro přihlášení k odběru <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> událost nadřazené položky.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]  
  
3.  V obslužné rutině pro nadřazené položky <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> události, zrušte platnost položky aktualizovat zobrazení s novou povoleného stavu.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu poskytuje kompletní `ToolStripRadioButtonMenuItem` třídy a <xref:System.Windows.Forms.Form> třídy a `Program` třídy k předvedení přepínač chování.  
  
 [!code-csharp[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
 [!code-vb[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RadioButtonRenderer>
- [Ovládací prvek MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
- [Postupy: Implementace vlastního prvku ToolStripRenderer](../../../../docs/framework/winforms/controls/how-to-implement-a-custom-toolstriprenderer.md)
