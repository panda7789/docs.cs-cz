---
title: 'Postupy: Zobrazení bočně zarovnaných karet pomocí ovládacího prvku TabControl'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tab pages [Windows Forms], displaying side-aligned tabs
- tabs [Windows Forms], displaying side-aligned tabs
- TabControl control [Windows Forms], displaying side-aligned tabs
ms.assetid: 110d5abd-3ae3-4ded-95bf-778aaac798a0
ms.openlocfilehash: d98c5906d99dff9371f8290e7dbc9c9011cd0c29
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338784"
---
# <a name="how-to-display-side-aligned-tabs-with-tabcontrol"></a>Postupy: Zobrazení bočně zarovnaných karet pomocí ovládacího prvku TabControl
<xref:System.Windows.Forms.TabControl.Alignment%2A> Vlastnost <xref:System.Windows.Forms.TabControl> podporuje zobrazení tabulek svisle (podél levého nebo pravého okraje ovládacího prvku) nikoli vodorovně (v horní nebo dolní okraj ovládacího prvku). Ve výchozím nastavení, svislé zobrazení má za následek nízký uživatelské prostředí, protože <xref:System.Windows.Forms.TabPage.Text%2A> vlastnost <xref:System.Windows.Forms.TabPage> objekt se nezobrazuje na kartě Pokud jsou vizuální styly povoleny. Neexistuje žádný přímý způsob, jak řídit směr textu v kartě. Můžete použít vlastníka nakreslit <xref:System.Windows.Forms.TabControl> na zdokonalování tohoto prostředí.  
  
 Následující postup ukazuje, jak lze vykreslit vpravo bočně zarovnaných karet s textem karty systémem zleva doprava, pomocí funkce "owner draw".  
  
### <a name="to-display-right-aligned-tabs"></a>Chcete-li zobrazit vpravo bočně zarovnaných karet  
  
1. Přidat <xref:System.Windows.Forms.TabControl> do formuláře.  
  
2. Nastavte <xref:System.Windows.Forms.TabControl.Alignment%2A> vlastnost <xref:System.Windows.Forms.TabAlignment.Right>.  
  
3. Nastavte <xref:System.Windows.Forms.TabControl.SizeMode%2A> vlastnost <xref:System.Windows.Forms.TabSizeMode.Fixed>, tak, že jsou všechny karty mají stejnou šířku.  
  
4. Nastavte <xref:System.Windows.Forms.TabControl.ItemSize%2A> vlastnost upřednostňovanou pevnou velikost karet. Mějte na paměti, která <xref:System.Windows.Forms.TabControl.ItemSize%2A> vlastnost chová, jako by byly karty v horní části, i když jsou zarovnaná vpravo. Kvůli tomu, aby bylo možné širší karty, musíte změnit <xref:System.Drawing.Size.Height%2A> vlastnost, a aby bylo možné je vyšší, musíte změnit <xref:System.Drawing.Size.Width%2A> vlastnost.  
  
     Pro nejlepší výsledky s následující příklad kódu, nastavte <xref:System.Drawing.Size.Width%2A> karet na 25 a <xref:System.Drawing.Size.Height%2A> do 100.  
  
5. Nastavte <xref:System.Windows.Forms.TabControl.DrawMode%2A> vlastnost <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.  
  
6. Definování obslužné rutiny pro <xref:System.Windows.Forms.TabControl.DrawItem> událost <xref:System.Windows.Forms.TabControl> , která generuje text zleva doprava.  
  
     [!code-csharp[TabControl.RightAlignedTabs#1](~/samples/snippets/csharp/VS_Snippets_Winforms/TabControl.RightAlignedTabs/CS/Form1.cs#1)]
     [!code-vb[TabControl.RightAlignedTabs#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/TabControl.RightAlignedTabs/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [TabControl – ovládací prvek](tabcontrol-control-windows-forms.md)
