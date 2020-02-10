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
ms.openlocfilehash: f7ef3312d876324b44b055d70fd22e3fba075ec6
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095169"
---
# <a name="how-to-invoke-a-print-dialog"></a>Postupy: Vyvolání dialogového okna Tisk
Chcete-li umožnit tisk z vaší aplikace, můžete jednoduše vytvořit a otevřít objekt <xref:System.Windows.Controls.PrintDialog>.  
  
## <a name="example"></a>Příklad  
 Ovládací prvek <xref:System.Windows.Controls.PrintDialog> poskytuje jeden vstupní bod pro [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], konfiguraci a odeslání úlohy ve formátu XPS. Ovládací prvek lze snadno použít a vytvořit jeho instanci pomocí kódu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nebo kódu. Následující příklad ukazuje, jak vytvořit instanci a otevřít ovládací prvek v kódu a jak z něho tisknout. Také ukazuje, jak zajistit, aby měl dialog uživateli možnost nastavení konkrétního rozsahu stránek. Vzorový kód předpokládá, že v kořenu jednotky C: je soubor FixedDocumentSequence. XPS.  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 Po otevření dialogového okna budou uživatelé moci vybírat z tiskáren nainstalovaných v počítači. Budou mít taky možnost vybrat [zapisovač dokumentů Microsoft XPS](/windows/win32/printdocs/microsoft-xps-document-writer) a místo tisku vytvořit soubor XPS (XML Paper Specification).  
  
> [!NOTE]
> <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> ovládací prvek WPF, který je popsán v tomto tématu, by neměl být zaměněn pomocí <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> součásti model Windows Forms.  
  
 Výhradně řečeno, můžete použít metodu <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> bez předchozího otevření dialogového okna. V takovém smyslu lze ovládací prvek použít jako nepřehlednou tiskovou komponentu. Ale z důvodů výkonu by bylo lepší použít buď metodu <xref:System.Printing.PrintQueue.AddJob%2A>, nebo jednu z mnoha <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> a <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metod <xref:System.Windows.Xps.XpsDocumentWriter>. Další informace najdete v tématu [programové tiskové soubory XPS](how-to-programmatically-print-xps-files.md) a.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.PrintDialog>
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Přehled tisku](printing-overview.md)
- [Zapisovač dokumentů Microsoft XPS](/windows/win32/printdocs/microsoft-xps-document-writer)
