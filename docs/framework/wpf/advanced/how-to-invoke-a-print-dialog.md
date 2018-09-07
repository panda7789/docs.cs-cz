---
title: 'Postupy: Vyvolání dialogového okna Tisk'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
ms.openlocfilehash: 271652fe9e98f9a381da5655bd313e12f8ee917d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44068547"
---
# <a name="how-to-invoke-a-print-dialog"></a>Postupy: Vyvolání dialogového okna Tisk
Pokud chcete poskytnout možnost tisku z vaší aplikace, můžete jednoduše vytvořit a otevřít <xref:System.Windows.Controls.PrintDialog> objektu.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Controls.PrintDialog> Řízení poskytuje jeden vstupní bod pro [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], konfiguraci a [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] úlohy odeslání. Ovládací prvek se snadno používá a můžete vytvořit instanci pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] značek nebo kódu. Následující příklad ukazuje, jak vytvořit instanci a otevření ovládacího prvku v kódu a tom, jak vytisknout. Také ukazuje, jak zajistit, aby dialogové okno bude uživatel možnost nastavení konkrétního rozsahu objektů stránky. Příklad kódu předpokládá, že je soubor FixedDocumentSequence.xps v kořenové složce jednotky C:.  
  
 [!code-csharp[printdialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 Jakmile se otevře dialogové okno, uživatelé budou moct vybrat z tiskáren v počítači nainstalovanou. Budou mít i možnost výběru [zapisovací modul dokumentů Microsoft XPS](https://go.microsoft.com/fwlink/?LinkId=147319) k vytvoření [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] souboru místo tisk.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Kontrolu nad [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], která je popsána v tomto tématu, neměly by být zaměňovány s <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> komponenty Windows Forms.  
  
 Přesněji řečeno, můžete použít <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> metoda bez někdy otevření dialogového okna. V tomto smyslu ovládací prvek může sloužit jako komponentu nezobrazený tisku. Z důvodů výkonu by bylo vhodnější použít jednu, ale <xref:System.Printing.PrintQueue.AddJob%2A> metody nebo jeden mnoho <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> a <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter>. Další informace najdete v části [programově tisk souborů XPS z](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md) a.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.PrintDialog>  
 [Dokumenty v platformě WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Přehled tisku](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Zapisovací modul dokumentů Microsoft XPS](https://go.microsoft.com/fwlink/?LinkId=147319)
