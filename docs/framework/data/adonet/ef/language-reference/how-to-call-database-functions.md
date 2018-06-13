---
title: 'Postupy: volání funkce databáze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
ms.openlocfilehash: b885cedbb324ee0a076990bceb28bf256814bb26
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760645"
---
# <a name="how-to-call-database-functions"></a>Postupy: volání funkce databáze
<xref:System.Data.Objects.SqlClient.SqlFunctions> Třída obsahuje metody, které zveřejňují funkce SQL Server pomocí v technologii LINQ dotazů entity. Při použití <xref:System.Data.Objects.SqlClient.SqlFunctions> metody v technologii LINQ dotazů entity, odpovídající funkce databáze jsou spouštěny v databázi.  
  
> [!NOTE]
>  Funkce databáze, které provádět výpočet sadu hodnot a vrátí jednu hodnotu (také označované jako databáze agregační funkce) můžete přímo vyvolat. Další kanonické funkce lze volat pouze jako součást dotazu LINQ to Entities. Chcete-li volat přímo agregační funkci, musíte zadat <xref:System.Data.Objects.ObjectQuery%601> funkce. Další informace najdete v druhém níže uvedeném příkladu.  
  
> [!NOTE]
>  Metody v <xref:System.Data.Objects.SqlClient.SqlFunctions> třídy jsou specifické pro funkce systému SQL Server. Podobně jako třídy, které zveřejňují funkce databáze může být k dispozici prostřednictvím dalších zprostředkovatelů.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832). V příkladu provede dotazu LINQ to Entities používající <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> metody, která vrátí všechny kontakty, jejichž příjmení začíná "Ma":  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832). V příkladu volá agregace <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> metoda přímo. Všimněte si, že <xref:System.Data.Objects.ObjectQuery%601> předaný funkci, která umožňuje volá se, aniž by byly součástí dotazu LINQ to Entities.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a>Viz také  
 [Volání funkcí v dotazech LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [Dotazy v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
