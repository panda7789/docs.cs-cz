---
title: "Reflexe zprostředkovatele (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, providers
ms.assetid: ef5ba300-6d7c-455e-a7bd-d0cc6d211ad4
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 865fbf4195b9005e4fbc9ebf6b1e3140b11df85d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="reflection-provider-wcf-data-services"></a>Reflexe zprostředkovatele (služby WCF Data Services)
Kromě úniku dat z datového modelu prostřednictvím rozhraní Entity Framework [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] můžou zpřístupnit data, která není definován výhradně ve model na základě entity. Zprostředkovatel reflexe poskytuje data v třídy, které návratové typy, které implementují <xref:System.Linq.IQueryable%601> rozhraní. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]odvození datový model pro tyto třídy pomocí reflexe a může překládat adresy vytvářet dotazy na prostředky do jazyka integrovaného dotazu (LINQ) – na základě dotazů vůči zveřejněné <xref:System.Linq.IQueryable%601> typy.  
  
> [!NOTE]
>  Můžete použít <xref:System.Linq.Queryable.AsQueryable%2A> metodu pro návrat <xref:System.Linq.IQueryable%601> z libovolné třídy, který implementuje rozhraní <xref:System.Collections.Generic.IEnumerable%601> rozhraní. To umožňuje nejvíce obecné typy kolekcí má být použit jako zdroj dat pro služby data.  
  
 Reflexe poskytovatel podporuje hierarchie typů. Další informace najdete v tématu [postupy: vytvoření služby Data pomocí poskytovatele reflexe](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).  
  
## <a name="inferring-the-data-model"></a>Odvození datový Model  
 Když vytváříte službu data, zprostředkovatele odvodí datový model pomocí reflexe. Následující seznam uvádí, jak zprostředkovatele reflexe odvodí datový model:  
  
-   Kontejneru entit – třída, která zveřejňuje data jako vlastnosti, které vracejí <xref:System.Linq.IQueryable%601> instance. Při adresování model dat na základě reflexe kontejneru entit představuje kořenový adresář služby. Kontejner – třída pouze jednu entitu je podporována pro daný obor názvů.  
  
-   Nastaví entity – vlastnosti, které vracejí <xref:System.Linq.IQueryable%601> instance jsou považovány za sady entit. Sad entit řešeny přímo jako prostředky v dotazu. Může vrátit pouze jednu vlastnost v kontejneru entit <xref:System.Linq.IQueryable%601> instanci daného typu.  
  
-   Typy entit – typ `T` z <xref:System.Linq.IQueryable%601> , vrátí sady entit. Třídy, které jsou součástí hierarchie dědičnosti se přeložit poskytovatelem reflexe na ekvivalentní entity typu hierarchie.  
  
-   Klíče entit – třída každý data, která je typ entity, musí mít klíčovou vlastnost. Tato vlastnost je opatřená <xref:System.Data.Services.Common.DataServiceKeyAttribute> atribut (`[DataServiceKeyAttribute]`).  
  
    > [!NOTE]
    >  Byste měli použít pouze <xref:System.Data.Services.Common.DataServiceKeyAttribute> atribut na vlastnost, která slouží k jednoznačné identifikaci instance typu entity. Tento atribut je ignorována, pokud se použije k navigační vlastnosti.  
  
-   Vlastnosti typu entity - jiné než klíči entity zprostředkovatele reflexe zpracovává přístupný, bez indexer vlastnosti třídy, která je typ entity následujícím způsobem:  
  
    -   Pokud vlastnost vrací primitivní typ, se předpokládá vlastnost jako vlastnost typu entity.  
  
    -   Pokud vlastnost vrátí typ, který je také typ entity, se předpokládá vlastnost jako vlastnost navigace, která představuje "1" Konec relace n: 1 nebo 1: 1.  
  
    -   Pokud vlastnost vrací <xref:System.Collections.Generic.IEnumerable%601> typu entity, pak vlastnost předpokládá se, že navigační vlastnost, která představuje "n" konec vztah jeden mnoho nebo n: n.  
  
    -   Pokud je návratový typ vlastnosti typ hodnoty, představuje vlastnost komplexního typu.  
  
> [!NOTE]
>  Na rozdíl od datový model, který je založen na modelu entity relační modely, které jsou založené na zprostředkovateli reflexe není srozumitelný relační data. Rozhraní Entity Framework by měl použít ke zveřejnění relačních dat prostřednictvím [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  
  
## <a name="data-type-mapping"></a>Mapování datového typu  
 Když datový model je odvozen z tříd rozhraní .NET Framework, primitivní typy v datovém modelu mapovány na rozhraní .NET Framework datové typy následujícím způsobem:  
  
|Datový typ rozhraní .NET framework|Typ modelu dat|  
|------------------------------|---------------------|  
|<xref:System.Byte>`[]`|`Edm.Binary`|  
|<xref:System.Boolean>|`Edm.Boolean`|  
|<xref:System.Byte>|`Edm.Byte`|  
|<xref:System.DateTime>|`Edm.DateTime`|  
|<xref:System.Decimal>|`Edm.Decimal`|  
|<xref:System.Double>|`Edm.Double`|  
|<xref:System.Guid>|`Edm.Guid`|  
|<xref:System.Int16>|`Edm.Int16`|  
|<xref:System.Int32>|`Edm.Int32`|  
|<xref:System.Int64>|`Edm.Int64`|  
|<xref:System.SByte>|`Edm.SByte`|  
|<xref:System.Single>|`Edm.Single`|  
|<xref:System.String>|`Edm.String`|  
  
> [!NOTE]
>  Typy s možnou hodnotou Null hodnot rozhraní .NET framework, jsou namapované na stejnou modelu typy dat, jako odpovídající typy hodnot, které nelze přiřadit hodnotu null.  
  
## <a name="enabling-updates-in-the-data-model"></a>Povolení aktualizací v datovém modelu  
 Chcete-li povolit aktualizace dat, který je zveřejněný prostřednictvím tento druh datový model, zprostředkovatel reflexe definuje <xref:System.Data.Services.IUpdatable> rozhraní. Toto rozhraní dá pokyn službu data o tom, jak zachovat aktualizace zveřejněné typy. Chcete-li aktualizace na prostředky, které jsou definovány v datovém modelu, musí implementovat třídu kontejneru entity <xref:System.Data.Services.IUpdatable> rozhraní. Příklad implementace <xref:System.Data.Services.IUpdatable> rozhraní najdete v tématu [postupy: vytvoření službu dat pomocí LINQ to SQL zdroj dat](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).  
  
 <xref:System.Data.Services.IUpdatable> Rozhraní vyžaduje, aby tak, aby aktualizace mohou být přeneseny do zdroje dat pomocí zprostředkovatele reflexe implementovat následující členy:  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.Data.Services.IUpdatable.AddReferenceToCollection%2A>|Poskytuje funkce, které chcete přidat objekt do kolekce souvisejících objektů, které jsou přístupné z navigační vlastnosti.|  
|<xref:System.Data.Services.IUpdatable.ClearChanges%2A>|Poskytuje funkce, která zruší čekající změny v datech.|  
|<xref:System.Data.Services.IUpdatable.CreateResource%2A>|Poskytuje funkce pro vytvoření nového prostředku v zadaném kontejneru.|  
|<xref:System.Data.Services.IUpdatable.DeleteResource%2A>|Poskytuje funkce odstranění prostředku.|  
|<xref:System.Data.Services.IUpdatable.GetResource%2A>|Poskytuje funkce pro načtení prostředků, která je identifikovaná určitý dotazu a zadejte název.|  
|<xref:System.Data.Services.IUpdatable.GetValue%2A>|Poskytuje funkci, která vrátí hodnotu vlastnosti prostředku.|  
|<xref:System.Data.Services.IUpdatable.RemoveReferenceFromCollection%2A>|Poskytuje funkce pro odebrat objekt do kolekce souvisejících objektů, které jsou k němu přistupovat z navigační vlastnost.|  
|<xref:System.Data.Services.IUpdatable.ResetResource%2A>|Poskytuje funkce se aktualizovat zadaný prostředek.|  
|<xref:System.Data.Services.IUpdatable.ResolveResource%2A>|Poskytuje funkce vrátit prostředků, která je reprezentována instance určitý objekt.|  
|<xref:System.Data.Services.IUpdatable.SaveChanges%2A>|Poskytuje funkce pro všechny čekající změny uložte.|  
|<xref:System.Data.Services.IUpdatable.SetReference%2A>|Poskytuje funkce pro nastavení odkazem na objekt v relaci pomocí navigační vlastnost.|  
|<xref:System.Data.Services.IUpdatable.SetValue%2A>|Poskytuje funkce pro nastavení hodnoty vlastnosti prostředku.|  
  
## <a name="handling-concurrency"></a>Zpracování souběžnosti  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]podporuje model optimistickou metodu souběžného tím, že vám definovat token souběžnosti pro entitu. Tento token souběžnosti, která obsahuje jednu nebo více vlastností entity, se službou data používá k určení, zda data, která jsou požadována, aktualizovaných nebo odstraněných došlo ke změně. Pokud token hodnoty získané z eTag v žádosti se liší od aktuální hodnoty entity, je vyvolána výjimka službou data. <xref:System.Data.Services.ETagAttribute> Platí pro typ entity k definování token souběžnosti ve zprostředkovateli reflexe. Token souběžnosti nemůže obsahovat vlastnost klíče nebo navigační vlastnost. Další informace najdete v tématu [aktualizaci dat služby](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
## <a name="using-linq-to-sql-with-the-reflection-provider"></a>Technologie LINQ to SQL pomocí reflexe zprostředkovatele  
 Protože ve výchozím nastavení jsou nativně podporovány rozhraní Entity Framework, je zprostředkovatel doporučené dat pro použití relačních dat s [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Můžete ale poskytovateli reflexe třídy SQL se službou dat pomocí LINQ. <xref:System.Data.Linq.Table%601> Způsobit sad, které se vrátí pomocí metody na <xref:System.Data.Linq.DataContext> generované LINQ to SQL Návrhář relací objektů (Návrhář relací objektů) implementace <xref:System.Linq.IQueryable%601> rozhraní. To umožňuje reflexe zprostředkovatele, který má přístup k tyto metody a vrátit entity data ze systému SQL Server pomocí generované třídy LINQ to SQL. Ale protože neimplementuje technologie LINQ to SQL <xref:System.Data.Services.IUpdatable> rozhraní, je nutné přidat konkrétní třídu, která rozšiřuje existující <xref:System.Data.Linq.DataContext> třídu přidat <xref:System.Data.Services.IUpdatable> implementace. Další informace najdete v tématu [postupy: vytvoření službu dat pomocí LINQ to SQL zdroj dat](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).  
  
## <a name="see-also"></a>Viz také  
 [Zprostředkovatelé dat služby](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
