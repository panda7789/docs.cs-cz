---
title: 'Postupy: Definování tabulky pomocí jazyka XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], defining tables
- documents [WPF], defining tables with XAML
- tables [WPF], defining with XAML
ms.assetid: 83f2dc58-437e-4cdc-b5dd-0019810c7a85
ms.openlocfilehash: 011f612527f0c9e89ec05643edbb95b2d908488c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776579"
---
# <a name="how-to-define-a-table-with-xaml"></a>Postupy: Definování tabulky pomocí jazyka XAML
Následující příklad ukazuje, jak definovat <xref:System.Windows.Documents.Table> pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  Příklad tabulka obsahuje čtyři sloupce (představované <xref:System.Windows.Documents.TableColumn> prvky) a několik řádků (reprezentována <xref:System.Windows.Documents.TableRow> prvky) obsahující data při selhání jako title, záhlaví a zápatí informace.  Musí být součástí řádky <xref:System.Windows.Documents.TableRowGroup> elementu.  Každý řádek v tabulce se skládá z jednoho nebo více buněk (představované <xref:System.Windows.Documents.TableCell> elementy).  Obsah v buňce tabulky musí být součástí <xref:System.Windows.Documents.Block> element; v takovém případě <xref:System.Windows.Documents.Paragraph> elementy se používají.  V tabulce také hostitelem hypertextový odkaz (reprezentované <xref:System.Windows.Documents.Hyperlink> element) v řádku zápatí.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[TableSnippetsXAML#_TableXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 Následující obrázek ukazuje, jak se vykreslí v tabulce definované v tomto příkladu:  
  
 ![Snímek obrazovky tabulce definován pomocí XAML.](./media/how-to-define-a-table-with-xaml/planetary-information-xaml-table.png)
