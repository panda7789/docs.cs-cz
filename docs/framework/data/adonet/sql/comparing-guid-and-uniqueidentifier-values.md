---
title: Porovnáním různých GUID a hodnoty uniqueidentifier
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
ms.openlocfilehash: ce6ba9a73e65b5f418ff9cf5a1ef4ca4ff0c36ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357767"
---
# <a name="comparing-guid-and-uniqueidentifier-values"></a>Porovnáním různých GUID a hodnoty uniqueidentifier
Datový typ globálně jedinečný identifikátor (GUID) v systému SQL Server je reprezentována `uniqueidentifier` datového typu, který uloží binární hodnotu 16 bajtů. Identifikátor GUID je binární číslo a je nejčastěji se využívá jako identifikátor, který musí být jedinečné v síti, která má mnoho počítačů v mnoha lokalitách. Identifikátory GUID může být generována volání funkce NEWID Transact-SQL a je musí být jedinečný v celém světě. Další informace najdete v tématu "Uniqueidentifier pomocí dat" v SQL Server Books Online.  
  
## <a name="working-with-sqlguid-values"></a>Práce s hodnotami SqlGuid  
 Protože jsou identifikátory GUID hodnoty dlouhé a skrytého, nejsou důležité pro uživatele. Pokud náhodně generované identifikátory GUID, které se používají pro hodnoty klíče a vložit mnoho řádků, získáte náhodných vstupně-výstupních do vaší indexy, které může mít negativní vliv na výkon. Identifikátory GUID je také relativně velké srovnání na jiné datové typy. Obecně doporučujeme používat identifikátory GUID pouze pro velmi krátkého scénáře, pro které žádná další data typ je vhodný.  
  
### <a name="comparing-guid-values"></a>Porovnání hodnot identifikátoru GUID  
 Operátory porovnání lze použít s `uniqueidentifier` hodnoty. Však řazení není implementována porovnáním vzorů bit dvou hodnot. Pouze operace, které jsou povoleny před `uniqueidentifier` hodnota jsou porovnání (= <>, \<, >, \<=, > =) a kontrolu NULL (IS NULL a IS NOT NULL). Nepovolení aritmetických operátorů jsou povoleny.  
  
 Obě <xref:System.Guid> a <xref:System.Data.SqlTypes.SqlGuid> mít `CompareTo` metodu pro porovnání hodnot jiný identifikátor GUID. Ale `System.Guid.CompareTo` a `SqlTypes.SqlGuid.CompareTo` jsou implementované jinak. <xref:System.Data.SqlTypes.SqlGuid> implementuje `CompareTo` pomocí chování systému SQL Server, v posledních šest bajtů hodnoty jsou nejdůležitější. <xref:System.Guid> vyhodnotí všechny 16 bajtů. Následující příklad ukazuje, toto chování rozdíl. V první části kódu zobrazuje neseřazené <xref:System.Guid> hodnoty a druhá část kódu ukazuje setříděné <xref:System.Guid> hodnoty. Třetí části se dozvíte, setříděné <xref:System.Data.SqlTypes.SqlGuid> hodnoty. Výstup se zobrazí pod výpis kódu.  
  
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
 [Datové typy SQL Serveru a ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
