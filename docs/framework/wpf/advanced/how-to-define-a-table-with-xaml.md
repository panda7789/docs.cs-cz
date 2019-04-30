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
# <a name="how-to-define-a-table-with-xaml"></a><span data-ttu-id="7e22b-102">Postupy: Definování tabulky pomocí jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="7e22b-102">How to: Define a Table with XAML</span></span>
<span data-ttu-id="7e22b-103">Následující příklad ukazuje, jak definovat <xref:System.Windows.Documents.Table> pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7e22b-103">The following example demonstrates how to define a <xref:System.Windows.Documents.Table> using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  <span data-ttu-id="7e22b-104">Příklad tabulka obsahuje čtyři sloupce (představované <xref:System.Windows.Documents.TableColumn> prvky) a několik řádků (reprezentována <xref:System.Windows.Documents.TableRow> prvky) obsahující data při selhání jako title, záhlaví a zápatí informace.</span><span class="sxs-lookup"><span data-stu-id="7e22b-104">The example table has four columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and several rows (represented by <xref:System.Windows.Documents.TableRow> elements) containing data as well as title, header, and footer information.</span></span>  <span data-ttu-id="7e22b-105">Musí být součástí řádky <xref:System.Windows.Documents.TableRowGroup> elementu.</span><span class="sxs-lookup"><span data-stu-id="7e22b-105">Rows must be contained in a <xref:System.Windows.Documents.TableRowGroup> element.</span></span>  <span data-ttu-id="7e22b-106">Každý řádek v tabulce se skládá z jednoho nebo více buněk (představované <xref:System.Windows.Documents.TableCell> elementy).</span><span class="sxs-lookup"><span data-stu-id="7e22b-106">Each row in the table is comprised of one or more cells (represented by <xref:System.Windows.Documents.TableCell> elements).</span></span>  <span data-ttu-id="7e22b-107">Obsah v buňce tabulky musí být součástí <xref:System.Windows.Documents.Block> element; v takovém případě <xref:System.Windows.Documents.Paragraph> elementy se používají.</span><span class="sxs-lookup"><span data-stu-id="7e22b-107">Content in a table cell must be contained in a <xref:System.Windows.Documents.Block> element; in this case <xref:System.Windows.Documents.Paragraph> elements are used.</span></span>  <span data-ttu-id="7e22b-108">V tabulce také hostitelem hypertextový odkaz (reprezentované <xref:System.Windows.Documents.Hyperlink> element) v řádku zápatí.</span><span class="sxs-lookup"><span data-stu-id="7e22b-108">The table also hosts a hyperlink (represented by the <xref:System.Windows.Documents.Hyperlink> element) in the footer row.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e22b-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e22b-109">Example</span></span>  
 [!code-xaml[TableSnippetsXAML#_TableXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 <span data-ttu-id="7e22b-110">Následující obrázek ukazuje, jak se vykreslí v tabulce definované v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="7e22b-110">The following figure shows how the table defined in this example renders:</span></span>  
  
 ![Snímek obrazovky tabulce definován pomocí XAML.](./media/how-to-define-a-table-with-xaml/planetary-information-xaml-table.png)
