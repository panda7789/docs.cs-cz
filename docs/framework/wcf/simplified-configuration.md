---
title: Zjednodušená konfigurace
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: cdb5d819ce3af372ce44ee2c038556c1383acfe3
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987220"
---
# <a name="simplified-configuration"></a>Zjednodušená konfigurace
Konfigurace služeb Windows Communication Foundation (WCF) může být složitý úkol. Existuje mnoho různých možností a není vždy snadné určit, která nastavení se vyžadují. Přestože konfigurační soubory zvyšují flexibilitu služeb WCF, jsou také zdrojem mnoha obtíží při hledání problémů. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]řeší tyto problémy a poskytuje způsob, jak omezit velikost a složitost konfigurace služby.  
  
## <a name="simplified-configuration"></a>Zjednodušená konfigurace  
 V konfiguračních souborech služby WCF obsahuje oddíl <`system.serviceModel`> <`service`prvek > pro každou hostovanou službu. Prvek <`service`> obsahuje kolekci prvků <`endpoint`>, které určují koncové body vystavené pro každou službu a volitelně také chování sady služeb. Prvky <`endpoint`> určují adresu, vazbu a kontrakt vystavený koncovým bodem a volitelně naváže chování konfigurace a koncového bodu. Oddíl <`system.serviceModel`> obsahuje také prvek <`behaviors`>, který umožňuje určit chování služby nebo koncového bodu. Následující příklad ukazuje oddíl <`system.serviceModel`> konfiguračního souboru.  
  
```  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]zjednodušuje konfiguraci služby WCF odebráním požadavku na <`service`> elementu. Pokud nepřidáte oddíl <`service`> nebo přidáte žádné koncové body do oddílu <`service`> a vaše služba programově nedefinuje žádné koncové body, pak se do vaší služby automaticky přidají sada výchozích koncových bodů, jednu pro každou základní adresa služby a pro každý kontrakt implementovaný vaší službou. V každém z těchto koncových bodů adresa koncového bodu odpovídá základní adrese. vazba je určena základním adresním schématem a smlouva je ta, kterou implementuje vaše služba. Pokud nepotřebujete zadat žádné koncové body nebo chování služby nebo provést žádné změny nastavení vazby, nemusíte vůbec zadávat konfigurační soubor služby. Pokud služba implementuje dvě smlouvy a hostitel povolí přenos přes protokol HTTP i TCP, vytvoří hostitel služby čtyři výchozí koncové body, jednu pro každou kontrakt pomocí každého přenosu. Chcete-li vytvořit výchozí koncové body, musí hostitel služby zjistit, jaké vazby se mají použít. Tato nastavení jsou uvedena v části <`protocolMappings`> v části <`system.serviceModel`>. Oddíl <`protocolMappings`> obsahuje seznam schémat přenosových protokolů mapovaných na typy vazeb. Hostitel služby používá předaných základních adres k určení, která vazba se má použít. Následující příklad používá prvek <`protocolMappings`>.  
  
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
  
 V předchozím příkladu koncový bod se základní adresou začínající schématem HTTP používá <xref:System.ServiceModel.BasicHttpBinding>. Koncový bod se základní adresou začínající schématem NET. TCP používá <xref:System.ServiceModel.NetTcpBinding>. Nastavení můžete přepsat v souboru Local App. config nebo Web. config.  
  
 Každý prvek v oddílu <`protocolMappings`> musí určovat schéma a vazbu. Volitelně můžete určit `bindingConfiguration` atribut, který určuje konfiguraci vazby v rámci <`bindings`> oddílu konfiguračního souboru. `bindingConfiguration` Pokud není zadaný, použije se konfigurace anonymní vazby příslušného typu vazby.  
  
 Chování služby je konfigurováno pro výchozí koncové body pomocí anonymních`behavior`< > sekcí v`serviceBehaviors`rámci <ch >ch sekcí. Ke konfiguraci chování služby se`behavior`používají všechny nepojmenované < > prvky v <`serviceBehaviors`>. Například následující konfigurační soubor umožňuje publikování metadat služby pro všechny služby v rámci hostitele.  
  
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
  
 Chování koncového bodu se konfiguruje pomocí anonymních <`behavior`> sekcí v rámci <ch`serviceBehaviors`> sekcí.  
  
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
> Tato funkce se týká pouze konfigurace služby WCF, nikoli konfigurace klienta. Ve většině případů bude konfigurace klienta WCF vygenerována nástrojem, jako je Svcutil. exe, nebo přidáním odkazu na službu ze sady Visual Studio. Pokud ručně konfigurujete klienta WCF, bude nutné přidat \<do konfigurace klienta > element a zadat všechny koncové body, které chcete zavolat.  
  
## <a name="see-also"></a>Viz také:

- [Konfigurace služeb pomocí konfiguračních souborů](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [Konfigurace vazeb pro služby](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [Konfigurace vazeb poskytovaných systémem](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurace služeb](../../../docs/framework/wcf/configuring-services.md)
- [Konfigurace služeb WCF](configuring-services.md)
- [Konfigurace služeb WCF v kódu](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)
