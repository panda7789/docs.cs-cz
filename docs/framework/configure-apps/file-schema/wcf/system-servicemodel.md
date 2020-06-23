---
title: <system.serviceModel>
description: Přečtěte si o prvcích konfigurace ServiceModel WCF, které umožňují nakonfigurovat službu WCF a klientské aplikace.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
ms.openlocfilehash: 567cbd2cc07ee82e795daa067b9034b2b8dc1974
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85243955"
---
# \<system.serviceModel>
Tento oddíl konfigurace obsahuje všechny prvky konfigurace ServiceModel Windows Communication Foundation (WCF).  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.serviceModel>**  
  
## <a name="syntax"></a>Syntax  
  
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
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<behaviors>](behaviors.md)|V této části jsou definovány dvě podřízené kolekce s názvem `endpointBehaviors` a `serviceBehaviors` .  Každá kolekce definuje prvky chování spotřebované koncovými body a službami v uvedeném pořadí. Každý prvek chování je identifikován jeho jedinečné `name` atributu.|  
|[\<bindings>](bindings.md)|Tato část obsahuje kolekci standardních a vlastních vazeb. Každá položka je identifikována jejím jedinečným `name` . Služby používají vazby propojením s použitím `name` .|  
|[\<client>](client.md)|Tato část obsahuje seznam koncových bodů, které klient používá pro připojení ke službě.|  
|[\<comContracts>](comcontracts.md)|Tato část definuje kontrakty COM aktivované pro WCF a zprostředkovatele komunikace s objekty COM.|  
|[\<commonBehaviors>](commonbehaviors.md)|Tento oddíl lze definovat pouze v souboru machine.config. Definuje dvě podřízené kolekce s názvem `endpointBehaviors` a `serviceBehaviors` .  Každá kolekce definuje prvky chování spotřebované všemi koncovými body a službami WCF v daném počítači.  Pokud je chování definováno v obou `<commonBehaviors>` částech a `<behaviors>` , chování v \<behaviors> oddílu má přednost.|  
|[\<diagnostics>](diagnostics.md)|Tato část obsahuje nastavení pro diagnostické funkce služby WCF. Uživatel může povolit nebo zakázat trasování, čítače výkonu a zprostředkovatele rozhraní WMI a může přidat vlastní filtry zpráv.|  
|[\<extensions>](extensions-section.md)|Tato část obsahuje kolekci rozšíření, která umožňují uživateli vytvořit uživatelsky definované vazby, chování a další aspekty rozšíření.|  
|[\<protocolMapping>](protocolmapping.md)|Tato část definuje sadu výchozích mapování protokolů mezi schématy transportního protokolu (např. http, NET. TCP, NET. pipe, atd.) a WCF vazbami.|  
|[\<routing>](routing.md)|Tato část definuje sadu směrovacích filtrů, které určují typ Windows Communication Foundation (WCF), který <xref:System.ServiceModel.Dispatcher.MessageFilter> se má použít při vyhodnocování příchozích zpráv, jakož i směrovací tabulky definující cílové koncové body, na které se budou posílat zprávy, když filtr odpovídá.|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|V této části je definován typ, který hostující prostředí služby vytvoří pro konkrétní přenos. Pokud je tato část prázdná, použije se výchozí typ.|  
|[\<services>](services.md)|Oddíl obsahuje kolekci služeb. Pro každou službu definovanou v sestavení tento element obsahuje element, který `service` Určuje nastavení pro službu.|  
|[\<standardEndpoints>](standardendpoints.md)|Tato část definuje kolekci standardních koncových bodů, které jsou opakovaně použitelnými koncovými body. Standardní koncový bod bude mít jednu nebo víc atributů adresa, vazba a kontraktu nastavenou na pevnou hodnotu. Například ve koncovém bodě zjišťování je smlouva opravena. Pomocí standardních koncových bodů můžete také rozšířenit koncový bod služby s novými vlastnostmi podobnými definování vlastních vazeb.|
|[\<tracking>](tracking-of-wcf.md)|Tato část definuje nastavení sledování pro službu pracovního postupu.|

### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|\<configuration>|Kořenový element pro všechny elementy konfigurace v konfiguračním souboru .NET.|  
  
## <a name="remarks"></a>Poznámky  
 Technologie WCF nepřidává prvky do konfiguračních oddílů jiných produktů.  
  
 Služby WCF jsou definovány v `services` části konfiguračního souboru. Sestavení může obsahovat libovolný počet služeb. Každá služba má vlastní `service` konfigurační oddíl. Oddíl a jeho obsah definují kontrakt služby, chování a koncové body konkrétní služby.  
  
 `name`Je vyžadován pouze atribut služby.  Ve výchozím nastavení popisuje název služby základní typ CLR používaný k implementaci služby. Můžete však změnit vlastnost ConfigurationName pro na, aby bylo možné <xref:System.ServiceModel.ServiceContractAttribute> přepsat požadavek typu CLR.  
  
 `behaviorConfiguration`Atribut je nepovinný. Identifikuje chování služby používané službou. Chování zadané pomocí tohoto atributu musí odkazovat na chování služby definované v oboru stejného konfiguračního souboru (tj. stejný soubor nebo nadřazený soubor).  
  
 Každá služba zveřejňuje jeden nebo více koncových bodů definovaných v `endpoint` elementu. Každý koncový bod má svou vlastní adresu a vazbu. Všechny vazby používané v konfiguračním souboru musí být definovány v rozsahu souboru.  
  
 Vazby jsou propojeny s koncovými body pomocí kombinace atributů `name` a `bindingConfiguration` . `binding`Atribut definuje, v jakém oddílu je vazba definována. `bindingConfiguration`Atribut určuje, která konfigurovaná vazba v rámci oddílu Binding je použita. Oddíl Binding může definovat několik nakonfigurovaných vazeb.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
