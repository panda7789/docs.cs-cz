---
title: "Dotazování na kolekci DataRowView v v zobrazení DataView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 02b32157fe88bddfd9a777042f6da87aa48ca551
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a>Dotazování na kolekci DataRowView v v zobrazení DataView
<xref:System.Data.DataView> Zpřístupní vyčíslitelná kolekce <xref:System.Data.DataRowView> objekty. <xref:System.Data.DataRowView>představuje vlastní pohled <xref:System.Data.DataRow> a zobrazí se na konkrétní verzi této <xref:System.Data.DataRow> v ovládacím prvku. Jenom jedna verze nástroje <xref:System.Data.DataRow> lze zobrazit pomocí ovládacího prvku, například <xref:System.Windows.Forms.DataGridView>. Dostanete <xref:System.Data.DataRow> který je zveřejněný prostřednictvím <xref:System.Data.DataRowView> prostřednictvím <xref:System.Data.DataRowView.Row%2A> vlastnost <xref:System.Data.DataRowView>. Při zobrazení hodnoty pomocí <xref:System.Data.DataRowView>, <xref:System.Data.DataView.RowStateFilter%2A> vlastnost určuje, která verze řádku základní <xref:System.Data.DataRow> zpřístupněn. Informace o přístupu k jiné řádek verze, která používá <xref:System.Data.DataRow>, najdete v části [stavy řádků a verze řádku](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md). Protože kolekce <xref:System.Data.DataRowView> objekty, které jsou zveřejněné <xref:System.Data.DataView> je vyčíslitelná, můžete použít [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu nad ním.  
  
 Následující příklad dotazy `Product` tabulky produktů red stejné barvy a vytvoří tabulku z tohoto dotazu. A <xref:System.Data.DataView> se vytvoří z tabulky a <xref:System.Data.DataView.RowStateFilter%2A> je nastavena na filtrovat odstraněné a upravených řádků. <xref:System.Data.DataView> Se pak použije jako zdroj v dotazu LINQ a <xref:System.Data.DataRowView> objekty, které byly upravit a odstranit je vázána na <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 Následující příklad vytvoří tabulku produktů ze zobrazení, která je vázána <xref:System.Windows.Forms.DataGridView> ovládacího prvku. <xref:System.Data.DataView> Je dotazován na stejné barvy red produkty a seřazené výsledků je vázána na <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a>Viz také  
 [Datová vazba a LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
