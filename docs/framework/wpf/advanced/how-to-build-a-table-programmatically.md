---
title: "Postupy: Sestavení tabulky z programu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables [WPF], creating programmatically
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fca6a304ea12dd90a71f8718fed5f1595f4cd4b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-a-table-programmatically"></a>Postupy: Sestavení tabulky z programu
Následující příklady ukazují, jak vytvořit prostřednictvím kódu programu <xref:System.Windows.Documents.Table> a jeho naplnění obsah. Obsah v tabulce jsou rozdělených do pěti řádků (reprezentována <xref:System.Windows.Documents.TableRow> objekty obsažené v <xref:System.Windows.Documents.Table.RowGroups%2A> objekt) a šesti sloupců (reprezentována <xref:System.Windows.Documents.TableColumn> objektů). Řádky se používají pro účely různých prezentace, včetně názvu řádek má title celou tabulku popisující sloupce dat v tabulce Řádek záhlaví a zápatí řádek s souhrnné informace.  Všimněte si, že znalost problematicky "title", "záhlaví" a "zápatí" řádků nepatří do tabulky; Jedná se o jednoduše řádky s různými charakteristikami. Buněk tabulky obsahují skutečný obsah, který se může skládat z text, obrázky nebo téměř žádné jiné [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elementu.  
  
## <a name="example"></a>Příklad  
 První, <xref:System.Windows.Documents.FlowDocument> je vytvořena na hostitele <xref:System.Windows.Documents.Table>a nový <xref:System.Windows.Documents.Table> je vytvořen a přidán k obsahu <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a>Příklad  
 Další, půl <xref:System.Windows.Documents.TableColumn> objekty jsou vytvořeny a do tabulky přidat <xref:System.Windows.Documents.Table.Columns%2A> kolekce s některé formátování použít.  
  
> [!NOTE]
>  Všimněte si, že v tabulce <xref:System.Windows.Documents.Table.Columns%2A> kolekce používá standardní indexování od nuly.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a>Příklad  
 Řádek název v dalším kroku je vytvořen a přidán do tabulky s některé formátování použité.  Název řádek se stane obsahovat jednu buňku, která zahrnuje všechny šesti sloupce v tabulce.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a>Příklad  
 V dalším kroku se vytvoří a přidat do tabulky řádek záhlaví a buňky v řádku záhlaví jsou vytvořeny a naplněny s obsahem.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a>Příklad  
 V dalším kroku se vytvoří a přidat do tabulky řádek pro data, a v buňkách v tomto řádku jsou vytvořeny a naplněny s obsahem.  Vytváření tento řádek je podobná vytváření řádek záhlaví s použitým formátováním mírně lišit.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a>Příklad  
 Nakonec řádek zápatí vytvářet, přidat a formátovat.  Jako název řádek zápatí obsahuje jednu buňku, která zahrnuje všechny šesti sloupce v tabulce.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled tabulky](../../../../docs/framework/wpf/advanced/table-overview.md)
