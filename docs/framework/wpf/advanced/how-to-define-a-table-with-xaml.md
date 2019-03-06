---
title: 'Postupy: Definice tabulky pomocí XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], defining tables
- documents [WPF], defining tables with XAML
- tables [WPF], defining with XAML
ms.assetid: 83f2dc58-437e-4cdc-b5dd-0019810c7a85
ms.openlocfilehash: 7398af6fddae56238e1af3ee4e726420c01ab7ea
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376920"
---
# <a name="how-to-define-a-table-with-xaml"></a>Postupy: Definice tabulky pomocí XAML
Následující příklad ukazuje, jak definovat <xref:System.Windows.Documents.Table> pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  Příklad tabulka obsahuje čtyři sloupce (představované <xref:System.Windows.Documents.TableColumn> prvky) a několik řádků (reprezentována <xref:System.Windows.Documents.TableRow> prvky) obsahující data při selhání jako title, záhlaví a zápatí informace.  Musí být součástí řádky <xref:System.Windows.Documents.TableRowGroup> elementu.  Každý řádek v tabulce se skládá z jednoho nebo více buněk (představované <xref:System.Windows.Documents.TableCell> elementy).  Obsah v buňce tabulky musí být součástí <xref:System.Windows.Documents.Block> element; v takovém případě <xref:System.Windows.Documents.Paragraph> elementy se používají.  V tabulce také hostitelem hypertextový odkaz (reprezentované <xref:System.Windows.Documents.Hyperlink> element) v řádku zápatí.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[TableSnippetsXAML#_TableXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 Následující obrázek ukazuje, jak se vykreslí v tabulce definované v tomto příkladu.  
  
 ![Vykreslený tabulky. ](./media/tableeg.png "TableEG")
