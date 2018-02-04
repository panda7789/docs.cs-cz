---
title: "Odložení versus okamžitou načítání"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d1d7247f-a3b7-460b-b342-5c1a2365aa1a
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 8a4fa1574b8e25a5d98f9547ad916a3c84f10b01
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="deferred-versus-immediate-loading"></a>Odložení versus okamžitou načítání
Při dotazu pro objekt, načíst ve skutečnosti jenom na objekt, který jste požádali. *Související* objekty nejsou automaticky načtených ve stejnou dobu. (Další informace najdete v tématu [dotazování napříč vztahy](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).) Nejde zobrazit, že skutečnost, že souvisejících objektů, které ještě nejsou načíst, protože pokus o přístup k těmto vytváří požadavek, který je načte.  
  
 Můžete například chtít dotazovat na konkrétní sadu objednávek a jen občas odeslat e-mailové oznámení pro konkrétní zákazníky. Můžete nemusí nutně nejdřív načíst všechna data zákazníků s každou pořadí. Odložené načítání můžete použít k odložení načtení doplňující informace, dokud je nezbytně nutné. Podívejte se na následující příklad:  
  
 [!code-csharp[DLinqQueryConcepts#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#1)]
 [!code-vb[DLinqQueryConcepts#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#1)]  
  
 Naopak může být také hodnotu true. Máte aplikaci, která se má zobrazit zákazníka a pořadí dat ve stejnou dobu. Víte, že je nutné, aby obě sady dat. Víte, že aplikace musí pro každého zákazníka a informace o objednávce také získat výsledky. Byste neměli chtít odeslat jednotlivé dotazy na objednávky pro každý zákazníka. Co chcete je načíst data pořadí společně s zákazníků.  
  
 [!code-csharp[DLinqQueryConcepts#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#2)]
 [!code-vb[DLinqQueryConcepts#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#2)]  
  
 Tím, které tvoří smíšený produkt a načítání relativní bity data jako jeden velký projekce můžete také spojení zákazníci a objednávky v dotazu. Ale tyto výsledky nejsou entity. (Další informace najdete v tématu [technologii LINQ to SQL objektový Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)). Entity jsou objekty, které mají identity a že můžete upravit, zatímco tyto výsledky by měli být projekce, které nelze změnit a trvalé. I horší můžete by být načítání velké množství redundantních dat jako každého zákazníka a opakuje pro každý pořadí, ve výstupu plochou spojení.  
  
 Je třeba je způsob, jak načíst sadu souvisejících objektů, které ve stejnou dobu. Sada je vymezen oddíl graf tak, aby vám by nikdy být načítání vyšší nebo nižší než to bylo nezbytné pro zamýšlený účel. Pro tento účel [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje <xref:System.Data.Linq.DataLoadOptions> pro okamžité načítání oblasti objektový model. Metody patří:  
  
-   <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> Metoda okamžitě načíst data související s hlavní cíl.  
  
-   <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> Metodu, filtrovat objekty načtené pro konkrétní relace.  
  
## <a name="see-also"></a>Viz také  
 [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
