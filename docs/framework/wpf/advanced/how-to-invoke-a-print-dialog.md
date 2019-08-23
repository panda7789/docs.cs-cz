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
ms.openlocfilehash: cd7b06030e0fb2bba74590ee80c07c34047c5b47
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950614"
---
# <a name="how-to-invoke-a-print-dialog"></a>Postupy: Vyvolání dialogového okna Tisk
Chcete-li umožnit tisk z vaší aplikace, můžete jednoduše vytvořit a otevřít <xref:System.Windows.Controls.PrintDialog> objekt.  
  
## <a name="example"></a>Příklad  
 Ovládací prvek poskytuje jeden vstupní bod pro [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], konfiguraci a [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] odeslání úlohy. <xref:System.Windows.Controls.PrintDialog> Ovládací prvek lze snadno použít a vytvořit jeho instanci pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] značek nebo kódu. Následující příklad ukazuje, jak vytvořit instanci a otevřít ovládací prvek v kódu a jak z něho tisknout. Také ukazuje, jak zajistit, aby měl dialog uživateli možnost nastavení konkrétního rozsahu stránek. Vzorový kód předpokládá, že v kořenu jednotky C: je soubor FixedDocumentSequence. XPS.  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 Po otevření dialogového okna budou uživatelé moci vybírat z tiskáren nainstalovaných v počítači. Budou mít taky možnost vybrat [zapisovač dokumentů Microsoft XPS](https://go.microsoft.com/fwlink/?LinkId=147319) a vytvořit [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] soubor místo tisku.  
  
> [!NOTE]
> Ovládací prvek, který je popsán v tomto tématu, by neměl být zaměněn se <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> součástí model Windows Forms. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>  
  
 Výhradně řečeno, můžete použít <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> metodu bez předchozího otevření dialogového okna. V takovém smyslu lze ovládací prvek použít jako nepřehlednou tiskovou komponentu. Ale z důvodů výkonu by <xref:System.Printing.PrintQueue.AddJob%2A> bylo lepší použít buď metodu, nebo jednu z mnoha <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> metod <xref:System.Windows.Xps.XpsDocumentWriter>a <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> . Další informace najdete v tématu [programové tiskové soubory XPS](how-to-programmatically-print-xps-files.md) a.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.PrintDialog>
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Přehled tisku](printing-overview.md)
- [Zapisovač dokumentů Microsoft XPS](https://go.microsoft.com/fwlink/?LinkId=147319)
