---
title: Dotazování na kolekci DataRowView v zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
ms.openlocfilehash: 8b6b6c5b9d7157b1279f23770b1d223635252685
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651828"
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a>Dotazování na kolekci DataRowView v zobrazení dat
<xref:System.Data.DataView> Zpřístupňuje vyčíslitelné kolekce <xref:System.Data.DataRowView> objekty. <xref:System.Data.DataRowView> představuje vlastní zobrazení <xref:System.Data.DataRow> a zobrazí konkrétní verzi, která <xref:System.Data.DataRow> v ovládacím prvku. Pouze jednu verzi <xref:System.Data.DataRow> lze zobrazit pomocí ovládacího prvku, například <xref:System.Windows.Forms.DataGridView>. Můžete přistupovat <xref:System.Data.DataRow> , který je zveřejněný prostřednictvím <xref:System.Data.DataRowView> prostřednictvím <xref:System.Data.DataRowView.Row%2A> vlastnost <xref:System.Data.DataRowView>. Při zobrazení hodnoty pomocí <xref:System.Data.DataRowView>, <xref:System.Data.DataView.RowStateFilter%2A> vlastnost rozhodne, kterou verzi řádku základního <xref:System.Data.DataRow> je přístupný. Informace o přístupu k pomocí verze odlišný řádek <xref:System.Data.DataRow>, naleznete v tématu [stavy řádků a verze řádků](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md). Protože kolekce <xref:System.Data.DataRowView> objekty, které jsou vystavené <xref:System.Data.DataView> je vyčíslitelná, můžete použít [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] k dotazu nad ním.  
  
 Následující příklady dotazů `Product` tabulky produktů red barevné a vytvoří tabulku z dotazu. A <xref:System.Data.DataView> se vytvoří z tabulky a <xref:System.Data.DataView.RowStateFilter%2A> je nastavena na filtrování odstraněné a upravené řádky. <xref:System.Data.DataView> Se pak použije jako zdroj v dotazu LINQ a <xref:System.Data.DataRowView> objekty, které byly upravit a odstranit je vázána na <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 Následující příklad vytvoří tabulku produktů ze zobrazení, které je vázán na <xref:System.Windows.Forms.DataGridView> ovládacího prvku. <xref:System.Data.DataView> Dotaz na produkty red barevné a uspořádaný výsledky, které jsou vázány na <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a>Viz také:

- [Datová vazba a LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
