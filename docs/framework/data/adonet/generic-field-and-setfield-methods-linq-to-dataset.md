---
title: Obecné pole a metody SetField (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
ms.openlocfilehash: 310eb3ccecc3159234ed362ed044be7ad704dde4
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634830"
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>Obecné pole a metody SetField (LINQ to DataSet)
LINQ to DataSet poskytuje metody rozšíření pro třídu <xref:System.Data.DataRow> pro přístup k hodnotám sloupců: metoda <xref:System.Data.DataRowExtensions.Field%2A> a metoda <xref:System.Data.DataRowExtensions.SetField%2A>. Tyto metody poskytují snazší přístup k hodnotám sloupců pro vývojáře, zejména ohledně hodnot null. <xref:System.Data.DataSet> používá <xref:System.DBNull.Value?displayProperty=nameWithType>, které reprezentují hodnoty null, zatímco LINQ používá typy <xref:System.Nullable> a <xref:System.Nullable%601>. Použití již existujícího přístupového objektu sloupce v <xref:System.Data.DataRow> vyžaduje přetypování návratového objektu na příslušný typ. Pokud konkrétní pole v <xref:System.Data.DataRow> může mít hodnotu null, je nutné explicitně vyhledat hodnotu null, protože vrácení <xref:System.DBNull.Value?displayProperty=nameWithType> a implicitně přetypování na jiný typ vyvolá <xref:System.InvalidCastException>. V následujícím příkladu, pokud <xref:System.Data.DataRow.IsNull%2A?displayProperty=nameWithType> metoda nebyla použita pro kontrolu hodnoty null, výjimka by byla vyvolána, pokud indexer vrátil <xref:System.DBNull.Value?displayProperty=nameWithType> a pokusil se ho přetypovat na <xref:System.String>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 Metoda <xref:System.Data.DataRowExtensions.Field%2A> poskytuje přístup k hodnotám sloupců <xref:System.Data.DataRow> a <xref:System.Data.DataRowExtensions.SetField%2A> nastaví hodnoty sloupců v <xref:System.Data.DataRow>. Metoda <xref:System.Data.DataRowExtensions.Field%2A> a metoda <xref:System.Data.DataRowExtensions.SetField%2A> zpracovávají typy s možnou hodnotou null, takže nemusíte explicitně kontrolovat hodnoty null jako v předchozím příkladu. Obě metody jsou obecné metody, takže nemusíte přetypování návratový typ.  
  
 Následující příklad používá metodu <xref:System.Data.DataRowExtensions.Field%2A>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 Všimněte si, že datový typ zadaný v obecném parametru `T` metody <xref:System.Data.DataRowExtensions.Field%2A> a metoda <xref:System.Data.DataRowExtensions.SetField%2A> se musí shodovat s typem základní hodnoty. V opačném případě bude vyvolána výjimka <xref:System.InvalidCastException>. Zadaný název sloupce musí také odpovídat názvu sloupce v <xref:System.Data.DataSet>, nebo bude vyvolána <xref:System.ArgumentException>. V obou případech je výjimka vyvolána v době spuštění během výčtu dat při spuštění dotazu.  
  
 Samotná metoda <xref:System.Data.DataRowExtensions.SetField%2A> neprovádí žádné převody typu. To však neznamená, že převod typu nebude proveden. Metoda <xref:System.Data.DataRowExtensions.SetField%2A> zpřístupňuje ADO.NET chování třídy <xref:System.Data.DataRow>. Převod typu může být proveden objektem <xref:System.Data.DataRow> a převedená hodnota by pak byla uložena do objektu <xref:System.Data.DataRow>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataRowExtensions>
