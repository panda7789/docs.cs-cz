---
title: Hodnoty porovnání GUID a uniqueidentifier
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
ms.openlocfilehash: 7d982b73332a2629ccd32c409e0de6fe1ce6eb98
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47087249"
---
# <a name="comparing-guid-and-uniqueidentifier-values"></a>Hodnoty porovnání GUID a uniqueidentifier
Datový typ globálně jedinečný identifikátor (GUID) v systému SQL Server je reprezentována `uniqueidentifier` datového typu, který uloží binární hodnotu 16 bajtů. Identifikátor GUID je binární číslo a nejčastěji se využívá jako identifikátor, který musí být jedinečný v síti, která má mnoho počítačů ve více lokalitách. Identifikátory GUID mohou být generovány volání funkce NEWID příkazů jazyka Transact-SQL a zaručeně jedinečná v celém světě. Další informace najdete v tématu [uniqueidentifier (Transact-SQL)](/sql/t-sql/data-types/uniqueidentifier-transact-sql).  
  
## <a name="working-with-sqlguid-values"></a>Práce s hodnotami SqlGuid  
 Protože jsou identifikátory GUID hodnoty dlouhé a skrytého, nejsou smysl pro uživatele. Pokud náhodně generované identifikátory GUID slouží pro klíčové hodnoty a vložit velké množství řádků, získáte do indexů, které může mít negativní vliv na výkon náhodných vstupně-výstupních operací. Identifikátory GUID jsou také relativně velké ve srovnání s jinými datovými typy. Obecně doporučujeme používat identifikátory GUID pouze pro velmi krátkého scénáře, pro které žádná jiná data typ je vhodný.  
  
### <a name="comparing-guid-values"></a>Porovnání hodnoty GUID  
 Operátory porovnání lze použít s `uniqueidentifier` hodnoty. Ale řazení není implementováno pomocí porovnávání vzorů bit ze dvou hodnot. Jediné operace, které jsou povoleny před `uniqueidentifier` hodnota jsou porovnání (= <>, \<, >, \<=, > =) a kontrola NULL (IS NULL a IS NOT NULL). Nepovolení aritmetických operátorů jsou povoleny.  
  
 Obě <xref:System.Guid> a <xref:System.Data.SqlTypes.SqlGuid> mít `CompareTo` metody pro porovnávání hodnot jiný identifikátor GUID. Ale `System.Guid.CompareTo` a `SqlTypes.SqlGuid.CompareTo` jsou implementováno jinak. <xref:System.Data.SqlTypes.SqlGuid> implementuje `CompareTo` pomocí chování systému SQL Server v posledních šest bajtů hodnoty jsou nejdůležitější. <xref:System.Guid> vyhodnotí všechny 16 bajtů. Následující příklad ukazuje toto chování rozdíl. První část kódu zobrazí neseřazené <xref:System.Guid> hodnoty a druhá část kódu znázorňuje seřazené <xref:System.Guid> hodnoty. Třetí část ukazuje seřazené <xref:System.Data.SqlTypes.SqlGuid> hodnoty. Ve výstupu se zobrazí pod výpis kódu.  
  
 [!code-csharp[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/VB/source.vb#1)]  
  
 Tento příklad vytvoří následující výsledky.  
  
```  
Unsorted Guids:  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
  
Sorted Guids:  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
  
Sorted SqlGuids:  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
```  
  
## <a name="see-also"></a>Viz také  

[Datové typy SQL Serveru a ADO.NET](sql-server-data-types.md)  
[Přehled ADO.NET](../ado-net-overview.md)  
