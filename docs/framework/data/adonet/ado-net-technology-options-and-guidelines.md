---
title: Možnosti technologie ADO.NET a pokyny
ms.date: 03/30/2017
ms.assetid: c8577281-38e6-4ce5-b036-572039a4c3d8
ms.openlocfilehash: 7312b2eae0e307fa50c89d37918403ee33412ec3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507989"
---
# <a name="adonet-technology-options-and-guidelines"></a>Možnosti technologie ADO.NET a pokyny
Datová Platforma ADO.NET je strategie více vydání ke snížení množství kódu a údržba vyžaduje pro vývojáře tak, že programovat proti koncepční entity data model. Tato platforma zahrnuje ADO.NET Entity Framework a souvisejících technologiích.  
  
## <a name="entity-framework"></a>Entity Framework  
 ADO.NET Entity Framework je určen k vývojářům umožňují vytvářet aplikace přistupující k datům programování v modelu koncepční aplikace namísto programování přímo proti schématu relační úložiště. Cílem je snížit množství kódu a údržba vyžaduje pro aplikace orientované na data. Další informace najdete v tématu [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
### <a name="entity-data-model-edm"></a>Entity Data Model (EDM)  
 Entity Data Model (EDM) je specifikace návrhu, který definuje data aplikací podle sad entit a vztahů. Data v tomto modelu podporuje objektově relační mapování a data programovatelnosti přes hranice aplikace.  
  
### <a name="object-services"></a>Objekt služby  
 Objekt služby umožňuje programátorům k interakci s Koncepční model pomocí sady common language runtime (CLR) třídy. Tyto třídy je možné vygenerovat automaticky z konceptuálního modelu nebo mohou být vytvořeny nezávisle tak, aby odrážely struktura konceptuálního modelu. Objekt služby také poskytuje podporu infrastruktury pro Entity Framework, včetně služeb, jako je správa stavů, řešení change tracking, rozlišení identity, načítání a navigace v relacích, šíření změn objektu tak změny databáze a vytváření podporu pro Entity SQL dotazu. Další informace najdete v tématu [Přehled služby objektů (Entity Framework)](https://msdn.microsoft.com/library/43014cf9-c9cb-4538-bfbb-197820b60038).  
  
### <a name="linq-to-entities"></a>LINQ to Entities  
 Technologie LINQ to Entities je implementace jazyka integrované dotazu (LINQ), který umožňuje vývojářům vytvářet dotazy silného typu na objektu kontextu Entity Framework pomocí LINQ – výrazy a operátory standardního dotazu LINQ. Technologie LINQ to Entities umožňuje vývojářům pracovat s konceptuálního modelu s velmi flexibilní objektově relační mapování mezi Microsoft SQL serveru a databází výrobců. Další informace najdete v tématu [technologii LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md).  
  
### <a name="entity-sql"></a>Entity SQL  
 Entita SQL je navržen pro interakci se Entity Data Model založený na textu dotazovací jazyk. Entita SQL je SQL dialekt obsahující konstrukce pro dotazování z hlediska vyšší úrovně modelování koncepty, jako je dědičnost, komplexní typy a explicitní vztahy. Vývojáři mohou pomocí Entity SQL také přímo pomocí objektů služby. Další informace najdete v tématu [jazyk Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md).  
  
### <a name="entityclient"></a>Zprostředkovatel EntityClient  
 Zprostředkovatel EntityClient je nový zprostředkovatel dat .NET Framework používá pro komunikaci s datového modelu Entity. Zprostředkovatel EntityClient následuje vzor poskytovatel dat rozhraní .NET Framework vystavení <xref:System.Data.EntityClient.EntityConnection> a <xref:System.Data.EntityClient.EntityCommand> objektů, který vrací <xref:System.Data.EntityClient.EntityDataReader>. Zprostředkovatel EntityClient funguje s jazykem Entity SQL poskytuje flexibilní mapování na poskytovatele dat pro konkrétní úložiště. Další informace najdete v tématu [zprostředkovatel EntityClient a Entity SQL](https://msdn.microsoft.com/library/49202ab9-ac98-4b4b-a05c-140e422bf527).  
  
### <a name="entity-data-model-tools"></a>Nástroje modelu Entity Data  
 Entity Framework poskytuje nástroje příkazového řádku, průvodci a návrháři usnadnit vytváření EDM aplikací. Ovládací prvek EntityDataSource podporuje scénáře datových vazeb založené na modelu EDM. Programovací plochu ovládacího prvku EntityDataSource je podobně jako jiné ovládací prvky zdroje dat v sadě Visual Studio. Další informace najdete v tématu [ADO.NET Entity Data Model Tools](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527).  
  
## <a name="linq-to-sql"></a>Technologie LINQ to SQL  
 Technologie LINQ to SQL je relační mapování objektů (nebo / M) implementace, která umožňuje modelovat do databáze SQL serveru s použitím tříd rozhraní .NET Framework. Technologie LINQ to SQL umožňuje dotazy na databázi pomocí jazyka LINQ, jakož i aktualizovat, vložení a odstranění dat z něj. Technologie LINQ to SQL podporuje transakce, zobrazení a uložených procedur, poskytuje snadný způsob, jak integrovat ověřování dat a obchodní logiky pravidla do datového modelu. Návrhář relací objektů (O/R Designer) slouží k modelování tříd entit a přidružení, které jsou založené na objektech v databázi. Další informace najdete v tématu [LINQ to SQL nástroje v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
## <a name="wcf-data-services"></a>WCF Data Services  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] nasadí datové služby na webu nebo intranetu. Strukturovaná data jako entitami a relacemi podle specifikace modelu Entity Data Model. Data nasazené na tento model je adresovat pomocí standardního protokolu HTTP. Další informace najdete v tématu [4.5 služby WCF Data](../../../../docs/framework/data/wcf/index.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [Novinky v ADO.NET](../../../../docs/framework/data/adonet/whats-new.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
