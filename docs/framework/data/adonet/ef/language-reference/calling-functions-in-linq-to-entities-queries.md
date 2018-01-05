---
title: "Volání funkcí v technologii LINQ to Entities dotazy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b4989fcce44f6081dba52cd17d0349c87197d508
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="calling-functions-in-linq-to-entities-queries"></a>Volání funkcí v technologii LINQ to Entities dotazy
Témata v této části popisují, jak volat funkce v technologii LINQ dotazy entity.  
  
 <xref:System.Data.Objects.EntityFunctions> a <xref:System.Data.Objects.SqlClient.SqlFunctions> třídy poskytují přístup k kanonické a funkce databáze v rámci rozhraní Entity Framework. Další informace najdete v tématu [postupy: volání kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) a [postupy: volání funkce databáze](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).  
  
 Proces pro volání vlastní funkce vyžaduje tři základní kroky:  
  
1.  Definice funkce v konceptuálním modelu nebo deklarovat funkce v modelu úložiště.  
  
2.  Přidání metody do vaší aplikace a namapovat je funkce v modelu s <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.  
  
3.  Volání funkce v dotazu LINQ to Entities.  
  
 Další informace najdete v tématech v této části.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Volání kanonických funkcí](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [Postupy: Volání databázových funkcí](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [Postupy: Volání vlastních databázových funkcí](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [Postupy: Volání modelově definovaných funkcí v dotazech](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [Postupy: Volání modelově definovaných funkcí jako objektových metod](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>Viz také  
 [Dotazy v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [Kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)  
 [Přehled souboru EDMX](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Postupy: definování vlastní funkce v konceptuálním modelu](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f)
