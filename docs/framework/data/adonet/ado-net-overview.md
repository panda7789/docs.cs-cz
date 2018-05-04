---
title: ADO.NET – přehled
ms.date: 03/30/2017
ms.assetid: ee3bc1d8-11db-4be4-89eb-c708cf04117d
ms.openlocfilehash: 50881c05c8b6f2602d19817373a16e4661d3d133
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="adonet-overview"></a>ADO.NET – přehled
ADO.NET zajišťuje konzistentní přístup ke zdrojům dat, jako je například SQL Server a XML a zdroje dat, které jsou k dispozici prostřednictvím technologie OLE DB a rozhraní ODBC. Sdílení dat příjemce aplikace můžete použít technologie ADO.NET pro připojení k těmto zdrojům dat a načtení, zpracování a aktualizovat data, která obsahují.  
  
 ADO.NET odděluje přístup k datům z manipulaci s daty do samostatné součásti, které lze použít samostatně nebo v kombinaci. ADO.NET obsahuje zprostředkovatele dat .NET Framework pro připojení k databázi, provádění příkazů a načíst výsledky. Tyto výsledky se buď zpracovávají přímo, umístit do technologie ADO.NET <xref:System.Data.DataSet> objekt, chcete-li zpřístupnit pro uživatele ad hoc způsobem, společně s daty z více zdrojů nebo předán mezi vrstvami. `DataSet` Objekt také lze použít nezávisle na zprostředkovatel dat .NET Framework ke správě dat místní aplikace nebo jako zdroj XML.  
  
 ADO.NET třídy se nacházejí v System.Data.dll a jsou integrované s nalezené v System.Xml.dll třídy XML. Ukázkový kód, který se připojuje k databázi, načte data z něj a potom tato data zobrazí v okně konzoly, najdete v části [příklady kódu pro technologii ADO.NET](../../../../docs/framework/data/adonet/ado-net-code-examples.md).  
  
 ADO.NET poskytuje funkce pro vývojáře, kteří vytvářejí spravovaného kódu, které jsou podobné funkce poskytované nativní součást object model (COM) vývojářům pomocí objektů ADO (ActiveX Data). Doporučujeme, abyste používali ADO.NET, není ADO pro přístup k datům v aplikacích .NET.  
  
 ADO.NET poskytuje metodě nejvíce přímý přístup k datům v rozhraní .NET Framework. Abstrakce vyšší úrovně, který umožňuje aplikacím pracovat v konceptuálním modelu místo základní model úložiště, najdete v článku [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
 **Prohlášení o ochraně osobních údajů**: sestavení System.Data.dll, System.Data.Design.dll, System.Data.OracleClient.dll, System.Data.SqlXml.dll, knihovně System.Data.Linq.dll, System.Data.SqlServerCe.dll a System.Data.DataSetExtensions.dll nepodporují rozlišení mezi uživatele privátní a veřejné daty.  Tyto sestavení není shromažďování, ukládání nebo přenosu dat privátní všechny uživatele. Aplikace jiných výrobců mohou však shromažďování, ukládání nebo přenosu privátních dat uživatele pomocí těchto sestavení.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Architektura ADO.NET](../../../../docs/framework/data/adonet/ado-net-architecture.md)  
 Poskytuje přehled o architektuře a součástí ADO.NET.  
  
 [Možnosti a pokyny pro ADO.NET](../../../../docs/framework/data/adonet/ado-net-technology-options-and-guidelines.md)  
 Popisuje produkty a technologie, které jsou součástí platformy Data Entity.  
  
 [LINQ a ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 Popisuje, jak je implementované Language-Integrated Query (LINQ) v ADO.NET a poskytuje odkazy na související témata.  
  
 [Zprostředkovatelé dat .NET Framework](../../../../docs/framework/data/adonet/data-providers.md)  
 Obsahuje přehled návrhu zprostředkovatel dat .NET Framework a zprostředkovatele dat rozhraní .NET Framework, které jsou součástí ADO.NET.  
  
 [Datové sady ADO.NET](../../../../docs/framework/data/adonet/ado-net-datasets.md)  
 Obsahuje přehled `DataSet` návrhu a součásti.  
  
 [Souběžné spouštění v ADO.NET](../../../../docs/framework/data/adonet/side-by-side-execution.md)  
 Popisuje rozdíly v ADO.NET verze a jejich vliv na spuštění vedle sebe a kompatibility aplikací.  
  
 [Příklady kódu ADO.NET](../../../../docs/framework/data/adonet/ado-net-code-examples.md)  
 Poskytuje ukázek kódu, které načtení dat pomocí zprostředkovatele dat ADO.NET.  
  
## <a name="related-sections"></a>Související oddíly  
 [Novinky v ADO.NET](../../../../docs/framework/data/adonet/whats-new.md)  
 Nabízí funkce, které jsou v nové [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
 [Zabezpečení aplikací ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 Popisuje postupy pro zabezpečené kódování při použití ADO.NET.  
  
 [Mapování datového typu v ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 Popisuje mapování datového typu mezi datovými typy rozhraní .NET Framework a zprostředkovatele dat .NET Framework.  
  
 [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 Popisuje, jak se připojit ke zdroji dat, načtení dat a upravovat data. To zahrnuje `DataReaders` a `DataAdapters`.  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 [Přístup k datům v sadě Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
