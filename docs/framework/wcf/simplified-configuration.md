---
title: Zjednodušená konfigurace
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 3bed6fe961712c976d5e1446ace43e7073036697
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423707"
---
# <a name="simplified-configuration"></a>Zjednodušená konfigurace
Konfigurace služeb Windows Communication Foundation (WCF) může být složitý úkol. Existuje mnoho různých možností a není vždy snadné určit, která nastavení se vyžadují. Přestože konfigurační soubory zvyšují flexibilitu služeb WCF, jsou také zdrojem mnoha obtíží při hledání problémů. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] řeší tyto problémy a poskytuje způsob, jak omezit velikost a složitost konfigurace služby.  
  
## <a name="simplified-configuration"></a>Zjednodušená konfigurace  
 V konfiguračních souborech služby WCF <`system.serviceModel`> oddíl obsahuje prvek <`service`> pro každou hostovanou službu. < Prvek `service` > obsahuje kolekci < `endpoint` > prvků, které určují koncové body vystavené pro každou službu a volitelně také chování sady. < Prvky `endpoint` > určují adresu, vazbu a kontrakt vystavený koncovým bodem a volitelně vazby chování konfigurace a koncového bodu. Oddíl <`system.serviceModel`> obsahuje také prvek <`behaviors`>, který umožňuje určit chování služby nebo koncového bodu. Následující příklad ukazuje < oddíl `system.serviceModel` > konfiguračního souboru.  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true">  
        <serviceDebug includeExceptionDetailInFaults="false">  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <bindings>  
   <basicHttpBinding>  
      <binding name=MyBindingConfig"  
               maxBufferSize="100"  
               maxReceiveBufferSize="100" />  
   </basicHttpBinding>  
   </bindings>   <services>  
    <service behaviorConfiguration="MyServiceBehavior"  
             name="MyService">  
      <endpoint address=""  
                binding="basicHttpBinding"  
                contract="ICalculator"  
                bindingConfiguration="MyBindingConfig" />  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange"/>  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] usnadňuje konfiguraci služby WCF tím, že odebere požadavek pro <`service`prvek >. Pokud nepřidáte < oddíl `service` > nebo přidáte žádné koncové body do < `service` > a vaše služba nedefinuje žádné koncové body, pak se do vaší služby automaticky přidají sada výchozích koncových bodů, jednu pro každou základní adresu služby. a pro každou smlouvu, kterou služba implementuje. V každém z těchto koncových bodů adresa koncového bodu odpovídá základní adrese. vazba je určena základním adresním schématem a smlouva je ta, kterou implementuje vaše služba. Pokud nepotřebujete zadat žádné koncové body nebo chování služby nebo provést žádné změny nastavení vazby, nemusíte vůbec zadávat konfigurační soubor služby. Pokud služba implementuje dvě smlouvy a hostitel povolí přenos přes protokol HTTP i TCP, vytvoří hostitel služby čtyři výchozí koncové body, jednu pro každou kontrakt pomocí každého přenosu. Chcete-li vytvořit výchozí koncové body, musí hostitel služby zjistit, jaké vazby se mají použít. Tato nastavení jsou uvedená v < `protocolMappings` > v části < `system.serviceModel` >. Část < `protocolMappings` > obsahuje seznam schémat přenosových protokolů mapovaných na typy vazeb. Hostitel služby používá předaných základních adres k určení, která vazba se má použít. Následující příklad používá < prvek `protocolMappings` >.  
  
> [!WARNING]
> Změna výchozích prvků konfigurace, jako jsou vazby nebo chování, může ovlivnit služby definované v nižších úrovních konfigurační hierarchie, protože by mohly používat tyto výchozí vazby a chování. I když se jim budou měnit výchozí vazby a chování, je třeba si uvědomit, že tyto změny mohou ovlivnit jiné služby v hierarchii.  
  
> [!NOTE]
> Služby hostované v rámci služby Internetová informační služba (IIS) nebo aktivační služba procesů systému Windows (WAS) používají jako základní adresu virtuální adresář.  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 V předchozím příkladu koncový bod se základní adresou začínající schématem HTTP používá <xref:System.ServiceModel.BasicHttpBinding>. Koncový bod se základní adresou, který začíná schématem NET. TCP, používá <xref:System.ServiceModel.NetTcpBinding>. Nastavení můžete přepsat v souboru Local App. config nebo Web. config.  
  
 Každý prvek v části < `protocolMappings` > musí určovat schéma a vazbu. Volitelně můžete zadat atribut `bindingConfiguration`, který určuje konfiguraci vazby v části < `bindings` > konfiguračního souboru. Pokud není zadaný žádný `bindingConfiguration`, použije se konfigurace anonymní vazby příslušného typu vazby.  
  
 Chování služby se konfiguruje pro výchozí koncové body pomocí anonymních < `behavior` > oddíly v < `serviceBehaviors` > oddíly. Ke konfiguraci chování služby se používají všechny nepojmenované < prvky `behavior` > v rámci < `serviceBehaviors` >. Například následující konfigurační soubor umožňuje publikování metadat služby pro všechny služby v rámci hostitele.  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <!-- No <service> tag is necessary. Default endpoints are added to the service -->  
    <!-- The service behavior with name="" is picked up by the service -->  
 </system.serviceModel>  
```  
  
 Chování koncového bodu se konfiguruje pomocí anonymního <`behavior`> oddíly v sekcích <`serviceBehaviors`>.  
  
 Následující příklad je konfigurační soubor, který je ekvivalentní k tomu na začátku tohoto tématu, které používá zjednodušený konfigurační model.  
  
```xml  
<system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="true" />
          <serviceDebug includeExceptionDetailInFaults="false" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <bindings>
       <basicHttpBinding>
          <binding maxBufferSize="100"
                   maxReceiveBufferSize="100" />
       </basicHttpBinding>
    </bindings>
    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->
    <!-- The service behavior with name="" will be picked up by the service -->
    <protocolMapping>
      <add scheme="http" binding="basicHttpBinding" />
  </protocolMapping>
  </system.serviceModel>
```  
  
> [!IMPORTANT]
> Tato funkce se týká pouze konfigurace služby WCF, nikoli konfigurace klienta. Ve většině případů bude konfigurace klienta WCF vygenerována nástrojem, jako je Svcutil. exe, nebo přidáním odkazu na službu ze sady Visual Studio. Pokud ručně konfigurujete klienta WCF, bude nutné do konfigurace přidat prvek \<client > a zadat koncové body, které chcete volat.  
  
## <a name="see-also"></a>Viz také:

- [Konfigurace služeb pomocí konfiguračních souborů](configuring-services-using-configuration-files.md)
- [Konfigurace vazeb pro služby](configuring-bindings-for-wcf-services.md)
- [Konfigurace vazeb poskytovaných systémem](./feature-details/configuring-system-provided-bindings.md)
- [Konfigurace služeb](configuring-services.md)
- [Konfigurace služeb WCF](configuring-services.md)
- [Konfigurace služeb WCF v kódu](configuring-wcf-services-in-code.md)
