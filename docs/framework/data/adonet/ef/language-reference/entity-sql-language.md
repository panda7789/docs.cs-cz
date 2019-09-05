---
title: Jazyk Entity SQL
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: a2e4b7245dbfccf7864481b52a0e868a85efbca6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251017"
---
# <a name="entity-sql-language"></a>Jazyk Entity SQL
Entity SQL je dotazovací jazyk nezávislý na úložišti, který se podobá jazyku SQL. Entity SQL umožňuje dotazovat se na data entity, a to buď jako objekty, nebo v tabulkovém formátu. Měli byste zvážit použití Entity SQL v následujících případech:  
  
- Když je nutné dotaz dynamicky sestavit za běhu. V takovém případě byste měli zvážit také použití metod <xref:System.Data.Objects.ObjectQuery%601> Tvůrce dotazů namísto konstrukce řetězce dotazu Entity SQL za běhu.  
  
- Pokud chcete zadat dotaz jako součást definice modelu. V datovém modelu se podporuje jenom Entity SQL. Další informace naleznete v tématu [QueryView element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)  
  
- Při použití EntityClient k vrácení dat entity jen pro čtení jako sad řádků pomocí <xref:System.Data.EntityClient.EntityDataReader>. Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](../entityclient-provider-for-the-entity-framework.md).  
  
- Pokud jste již odborník v jazycích dotazů založených na jazyce SQL, Entity SQL se může zdát, že je to pro vás nejpřirozenější.  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a>Použití Entity SQL u poskytovatele EntityClient  
 Pokud chcete použít Entity SQL u poskytovatele EntityClient, přečtěte si následující témata, kde najdete další informace:  
  
 [Zprostředkovatel EntityClient pro Entity Framework](../entityclient-provider-for-the-entity-framework.md)  
  
 [Postupy: Vytvoření připojovacího řetězce EntityConnection](../how-to-build-an-entityconnection-connection-string.md)  
  
 [Postupy: Spustí dotaz, který vrátí výsledky PrimitiveType.](../how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Postupy: Provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Postupy: Provedení dotazu, který vrátí výsledky RefType](../how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Postupy: Spustí dotaz, který vrátí komplexní typy.](../how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Postupy: Spustit dotaz, který vrátí vnořené kolekce](../how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Postupy: Provedení parametrizovaného Entity SQLového dotazu pomocí EntityCommand](../how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Postupy: Provedení parametrizované uložené procedury pomocí EntityCommand](../how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Postupy: Spustit polymorfní dotaz](../how-to-execute-a-polymorphic-query.md)  
  
 [Postupy: Navigace v relacích pomocí operátoru navigace](../how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a>Použití Entity SQL s dotazy na objekty  
 Pokud chcete použít Entity SQL s dotazy na objekty, přečtěte si následující témata, kde najdete další informace:  
  
 [Postupy: Spustit dotaz, který vrací objekty typu entity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))  
  
 [Postupy: Provedení parametrizovaného dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))  
  
 [Postupy: Navigace v relacích pomocí vlastností navigace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))  
  
 [Postupy: Volání uživatelsky definované funkce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))  
  
 [Postupy: Filtrovat data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))  
  
 [Postupy: Seřadit data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))  
  
 [Postupy: Seskupit data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))  
  
 [Postupy: Agregovaná data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))  
  
 [Postupy: Spustit dotaz, který vrací objekty anonymního typu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))  
  
 [Postupy: Spustí dotaz, který vrátí kolekci primitivních typů.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))  
  
 [Postupy: Dotazování souvisejících objektů v objektu EntityCollection](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))  
  
 [Postupy: Seřazení sjednocení dvou dotazů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))  
  
 [Postupy: Stránka prostřednictvím výsledků dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled Entity SQL](entity-sql-overview.md)  
  
 [Reference k Entity SQL](entity-sql-reference.md)  
  
## <a name="see-also"></a>Viz také:

- [ADO.NET Entity Framework](../index.md)
- [Referenční dokumentace jazyka](index.md)
