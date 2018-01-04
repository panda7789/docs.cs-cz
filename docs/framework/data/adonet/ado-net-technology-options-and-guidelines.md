---
title: "Možnosti technologie ADO.NET a pokyny"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8577281-38e6-4ce5-b036-572039a4c3d8
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 11ca23427460ed4c469fc45e43f3b32e4ec5eb25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="adonet-technology-options-and-guidelines"></a>Možnosti technologie ADO.NET a pokyny
Platforma dat ADO.NET je více verzí strategie pro snížit množství kódování a údržby, které jsou potřeba pro vývojáře je povolením programu na modely dat koncepční entity. Tato platforma obsahuje ADO.NET Entity Framework a souvisejících technologiích.  
  
## <a name="entity-framework"></a>Entity Framework  
 Je určen ADO.NET Entity Framework a umožňuje vývojářům vytvářet aplikace přístup dat programování s koncepční aplikační model místo programování přímo proti schématu relační úložiště. Cílem je snížit množství kód a údržby, které jsou potřeba pro aplikace orientované na data. Další informace najdete v tématu [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
### <a name="entity-data-model-edm"></a>Entity Data Model (EDM)  
 Model dat Entity (EDM) je specifikace návrhu, která definuje data aplikací jako nastaví entity a vztahy. Data v tomto modelu podporuje relační objekt mapování a programovatelnosti dat napříč hranicemi aplikace.  
  
### <a name="object-services"></a>Objekt služby  
 Objekt služby umožňuje programátorům interakci s konceptuálního modelu pomocí sady třídy společných language runtime (CLR). Tyto třídy můžete automaticky generovaný z konceptuálního modelu nebo mohou být vytvořeny nezávisle tak, aby odrážela strukturu konceptuálního modelu. Objekt služby také poskytuje podporu infrastruktury pro rozhraní Entity Framework, včetně služeb, jako je například Správa stavu, sledování, řešení identity změn načítání a navigace relací, šíření změny objektu databáze úprav a podpora pro Entity SQL sestavení dotazu. Další informace najdete v tématu [přehled služeb objektů (rozhraní Entity Framework)](http://msdn.microsoft.com/en-us/43014cf9-c9cb-4538-bfbb-197820b60038).  
  
### <a name="linq-to-entities"></a>LINQ to Entities  
 Technologie LINQ to Entities je implementace language-integrated query (LINQ), která umožňuje vývojářům vytvářet dotazy na silného typu pro kontext Entity Framework objektu pomocí LINQ – výrazy a LINQ standardní operátory dotazu. Technologie LINQ to Entities umožňuje vývojářům pracovat s konceptuálního modelu s velmi flexibilní relační objekt mapování mezi Microsoft SQL Server a databáze třetích stran. Další informace najdete v tématu [technologie LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md).  
  
### <a name="entity-sql"></a>Entity SQL  
 Entita SQL je založený na textu dotazovací jazyk, který je navržen pro interakci s datového modelu Entity. Entita SQL je dialekt SQL, který obsahuje konstrukce pro dotazování z hlediska vyšší úrovně modelování koncepty, jako jsou dědičnosti, komplexní typy a explicitní vztahy. Vývojáři mohou použít Entity SQL také přímo s služby objektu. Další informace najdete v tématu [jazyk SQL Entity](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md).  
  
### <a name="entityclient"></a>Zprostředkovatel EntityClient  
 Zprostředkovatel EntityClient je nový zprostředkovatel dat .NET Framework používá pro interakci s datového modelu Entity. Zprostředkovatel EntityClient odpovídá vzorci zprostředkovatele dat .NET Framework vystavení <xref:System.Data.EntityClient.EntityConnection> a <xref:System.Data.EntityClient.EntityCommand> objekty, který vrací <xref:System.Data.EntityClient.EntityDataReader>. Zprostředkovatel EntityClient funguje s jazykem Entity SQL, poskytuje flexibilní mapování na konkrétní úložiště dat zprostředkovatele. Další informace najdete v tématu [EntityClient a Entity SQL](http://msdn.microsoft.com/en-us/49202ab9-ac98-4b4b-a05c-140e422bf527).  
  
### <a name="entity-data-model-tools"></a>Nástroje modelu Entity Data  
 Rozhraní Entity Framework poskytuje nástroje pro příkazový řádek, průvodců a návrháři usnadňuje vytváření EDM aplikace. Ovládací prvek EntityDataSource podporuje scénáře datových vazeb založené na modelu EDM. Programovací prostor ovládacího prvku EntityDataSource je podobné jako další ovládací prvky zdroje dat v sadě Visual Studio. Další informace najdete v tématu [nástrojů modelu ADO.NET Entity Data Model](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527).  
  
## <a name="linq-to-sql"></a>Technologie LINQ to SQL  
 Technologie LINQ to SQL je relační mapování u objektu (nebo / M) implementace, která umožňuje modelu databázi systému SQL Server pomocí třídy rozhraní .NET Framework. Technologie LINQ to SQL umožňuje dotazování databáze pomocí LINQ, a také aktualizovat, insert a odstranění dat z něj. Technologie LINQ to SQL podporuje transakce, zobrazení a uložených procedur, poskytuje snadný způsob, jak integrovat ověřování dat a obchodní logiku pravidla do datového modelu. Návrhář relací objektů (Návrhář relací objektů) můžete model tříd entit a přidružení, které jsou založeny na objekty v databázi. Další informace najdete v tématu [technologie LINQ to SQL nástroje v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
## <a name="wcf-data-services"></a>WCF Data Services  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]nasadí data services na webu nebo v síti intranet. Strukturovaná data jako entity a vztahy podle specifikací modelu Entity Data Model. Data pro tento model nasazení je adresovat pomocí standardní protokol HTTP. Další informace najdete v tématu [WCF Data Services 4.5](../../../../docs/framework/data/wcf/index.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [Novinky v ADO.NET](../../../../docs/framework/data/adonet/whats-new.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
