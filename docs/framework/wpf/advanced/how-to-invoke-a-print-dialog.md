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
ms.openlocfilehash: 75a4160366766efbd19d6e8ae26fbec102e7f95b
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924497"
---
# <a name="how-to-invoke-a-print-dialog"></a>Postupy: Vyvolání dialogového okna Tisk
Chcete-li umožnit tisk z vaší aplikace, můžete jednoduše vytvořit a otevřít <xref:System.Windows.Controls.PrintDialog> objekt.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Controls.PrintDialog>Ovládací prvek poskytuje jeden vstupní bod pro [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] odesílání, konfiguraci a odeslání úlohy ve formátu XPS. Ovládací prvek lze snadno použít a vytvořit jeho instanci pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] značek nebo kódu. Následující příklad ukazuje, jak vytvořit instanci a otevřít ovládací prvek v kódu a jak z něho tisknout. Také ukazuje, jak zajistit, aby měl dialog uživateli možnost nastavení konkrétního rozsahu stránek. Vzorový kód předpokládá, že v kořenu jednotky C: je soubor FixedDocumentSequence. XPS.  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 Po otevření dialogového okna budou uživatelé moci vybírat z tiskáren nainstalovaných v počítači. Budou mít taky možnost vybrat [zapisovač dokumentů Microsoft XPS](/windows/win32/printdocs/microsoft-xps-document-writer) a místo tisku vytvořit soubor XPS (XML Paper Specification).  
  
> [!NOTE]
> <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>Ovládací prvek WPF, který je popsán v tomto tématu, by neměl být zaměněn se <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> součástí model Windows Forms.  
  
 Výhradně řečeno, můžete použít <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> metodu bez předchozího otevření dialogového okna. V takovém smyslu lze ovládací prvek použít jako nepřehlednou tiskovou komponentu. Ale z důvodů výkonu by bylo lepší použít buď <xref:System.Printing.PrintQueue.AddJob%2A> metodu, nebo jednu z mnoha <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metod a <xref:System.Windows.Xps.XpsDocumentWriter> . Další informace najdete v tématu [programové tiskové soubory XPS](how-to-programmatically-print-xps-files.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.PrintDialog>
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Přehled tisku](printing-overview.md)
- [Zapisovací modul dokumentů Microsoft XPS](/windows/win32/printdocs/microsoft-xps-document-writer)
