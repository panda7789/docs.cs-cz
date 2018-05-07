---
title: 'Postupy: Zobrazení bočně zarovnaných karet pomocí TabControl'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tab pages [Windows Forms], displaying side-aligned tabs
- tabs [Windows Forms], displaying side-aligned tabs
- TabControl control [Windows Forms], displaying side-aligned tabs
ms.assetid: 110d5abd-3ae3-4ded-95bf-778aaac798a0
ms.openlocfilehash: e145547ba4c8648a765e9507b7f35e50cb15fd82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-side-aligned-tabs-with-tabcontrol"></a>Postupy: Zobrazení bočně zarovnaných karet pomocí TabControl
<xref:System.Windows.Forms.TabControl.Alignment%2A> Vlastnost <xref:System.Windows.Forms.TabControl> podporuje zobrazení karet svisle (společně levý nebo pravý okraj ovládacího prvku), naproti tomu vodorovně (přes horní nebo dolní části ovládacího prvku). Ve výchozím nastavení, tento svislé zobrazení výsledků v nízký uživatelské prostředí, protože <xref:System.Windows.Forms.TabPage.Text%2A> vlastnost <xref:System.Windows.Forms.TabPage> objekt nejsou zobrazeny na kartě, pokud jsou povolené vizuální styly. Je také přímý způsob, jak řídit směru textu v rámci kartě. Můžete použít vlastníka kreslení v <xref:System.Windows.Forms.TabControl> ke zlepšení toto prostředí.  
  
 Následující postup ukazuje, jak k vykreslení vpravo bočně zarovnaných karet s textem karta službou zleva doprava, a použijte funkci "kreslení vlastníka".  
  
### <a name="to-display-right-aligned-tabs"></a>Chcete-li zobrazit práva bočně zarovnaných karet  
  
1.  Přidat <xref:System.Windows.Forms.TabControl> do svého formuláře.  
  
2.  Nastavte <xref:System.Windows.Forms.TabControl.Alignment%2A> vlastnost <xref:System.Windows.Forms.TabAlignment.Right>.  
  
3.  Nastavte <xref:System.Windows.Forms.TabControl.SizeMode%2A> vlastnost <xref:System.Windows.Forms.TabSizeMode.Fixed>tak, aby všechny karty jsou stejné šířky.  
  
4.  Nastavte <xref:System.Windows.Forms.TabControl.ItemSize%2A> vlastnost upřednostňovanou pevnou velikost karty. Mějte na paměti, že <xref:System.Windows.Forms.TabControl.ItemSize%2A> vlastnost chová, jako by byly na karty nahoře, i když jsou zarovnaný doprava. Výsledkem je, aby bylo možné širší karty, musíte změnit <xref:System.Drawing.Size.Height%2A> vlastnost, a aby bylo možné je vyšší, musíte změnit <xref:System.Drawing.Size.Width%2A> vlastnost.  
  
     Nejlepších výsledků s následujícím příkladu kódu nastavit <xref:System.Drawing.Size.Width%2A> z karet na 25 a <xref:System.Drawing.Size.Height%2A> do 100.  
  
5.  Nastavte <xref:System.Windows.Forms.TabControl.DrawMode%2A> vlastnost <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.  
  
6.  Definování obslužné rutiny pro <xref:System.Windows.Forms.TabControl.DrawItem> události <xref:System.Windows.Forms.TabControl> , vykreslí textu zleva doprava.  
  
     [!code-csharp[TabControl.RightAlignedTabs#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/TabControl.RightAlignedTabs/CS/Form1.cs#1)]
     [!code-vb[TabControl.RightAlignedTabs#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/TabControl.RightAlignedTabs/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvek TabControl](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)
