---
title: 'Postupy: Volání databázových funkcí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
ms.openlocfilehash: 115c50f157023b71a916b45b4498f9c59ad744bf
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397632"
---
# <a name="how-to-call-database-functions"></a>Postupy: Volání databázových funkcí
<xref:System.Data.Objects.SqlClient.SqlFunctions> Třída obsahuje metody, které zpřístupňují funkce SQL Server pro použití v LINQ to Entitiesch dotazech. Když použijete <xref:System.Data.Objects.SqlClient.SqlFunctions> metody v LINQ to Entities dotazy, v databázi se spustí odpovídající funkce databáze.  
  
> [!NOTE]
> Funkce databáze, které provádějí výpočet ze sady hodnot a vracejí jednu hodnotu (známé také jako agregační databázové funkce), lze vyvolat přímo. Jiné kanonické funkce lze volat pouze jako součást dotazu LINQ to Entities. Chcete-li volat agregační funkci přímo, musíte předat <xref:System.Data.Objects.ObjectQuery%601> funkci. Další informace najdete v druhém příkladu níže.  
  
> [!NOTE]
> Metody ve <xref:System.Data.Objects.SqlClient.SqlFunctions> třídě jsou specifické pro funkce SQL Server. Podobné třídy, které zveřejňují databázové funkce, mohou být k dispozici prostřednictvím jiných poskytovatelů.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je použit [model AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). V příkladu se spustí dotaz LINQ to Entities, který používá <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> metodu k vrácení všech kontaktů, jejichž příjmení začíná řetězcem "si":  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je použit [model AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Příklad volá přímo agregační <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> metodu. Všimněte si, <xref:System.Data.Objects.ObjectQuery%601> že objekt je předán do funkce, která umožňuje jeho volání bez části dotazu LINQ to Entities.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a>Viz také:

- [Volání funkcí v dotazech LINQ to Entities](calling-functions-in-linq-to-entities-queries.md)
- [Dotazy v technologii LINQ to Entities](queries-in-linq-to-entities.md)
