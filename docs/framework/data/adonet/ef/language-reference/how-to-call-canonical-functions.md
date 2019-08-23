---
title: 'Postupy: Volání kanonických funkcí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
ms.openlocfilehash: 01a638d494b988e29ccf07763a7e0aecf54cc11c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936069"
---
# <a name="how-to-call-canonical-functions"></a>Postupy: Volání kanonických funkcí
<xref:System.Data.Objects.EntityFunctions> Třída obsahuje metody, které zpřístupňují kanonické funkce pro použití v LINQ to Entitiesch dotazech. Informace o kanonických funkcích naleznete v tématu [kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).  
  
> [!NOTE]
> Metody <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> a <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> ve<xref:System.Data.Objects.EntityFunctions> třídě nemají ekvivalenty kanonické funkce.  
  
 Kanonické funkce, které provádějí výpočty pro sadu hodnot a vracejí jednu hodnotu (známé také jako agregované kanonické funkce), mohou být přímo vyvolány. Jiné kanonické funkce lze volat pouze jako součást dotazu LINQ to Entities. Chcete-li volat agregační funkci přímo, musíte předat <xref:System.Data.Objects.ObjectQuery%601> funkci. Další informace najdete v druhém příkladu níže.  
  
 Můžete volat některé kanonické funkce pomocí metod modulu CLR (Common Language Runtime) v LINQ to Entitiesch dotazech. Seznam metod CLR, které jsou mapovány na kanonické funkce, naleznete v tématu [Metoda CLR na kanonické mapování funkcí](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je použit [model AdventureWorks Sales](https://archive.codeplex.com/?p=msftdbprodsamples). V příkladu se spustí dotaz LINQ to Entities, který používá <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> metodu k vrácení všech produktů, pro které je rozdíl `SellEndDate` mezi `SellStartDate` a menší než 365 dní:  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je použit [model AdventureWorks Sales](https://archive.codeplex.com/?p=msftdbprodsamples). Příklad volá agregační <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> metodu přímo pro návrat směrodatné odchylky `SalesOrderHeader` mezisoučtů. Všimněte si, <xref:System.Data.Objects.ObjectQuery%601> že objekt je předán do funkce, která umožňuje jeho volání bez části dotazu LINQ to Entities.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Volání funkcí v dotazech LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [Dotazy v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
