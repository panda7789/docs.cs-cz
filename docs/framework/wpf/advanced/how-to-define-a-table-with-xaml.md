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
ms.workload: dotnet
ms.openlocfilehash: b932c7df822edabc5626f20af2bfc1eb3a7f93ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-table-with-xaml"></a>Postupy: Definice tabulky pomocí XAML
Následující příklad ukazuje, jak definovat <xref:System.Windows.Documents.Table> pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  Příklad tabulka obsahuje čtyři sloupce (reprezentována <xref:System.Windows.Documents.TableColumn> prvky) a několik řádků (reprezentována <xref:System.Windows.Documents.TableRow> elementy) obsahující data také jako title, záhlaví a zápatí informace.  Musí být součástí řádky <xref:System.Windows.Documents.TableRowGroup> elementu.  Každý řádek v tabulce se skládá z jedné nebo více buněk (reprezentována <xref:System.Windows.Documents.TableCell> elementy).  Obsah v buňce tabulky musí být obsažená v <xref:System.Windows.Documents.Block> element; v takovém případě <xref:System.Windows.Documents.Paragraph> prvky se používají.  V tabulce kromě toho hostuje také hypertextový odkaz (reprezentována <xref:System.Windows.Documents.Hyperlink> element) v řádku zápatí.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[TableSnippetsXAML#_TableXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 Následující obrázek ukazuje, jak vykreslí tabulky definované v tomto příkladu.  
  
 ![Vykreslené tabulka. ] (../../../../docs/framework/wpf/advanced/media/tableeg.png "TableEG")
