---
title: SqlClient pro Entity Framework
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: ec67637c416f2560c1f5d0a9fd0e856703820a84
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69954971"
---
# <a name="sqlclient-for-the-entity-framework"></a>SqlClient pro Entity Framework
Tato část popisuje .NET Framework Zprostředkovatel dat pro SQL Server (SqlClient), která umožňuje Entity Framework pracovat na Microsoft SQL Server.  
  
## <a name="provider-schema-attribute"></a>Atribut schématu poskytovatele  
 `Provider`je atributem `Schema` elementu ve službě Store Schema Definition Language (SSDL).  
  
 Chcete-li použít SqlClient, přiřaďte řetězec "System. data. SqlClient" `Provider` do atributu `Schema` elementu.  
  
## <a name="providermanifesttoken-schema-attribute"></a>ProviderManifestToken – atribut schématu  
 `ProviderManifestToken`je vyžadovaný atribut `Schema` elementu v ssdl. Tento token slouží k načtení manifestu poskytovatele pro offline scénáře. Další informace o `ProviderManifestToken` atributu naleznete v tématu [Schema element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).  
  
 SqlClient lze použít jako zprostředkovatele dat pro různé verze SQL Server. Tyto verze mají různé možnosti. Například SQL Server 2000 `varchar(max)` nepodporuje a `nvarchar(max)` typy, které byly představeny s SQL Server 2005.  
  
 SqlClient vytváří a přijímá následující tokeny manifestu poskytovatele pro různé verze SQL Server.  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|-|-|-|  
|2000|2005|2008|  
  
> [!NOTE]
> Počínaje sadou Visual Studio 2010 [nástroje ADO.NET model EDM (Entity Data Model)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) nepodporují SQL Server 2000.  
  
## <a name="provider-namespace-name"></a>Název oboru názvů poskytovatele  
 Všichni poskytovatelé musí specifikovat obor názvů. Tato vlastnost oznamuje Entity Framework, která předpona je používána poskytovatelem pro konkrétní konstrukce, jako jsou typy a funkce. Obor názvů manifestů poskytovatele SqlClient je `SqlServer`. Další informace o oborech názvů najdete v tématu [obory názvů](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).  
  
## <a name="types"></a>Typy  
 Zprostředkovatel SqlClient pro Entity Framework poskytuje informace o mapování mezi typy konceptuálních modelů a typy SQL Server. Další informace najdete v tématu [SqlClient pro Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).  
  
## <a name="functions"></a>Funkce  
 Zprostředkovatel SqlClient pro Entity Framework definuje seznam funkcí podporovaných zprostředkovatelem. Seznam podporovaných funkcí najdete v tématu [SqlClient for Entity Framework Functions](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [SqlClient pro funkce Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [SqlClient pro typy Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [Známé problémy v SqlClient pro Entity Framework](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>Viz také:

- [Jazyk Entity SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [Referenční dokumentace jazyka](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
- [Známé problémy ve zprostředkovateli SqlClient pro Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
