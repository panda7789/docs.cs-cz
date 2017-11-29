---
title: "SqlClient rozhraní Entity Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3cb7880621a849b7162ea5f86ee0786f6184ea58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sqlclient-for-the-entity-framework"></a>SqlClient rozhraní Entity Framework
Tato část popisuje zprostředkovatele dat .NET Framework pro SQL Server (SqlClient), která umožňuje rozhraní Entity Framework pracovat prostřednictvím systému Microsoft SQL Server.  
  
## <a name="provider-schema-attribute"></a>Atribut schématu zprostředkovatele  
 `Provider`je atributem `Schema` element v store schema definition language (SSDL).  
  
 Chcete-li použít SqlClient, přiřadit řetězec "System.Data.SqlClient" `Provider` atribut `Schema` elementu.  
  
## <a name="providermanifesttoken-schema-attribute"></a>Atribut ProviderManifestToken schématu  
 `ProviderManifestToken`je požadovaný atribut `Schema` element v SSDL. Tento token slouží k načtení manifestu zprostředkovatele pro scénáře v režimu offline. Další informace o `ProviderManifestToken` atributů najdete v tématu [Element schématu (SSDL)](http://msdn.microsoft.com/en-us/fec75ae4-7f16-4421-9265-9dac61509222).  
  
 SqlClient lze použít jako zprostředkovatele dat pro různé verze [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. Tyto verze mají různé možnosti. Například [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] nepodporuje `varchar(max)` a `nvarchar(max)` typy, které byly zavedeny v [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)].  
  
 SqlClient vytváří a přijímá následující tokeny manifestu zprostředkovatele pro různé verze systému SQL Server.  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|-|-|-|  
|2000|2005|2008|  
  
> [!NOTE]
>  Počínaje [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] 2010, [nástrojů modelu ADO.NET Entity Data Model](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527) nepodporují systém SQL Server 2000.  
  
## <a name="provider-namespace-name"></a>Název zprostředkovatele Namespace  
 Všichni poskytovatelé musí specifikovat obor názvů. Tato vlastnost určuje Entity Framework, která předpona je používána poskytovatele pro konkrétní konstrukce, jako jsou typy a funkce. Obor názvů pro manifesty SqlClient zprostředkovatele je `SqlServer`. Další informace o oborech názvů najdete v tématu [obory názvů](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).  
  
## <a name="types"></a>Typy  
 Poskytovatel Sqlclienta rozhraní Entity Framework poskytuje informace o mapování mezi konceptuálního modelu typy a typy systému SQL Server. Další informace najdete v tématu [SqlClient pro Entity FrameworkTypes](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).  
  
## <a name="functions"></a>Funkce  
 Poskytovatel Sqlclienta rozhraní Entity Framework definuje seznam funkcí, které jsou podporována zprostředkovatelem. Seznam podporovaných funkcí najdete v tématu [SqlClient pro funkce Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [SqlClient pro funkce Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [SqlClient pro Entity FrameworkTypes](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [Známé problémy v SqlClient rozhraní Entity Framework](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>Viz také  
 [Jazyk SQL entity](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [Referenční dokumentace jazyka](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)  
 [Známé problémy v SqlClient zprostředkovatele Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
