---
title: '&lt;system.serviceModel&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 16a3b9b361048344993fdc338544b6b0ceb95387
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltsystemservicemodelgt"></a>&lt;system.serviceModel&gt;
Tento konfigurační oddíl obsahuje všechny [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] ServiceModel konfigurace – elementy.  
  
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
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování >](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)|Tento oddíl definuje dva podřízené kolekce s názvem `endpointBehaviors` a `serviceBehaviors`.  Každá kolekce definuje chování elementy spotřebovávají koncové body a služby. Každý prvek chování je identifikován jeho jedinečné `name` atributu.|  
|[\<vazby >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Tato část obsahuje kolekci standardní a vlastní vazby. Každá položka je identifikována jeho jedinečné `name`. Služby používají vazby jejich propojováním pomocí `name`.|  
|[\<klient >](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|Tato část obsahuje seznam koncových bodů, které klient používá pro připojení ke službě.|  
|[\<comContracts >](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)|Tento oddíl definuje kontrakty COM povolen pro WCF a rozhraní COM zprostředkovatel komunikace s objekty.|  
|[\<commonBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)|V této části můžete definovat pouze v souboru machine.config. Definuje dva podřízené kolekce s názvem `endpointBehaviors` a `serviceBehaviors`.  Každá kolekce definuje chování prvky používané ve všech [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] koncových bodů a služeb na počítači v uvedeném pořadí.  Pokud chování je definovaný jak v `<commonBehaviors>` a `<behaviors>` jejich chování v oddílech \<chování > části je přednost.|  
|[\<Rozšíření >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions-section.md)|Tato část obsahuje kolekci rozšíření, která uživateli umožňuje vytvořit uživatelem definované vazby, chování a dalších aspektů rozšíření.|  
|[\<Diagnostika >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|Tato část obsahuje nastavení pro diagnostiku funkcím WCF. Uživatel může povolit či zakázat trasování, čítače výkonu a zprostředkovatele rozhraní WMI a můžete přidat vlastní zprávu filtry.|  
|[\<protocolMapping >](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|Tento oddíl definuje sadu výchozí protokol mapování mezi přenosu protokolu schémata (např. http, net.tcp, net.pipe atd.) a vazeb WCF.|  
|[\<směrování >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Tento oddíl definuje sadu směrování filtry, které určují typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy, jakož i směrování tabulky definující cílové koncové body k odesílání zpráv do kdy odpovídá filtru.|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Tento oddíl definuje, co zadejte službu, kterou vytvoří hostitelské prostředí konkrétního přenosu. Pokud tato část je prázdná, použije se výchozí typ.|  
|[\<služby >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|Oddíl obsahuje kolekci služeb. U každé služby definované v sestavení, obsahuje tento prvek `service` element zadání nastavení pro službu.|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Tento oddíl definuje kolekce standardních koncových bodů, které jsou opakovaně použitelné předem nakonfigurované koncové body. Koncový bod standardní bude mít jeden nebo více adresy, vazby a atributy kontrakt nastavte na pevnou hodnotu. Například v koncový bod zjišťování vyřešen kontrakt. Standardní koncové body můžete taky rozšířit koncový bod služby s nové vlastnosti podobná definování vlastní vazby.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|\<Konfigurace >|Kořenový element pro všechny elementy konfigurace v konfiguračním souboru .NET.|  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]nepřidává žádné další prvky konfigurace části Další produkty.  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]služby jsou definovány v `services` oddílu konfiguračního souboru. Sestavení může obsahovat libovolný počet služeb. Každá služba má svůj vlastní `service` konfigurační oddíl. Části a jejího obsahu definovat kontrakt služby, chování a koncové body konkrétní služby.  
  
 Pouze služby `name` atribut je požadován.  Ve výchozím nastavení název služby popisuje základní typ CLR použít k implementaci služby; Můžete však změnit vlastnost ConfigurationName na <xref:System.ServiceModel.ServiceContractAttribute> potlačit požadavek na typ CLR.  
  
 `behaviorConfiguration` Atribut je volitelný. Určuje chování služby používané služby. Nastavení chování tímto atributem propojit chování služby definovaný v oboru stejné konfigurační soubor (tj. stejný soubor nebo soubor nadřazené).  
  
 Každá služba vystavuje jeden nebo více koncové body definované v `endpoint` elementu. Každý koncový bod má svou vlastní adresu a vazby. Všechny vazby používaných v rámci konfiguračního souboru musí být definován v oboru souboru.  
  
 Vazby jsou propojeny s koncových bodů prostřednictvím kombinace atributů `name` a `bindingConfiguration`. `binding` Atribut definuje, ve které části je definovaný vazby. `bindingConfiguration` Atribut definuje, které nakonfigurovanou vazbu v rámci části vazby se používá. Vazba části můžete definovat několik nakonfigurované vazby.  
  
## <a name="example"></a>Příklad  
 Jedná se o příklad konfiguračního souboru WCF.  
  
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
        <diagnostics wmiProviderEnabled="false" performanceCountersEnabled="false" tracingEnabled="false">  
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
 <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
