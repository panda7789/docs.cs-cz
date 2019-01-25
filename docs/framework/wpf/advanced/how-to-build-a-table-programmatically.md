---
title: 'Postupy: Sestavení tabulky z programu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables [WPF], creating programmatically
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
ms.openlocfilehash: 7eced80759f4c250cba5b4fb98ab33957b33de14
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715501"
---
# <a name="how-to-build-a-table-programmatically"></a>Postupy: Sestavení tabulky z programu
Následující příklady ukazují, jak prostřednictvím kódu programu vytvořit <xref:System.Windows.Documents.Table> a jeho naplnění obsah. Obsah tabulky jsou rozdělených do pěti řádcích (reprezentované <xref:System.Windows.Documents.TableRow> objekty obsažené v <xref:System.Windows.Documents.Table.RowGroups%2A> objekt) a šest sloupců (reprezentované <xref:System.Windows.Documents.TableColumn> objekty). Řádky se používají pro účely jiné prezentace, včetně titulní řádek určený pro titulek celou tabulku popisující sloupce dat v tabulce Řádek záhlaví a řádek zápatí se souhrnnými informacemi.  Všimněte si, že pojem "title", "záhlaví" a "zápatí" řádek nepatří do tabulky; Jedná se o jednoduše řádky s různými charakteristikami. Buňky tabulky obsahují skutečný obsah, který se může skládat z textu, obrázků nebo téměř jakýkoli jiný [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elementu.  
  
## <a name="example"></a>Příklad  
 První, <xref:System.Windows.Documents.FlowDocument> se vytvoří na hostitele <xref:System.Windows.Documents.Table>a nové <xref:System.Windows.Documents.Table> je vytvořen a přidán do obsahu <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a>Příklad  
 Dále šest <xref:System.Windows.Documents.TableColumn> objekty jsou vytvořen a přidán do tabulky <xref:System.Windows.Documents.Table.Columns%2A> kolekce s některé aplikované formátování.  
  
> [!NOTE]
>  Všimněte si, že v tabulce <xref:System.Windows.Documents.Table.Columns%2A> kolekce používá standardní indexování od nuly.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a>Příklad  
 Titulní řádek v dalším kroku je vytvořen a přidán do tabulky s některé aplikované formátování.  Titulní řádek se stane, tak, aby obsahovala jedinou buňku, která překlenuje všechny šest sloupců v tabulce.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a>Příklad  
 V dalším kroku řádek záhlaví je vytvořen a přidán do tabulky a buňky v řádku záhlaví jsou vytvořeny a naplněny s obsahem.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a>Příklad  
 V dalším kroku řádků dat je vytvořen a přidán do tabulky a buňky v tomto řádku jsou vytvořeny a naplněny s obsahem.  Vytváření tento řádek je podobný sestavování řádek záhlaví s mírně odlišné formátování.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a>Příklad  
 Nakonec řádek zápatí vytvořili, přidat a ve formátu.  V zápatí je uvedené jako titulní řádek obsahuje jedinou buňku, která překlenuje všechny šest sloupců v tabulce.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Viz také:
- [Přehled tabulky](../../../../docs/framework/wpf/advanced/table-overview.md)
