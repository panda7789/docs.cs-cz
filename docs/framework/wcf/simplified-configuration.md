---
title: Zjednodušená konfigurace
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 4e316290c045b75896c61e36c1646440c18678e2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249627"
---
# <a name="simplified-configuration"></a>Zjednodušená konfigurace
Konfigurace služeb Windows Communication Foundation (WCF) může být složitý úkol. Existuje mnoho různých možností a není vždy snadné určit, jaká nastavení jsou požadována. Zatímco konfigurační soubory zvyšují flexibilitu služeb WCF, jsou také zdrojem pro mnoho problémů, které se těžko nacházejí. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]řeší tyto problémy a poskytuje způsob, jak snížit velikost a složitost konfigurace služby.  
  
## <a name="simplified-configuration"></a>Zjednodušená konfigurace  
 V konfiguračních souborech služby WCF obsahuje část> služby <`system.serviceModel` <prvek> <`service` pro každou hostovanci služby. Prvek `service` <> obsahuje kolekci <`endpoint`> prvků, které určují koncové body vystavené pro každou službu a volitelně sadu chování služby. <`endpoint`> prvky určují adresu, vazbu a kontrakt vystavený koncovým bodem a volitelně vazby konfigurace a chování koncového bodu. Oddíl `system.serviceModel` <> obsahuje `behaviors` také prvek <>, který umožňuje určit chování služby nebo koncového bodu. Následující příklad ukazuje `system.serviceModel` <> části konfiguračního souboru.  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true" />  
        <serviceDebug includeExceptionDetailInFaults="false" />  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]usnadňuje konfiguraci služby WCF odebráním požadavku `service` na <> element. Pokud nepřidáte oddíl `service` <> nebo nepřidáte žádné `service` koncové body v <> části a vaše služba programově nedefinuje žádné koncové body, bude do vaší služby automaticky přidána sada výchozích koncových bodů, jeden pro každou adresu základny služeb a pro každou smlouvu implementovanou vaší službou. V každém z těchto koncových bodů adresa koncového bodu odpovídá základní adrese, vazba je určena schématem základní adresy a smlouva je ta implementovaná vaší službou. Pokud není nutné zadat žádné koncové body nebo chování služby nebo provádět změny nastavení vazby, není nutné zadat konfigurační soubor služby vůbec. Pokud služba implementuje dvě smlouvy a hostitel umožňuje přenosy HTTP i TCP, hostitel služby vytvoří čtyři výchozí koncové body, jeden pro každou smlouvu pomocí každého přenosu. Chcete-li vytvořit výchozí koncové body, musí hostitel služby vědět, jaké vazby se mají použít. Tato nastavení jsou určena `protocolMappings` v oddílu `system.serviceModel` <> v části <>. <`protocolMappings`> část obsahuje seznam schémat protokolu přenosu mapovaných na typy vazeb. Hostitel služby používá základní adresy, které mu byly předány, k určení, kterou vazbu použít. Následující příklad používá `protocolMappings` prvek <>.  
  
> [!WARNING]
> Změna výchozích prvků konfigurace, jako jsou vazby nebo chování, může ovlivnit služby definované v nižších úrovních hierarchie konfigurace, protože mohou používat tyto výchozí vazby a chování. Takže ten, kdo změní výchozí vazby a chování musí být vědomi, že tyto změny mohou mít vliv na jiné služby v hierarchii.  
  
> [!NOTE]
> Služby hostované v rámci Služby internetovou informační služby (IIS) nebo služby aktivace procesů systému Windows (WAS) používají virtuální adresář jako svou základní adresu.  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 V předchozím příkladu koncový bod se základní adresou, která začíná <xref:System.ServiceModel.BasicHttpBinding>schématem http, používá . Koncový bod se základní adresou, která začíná schématem net.tcp, používá rozhraní <xref:System.ServiceModel.NetTcpBinding>. Nastavení můžete přepsat v místním souboru App.config nebo Web.config.  
  
 Každý prvek v `protocolMappings` oddílu <> musí určit schéma a vazbu. Volitelně může určit `bindingConfiguration` atribut, který určuje konfiguraci `bindings` vazby v části <> konfiguračního souboru. Pokud `bindingConfiguration` není zadána žádná, použije se konfigurace anonymní vazby příslušného typu vazby.  
  
 Chování služby jsou konfigurovány pro výchozí `behavior` koncové body `serviceBehaviors` pomocí anonymních <> oddíly v <> oddíly. Všechny nepojmenované `behavior` prvky `serviceBehaviors`> <v rámci <> se používají ke konfiguraci chování služby. Následující konfigurační soubor například umožňuje publikování metadat služby pro všechny služby v rámci hostitele.  
  
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
  
 Chování koncových bodů se nakonfiguruje pomocí anonymních <`behavior`> oddílů v <`serviceBehaviors` oddílech>.  
  
 Následující příklad je konfigurační soubor ekvivalentní souboru na začátku tohoto tématu, který používá zjednodušený konfigurační model.  
  
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
> Tato funkce se vztahuje pouze na konfiguraci služby WCF, nikoli konfigurace klienta. Ve většině případů wcf konfigurace klienta budou generovány nástrojem, jako je například svcutil.exe nebo přidání odkazu na službu z visual studio. Pokud ručně konfigurujete klienta WCF, \<budete muset přidat prvek klienta> do konfigurace a zadat všechny koncové body, které chcete volat.  
  
## <a name="see-also"></a>Viz také

- [Konfigurace služeb pomocí konfiguračních souborů](configuring-services-using-configuration-files.md)
- [Konfigurace vazeb pro služby](configuring-bindings-for-wcf-services.md)
- [Konfigurace vazeb poskytovaných systémem](./feature-details/configuring-system-provided-bindings.md)
- [Konfigurace služeb](configuring-services.md)
- [Konfigurace služeb WCF](configuring-services.md)
- [Konfigurace služeb WCF v kódu](configuring-wcf-services-in-code.md)
