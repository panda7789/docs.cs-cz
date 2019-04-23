---
title: 'Postupy: Volání kanonických funkcí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
ms.openlocfilehash: 6e555b3d896862db491b34e11564e70bbe2d15eb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213152"
---
# <a name="how-to-call-canonical-functions"></a>Postupy: Volání kanonických funkcí
<xref:System.Data.Objects.EntityFunctions> Třída obsahuje metody, která zpřístupňují kanonické funkce pro použití v LINQ na dotazy na entity. Informace o kanonické funkce najdete v tématu [kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).  
  
> [!NOTE]
>  <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> a <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> metody v <xref:System.Data.Objects.EntityFunctions> třídy nemají kanonické funkce ekvivalenty.  
  
 Kanonické funkce, které provádí výpočet na sadu hodnot a vrací jedinou hodnotu (označované také jako agregační kanonické funkce) lze vyvolat přímo. Jiné kanonické funkce lze volat pouze jako součást dotazu LINQ to Entities. Agregační funkci volat přímo, je nutné předat <xref:System.Data.Objects.ObjectQuery%601> funkci. Další informace najdete ve druhém příkladu níže.  
  
 Některé kanonické funkce můžete volat pomocí common language runtime (CLR) metody v jazyce LINQ dotazy na entity. Seznam metod modulu CLR, které mapují na kanonické funkce najdete v tématu [metoda CLR pro mapování kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples). V příkladu provede LINQ to Entities dotaz, který používá <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> metoda vrátit všechny produkty, pro kterou rozdíl mezi `SellEndDate` a `SellStartDate` je menší než 365 dnů:  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples). Příklad volá agregace <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> metoda přímo Vrátí směrodatnou odchylku `SalesOrderHeader` mezisoučty. Všimněte si, že <xref:System.Data.Objects.ObjectQuery%601> je předán do funkce, což umožňuje volat bez se zapojil dotazu LINQ to Entities.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Volání funkcí v dotazech LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [Dotazy v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
