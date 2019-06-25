---
title: Obecné pole a metody SetField (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
ms.openlocfilehash: 9a2913de6534612455c14858f6baffea8ef78976
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347479"
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>Obecné pole a metody SetField (LINQ to DataSet)
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] poskytuje rozšiřující metody, které <xref:System.Data.DataRow> třídy pro přístup k hodnoty ve sloupcích: <xref:System.Data.DataRowExtensions.Field%2A> – metoda a <xref:System.Data.DataRowExtensions.SetField%2A> metoda. Tyto metody poskytují jednodušší přístup k hodnotám sloupce pro vývojáře, zejména pokud jde o hodnoty null. <xref:System.Data.DataSet> Používá <xref:System.DBNull.Value?displayProperty=nameWithType> k reprezentaci hodnoty null, zatímco [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] používá <xref:System.Nullable> a <xref:System.Nullable%601> typy. Použití existující přistupující objekt sloupce v <xref:System.Data.DataRow> vyžaduje, abyste přetypovat vrácený objekt do příslušného typu. Pokud konkrétní pole v <xref:System.Data.DataRow> může mít hodnotu null, musí explicitně kontrola hodnot null protože vrací <xref:System.DBNull.Value?displayProperty=nameWithType> a implicitně přetypování na jiný typ vyvolá <xref:System.InvalidCastException>. V následujícím příkladu Pokud <xref:System.Data.DataRow.IsNull%2A?displayProperty=nameWithType> metoda nebyl použit ke kontrole hodnot null, bude vyvolána výjimka, pokud indexer vrátil <xref:System.DBNull.Value?displayProperty=nameWithType> a pokusili přetypovat na <xref:System.String>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 <xref:System.Data.DataRowExtensions.Field%2A> Metoda poskytuje přístup k hodnoty sloupce <xref:System.Data.DataRow> a <xref:System.Data.DataRowExtensions.SetField%2A> nastaví hodnoty ve sloupcích v <xref:System.Data.DataRow>. Oba <xref:System.Data.DataRowExtensions.Field%2A> metoda a <xref:System.Data.DataRowExtensions.SetField%2A> metoda zpracování typy připouštějící hodnotu Null, takže není potřeba explicitně kontrola hodnot null jako v předchozím příkladu. Obě metody jsou obecné metody, také, takže není nutné přetypovat návratový typ.  
  
 V následujícím příkladu <xref:System.Data.DataRowExtensions.Field%2A> metody.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 Všimněte si, že datový typ zadaný v parametru obecného `T` z <xref:System.Data.DataRowExtensions.Field%2A> metoda a <xref:System.Data.DataRowExtensions.SetField%2A> metoda musí odpovídat typu zdrojovou hodnotu. V opačném případě <xref:System.InvalidCastException> , bude vyvolána výjimka. Zadaný název sloupce musí taky shodovat s názvem sloupce v <xref:System.Data.DataSet>, nebo <xref:System.ArgumentException> bude vyvolána výjimka. V obou případech je vyvolána výjimka za běhu během výčtu dat při spuštění dotazu.  
  
 <xref:System.Data.DataRowExtensions.SetField%2A> Metoda sám neprovádí žádné převody typů. To neznamená, ale, že nedojde k převodu typu. <xref:System.Data.DataRowExtensions.SetField%2A> Metoda zpřístupní chování ADO.NET <xref:System.Data.DataRow> třídy. Může provádět převod typu <xref:System.Data.DataRow> objektu a převedená hodnota by pak se uložila <xref:System.Data.DataRow> objektu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataRowExtensions>
