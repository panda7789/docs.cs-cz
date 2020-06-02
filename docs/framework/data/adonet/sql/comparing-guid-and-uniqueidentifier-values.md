---
title: Porovnání hodnoty GUID a uniqueidentifier
description: Naučte se, jak vytvořit a porovnat hodnoty GUID v .NET Framework Zprostředkovatel dat pro SQL Server, které jsou reprezentované datovým typem uniqueidentifier.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
ms.openlocfilehash: 245b7246712822043d302c43a765c29ac2090e00
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286504"
---
# <a name="comparing-guid-and-uniqueidentifier-values"></a>Porovnání hodnoty GUID a uniqueidentifier
Datový typ globálně jedinečný identifikátor (GUID) v SQL Server je reprezentován `uniqueidentifier` datovým typem, který ukládá 16 bajtů binární hodnoty. Identifikátor GUID je binární číslo a jeho hlavní použití je identifikátor, který musí být jedinečný v síti, která má mnoho počítačů v mnoha lokalitách. Identifikátory GUID lze generovat voláním funkce Transact-SQL NEWID a zaručená, aby byla v celém světě jedinečná. Další informace naleznete v tématu [uniqueidentifier (Transact-SQL)](/sql/t-sql/data-types/uniqueidentifier-transact-sql).  
  
## <a name="working-with-sqlguid-values"></a>Práce s hodnotami SqlGuid  
 Vzhledem k tomu, že hodnoty GUID jsou dlouhé a zakryté, nejsou pro uživatele smysluplné. Pokud jsou pro klíčové hodnoty použity náhodně generované identifikátory GUID a vložíte mnoho řádků, dostanete do svých indexů náhodné vstupně-výstupní operace, což může mít negativní vliv na výkon. V porovnání s jinými datovými typy jsou GUID také poměrně velká. Obecně doporučujeme používat identifikátory GUID jenom pro velmi úzké scénáře, pro které není vhodný žádný jiný datový typ.  
  
### <a name="comparing-guid-values"></a>Porovnání hodnot GUID  
 Operátory porovnání lze použít s `uniqueidentifier` hodnotami. Řazení však není implementováno porovnáním bitových vzorů dvou hodnot. Pouze operace, které jsou povoleny proti `uniqueidentifier` hodnotě, jsou srovnávány (=,  <> \<, > , \<=, > =) a kontrola hodnoty NULL (je NULL a není null). Nejsou povoleny žádné jiné aritmetické operátory.  
  
 Oba <xref:System.Guid> a <xref:System.Data.SqlTypes.SqlGuid> mají `CompareTo` metodu pro porovnání různých hodnot GUID. `System.Guid.CompareTo`A jsou však `SqlTypes.SqlGuid.CompareTo` implementovány jinak. <xref:System.Data.SqlTypes.SqlGuid>implementuje `CompareTo` pomocí chování SQL Server za posledních šest bajtů hodnoty největší význam. <xref:System.Guid>vyhodnotí všechny 16 bajtů. Následující příklad demonstruje tento rozdíl chování. První část kódu zobrazuje neseřazené <xref:System.Guid> hodnoty a druhá část kódu zobrazuje seřazené <xref:System.Guid> hodnoty. Třetí část zobrazuje seřazené <xref:System.Data.SqlTypes.SqlGuid> hodnoty. Výstup se zobrazí pod seznamem kódu.  
  
 [!code-csharp[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/VB/source.vb#1)]  
  
 Tento příklad vytvoří následující výsledky.  
  
```output  
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

- [Datové typy SQL Serveru a ADO.NET](sql-server-data-types.md)
- [Přehled ADO.NET](../ado-net-overview.md)
