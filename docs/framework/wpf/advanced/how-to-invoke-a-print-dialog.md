---
title: 'Postupy: Vyvolání dialogového okna Tisk'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 65ea65e13d3217466eeacdac4c386cc02c68b29a
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-invoke-a-print-dialog"></a>Postupy: Vyvolání dialogového okna Tisk
Pokud chcete zadat možnost tisknout z aplikace, můžete jednoduše vytvořit a otevřete <xref:System.Windows.Controls.PrintDialog> objektu.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Controls.PrintDialog> Řízení poskytuje jeden vstupní bod pro [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], konfiguraci a [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] úlohy odeslání. Ovládací prvek se snadno používá a může být vytvořena pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kód. Následující příklad ukazuje, jak vytvořit instanci a otevřete ovládací prvek v kódu a jak tisknout z něj. Také ukazuje, jak zajistit, aby dialogové okno bude uživatel možnost nastavení určitého rozsahu stránek. Příklad kódu předpokládá, že je soubor FixedDocumentSequence.xps v kořenové složce jednotky C:.  
  
 [!code-csharp[printdialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 Jakmile otevřete dialogové okno, budou uživatelé moci vybrat z tiskárny v počítači nainstalovanou. Možnost výběru budou mít i [zapisovací modul dokumentů Microsoft XPS](http://go.microsoft.com/fwlink/?LinkId=147319) vytvořit [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] souboru místo.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Kontrolu nad [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], které je popsané v tomto tématu byste neměli zaměňovat s <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> součásti Windows Forms.  
  
 Přesněji řečeno, můžete použít <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> metoda bez někdy otevření dialogu. V smysl můžete využít jako komponentu neviditelný tisk ovládacího prvku. Ale z důvodů výkonu by bylo vhodnější použít buď <xref:System.Printing.PrintQueue.AddJob%2A> metoda nebo jednoho z dalších <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> a <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter>. Další informace o tom najdete v tématu [programové soubory XPS tiskových](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md) a.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.PrintDialog>  
 [Dokumenty v platformě WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Přehled tisku](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Zapisovací modul dokumentů Microsoft XPS](http://go.microsoft.com/fwlink/?LinkId=147319)
