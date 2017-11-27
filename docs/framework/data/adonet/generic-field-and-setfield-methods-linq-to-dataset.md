---
title: "Obecné pole a SetField metody (LINQ na DataSet)"
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
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 58c2126c97d68fbe33d53b9d9ffa81fcc1aec8a0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>Obecné pole a SetField metody (LINQ na DataSet)
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]poskytuje rozšiřující metody pro <xref:System.Data.DataRow> třídy pro přístup k hodnot sloupce: <xref:System.Data.DataRowExtensions.Field%2A> metoda a <xref:System.Data.DataRowExtensions.SetField%2A> metoda. Tyto metody poskytují jednodušší přístup k hodnotám sloupce pro vývojáře, zejména pokud jde o hodnoty null. <xref:System.Data.DataSet> Používá <xref:System.DBNull.Value> k reprezentaci hodnoty null, zatímco [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] používá podpora s možnou hodnotou Null typu počínaje [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]. Použití existující přistupující objekt sloupce v <xref:System.Data.DataRow> vyžaduje, abyste návratový objekt na příslušný typ přetypování. Pokud konkrétní pole v <xref:System.Data.DataRow> může mít hodnotu null, musí explicitně zkontrolovala pro hodnotu null protože vrácení <xref:System.DBNull.Value> a ho implicitně přetypování na jiný typ vyvolává <xref:System.InvalidCastException>. V následujícím příkladu Pokud <xref:System.Data.DataRow.IsNull%2A> metoda nebyla použita k vyhledání hodnotu null, by být vyvolána výjimka, pokud indexer vrátil <xref:System.DBNull.Value> a pokusil vysílat <xref:System.String>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 <xref:System.Data.DataRowExtensions.Field%2A> Metoda poskytuje přístup k hodnotám sloupce <xref:System.Data.DataRow> a <xref:System.Data.DataRowExtensions.SetField%2A> nastaví hodnoty ve sloupcích v <xref:System.Data.DataRow>. Obě <xref:System.Data.DataRowExtensions.Field%2A> metoda a <xref:System.Data.DataRowExtensions.SetField%2A> metoda zpracovat typy s možnou hodnotou Null, takže není nutné explicitně zkontrolovala hodnot null jako v předchozím příkladu. Obě metody jsou obecné metody navíc, takže nemusíte návratový typ přetypování.  
  
 Následující příklad používá <xref:System.Data.DataRowExtensions.Field%2A> metoda.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 Všimněte si, že datový typ zadaný v parametru Obecné `T` z <xref:System.Data.DataRowExtensions.Field%2A> metoda a <xref:System.Data.DataRowExtensions.SetField%2A> metoda musí shodovat s typem základní hodnoty. Jinak <xref:System.InvalidCastException> dojde k výjimce. Zadaný název sloupce taky musí shodovat s názvem sloupce v <xref:System.Data.DataSet>, nebo <xref:System.ArgumentException> bude vyvolána. V obou případech je vyvolána výjimka v průběhu výčtu dat při spuštění dotazu.  
  
 <xref:System.Data.DataRowExtensions.SetField%2A> Metoda sama neprovede všechny převody typů. To neznamená, ale, že nedojde, převod typů. <xref:System.Data.DataRowExtensions.SetField%2A> Metoda zpřístupňuje [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] chování <xref:System.Data.DataRow> třídy. Převod typů může provést <xref:System.Data.DataRow> objekt a převedená hodnota by pak uložena do <xref:System.Data.DataRow> objektu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataRowExtensions>
