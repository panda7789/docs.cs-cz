---
title: Jazyk Entity SQL
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: ecbf9bc555594d205281237559037ac2a0e1cdb0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64631695"
---
# <a name="entity-sql-language"></a>Jazyk Entity SQL
Entita SQL je nezávislý na úložišti dotazovací jazyk podobný SQL. Entita SQL vám umožní provádět dotazy na entity data, jako objekty nebo ve formě tabulky. Měli byste zvážit použití Entity SQL v následujících případech:  
  
- Pokud dotaz musí dynamicky zkonstruovat za běhu. V takovém případě byste měli také zvážit použití metody Tvůrce dotazů <xref:System.Data.Objects.ObjectQuery%601> místo vytváření Entity SQL řetězec za běhu dotazu.  
  
- Pokud chcete definovat dotaz jako součást definice modelu. V datovém modelu se podporuje jenom Entity SQL. Další informace najdete v tématu [Element QueryView (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)  
  
- Při použití zprostředkovatel EntityClient pro vrácení dat jen pro čtení entity jako s použitím sady řádků <xref:System.Data.EntityClient.EntityDataReader>. Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
- Pokud jste už jste odborník v jazycích dotazů založených na SQL, se může zdát vám nejvíc fyzické Entity SQL.  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a>Použití se zprostředkovatelem EntityClient Entity SQL  
 Pokud chcete používat Entity SQL se zprostředkovatelem EntityClient, naleznete v následujících tématech pro další informace:  
  
 [Zprostředkovatel EntityClient pro Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [Postupy: Vytvoření připojovacího řetězce EntityConnection](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [Postupy: Spustit dotaz, který vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Postupy: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Postupy: Spustit dotaz, který vrátí výsledky typu RefType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Postupy: Provedení dotazu, který vrátí komplexní typy](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Postupy: Provedení dotazu, který vrátí vnořené kolekce](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Postupy: Provést parametrizovaného dotazu Entity SQL pomocí EntityCommand](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Postupy: Spuštění parametrizované uložené procedury pomocí EntityCommand](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Postupy: Spuštění Polymorfního dotazu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [Postupy: Procházení vztahů pomocí navigačního operátoru](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a>Pomocí dotazy objektu Entity SQL  
 Pokud chcete používat Entity SQL pomocí objektu dotazů, naleznete v následujících tématech pro další informace:  
  
 [Postupy: Provedení dotazu, který vrací objekty typu Entity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))  
  
 [Postupy: Spuštění parametrizovaného dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))  
  
 [Postupy: Procházení vztahů pomocí navigačních vlastností](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))  
  
 [Postupy: Volání uživatelem definované funkce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))  
  
 [Postupy: Filtrování dat](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))  
  
 [Postupy: Řazení dat](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))  
  
 [Postupy: Skupiny dat](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))  
  
 [Postupy: Aggregate Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))  
  
 [Postupy: Provedení dotazu, který vrací objekty anonymního typu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))  
  
 [Postupy: Provedení dotazu, který vrátí kolekce primitivních typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))  
  
 [Postupy: Dotaz v objekt EntityCollection související objekty](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))  
  
 [Postupy: Pořadí sjednocení dva dotazy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))  
  
 [Postupy: Stránkovat výsledky dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a>Viz také:

- [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)
- [Referenční dokumentace jazyka](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
