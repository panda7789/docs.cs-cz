---
title: Přehled
description: Přečtěte si přehled ADO.NET v tématu .NET Framework a přečtěte si o prostředcích, kde najdete podrobnější vysvětlení a příklady.
ms.date: 03/30/2017
ms.assetid: ee3bc1d8-11db-4be4-89eb-c708cf04117d
ms.openlocfilehash: 2ff3b7ad197bfe1e1c12e382f3a59bd470c57a75
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287152"
---
# <a name="adonet-overview"></a>Přehled ADO.NET
ADO.NET poskytuje konzistentní přístup ke zdrojům dat, jako jsou SQL Server a XML, a zdrojům dat, které jsou zpřístupněny prostřednictvím OLE DB a rozhraní ODBC. Aplikace příjemce pro sdílení dat můžou pomocí ADO.NET se připojit k těmto zdrojům dat a načítat, zpracovávat a aktualizovat data, která obsahují.  
  
 ADO.NET odděluje přístup k datům z manipulace s daty do diskrétních součástí, které lze použít samostatně nebo společně. ADO.NET zahrnuje .NET Framework poskytovatelé dat pro připojení k databázi, spouštění příkazů a načítání výsledků. Tyto výsledky se buď zpracovávají přímo, umístěné v objektu ADO.NET, aby <xref:System.Data.DataSet> je bylo možné uživatelům zpřístupnit ad hoc způsobem, v kombinaci s daty z více zdrojů nebo mezi vrstvami. `DataSet`Objekt lze také použít nezávisle .NET Framework poskytovatel dat ke správě dat v místní aplikaci nebo zdroji z XML.  
  
 Třídy ADO.NET se nacházejí v System. data. dll a jsou integrovány s třídami XML nalezenými v souboru System. XML. dll. Pro vzorový kód, který se připojuje k databázi, načte z něj data a pak tato data zobrazí v okně konzoly, viz [Příklady kódu ADO.NET](ado-net-code-examples.md).  
  
 ADO.NET poskytuje funkce vývojářům, kteří napíší spravovaný kód podobně jako funkce poskytované vývojářům modelu COM (Component Object Model) pomocí rozhraní ADO (ActiveX Data Objects) (ADO). Pro přístup k datům v aplikacích .NET doporučujeme používat ADO.NET, ne ADO.  
  
 ADO.NET poskytuje nejpřímější způsob přístupu k datům v rámci .NET Framework. Pro abstrakci vyšší úrovně, která umožňuje aplikacím pracovat s koncepčním modelem namísto základního modelu úložiště, se podívejte na [ADO.NET Entity Framework](./ef/index.md).  
  
 **Prohlášení o zásadách ochrany osobních údajů**: System. data. dll, System. data. Design. dll, System. data. OracleClient. dll, System. data. SqlXml. dll, System. data. Linq. dll, System. data. SqlServerCe. dll a System. data. DataSetExtensions. dll nerozlišuje mezi soukromými daty uživatele a nesoukromými daty.  Tato sestavení neshromažďují, neukládají ani nepřenosují soukromá data uživatele. Aplikace třetích stran však mohou pomocí těchto sestavení shromažďovat, ukládat nebo přenášet privátní data uživatele.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Architektura ADO.NET](ado-net-architecture.md)  
 Poskytuje přehled o architektuře a komponentách ADO.NET.  
  
 [Možnosti a pokyny pro ADO.NET](ado-net-technology-options-and-guidelines.md)  
 Popisuje produkty a technologie, které jsou součástí platformy dat entity.  
  
 [LINQ a ADO.NET](linq-and-ado-net.md)  
 Popisuje, jakým způsobem je jazykově integrovaný dotaz (LINQ) implementován v ADO.NET a obsahuje odkazy na související témata.  
  
 [Zprostředkovatelé dat .NET Framework](data-providers.md)  
 Poskytuje přehled návrhu .NET Frameworkho poskytovatele dat a .NET Framework zprostředkovatelů dat, které jsou součástí ADO.NET.  
  
 [Datové sady ADO.NET](ado-net-datasets.md)  
 Poskytuje přehled `DataSet` návrhu a součástí.  
  
 [Souběžné spouštění v ADO.NET](side-by-side-execution.md)  
 Popisuje rozdíly ve verzích ADO.NET a jejich vlivu na souběžné spouštění a kompatibilitu aplikací.  
  
 [Příklady kódu ADO.NET](ado-net-code-examples.md)  
 Poskytuje ukázky kódu, které načítají data pomocí zprostředkovatelů dat ADO.NET.  
  
## <a name="related-sections"></a>Související oddíly  
 [Novinky v ADO.NET](whats-new.md)  
 Přináší nové funkce, které jsou v ADO.NET novinkou.  
  
 [Zabezpečení aplikací ADO.NET](securing-ado-net-applications.md)  
 Popisuje postupy zabezpečeného kódování při použití ADO.NET.  
  
 [Mapování datového typu v ADO.NET](data-type-mappings-in-ado-net.md)  
 Popisuje mapování datových typů mezi .NET Frameworkmi datovými typy a .NET Framework zprostředkovateli dat.  
  
 [Načítání a úpravy dat v ADO.NET](retrieving-and-modifying-data.md)  
 Popisuje, jak se připojit ke zdroji dat, jak načítat data a upravovat data. To zahrnuje `DataReaders` a `DataAdapters` .  
  
## <a name="see-also"></a>Viz také

- [ADO.NET](index.md)
- [Přístup k datům v sadě Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)
