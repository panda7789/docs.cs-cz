---
title: Zjednodušená konfigurace
description: Seznamte se s zjednodušenou konfigurací pro služby WCF. .NET Framework 4.6.1 poskytuje způsob, jak omezit velikost a složitost konfigurace služby.
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: defaf536d5a5b9f1479271c0976b43e9b1eb5bc4
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246035"
---
# <a name="simplified-configuration"></a>Zjednodušená konfigurace
Konfigurace služeb Windows Communication Foundation (WCF) může být složitý úkol. Existuje mnoho různých možností a není vždy snadné určit, která nastavení se vyžadují. Přestože konfigurační soubory zvyšují flexibilitu služeb WCF, jsou také zdrojem mnoha obtíží při hledání problémů. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]řeší tyto problémy a poskytuje způsob, jak omezit velikost a složitost konfigurace služby.  
  
## <a name="simplified-configuration"></a>Zjednodušená konfigurace  
 V konfiguračních souborech služby WCF `system.serviceModel` obsahuje oddíl <> <`service` prvek> pro každou hostovanou službu. Prvek <`service`> obsahuje kolekci `endpoint` prvků <>, které určují koncové body vystavené pro každou službu a volitelně také chování sady služeb. Prvky <`endpoint`> určují adresu, vazbu a kontrakt vystavený koncovým bodem a volitelně naváže chování konfigurace a koncového bodu. Oddíl <`system.serviceModel`> obsahuje také `behaviors` prvek <>, který umožňuje určit chování služby nebo koncového bodu. Následující příklad ukazuje `system.serviceModel` oddíl <> konfiguračního souboru.  
  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]zjednodušuje konfiguraci služby WCF odebráním požadavku na <`service`> elementu. Pokud nepřidáte `service` oddíl <> nebo přidáte žádné koncové body do `service` oddílu <> a vaše služba programově nedefinuje žádné koncové body, pak se do vaší služby automaticky přidají sada výchozích koncových bodů, jednu pro každou základní adresu služby a pro každý kontrakt implementovaný vaší službou. V každém z těchto koncových bodů adresa koncového bodu odpovídá základní adrese. vazba je určena základním adresním schématem a smlouva je ta, kterou implementuje vaše služba. Pokud nepotřebujete zadat žádné koncové body nebo chování služby nebo provést žádné změny nastavení vazby, nemusíte vůbec zadávat konfigurační soubor služby. Pokud služba implementuje dvě smlouvy a hostitel povolí přenos přes protokol HTTP i TCP, vytvoří hostitel služby čtyři výchozí koncové body, jednu pro každou kontrakt pomocí každého přenosu. Chcete-li vytvořit výchozí koncové body, musí hostitel služby zjistit, jaké vazby se mají použít. Tato nastavení jsou uvedena v části <`protocolMappings`> v `system.serviceModel` části <>. Oddíl <`protocolMappings`> obsahuje seznam schémat přenosových protokolů mapovaných na typy vazeb. Hostitel služby používá předaných základních adres k určení, která vazba se má použít. Následující příklad používá `protocolMappings` prvek <>.  
  
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
  
 V předchozím příkladu koncový bod se základní adresou začínající schématem HTTP používá <xref:System.ServiceModel.BasicHttpBinding> . Koncový bod se základní adresou začínající schématem NET. TCP používá <xref:System.ServiceModel.NetTcpBinding> . Nastavení můžete přepsat v místním souboru App.config nebo Web.config.  
  
 Každý prvek v oddílu <`protocolMappings`> musí určovat schéma a vazbu. Volitelně můžete určit `bindingConfiguration` atribut, který určuje konfiguraci vazby v rámci <`bindings`> oddílu konfiguračního souboru. Pokud `bindingConfiguration` není zadaný, použije se konfigurace anonymní vazby příslušného typu vazby.  
  
 Chování služby je konfigurováno pro výchozí koncové body pomocí anonymních <`behavior`> sekcí v rámci <ch `serviceBehaviors`>ch sekcí. `behavior` `serviceBehaviors` Ke konfiguraci chování služby se používají všechny nepojmenované <> prvky v <>. Například následující konfigurační soubor umožňuje publikování metadat služby pro všechny služby v rámci hostitele.  
  
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
  
 Chování koncového bodu se konfiguruje pomocí anonymních <`behavior`> sekcí v rámci <ch `serviceBehaviors`> sekcí.  
  
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
> Tato funkce se týká pouze konfigurace služby WCF, nikoli konfigurace klienta. Ve většině případů bude konfigurace klienta WCF vygenerována nástrojem, například svcutil.exe nebo přidáním odkazu na službu ze sady Visual Studio. Pokud ručně konfigurujete klienta WCF, bude nutné přidat \<client> prvek do konfigurace a zadat všechny koncové body, které chcete zavolat.  
  
## <a name="see-also"></a>Viz také

- [Konfigurace služeb pomocí konfiguračních souborů](configuring-services-using-configuration-files.md)
- [Konfigurace vazeb pro služby](configuring-bindings-for-wcf-services.md)
- [Konfigurace vazeb poskytovaných systémem](./feature-details/configuring-system-provided-bindings.md)
- [Konfigurace služeb](configuring-services.md)
- [Konfigurace služeb WCF](configuring-services.md)
- [Konfigurace služeb WCF v kódu](configuring-wcf-services-in-code.md)
