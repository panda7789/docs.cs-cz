---
title: Zjednodušená konfigurace
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 13cf8bd46ef3aabb011cb2ddd207963235468662
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967892"
---
# <a name="simplified-configuration"></a>Zjednodušená konfigurace
Konfigurace služby Windows Communication Foundation (WCF) může být složitý úkol. Spousta různých možností, a to není vždy jednoduché určit nastavení, které jsou požadovány. Konfigurační soubory zvýšit flexibilitu služeb WCF, ale také jsou zdroje pro mnoho obtížné najít problémy. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] řeší tyto problémy a poskytuje způsob, jak zmenšit velikost a složitost konfigurace služby.  
  
## <a name="simplified-configuration"></a>Zjednodušená konfigurace  
 V souborech konfigurace služby WCF <`system.serviceModel`> obsahuje oddíl <`service`> – element pro každé služby hostované. <`service`> Kolekce obsahuje element <`endpoint`> elementy, které určují koncových bodů pro každou službu a volitelně také sadu chování služby. <`endpoint`> Elementy zadejte adresy, vazby a kontrakt vystavit koncový bod a volitelně konfigurace vazby a chování koncového bodu. <`system.serviceModel`> Obsahuje také <`behaviors`> element, který vám umožní určit chování služby nebo koncového bodu. Následující příklad ukazuje <`system.serviceModel`> oddílu konfiguračního souboru.  
  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Díky konfigurace služby WCF jednodušší odebráním požadavek <`service`> element. Pokud nepřidáte <`service`> části nebo přidat žádné koncové body v <`service`> části a vaše služba nedefinuje programově žádné koncové body a pak sadu výchozí koncové body jsou automaticky přidány do vaší služby, jeden pro každou Základní adresa služby a pro každou smlouvu implementované vaší služby. V každém z těchto koncových bodů adresu koncového bodu odpovídá základní adresa, vazba se určuje podle schématu základní adresu a kontrakt je implementované vaše služba. Pokud není potřeba zadat všechny koncové body nebo chování služby nebo provést změny nastavení vazby, není potřeba zadat konfigurační soubor služby vůbec. Pokud služba implementuje dva kontrakty a hostitele umožňuje přenosy HTTP i protokol TCP hostitele služby vytvoří čtyři výchozí koncové body, jeden pro každou smlouvu pomocí jednotlivých přenosu. Vytvořit výchozí koncové body hostitele služby musíte vědět, jaké vazby použít. Tato nastavení jsou určené v <`protocolMappings`> části v rámci <`system.serviceModel`> oddílu. <`protocolMappings`> Oddíl obsahuje seznam z namapované na typů vazeb schématy přenosových protokolů. Hostitel služby používá základní adresy do něho předaný k určení použité vazby. V následujícím příkladu <`protocolMappings`> element.  
  
> [!WARNING]
>  Změna výchozí konfigurační prvky, jako je například vazby nebo chování, může mít vliv na služby definované v nižších úrovních hierarchie konfigurace, protože by mohly používat tyto výchozí vazby a chování. Tím, kdo mění výchozí vazby a chování musí mějte na paměti, že tyto změny mohou ovlivnit ostatní služby v hierarchii.  
  
> [!NOTE]
>  Služby hostované v rámci Internetové informační služby (IIS) nebo Windows Process Activation Service (WAS) použít virtuální adresář jako svoje základní adresa.  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 V předchozím příkladu používá koncový bod s základní adresa, která začíná textem "http" schéma <xref:System.ServiceModel.BasicHttpBinding>. Koncový bod s základní adresa, která začíná textem "net.tcp" schéma používá <xref:System.ServiceModel.NetTcpBinding>. Můžete přepsat nastavení v místním souboru App.config nebo Web.config.  
  
 Každý prvek v rámci <`protocolMappings`> části musíte zadat schéma a vazbu. Volitelně můžete zadat `bindingConfiguration` atribut, který určuje konfiguraci vazby v rámci <`bindings`> oddílu konfiguračního souboru. Pokud ne `bindingConfiguration` není zadána, bude použita konfigurace anonymní vytváření vazby typu odpovídající vazby.  
  
 Chování služby se konfigurují pro výchozí koncové body pomocí anonymní <`behavior`> v rámci oddílu <`serviceBehaviors`> oddíly. Žádné nepojmenované <`behavior`> elementů v rámci <`serviceBehaviors`> se používají ke konfiguraci chování služby. Například následující konfigurační soubor umožňuje publikování metadat služby pro všechny služby v rámci hostitele.  
  
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
  
 Chování koncového bodu se konfigurují přes anonymní <`behavior`> v rámci oddílu <`serviceBehaviors`> oddíly.  
  
 Následující příklad je ekvivalentní je na začátku tohoto tématu, který používá zjednodušené konfigurační model konfiguračního souboru.  
  
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
>  Tato funkce se týká pouze konfigurace služby WCF, není konfigurace klienta. Většinu času konfigurace klienta WCF se vygeneruje pomocí nástroje, jako je svcutil.exe nebo přidáním odkazu na službu v sadě Visual Studio. Při ruční konfiguraci klienta WCF je potřeba přidat \<klienta > element konfigurace a určete žádné koncové body, kterou chcete volat.  
  
## <a name="see-also"></a>Viz také:

- [Konfigurace služeb pomocí konfiguračních souborů](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [Konfigurace vazeb pro služby](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [Konfigurace vazeb poskytovaných systémem](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurace služeb](../../../docs/framework/wcf/configuring-services.md)
- [Konfigurace služeb WCF](configuring-services.md)
- [Konfigurace služeb WCF v kódu](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)
