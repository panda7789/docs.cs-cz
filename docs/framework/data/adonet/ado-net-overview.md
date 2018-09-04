---
title: Přehled ADO.NET
ms.date: 03/30/2017
ms.assetid: ee3bc1d8-11db-4be4-89eb-c708cf04117d
ms.openlocfilehash: 697911201171a540d6749d03c51f14efba945765
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43529920"
---
# <a name="adonet-overview"></a>Přehled ADO.NET
ADO.NET poskytuje konzistentní vzhledem k aplikacím přístup ke zdrojům dat jako SQL Server a XML a ke zdrojům dat prostřednictvím OLE DB a ODBC. Sdílení dat aplikace pro koncové uživatele slouží k připojení k těmto zdrojům dat a načtení, zpracování a aktualizace dat, které obsahují ADO.NET.  
  
 ADO.NET odděluje přístup k datům z manipulace s daty do samostatné součásti, které lze použít samostatně nebo v kombinaci. ADO.NET obsahuje zprostředkovatele dat .NET Framework pro připojení k databázi, provádění příkazů a načíst výsledky. Tyto výsledky se buď zpracovávají přímo, umístí do technologie ADO.NET <xref:System.Data.DataSet> objektu, aby bylo možné vystavit uživatele ad hoc způsobem, v kombinaci s daty z více zdrojů nebo předány mezi vrstvami. `DataSet` Objekt také lze použít bez ohledu na jejich zprostředkovatele dat .NET Framework ke správě dat místní aplikace nebo zdroj XML.  
  
 Třídy rozhraní ADO.NET se nacházejí v System.Data.dll a jsou integrovány s nalezené v System.Xml.dll třídy XML. Ukázkový kód, který se připojuje k databázi, načte data z něj a potom tato data zobrazí v okně konzoly, naleznete v tématu [příklady kódu ADO.NET](../../../../docs/framework/data/adonet/ado-net-code-examples.md).  
  
 ADO.NET poskytuje funkce pro vývojáře, kteří psaní spravovaného kódu podobně jako funkce poskytované vývojářům nativní součást object model (COM) podle objektů ADO (ActiveX Data). Doporučujeme používat technologie ADO.NET, není objekt ADO, pro přístup k datům v aplikacích .NET.  
  
 ADO.NET obsahuje velmi přímočarou metodou přístup k datům v rámci rozhraní .NET Framework. Abstrakce vyšší úrovně, která umožňuje aplikacím tak, aby odpovídaly Koncepční model místo základní model úložiště, najdete v článku [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
 **Zásady ochrany osobních údajů**: The System.Data.dll, System.Data.Design.dll, System.Data.OracleClient.dll, System.Data.SqlXml.dll, knihovně System.Data.Linq.dll, System.Data.SqlServerCe.dll a System.Data.DataSetExtensions.dll sestavení nepodporují rozlišovat mezi uživatele privátní a veřejné daty.  Tato sestavení shromažďovat, ukládat ani přenosu dat soukromých kteréhokoli uživatele. Aplikace třetích stran může však shromažďování, ukládání nebo přenosu dat soukromých uživatele tato sestavení používají.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Architektura ADO.NET](../../../../docs/framework/data/adonet/ado-net-architecture.md)  
 Poskytuje přehled o architektuře a komponenty rozhraní ADO.NET.  
  
 [Možnosti a pokyny pro ADO.NET](../../../../docs/framework/data/adonet/ado-net-technology-options-and-guidelines.md)  
 Popisuje produkty a technologie, které jsou součástí datové platformy Entity.  
  
 [LINQ a ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 Popisuje, jak je implementovaná Language-Integrated Query (LINQ) v ADO.NET a poskytuje odkazy na související témata.  
  
 [Zprostředkovatelé dat .NET Framework](../../../../docs/framework/data/adonet/data-providers.md)  
 Poskytuje přehled návrhu zprostředkovatele dat .NET Framework a zprostředkovatele dat .NET Framework, které jsou součástí technologie ADO.NET.  
  
 [Datové sady ADO.NET](../../../../docs/framework/data/adonet/ado-net-datasets.md)  
 Najdete zde přehled `DataSet` návrhu a komponenty.  
  
 [Souběžné spouštění v ADO.NET](../../../../docs/framework/data/adonet/side-by-side-execution.md)  
 Tento článek popisuje rozdíly v ADO.NET verze a jejich vliv na provádění vedle sebe a kompatibilitu aplikací.  
  
 [Příklady kódu ADO.NET](../../../../docs/framework/data/adonet/ado-net-code-examples.md)  
 Obsahuje ukázky kódu, které načítají data pomocí zprostředkovatele dat ADO.NET.  
  
## <a name="related-sections"></a>Související oddíly  
 [Novinky v ADO.NET](../../../../docs/framework/data/adonet/whats-new.md)  
 Nabízí funkce, které jsou v nové [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
 [Zabezpečení aplikací ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 Popisuje zabezpečené drželi osvědčených kódovacích postupů při použití technologie ADO.NET.  
  
 [Mapování datového typu v ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 Popisuje mapování datového typu mezi datovými typy rozhraní .NET Framework a zprostředkovatele dat .NET Framework.  
  
 [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 Popisuje, jak se připojit ke zdroji dat, načtení dat a upravovat data. Jedná se o `DataReaders` a `DataAdapters`.  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 [Přístup k datům v sadě Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
