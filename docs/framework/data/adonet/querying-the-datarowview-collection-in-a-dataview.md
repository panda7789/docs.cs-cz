---
title: Dotazování na kolekci DataRowView v zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
ms.openlocfilehash: 17fab6e4c178eee6b5135045fb953267db810898
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794465"
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a>Dotazování na kolekci DataRowView v zobrazení dat
Zpřístupňuje vyčíslitelné <xref:System.Data.DataRowView> kolekce objektů. <xref:System.Data.DataView> <xref:System.Data.DataRowView>představuje přizpůsobené zobrazení <xref:System.Data.DataRow> a a zobrazuje konkrétní verzi <xref:System.Data.DataRow> ovládacího prvku. Prostřednictvím ovládacího prvku <xref:System.Windows.Forms.DataGridView>lze zobrazit <xref:System.Data.DataRow> pouze jednu verzi a. <xref:System.Data.DataRow> Přístup k <xref:System.Data.DataRowView> portálu,<xref:System.Data.DataRowView.Row%2A> který je zveřejněn prostřednictvím vlastnosti, můžete získat z. <xref:System.Data.DataRowView> Pokud zobrazíte hodnoty pomocí <xref:System.Data.DataRowView> <xref:System.Data.DataView.RowStateFilter%2A> , vlastnost určuje, která verze řádku podkladu <xref:System.Data.DataRow> je zveřejněna. Informace o přístupu k různým verzím řádků pomocí <xref:System.Data.DataRow>nástroje naleznete v tématu [stavy řádků a verze řádků](./dataset-datatable-dataview/row-states-and-row-versions.md). Vzhledem k tomu, <xref:System.Data.DataRowView> že kolekce objektů vystavených <xref:System.Data.DataView> kolekcí je vyčíslitelné, můžete použít LINQ to DataSet k dotazování nad ní.  
  
 Následující příklad vyhledá v `Product` tabulce červené barvy produktů a vytvoří tabulku z tohoto dotazu. Vytvoří <xref:System.Data.DataView> se z tabulky <xref:System.Data.DataView.RowStateFilter%2A> a vlastnost je nastavená tak, aby se vyfiltroval na smazaných a upravených řádcích. Je pak použit jako zdroj v dotazu LINQ <xref:System.Data.DataRowView> a objekty, které byly upraveny a <xref:System.Windows.Forms.DataGridView> smazány, jsou svázány s ovládacím prvkem. <xref:System.Data.DataView>  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 Následující příklad vytvoří tabulku produktů ze zobrazení, které je svázáno <xref:System.Windows.Forms.DataGridView> s ovládacím prvkem. Je dotazován na červené barvy produktů a seřazené výsledky jsou svázány <xref:System.Windows.Forms.DataGridView> s ovládacím prvkem. <xref:System.Data.DataView>  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a>Viz také:

- [Datová vazba a LINQ to DataSet](data-binding-and-linq-to-dataset.md)
