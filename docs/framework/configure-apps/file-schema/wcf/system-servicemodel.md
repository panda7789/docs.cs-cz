---
title: <system.serviceModel>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
ms.openlocfilehash: c176f7f470cc65bb135e5f92935102e09c7e8485
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209824"
---
# <a name="systemservicemodel"></a>\<system.serviceModel>
Tento oddíl konfigurace obsahuje všechny elementy konfigurace ServiceModel Windows Communication Foundation (WCF).  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <behaviors>
  </behaviors>
  <bindings>
  </bindings>
  <client>
  </client>
  <comContracts>
  </comContracts>
  <commonBehaviors>
  </commonBehaviors>
  <diagnostics>
  </diagnostics>
  <extensions>
  </extensions>
  <protocolMapping>
  </protocolMapping>
  <routing>
  </routing>
  <serviceHostingEnvironment>
  </serviceHostingEnvironment>
  <services>
  </services>
  <standardEndpoints>
  </standardEndpoints>
  <tracking>
  </tracking>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování >](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)|Tento oddíl definuje dvě podkolekce s `endpointBehaviors` a `serviceBehaviors`.  Každou kolekci definuje chování elementů používané koncové body a služby. Každý prvek chování je identifikován jeho jedinečné `name` atributu.|  
|[\<vazby >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Tato část obsahuje sadu standardních a vlastních vazeb. Každá položka je identifikován jeho jedinečné `name`. Služby používají vazby jejich propojením pomocí `name`.|  
|[\<client>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|Tato část obsahuje seznam koncových bodů, které klient používá pro připojení ke službě.|  
|[\<comContracts>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)|Tento oddíl definuje kontrakty COM pro WCF a modelu COM interop povolené.|  
|[\<commonBehaviors>](../../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)|Tato část lze definovat pouze v souboru machine.config. Definuje dvě podkolekce s `endpointBehaviors` a `serviceBehaviors`.  Každou kolekci definuje chování elementů používané všech koncových bodů WCF a služeb na počítači.  Pokud chování je definován v `<commonBehaviors>` a `<behaviors>` části, chování \<chování > části je přednost.|  
|[\<Diagnostika >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|Tato část obsahuje nastavení pro funkce Diagnostika služby WCF. Uživatel můžete povolit nebo zakázat trasování, čítače výkonu a zprostředkovatele rozhraní WMI a můžete přidat vlastní zprávu filtry.|  
|[\<Rozšíření >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions-section.md)|Tento oddíl obsahuje kolekci rozšíření, které umožňují uživateli vytvořit uživatelem definované vazby, chování a další aspekty rozšíření.|  
|[\<protocolMapping>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|Tento oddíl definuje sadu výchozích mapování protokolů mezi schématy přenosových protokolů (např. http, net.tcp, net.pipe atd.) a vazbami WCF.|  
|[\<směrování >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Tento oddíl definuje sady směrovacích filtrů, které určují typ služby Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> má být použit při vyhodnocování příchozích zpráv, jakož i směrovací tabulky, které definujjí koncové body pro odesílání zpráv do kdy filtr hledá shodu.|  
|[\<serviceHostingEnvironment>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Tento oddíl definuje, jaký typ služby, který vytvoří instanci hostitelské prostředí pro konkrétní přenos. Pokud v této části je prázdný, je použit výchozí typ.|  
|[\<services>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|Oddíl obsahuje kolekci služeb. U každé služby definované v sestavení, obsahuje tento element `service` prvek nastavení pro službu.|  
|[\<standardEndpoints>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Tento oddíl definuje kolekci standardních koncových bodů, které jsou opakovaně použitelnými koncovými body. Standardní koncový bod bude mít jednu nebo více adresa, vazba a kontrakt atributy nastavit na pevnou hodnotu. Například v koncový bod zjišťování vyřešen kontrakt. Standardní koncové body můžete použít také k rozšíření koncového bodu služby s novou vlastností k definování vlastních vazeb.|
|[\<sledování >](../../../../../docs/framework/configure-apps/file-schema/wcf/tracking-of-wcf.md)|Tento oddíl definuje nastavení sledování služby pracovního postupu.|

### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|\<Konfigurace >|Kořenový element pro všechny elementy konfigurace v konfiguračním souboru .NET.|  
  
## <a name="remarks"></a>Poznámky  
 WCF nepřidá prvky do oddílu konfigurace ostatních produktů.  
  
 Služby WCF, které jsou definovány v `services` oddílu konfiguračního souboru. Sestavení může obsahovat libovolný počet služeb. Každá služba má svůj vlastní `service` konfigurační oddíl. Části a její obsah definování kontraktu služby, chování a koncové body konkrétní služby.  
  
 Pouze služby `name` atribut je vyžadován.  Ve výchozím nastavení název služby popisuje základní typ CLR používaný k implementaci služby; Můžete však změnit vlastnost ConfigurationName na <xref:System.ServiceModel.ServiceContractAttribute> přepsat požadovaný typ CLR.  
  
 `behaviorConfiguration` Atribut je volitelný. Určuje chování služby používané službou. Chování určené jinou tento atribut musí odkazovat na chování služby definované v oboru stejný konfigurační soubor (tj. na stejný soubor nebo nadřazený soubor).  
  
 Každá služba zpřístupňuje jeden nebo více koncových bodů podle `endpoint` elementu. Každý koncový bod má svou vlastní adresu a vazbu. Všechny vazby používá v konfiguračním souboru musí být definován v rozsahu souboru.  
  
 Vazby jsou propojeny do koncových bodů prostřednictvím kombinace atributů `name` a `bindingConfiguration`. `binding` Atribut definuje, ve které části je definována vazby. `bindingConfiguration` Atribut definuje, které nakonfigurovanou vazbu v rámci oddílu vazby se používá. Část vazby můžete definovat několik nakonfigurované vazby.  
  
## <a name="example"></a>Příklad  
 Toto je příklad konfiguračního souboru WCF.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <!-- List of Behaviors -->
    </behaviors>
    <client>
      <!-- List of Endpoints -->
    </client>
    <diagnostics wmiProviderEnabled="false"
                 performanceCountersEnabled="false"
                 tracingEnabled="false">
    </diagnostics>
    <serviceHostingEnvironment>
      <!-- List of entries -->
    </serviceHostingEnvironment>
    <comContracts>
      <!-- List of COM+ Contracts -->
    </comContracts>
    <services>
      <!-- List of Services -->
    </services>
    <bindings>
      <!-- List of Bindings -->
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
