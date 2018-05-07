---
title: Zjednodušená konfigurace
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: a07ab26b19004df97f4ac65f711b03fc6a6ba445
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="simplified-configuration"></a>Zjednodušená konfigurace
Konfigurace služby Windows Communication Foundation (WCF) může být složité úlohy. Existuje mnoho různých možností a není vždy snadno určit nastavení, které jsou vyžadovány. Při konfigurační soubory zvýšit flexibilitu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby, také se zdroji pro mnoho vyhledání problémů. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] řeší tyto problémy a poskytuje způsob, jak snížit velikost a složitost konfigurace služby.  
  
## <a name="simplified-configuration"></a>Zjednodušená konfigurace  
 V [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby konfigurační soubory, <`system.serviceModel`> obsahuje <`service`> element pro každou službu hostuje. <`service`> Kolekce obsahuje element <`endpoint`> elementy, které určují koncové body vystavený pro každou službu a volitelně sadu chování služby. <`endpoint`> Elementy zadejte adresy, vazby a kontraktu viditelné v koncovém bodě a volitelně Konfigurace vazeb a chování koncový bod. <`system.serviceModel`> Obsahuje také <`behaviors`> elementu, který umožňuje zadat chování služba nebo koncový bod. Následující příklad ukazuje <`system.serviceModel`> oddílu konfiguračního souboru.  
  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Umožňuje konfiguraci [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby jednodušší odebráním požadavek <`service`> elementu. Pokud nepřidáte <`service`> části nebo přidat žádné koncové body v <`service`> části a služby nedefinuje prostřednictvím kódu programu žádné koncové body a pak sadu výchozí koncové body se automaticky přidají do vaší služby, jeden pro každou Základní adresa služby a pro každou smlouvu implementované služby. V každé z těchto koncových bodů adresa koncového bodu odpovídá bázové adresy, vazby je dáno schéma základní adresa a kontrakt je implementované vaše služba. Pokud není potřeba žádné koncové body nebo chování služby a provedli změny nastavení vazby, není potřeba zadat konfigurační soubor služby vůbec. Pokud služba implementuje dva kontrakty a hostitele povolí přenosy HTTP a TCP hostitele služby vytvoří čtyři výchozí koncové body, jeden pro každou smlouvu použití každé přenosu. Chcete-li vytvořit výchozí koncové body hostitele služby musí znát které vazby použít. Tato nastavení jsou určené v <`protocolMappings`> části v rámci <`system.serviceModel`> části. <`protocolMappings`> Část obsahuje seznam přenosu protokolu schémata namapované na vazby typy. Hostitel služby používá základní adresy do ní předán k určení které vazby použít. Následující příklad používá <`protocolMappings`> elementu.  
  
> [!WARNING]
>  Změna výchozí konfigurační prvky, jako je například vazby nebo chování, může ovlivnit služby definované v nižších úrovních hierarchie konfigurace, protože by mohly používat tyto výchozí vazby a chování. Proto, kdo změní výchozí vazby a chování je potřeba vědět, že tyto změny mohou ovlivnit jiných služeb v hierarchii.  
  
> [!NOTE]
>  Služby hostované v rámci Internetové informační služby (IIS) nebo služby Aktivace procesů systému Windows (WAS) jako jejich základní adresa se použije virtuální adresář.  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 V předchozím příkladu používá koncový bod s základní adresa, který začíná na "http" schématu <xref:System.ServiceModel.BasicHttpBinding>. Koncový bod s základní adresa, který začíná na "net.tcp" schématu používá <xref:System.ServiceModel.NetTcpBinding>. Můžete přepsat nastavení v místním souboru App.config nebo Web.config.  
  
 Každý prvek v rámci <`protocolMappings`> části zadejte schéma a vazbu. Volitelně můžete zadat `bindingConfiguration` atribut, který určuje vazby konfigurace v rámci <`bindings`> oddílu konfiguračního souboru. Pokud žádné `bindingConfiguration` je zadána, bude použita konfigurace anonymní vazba typu odpovídající vazby.  
  
 Chování služby jsou nakonfigurovány pro jsou výchozí koncové body pomocí anonymní <`behavior`> částech v rámci <`serviceBehaviors`> oddíly. Všechny nepojmenované <`behavior`> elementů v rámci <`serviceBehaviors`> se používají ke konfiguraci chování služby. Například následující konfigurační soubor umožňuje publikování metadat služby pro všechny služby v rámci hostitele.  
  
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
  
 Koncový bod chování se konfigurují pomocí anonymní <`behavior`> částech v rámci <`serviceBehaviors`> oddíly.  
  
 Následující příklad je ekvivalentní jeden na začátku tohoto tématu, která používá zjednodušené konfigurační model konfiguračního souboru.  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="false"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <bindings>  
       <basicHttpBinding>  
          <binding maxBufferSize="100"  
                   maxReceiveBufferSize="100" />  
       </basicHttpBinding>  
    </bindings>    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->  
    <!-- The service behavior with name="" will be picked up by the service -->  
    <protocolMapping>  
      <add scheme="http"     binding="basicHttpBinding" / </protocolMapping>  
  </system.serviceModel>  
```  
  
> [!IMPORTANT]
>  Tato funkce se týká pouze konfigurace služby WCF, není konfigurace klienta. Většina dobu konfigurace klienta WCF se budou generovat pomocí nástroje, jako je svcutil.exe nebo přidání odkazu na službu ze sady Visual Studio. Pokud ručně nakonfigurujete klienta WCF budete muset přidat \<klienta > element ke konfiguraci a zadejte žádné koncové body, které chcete volat.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace služeb pomocí konfiguračních souborů](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [Konfigurace vazeb pro služby](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurace služeb](../../../docs/framework/wcf/configuring-services.md)  
 [Konfigurace aplikací pro Windows Communication Foundation](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 [Konfigurace služeb WCF v kódu](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)
