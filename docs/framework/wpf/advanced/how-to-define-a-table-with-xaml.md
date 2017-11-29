---
title: "Postupy: Definice tabulky pomocí XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [WPF], defining tables
- documents [WPF], defining tables with XAML
- tables [WPF], defining with XAML
ms.assetid: 83f2dc58-437e-4cdc-b5dd-0019810c7a85
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 350dff0b6ea9d92e919e45e4f46cf888f44f6212
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-define-a-table-with-xaml"></a><span data-ttu-id="4df99-102">Postupy: Definice tabulky pomocí XAML</span><span class="sxs-lookup"><span data-stu-id="4df99-102">How to: Define a Table with XAML</span></span>
<span data-ttu-id="4df99-103">Následující příklad ukazuje, jak definovat <xref:System.Windows.Documents.Table> pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4df99-103">The following example demonstrates how to define a <xref:System.Windows.Documents.Table> using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  <span data-ttu-id="4df99-104">Příklad tabulka obsahuje čtyři sloupce (reprezentována <xref:System.Windows.Documents.TableColumn> prvky) a několik řádků (reprezentována <xref:System.Windows.Documents.TableRow> elementy) obsahující data také jako title, záhlaví a zápatí informace.</span><span class="sxs-lookup"><span data-stu-id="4df99-104">The example table has four columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and several rows (represented by <xref:System.Windows.Documents.TableRow> elements) containing data as well as title, header, and footer information.</span></span>  <span data-ttu-id="4df99-105">Musí být součástí řádky <xref:System.Windows.Documents.TableRowGroup> elementu.</span><span class="sxs-lookup"><span data-stu-id="4df99-105">Rows must be contained in a <xref:System.Windows.Documents.TableRowGroup> element.</span></span>  <span data-ttu-id="4df99-106">Každý řádek v tabulce se skládá z jedné nebo více buněk (reprezentována <xref:System.Windows.Documents.TableCell> elementy).</span><span class="sxs-lookup"><span data-stu-id="4df99-106">Each row in the table is comprised of one or more cells (represented by <xref:System.Windows.Documents.TableCell> elements).</span></span>  <span data-ttu-id="4df99-107">Obsah v buňce tabulky musí být obsažená v <xref:System.Windows.Documents.Block> element; v takovém případě <xref:System.Windows.Documents.Paragraph> prvky se používají.</span><span class="sxs-lookup"><span data-stu-id="4df99-107">Content in a table cell must be contained in a <xref:System.Windows.Documents.Block> element; in this case <xref:System.Windows.Documents.Paragraph> elements are used.</span></span>  <span data-ttu-id="4df99-108">V tabulce kromě toho hostuje také hypertextový odkaz (reprezentována <xref:System.Windows.Documents.Hyperlink> element) v řádku zápatí.</span><span class="sxs-lookup"><span data-stu-id="4df99-108">The table also hosts a hyperlink (represented by the <xref:System.Windows.Documents.Hyperlink> element) in the footer row.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4df99-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="4df99-109">Example</span></span>  
 [!code-xaml[TableSnippetsXAML#_TableXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 <span data-ttu-id="4df99-110">Následující obrázek ukazuje, jak vykreslí tabulky definované v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="4df99-110">The following figure shows how the table defined in this example renders.</span></span>  
  
 <span data-ttu-id="4df99-111">![Vykreslené tabulka. ] (../../../../docs/framework/wpf/advanced/media/tableeg.png "TableEG")</span><span class="sxs-lookup"><span data-stu-id="4df99-111">![Rendered table.](../../../../docs/framework/wpf/advanced/media/tableeg.png "TableEG")</span></span>
