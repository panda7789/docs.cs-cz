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
ms.openlocfilehash: da2bb7edceaf83aa5178618fd4098631d65a7d49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a>Postupy: Zobrazení tlačítek možností v MenuStrip (Windows Forms)
Přepínače, také známé jako přepínače, jsou podobná zaškrtněte políčka s tím rozdílem, že uživatelé mohou vybrat vždy pouze jednu. I když ve výchozím nastavení <xref:System.Windows.Forms.ToolStripMenuItem> třída nenabízí možnost tlačítko chování, třída poskytuje chování zaškrtávací políčko, kterou si můžete přizpůsobit pro implementaci – tlačítko chování položek nabídky v <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.  
  
 Když <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> vlastnost položky nabídky je `true`, uživatelé kliknutím na položku k přepnutí zobrazení zaškrtnutí. <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> Vlastnost označuje aktuální stav položky. Chcete-li implementovat chování základní přepínač, je nutné zajistit, pokud je vybrána položka, můžete nastavit <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> vlastnost dříve vybrané položky do `false`.  
  
 Následující postupy popisují, jak tuto funkci implementovat a další funkce ve třídě, která dědí <xref:System.Windows.Forms.ToolStripMenuItem> třídy. `ToolStripRadioButtonMenuItem` Třída nahradí členy, jako <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> a <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> vám umožňuje výběr chování a vzhled tlačítek možností. Kromě toho tato třída přepsání <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnosti, které možnosti na podnabídky jsou zakázané, pokud je vybrána nadřazené položky.  
  
### <a name="to-implement-option-button-selection-behavior"></a>K implementaci chování výběru – tlačítko  
  
1.  Inicializace <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> vlastnost `true` umožňující výběr položek.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]  
  
2.  Přepsání <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> metoda zrušte výběr dříve vybrané položky, pokud je vybrána novou položku.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]  
  
3.  Přepsání <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> metodou, jak zajistit, že kliknete na položku, která již byla vybrána nebude zrušte zaškrtnutí políčka.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]  
  
### <a name="to-modify-the-appearance-of-the-option-button-items"></a>Chcete-li změnit vzhled položky – tlačítko  
  
1.  Přepsat <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> metody lze nahradit výchozí zaškrtnutí obsahuje přepínač s pomocí <xref:System.Windows.Forms.RadioButtonRenderer> třída.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]  
  
2.  Přepsání <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, a <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> metody pro sledování stavu myši a ujistěte se, že <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> metoda vybarví stav správný přepínač.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]  
  
### <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a>Zakázání možností na podnabídky, pokud není vybrané nadřazené položky  
  
1.  Přepsání <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnost tak, aby položka bude deaktivovaná, pokud má nadřazenou položku s oběma <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> hodnotu `true` a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> hodnotu `false`.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]  
  
2.  Přepsání <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> metoda přihlásit k odběru <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> událostí nadřazené položky.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]  
  
3.  V obslužné rutiny pro nadřazené položky <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> událostí, zneplatnit položka k aktualizaci zobrazení s novou povoleném stavu.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu poskytuje kompletní `ToolStripRadioButtonMenuItem` třída a <xref:System.Windows.Forms.Form> třídy a `Program` třída k předvedení chování možnost tlačítko.  
  
 [!code-csharp[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
 [!code-vb[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Drawing a System.Windows.Forms sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RadioButtonRenderer>  
 [Ovládací prvek MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)  
 [Postupy: Implementace vlastního prvku ToolStripRenderer](../../../../docs/framework/winforms/controls/how-to-implement-a-custom-toolstriprenderer.md)
