---
title: Volání funkcí v dotazech LINQ to Entities
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 6fa1a7204a91a62c30e8683c449cc2be44132b4f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312082"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a>Volání funkcí v dotazech LINQ to Entities
Témata v této části popisují, jak k volání funkce v jazyce LINQ dotazy na entity.  
  
 <xref:System.Data.Objects.EntityFunctions> a <xref:System.Data.Objects.SqlClient.SqlFunctions> třídy poskytují přístup k canonical a funkce databáze jako součást rozhraní Entity Framework. Další informace najdete v tématu [jak: Volání kanonických funkcí](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) a [jak: Volání databázových funkcí](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).  
  
 Proces pro volání vlastní funkce vyžaduje tři základní kroky:  
  
1. Definovat funkci v konceptuálním modelu nebo deklaraci funkce v modelu úložiště.  
  
2. Přidejte metodu do vaší aplikace a jejich mapování na funkci v modelu s <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.  
  
3. Volání funkce v technologii LINQ to Entities dotazu.  
  
 Další informace najdete v tématech v této části.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Volání kanonických funkcí](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [Postupy: Volání databázových funkcí](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [Postupy: Volání vlastních databázových funkcí](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [Postupy: Volání modelově definovaných funkcí v dotazech](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [Postupy: Volání modelově definovaných funkcí jako objektových metod](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>Viz také:

- [Dotazy v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
- [Kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
- [Přehled souboru EDMX](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Postupy: Definování vlastních funkcí v konceptuálním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))
