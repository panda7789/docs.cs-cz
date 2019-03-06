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
# <a name="how-to-define-a-table-with-xaml"></a><span data-ttu-id="f4394-102">Postupy: Definice tabulky pomocí XAML</span><span class="sxs-lookup"><span data-stu-id="f4394-102">How to: Define a Table with XAML</span></span>
<span data-ttu-id="f4394-103">Následující příklad ukazuje, jak definovat <xref:System.Windows.Documents.Table> pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f4394-103">The following example demonstrates how to define a <xref:System.Windows.Documents.Table> using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  <span data-ttu-id="f4394-104">Příklad tabulka obsahuje čtyři sloupce (představované <xref:System.Windows.Documents.TableColumn> prvky) a několik řádků (reprezentována <xref:System.Windows.Documents.TableRow> prvky) obsahující data při selhání jako title, záhlaví a zápatí informace.</span><span class="sxs-lookup"><span data-stu-id="f4394-104">The example table has four columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and several rows (represented by <xref:System.Windows.Documents.TableRow> elements) containing data as well as title, header, and footer information.</span></span>  <span data-ttu-id="f4394-105">Musí být součástí řádky <xref:System.Windows.Documents.TableRowGroup> elementu.</span><span class="sxs-lookup"><span data-stu-id="f4394-105">Rows must be contained in a <xref:System.Windows.Documents.TableRowGroup> element.</span></span>  <span data-ttu-id="f4394-106">Každý řádek v tabulce se skládá z jednoho nebo více buněk (představované <xref:System.Windows.Documents.TableCell> elementy).</span><span class="sxs-lookup"><span data-stu-id="f4394-106">Each row in the table is comprised of one or more cells (represented by <xref:System.Windows.Documents.TableCell> elements).</span></span>  <span data-ttu-id="f4394-107">Obsah v buňce tabulky musí být součástí <xref:System.Windows.Documents.Block> element; v takovém případě <xref:System.Windows.Documents.Paragraph> elementy se používají.</span><span class="sxs-lookup"><span data-stu-id="f4394-107">Content in a table cell must be contained in a <xref:System.Windows.Documents.Block> element; in this case <xref:System.Windows.Documents.Paragraph> elements are used.</span></span>  <span data-ttu-id="f4394-108">V tabulce také hostitelem hypertextový odkaz (reprezentované <xref:System.Windows.Documents.Hyperlink> element) v řádku zápatí.</span><span class="sxs-lookup"><span data-stu-id="f4394-108">The table also hosts a hyperlink (represented by the <xref:System.Windows.Documents.Hyperlink> element) in the footer row.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4394-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="f4394-109">Example</span></span>  
 [!code-xaml[TableSnippetsXAML#_TableXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 <span data-ttu-id="f4394-110">Následující obrázek ukazuje, jak se vykreslí v tabulce definované v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="f4394-110">The following figure shows how the table defined in this example renders.</span></span>  
  
 <span data-ttu-id="f4394-111">![Vykreslený tabulky. ](./media/tableeg.png "TableEG")</span><span class="sxs-lookup"><span data-stu-id="f4394-111">![Rendered table.](./media/tableeg.png "TableEG")</span></span>
