---
title: Obecné metody pole a setfieldu (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
ms.openlocfilehash: d7ddee775e91c6be6166a091997afd58113cfe6b
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249100"
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>Obecné metody pole a setfieldu (LINQ to DataSet)
LINQ to DataSet poskytuje <xref:System.Data.DataRow> metody rozšíření třídy pro <xref:System.Data.DataRowExtensions.Field%2A> přístup <xref:System.Data.DataRowExtensions.SetField%2A> k hodnotám sloupců: metodě a metodě. Tyto metody poskytují snadnější přístup k hodnotám sloupců pro vývojáře, zejména pokud jde o hodnoty null. Používá <xref:System.Data.DataSet> <xref:System.DBNull.Value?displayProperty=nameWithType> se k reprezentaci hodnoty null, vzhledem k tomu, LINQ používá <xref:System.Nullable> a <xref:System.Nullable%601> typy. Použití již existujícího přistupujícího objektu sloupce v aplikaci <xref:System.Data.DataRow> vyžaduje přetypovat návratový objekt na příslušný typ. Pokud určité pole <xref:System.Data.DataRow> v může být null, je nutné explicitně <xref:System.DBNull.Value?displayProperty=nameWithType> zkontrolovat hodnotu null, protože <xref:System.InvalidCastException>vrácení a implicitně přetypování na jiný typ vyvolá . V následujícím příkladu, <xref:System.Data.DataRow.IsNull%2A?displayProperty=nameWithType> pokud metoda nebyla použita <xref:System.DBNull.Value?displayProperty=nameWithType> <xref:System.String>ke kontrole hodnoty null, by byla vyvolána výjimka, pokud indexer vrátil a pokusil se přetypovat do .  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 Metoda <xref:System.Data.DataRowExtensions.Field%2A> poskytuje přístup k hodnotám <xref:System.Data.DataRow> sloupců a <xref:System.Data.DataRowExtensions.SetField%2A> a <xref:System.Data.DataRow>nastaví hodnoty sloupců v . <xref:System.Data.DataRowExtensions.Field%2A> Metoda i <xref:System.Data.DataRowExtensions.SetField%2A> metoda zpracovávají typy hodnot s možnou hodnotou s možnou hodnotou, takže není třeba explicitně kontrolovat hodnoty null jako v předchozím příkladu. Obě metody jsou obecné metody, také, takže není třeba přetypovat návratový typ.  
  
 Následující příklad používá <xref:System.Data.DataRowExtensions.Field%2A> metodu.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 Všimněte si, že datový `T` typ <xref:System.Data.DataRowExtensions.Field%2A> zadaný <xref:System.Data.DataRowExtensions.SetField%2A> v obecném parametru metody a metodě musí odpovídat typu podkladové hodnoty. V opačném <xref:System.InvalidCastException> případě bude vyvolána výjimka. Zadaný název sloupce se musí také shodovat s názvem sloupce v aplikaci <xref:System.Data.DataSet>, nebo <xref:System.ArgumentException> bude vyvolán. V obou případech je výjimka vyvolána v době běhu během výčtu dat při spuštění dotazu.  
  
 Samotná <xref:System.Data.DataRowExtensions.SetField%2A> metoda neprovádí žádné převody typu. To však neznamená, že nedojde k převodu typu. Metoda <xref:System.Data.DataRowExtensions.SetField%2A> zveřejňuje ADO.NET chování třídy. <xref:System.Data.DataRow> Převod typu by mohl <xref:System.Data.DataRow> být proveden objektem a převedená <xref:System.Data.DataRow> hodnota by pak byla uložena do objektu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Data.DataRowExtensions>
