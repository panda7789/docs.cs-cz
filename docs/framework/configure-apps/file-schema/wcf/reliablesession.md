---
title: '&lt;reliableSession&gt;'
ms.date: 03/30/2017
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
ms.openlocfilehash: 6b8049e2c493a652405a93eed68f05438819aecb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751438"
---
# <a name="ltreliablesessiongt"></a>&lt;reliableSession&gt;
Definuje nastavení WS-spolehlivé zasílání zpráv. Pokud tento element je přidat do vlastní vazby, výsledná kanál může podporovat přesně-jednou záruky doručení.  
  
 \<system.serviceModel>  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<reliableSession >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<reliableSession acknowledgementInterval="TimeSpan"  
        flowControlEnabled="Boolean"   
    inactivityTimeout="TimeSpan"  
    maxPendingChannels="Integer"  
    maxRetryCount="Integer"   
        maxTransferWindowSize="Integer"  
    reliableMessagingVersion="Default/WSReliableMessagingFebruary2005/WSReliableMessaging11"  
    ordered="Boolean" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|AcknowledgementInterval|A <xref:System.TimeSpan> obsahující maximální časový interval kanál se bude čekat na posílá potvrzení zprávy přijaté až tento bod. Výchozí hodnota je 00:00:0.2.|  
|FlowControlEnabled|Logická hodnota, která určuje, zda je aktivován řízení toku na Upřesnit, specifické pro společnost Microsoft implementace toku řízení pro WS-spolehlivé zasílání zpráv. Výchozí hodnota je `true`.|  
|InactivityTimeout|A <xref:System.TimeSpan> , který určuje maximální dobu, po který se bude kanál povolit druhou stranou komunikace posílat žádné zprávy před přerušením kanálu. Výchozí hodnota je 00:10:00.<br /><br /> Aktivity na kanál, který je definován jako přijímající aplikace nebo infrastruktury zprávy. Tato vlastnost určuje maximální množství času, které k zachování neaktivní relace připojení. Pokud se žádná aktivita úspěšně projde delší dobu, relace se přerušil infrastruktury a chyb kanálu. **Poznámka:** není nutné pro aplikaci pravidelného zasílání zpráv pro zachování připojení připojení.|  
|MaxPendingChannels|Celé číslo, které určuje maximální počet kanálů, které můžete čekat na naslouchací proces třeba přijmout. Tato hodnota by měla být mezi 1 na 16384. Výchozí hodnota je 4.<br /><br /> Kanály jsou čekající na vyřízení, když jsou čekání třeba přijmout. Po dosažení tohoto limitu se vytvoří žádné kanály. Místo toho jsou umístěny do čekající na vyřízení režimu dokud číslo dosáhne (přijetím čekající na vyřízení kanály). To je limit na vytváření.<br /><br /> Když je dosaženo prahové hodnoty a vzdálené aplikace pokusí o vytvoření nové spolehlivé relace, požadavek se odmítne a otevřete operaci, která se zobrazí výzva této chyby. Toto omezení se nevztahuje na počet čekajících odchozí kanály.|  
|MaxRetryCount|Celé číslo, které určuje maximální počet nezdařených pokusů o spolehlivé kanál se pokusí znovu pošlou zprávu, že neobdržel potvrzení, voláním odeslat na jeho základní kanálu.<br /><br /> Tato hodnota by měla být větší než nula. Výchozí hodnota je 8.<br /><br /> Tato hodnota by měla být celé číslo větší než nula. Není-li potvrzení přijata po poslední opakování přenosu, chyb kanálu.<br /><br /> Zpráva považuje za které se mají přenést, pokud jeho doručení na příjemce má byla potvrzena příjemce.<br /><br /> Pokud potvrzení nebyl přijat do určité doby pro zprávu, že bylo přeneseno, infrastrukturu automaticky odešle zprávu. Infrastruktury se pokusí znovu odeslat zprávu pro maximálně počet této vlastnosti. Není-li potvrzení přijata po poslední opakování přenosu, chyb kanálu.<br /><br /> Infrastruktury používá nepodporovaný algoritmus exponenciální back vypnout k určení, kdy se mají přenést, znovu podle počítaný průměrný čas odezvy. Čas začíná původně na 1 sekundu před opakování přenosu a zvýší zpoždění s všechny pokusy, což vede k přibližně šířka 8,5 minut předávání mezi první pokus o přenos a poslední pokus o opakování přenosu. Čas první pokus o opakování přenosu je upravena podle počítané času jejich návratu a výsledný stretch dobu trvat těmito pokusy se liší podle toho. To umožňuje dynamicky adaptovat podle aktuální na různých síťových podmínkách doba opakování přenosu.|  
|MaxTransferWindowSize|Celé číslo, které určuje maximální velikost vyrovnávací paměti. Platné hodnoty jsou od 1 do 4096 (včetně).<br /><br /> Na klientovi tento atribut definuje maximální velikost vyrovnávací paměti používané spolehlivé kanál pro uložení ještě nebyla potvrzena příjemce zprávy. Jednotka kvóty je zpráva. Pokud vyrovnávací paměť je plná, jsou zablokované další operace ODESÍLÁNÍ.<br /><br /> Na příjemce tento atribut definuje maximální velikost vyrovnávací paměti používá kanál k ukládání příchozích zpráv ještě odeslat do aplikace. Pokud vyrovnávací paměť je plná, další zprávy bezobslužně zahozených příjemce a odesílaných klientem.|  
|ordered|Logická hodnota, která určuje, zda jsou zprávy zaručené doručení v pořadí, ve kterém byly odeslány. Pokud toto nastavení je `false`, můžete k doručování zpráv mimo pořadí. Výchozí hodnota je `true`.|  
|ReliableMessagingVersion|Platná hodnota z <xref:System.ServiceModel.ReliableMessagingVersion> , určuje verzi protokolu WS-ReliableMessaging, který se má použít.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vazba >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vazba vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Spolehlivé relace poskytují funkce pro spolehlivé zasílání zpráv a relace. Spolehlivé zasílání zpráv opakování komunikace při selhání a umožňuje záruky doručení, jako je například v daném pořadí doručení zpráv, které mají být zadán. Relace uchování stavu pro klienty mezi volání. Tento element také volitelně poskytuje doručení seřazené zpráv. Tuto relaci implementovaná můžete křížová zprostředkovatele protokolu SOAP a přenosu.  
  
 Každý prvek vazby představuje krok zpracování při odesílání nebo přijímání zprávy. Prvky vazeb v době běhu vytvořit kanál továrny a naslouchací procesy, které jsou nezbytné k sestavení odchozí a příchozí kanál zásobníky potřeba odesílat a přijímat zprávy. `reliableSession` Poskytuje volitelné úroveň v zásobníku, která můžete vytvořit stabilní relaci mezi koncovými body a nakonfigurovat chování tuto relaci.  
  
 Další informace najdete v tématu [spolehlivé relace](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat vlastní vazby s různými přenosu a zprávu kódování elementy, zejména povolení spolehlivé relace, která udržuje stavu klienta a určuje záruky doručení v daném pořadí. Tato funkce je nakonfigurována v konfiguračních souborech aplikace pro klienta a služby. Příklad zobrazení konfiguraci služby.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->  
        <!-- specify customBinding binding and a binding configuration to use -->  
        <endpoint address=""  
                  binding="customBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->  
    <bindings>  
      <customBinding>  
        <binding name="Binding1">  
          <reliableSession />  
          <security authenticationMode="SecureConversation"  
                     requireSecurityContextCancellation="true">  
          </security>  
          <compositeDuplex />  
          <oneWay />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8" />  
          <httpTransport authenticationScheme="Anonymous" bypassProxyOnLocal="false"  
                        hostNameComparisonMode="StrongWildcard"   
                        proxyAuthenticationScheme="Anonymous" realm=""   
                        useDefaultWebProxy="true" />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ReliableSessionElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>  
 [Spolehlivé relace](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
