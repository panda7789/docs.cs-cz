---
title: Možnosti a pokyny pro technologie
ms.date: 03/30/2017
ms.assetid: c8577281-38e6-4ce5-b036-572039a4c3d8
ms.openlocfilehash: 1996a5f5b86715db099e52e163fd23be2497f5eb
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094459"
---
# <a name="adonet-technology-options-and-guidelines"></a>Možnosti a pokyny pro ADO.NET

ADO.NET Data Platform je strategie pro více verzí, která umožňuje snížit množství kódu a údržby, které jsou potřebné pro vývojáře, a umožnit jim tak programování v modelech konceptuálních entit. Tato platforma zahrnuje ADO.NET Entity Framework a související technologie.  
  
## <a name="entity-framework"></a>Entity Framework  
 Entity Framework ADO.NET je navržená tak, aby vývojářům umožnila vytvářet aplikace pro přístup k datům pomocí programování na koncepčním modelu aplikace namísto programování přímo proti schématu relačního úložiště. Cílem je snížit množství kódu a potřebnou údržbu pro aplikace orientované na data. Další informace najdete v tématu [ADO.NET Entity Framework](./ef/index.md).  
  
### <a name="entity-data-model-edm"></a>Entity Data Model (EDM)  
 Model EDM (Entity Data Model) (EDM) je specifikace návrhu, která definuje data aplikace jako sady entit a vztahů. Data v tomto modelu podporují pro objekty relační mapování a programovatelnost dat napříč hranicemi aplikací.  
  
### <a name="object-services"></a>Objektové služby  
 Objektové služby umožňují programátorům pracovat s koncepčním modelem prostřednictvím sady tříd modulu CLR (Common Language Runtime). Tyto třídy mohou být automaticky generovány z koncepčního modelu nebo mohou být vyvinuty nezávisle, aby odrážely strukturu koncepčního modelu. Objektové služby také poskytují podporu infrastruktury pro Entity Framework, včetně služeb, jako je Správa stavů, sledování změn, rozlišení identity, načítání a procházení vztahů, šíření změn objektů do úprav databáze. a dotaz na sestavení podpory pro Entity SQL. Další informace najdete v tématu [Přehled služby Object Services (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).  
  
### <a name="linq-to-entities"></a>LINQ to Entities  
 LINQ to Entities je implementace LINQ (Language-Integrated Query), která vývojářům umožňuje vytvářet dotazy silného typu proti kontextu objektu Entity Framework pomocí výrazů LINQ a operátorů LINQ Standard Query. LINQ to Entities umožňuje vývojářům pracovat s koncepčním modelem s flexibilním mapováním objektů napříč Microsoft SQL Server a databázemi třetích stran. Další informace najdete v tématu [LINQ to Entities](./ef/language-reference/linq-to-entities.md).  
  
### <a name="entity-sql"></a>Entity SQL  
 Entity SQL je textový dotazovací jazyk, který je navržený pro interakci s model EDM (Entity Data Model). Entity SQL je dialekt SQL, který obsahuje konstrukce pro dotazování z hlediska konceptů modelování vyšší úrovně, jako jsou dědičnost, komplexní typy a explicitní vztahy. Vývojáři mohou Entity SQL použít také přímo s objekty služby. Další informace najdete v tématu [Entity SQL Language](./ef/language-reference/entity-sql-language.md).  
  
### <a name="entityclient"></a>EntityClient  
 EntityClient je nový zprostředkovatel dat .NET Framework, který se používá pro interakci s model EDM (Entity Data Model). Zprostředkovatel EntityClient následuje model poskytovatele .NET Framework dat vystavení objektů <xref:System.Data.EntityClient.EntityConnection> a <xref:System.Data.EntityClient.EntityCommand>, které vracejí <xref:System.Data.EntityClient.EntityDataReader>. EntityClient spolupracuje s jazykem Entity SQL a poskytuje flexibilní mapování na zprostředkovatele dat specifických pro úložiště. Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).  
  
### <a name="entity-data-model-tools"></a>Nástroje modelu Entity Data  
 Entity Framework poskytuje nástroje příkazového řádku, průvodce a návrháře pro usnadnění sestavování aplikací modelu EDM. Ovládací prvek EntityDataSource podporuje scénáře datových vazeb založené na modelu EDM. Programovací plocha ovládacího prvku EntityDataSource je podobná ostatním ovládacím prvkům zdroje dat v aplikaci Visual Studio. Další informace najdete v tématu [ADO.NET model EDM (Entity Data Model) Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)).  
  
## <a name="linq-to-sql"></a>Technologie LINQ to SQL  
 LINQ to SQL je implementace relačního mapování objektů (nebo M), která umožňuje modelovat databázi SQL Server pomocí tříd .NET Framework. LINQ to SQL vám umožní dotazovat se na databázi pomocí LINQ a také aktualizovat, vkládat a odstraňovat data z ní. LINQ to SQL podporuje transakce, zobrazení a uložené procedury a poskytuje snadný způsob, jak do datového modelu integrovat ověřování dat a pravidla obchodní logiky. Pomocí Návrhář relací objektů (O/R Designer) můžete modelovat třídy entit a přidružení, které jsou založené na objektech v databázi. Další informace naleznete v tématu [LINQ to SQL Tools v aplikaci Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
## <a name="wcf-data-services"></a>WCF Data Services  
 WCF Data Services nasadí datové služby na webu nebo v intranetu. Data jsou strukturovaná jako entity a vztahy podle specifikací model EDM (Entity Data Model). Data nasazená v tomto modelu jsou adresovatelné pomocí standardního protokolu HTTP. Další informace najdete v tématu [WCF Data Services 4,5](../wcf/index.md).  
  
## <a name="see-also"></a>Viz také

- [Přehled ADO.NET](ado-net-overview.md)
- [Novinky v ADO.NET](whats-new.md)
