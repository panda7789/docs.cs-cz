---
title: "Postupy: volání funkce kanonickém tvaru"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 97ad63ea2aeb5ef1ef1acd1988254e995dbc63e0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-canonical-functions"></a>Postupy: volání funkce kanonickém tvaru
<xref:System.Data.Objects.EntityFunctions> Třída obsahuje metody, které zveřejňují kanonické funkce pomocí v technologii LINQ dotazů entity. Informace o kanonické funkce najdete v tématu [kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).  
  
> [!NOTE]
>  <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> a <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> metody v <xref:System.Data.Objects.EntityFunctions> třídy nemají ekvivalentní kanonické funkce.  
  
 Kanonické funkce, které provádět výpočet sadu hodnot a vrátí jednu hodnotu (také označované jako agregační kanonické funkce) může být volána přímo. Další kanonické funkce lze volat pouze jako součást dotazu LINQ to Entities. Chcete-li volat přímo agregační funkci, musíte zadat <xref:System.Data.Objects.ObjectQuery%601> funkce. Další informace najdete v druhém níže uvedeném příkladu.  
  
 Některé kanonické funkce můžete volat pomocí běžné metody language runtime (CLR) v technologii LINQ dotazů entity. Seznam metod modulu CLR, které mapují na kanonické funkce najdete v tématu [CLR metodu pro mapování kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832). V příkladu provede dotazu LINQ to Entities používající <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> metoda vrátí všechny produkty, pro kterou rozdíl mezi `SellEndDate` a `SellStartDate` je menší než 365 dnů:  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832). V příkladu volá agregace <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> metoda přímo Vrátí směrodatnou odchylku `SalesOrderHeader` mezisoučty. Všimněte si, že <xref:System.Data.Objects.ObjectQuery%601> předaný funkci, která umožňuje volá se, aniž by byly součástí dotazu LINQ to Entities.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Volání funkcí v dotazech LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [Dotazy v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
