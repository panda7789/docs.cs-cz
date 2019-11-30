---
title: Konfigurace datové služby (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 59efd4c8-cc7a-4800-a0a4-d3f8abe6c55c
ms.openlocfilehash: 80878c18143eaa603e624c8be63f11af91cfcfb6
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569306"
---
# <a name="configuring-the-data-service-wcf-data-services"></a>Konfigurace datové služby (WCF Data Services)
Pomocí WCF Data Services můžete vytvářet datové služby, které zpřístupňují kanály protokolu OData (Open Data Protocol). Data v těchto kanálech můžou pocházet z nejrůznějších zdrojů dat. WCF Data Services používá poskytovatele dat k vystavování těchto dat jako datový kanál OData. Tito poskytovatelé zahrnují poskytovatele Entity Framework, poskytovatele reflexe a sadu vlastních rozhraní poskytovatele datových služeb. Implementace zprostředkovatele definuje datový model pro službu. Další informace najdete v tématu [poskytovatelé Data Services](data-services-providers-wcf-data-services.md).  
  
 V WCF Data Services datová služba je třída, která dědí z třídy <xref:System.Data.Services.DataService%601>, kde typ datové služby je kontejner entity datového modelu. Tento kontejner entity obsahuje jednu nebo více vlastností, které vracejí <xref:System.Linq.IQueryable%601>, které slouží k přístupu k sadám entit v datovém modelu.  
  
 Chování datové služby jsou definována členy třídy <xref:System.Data.Services.DataServiceConfiguration> a členy třídy <xref:System.Data.Services.DataServiceBehavior>, která je k dispozici z vlastnosti <xref:System.Data.Services.DataServiceConfiguration.DataServiceBehavior%2A> třídy <xref:System.Data.Services.DataServiceConfiguration>. Třída <xref:System.Data.Services.DataServiceConfiguration> je dodávána metodě `InitializeService`, která je implementovaná datovou službou, jako v následující implementaci datové služby Northwind:  
  
[!code-csharp[Astoria Northwind Service#DataServiceConfigComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigcomplete)]  
[!code-vb[Astoria Northwind Service#DataServiceConfigComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigcomplete)]  
  
## <a name="data-service-configuration-settings"></a>Konfigurační nastavení datové služby  
 Třída <xref:System.Data.Services.DataServiceConfiguration> umožňuje zadat následující chování datové služby:  
  
|Člen|Předvídatelně|  
|------------|--------------|  
|<xref:System.Data.Services.DataServiceBehavior.AcceptCountRequests%2A>|Umožňuje zakázat požadavky na počet, které jsou odeslány do datové služby pomocí segmentu `$count` cesty a možnosti dotazu `$inlinecount`. Další informace najdete v tématu [konvence OData: identifikátor URI](https://go.microsoft.com/fwlink/?LinkId=185564).|  
|<xref:System.Data.Services.DataServiceBehavior.AcceptProjectionRequests%2A>|Umožňuje zakázat podporu pro projekci dat v žádostech odeslaných do datové služby pomocí možnosti dotazu `$select`. Další informace najdete v tématu [konvence OData: identifikátor URI](https://go.microsoft.com/fwlink/?LinkId=185564).|  
|<xref:System.Data.Services.DataServiceConfiguration.EnableTypeAccess%2A>|Umožňuje zpřístupnění datového typu v metadatech pro zprostředkovatele dynamického metadat definovaného pomocí rozhraní <xref:System.Data.Services.Providers.IDataServiceMetadataProvider>.|  
|<xref:System.Data.Services.DataServiceConfiguration.EnableTypeConversion%2A>|Umožňuje určit, zda má modul runtime datové služby převést typ obsažený v datové části na skutečný typ vlastnosti, který je uveden v požadavku.|  
|<xref:System.Data.Services.DataServiceBehavior.InvokeInterceptorsOnLinkDelete%2A>|Umožňuje určit, zda jsou zaregistrované zachycení změn vyvolány u souvisejících entit při odstranění propojení relace mezi dvěma entitami.|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxBatchCount%2A>|Umožňuje omezit počet sad změn a operací dotazů, které jsou povoleny v rámci jedné dávky. Další informace najdete v tématu [OData: dávkové](https://go.microsoft.com/fwlink/?LinkId=185602) a [dávkové operace](batching-operations-wcf-data-services.md).|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxChangesetCount%2A>|Umožňuje omezit počet změn, které lze zahrnout do jedné sady změn. Další informace najdete v tématu [Postup: povolení stránkování výsledků datové služby](how-to-enable-paging-of-data-service-results-wcf-data-services.md).|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxExpandCount%2A>|Umožňuje omezit velikost odpovědi tím, že omezuje počet souvisejících entit, které mohou být zahrnuty v jednom požadavku pomocí operátoru dotazu `$expand`. Další informace najdete v tématu věnovaném [konvencím OData: URI](https://go.microsoft.com/fwlink/?LinkId=185564) a [načítání odloženého obsahu](loading-deferred-content-wcf-data-services.md).|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxExpandDepth%2A>|Umožňuje omezit velikost odpovědi tím, že omezí hloubku grafu souvisejících entit, které mohou být zahrnuty do jedné žádosti pomocí operátoru dotazu `$expand`. Další informace najdete v tématu věnovaném [konvencím OData: URI](https://go.microsoft.com/fwlink/?LinkId=185564) a [načítání odloženého obsahu](loading-deferred-content-wcf-data-services.md).|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxObjectCountOnInsert%2A>|Umožňuje omezit počet entit, které mají být vloženy, které mohou být obsaženy v jednom požadavku POST.|  
|<xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A>|Definuje verzi protokolu Atom, který je používán datovou službou. Je-li hodnota <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> nastavena na hodnotu menší, než je maximální hodnota <xref:System.Data.Services.Common.DataServiceProtocolVersion>, nejsou klienti přistupující k datové službě k dispozici nejnovější funkce WCF Data Services. Další informace najdete v tématu [Správa verzí datových služeb](data-service-versioning-wcf-data-services.md).|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxResultsPerCollection%2A>|Umožňuje omezit velikost odpovědi tím, že omezí počet entit v každé sadě entit, která se vrátí jako datový kanál.|  
|<xref:System.Data.Services.DataServiceConfiguration.RegisterKnownType%2A>|Přidá datový typ do seznamu typů, které jsou rozpoznávány datovou službou.|  
|<xref:System.Data.Services.DataServiceConfiguration.SetEntitySetAccessRule%2A>|Nastaví přístupová práva pro prostředky sady entit, které jsou k dispozici v datové službě. Pro parametr Name lze zadat hodnotu hvězdičky (`*`) pro nastavení přístupu pro všechny zbývající sady entit na stejnou úroveň. Doporučujeme nastavit přístup k sadám entit tak, aby poskytovaly nejnižší oprávnění k prostředkům datové služby, které vyžadují klientské aplikace. Další informace najdete v tématu [zabezpečení WCF Data Services](securing-wcf-data-services.md). Příklady minimálních přístupových práv vyžadovaných pro daný identifikátor URI a akci HTTP najdete v tabulce v části [minimální požadavky na přístup k prostředkům](configuring-the-data-service-wcf-data-services.md#accessRequirements) .|  
|<xref:System.Data.Services.DataServiceConfiguration.SetEntitySetPageSize%2A>|Nastaví maximální velikost stránky pro prostředek sady entit. Další informace najdete v tématu [Postup: povolení stránkování výsledků datové služby](how-to-enable-paging-of-data-service-results-wcf-data-services.md).|  
|<xref:System.Data.Services.DataServiceConfiguration.SetServiceOperationAccessRule%2A>|Nastaví přístupová práva pro operace služby, které jsou definovány v datové službě. Další informace najdete v tématu [provozní operace](service-operations-wcf-data-services.md). Pro parametr Name lze zadat hodnotu hvězdičky (`*`) pro nastavení přístupu pro všechny operace služby na stejnou úroveň. Doporučujeme nastavit přístup k operacím služby, abyste poskytovali nejnižší oprávnění k prostředkům datové služby, které vyžadují klientské aplikace. Další informace najdete v tématu [zabezpečení WCF Data Services](securing-wcf-data-services.md).|  
|<xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A>|Tato vlastnost konfigurace umožňuje snadnější řešení potíží s datovou službou tím, že vrací další informace ve zprávě s chybovou odpovědí. Tato možnost není určena pro použití v produkčním prostředí. Další informace najdete v tématu [vývoj a nasazení WCF Data Services](developing-and-deploying-wcf-data-services.md).|  
  
<a name="accessRequirements"></a>   
## <a name="minimum-resource-access-requirements"></a>Minimální požadavky na přístup k prostředkům  
 Následující tabulka popisuje minimální práva sady entit, která musí být udělena ke spuštění konkrétní operace. Příklady cest jsou založené na datové službě Northwind, která se vytvoří po dokončení [rychlého](quickstart-wcf-data-services.md)startu. Vzhledem k tomu, že výčet <xref:System.Data.Services.EntitySetRights> i výčet <xref:System.Data.Services.ServiceOperationRights> jsou definovány pomocí <xref:System.FlagsAttribute>, můžete pomocí logického operátoru OR zadat více oprávnění pro jednu sadu entit nebo operaci. Další informace najdete v tématu [Postup: povolení přístupu k datové službě](how-to-enable-access-to-the-data-service-wcf-data-services.md).  
  
|Cesta/akce|`GET`|`DELETE`|`MERGE`|`POST`|`PUT`|  
|------------------|-----------|--------------|-------------|------------|-----------|  
|`/Customers`|<xref:System.Data.Services.EntitySetRights.ReadMultiple>|Není podporováno|Není podporováno|<xref:System.Data.Services.EntitySetRights.WriteAppend>|Není podporováno|  
|`/Customers('ALFKI')`|<xref:System.Data.Services.EntitySetRights.ReadSingle>|<xref:System.Data.Services.EntitySetRights.ReadSingle> a <xref:System.Data.Services.EntitySetRights.WriteDelete>|<xref:System.Data.Services.EntitySetRights.ReadSingle> a <xref:System.Data.Services.EntitySetRights.WriteMerge>|není k dispozici|<xref:System.Data.Services.EntitySetRights.ReadSingle> a <xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers('ALFKI')/Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> ani<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|Není podporováno|Není podporováno|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> a <xref:System.Data.Services.EntitySetRights.WriteMerge> nebo <xref:System.Data.Services.EntitySetRights.WriteReplace><br /><br /> ani<br /><br /> `Orders` `:` a <xref:System.Data.Services.EntitySetRights.WriteAppend>|Není podporováno|  
|`/Customers('ALFKI')/Orders(10643)`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> ani<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> ani<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> a <xref:System.Data.Services.EntitySetRights.WriteDelete>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> ani<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> a <xref:System.Data.Services.EntitySetRights.WriteMerge>|Není podporováno|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> ani<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> a <xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Orders(10643)/Customer`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> ani<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> a <xref:System.Data.Services.EntitySetRights.WriteDelete><br /><br /> ani<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> a <xref:System.Data.Services.EntitySetRights.WriteMerge>;<br /><br /> ani<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.WriteAppend><br /><br /> ani<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.WriteAppend> a <xref:System.Data.Services.EntitySetRights.ReadSingle>|Není podporováno|  
|`/Customers('ALFKI')/$links/Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> ani<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|Není podporováno|Není podporováno|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> a <xref:System.Data.Services.EntitySetRights.WriteMerge> nebo <xref:System.Data.Services.EntitySetRights.WriteReplace><br /><br /> ani<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|Není podporováno|  
|`/Customers('ALFKI')/$links/Orders(10643)`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> ani<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> a <xref:System.Data.Services.EntitySetRights.WriteMerge> nebo <xref:System.Data.Services.EntitySetRights.WriteReplace><br /><br /> ani<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|Není podporováno|Není podporováno|Není podporováno|  
|`/Orders(10643)/$links/Customer`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> ani<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> a <xref:System.Data.Services.EntitySetRights.WriteMerge> nebo <xref:System.Data.Services.EntitySetRights.WriteReplace>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> ani<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> a <xref:System.Data.Services.EntitySetRights.WriteMerge>|Není podporováno|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle>;<br /><br /> ani<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> a <xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers/$count`|<xref:System.Data.Services.EntitySetRights.ReadMultiple>|Není podporováno|Není podporováno|Není podporováno|Není podporováno|  
|`/Customers('ALFKI')/ContactName`|<xref:System.Data.Services.EntitySetRights.ReadSingle>|Není podporováno|<xref:System.Data.Services.EntitySetRights.WriteMerge>|Není podporováno|<xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers('ALFKI')/Address/StreetAddress/$value` <sup>1</sup>|<xref:System.Data.Services.EntitySetRights.ReadSingle>|<xref:System.Data.Services.EntitySetRights.WriteDelete>|Není podporováno|Není podporováno|Není podporováno|  
|`/Customers('ALFKI')/ContactName/$value`|<xref:System.Data.Services.EntitySetRights.ReadSingle>|<xref:System.Data.Services.EntitySetRights.ReadSingle> a <xref:System.Data.Services.EntitySetRights.WriteDelete>|<xref:System.Data.Services.EntitySetRights.WriteMerge>|Není podporováno|<xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers('ALFKI')/$value` <sup>2</sup>|<xref:System.Data.Services.EntitySetRights.ReadSingle>|Není podporováno|Není podporováno|Není podporováno|<xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers?$select=Orders/*&$expand=Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> ani<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|Není podporováno|Není podporováno|`Customers`: <xref:System.Data.Services.EntitySetRights.WriteAppend>|Není podporováno|  
|`/Customers('ALFKI')?$select=Orders/*&$expand=Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> ani<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|Není podporováno|Není podporováno|Není podporováno|Není podporováno|  
  
 <sup>1</sup> v tomto příkladu představuje `Address` vlastnost komplexního typu entity `Customers`, která má vlastnost s názvem `StreetAddress`. Model používaný datovými službami Northwind nedefinuje Tento komplexní typ explicitně. Pokud je datový model definován pomocí poskytovatele Entity Framework, můžete použít nástroje model EDM (Entity Data Model) k definování takového komplexního typu. Další informace naleznete v tématu [How to: Create and modify Complex Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).  
  
 <sup>2</sup> tento identifikátor URI se podporuje, když vlastnost, která vrací binární rozsáhlý objekt (BLOB), je definovaná jako mediální prostředek, který patří do entity, která je položkou odkazu na média, která v tomto případě je `Customers`. Další informace najdete v tématu [poskytovatel streamování](streaming-provider-wcf-data-services.md).  
  
<a name="versioning"></a>   
## <a name="versioning-requirements"></a>Požadavky na správu verzí  
 Následující chování konfigurace datové služby vyžaduje verzi 2 protokolu OData nebo novější verze:  
  
- Podpora počtu požadavků.  
  
- Podpora pro možnost dotazu $select pro projekci.  
  
 Další informace najdete v tématu [Správa verzí datových služeb](data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Definování datových služeb WCF Data Services](defining-wcf-data-services.md)
- [Hostování datové služby](hosting-the-data-service-wcf-data-services.md)
