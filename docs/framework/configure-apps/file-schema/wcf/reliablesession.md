---
title: <reliableSession>
ms.date: 03/30/2017
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
ms.openlocfilehash: add69cfe1503c5ab78640cebc7c241a1f93b364f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283670"
---
# <a name="reliablesession"></a>\<reliableSession>
Definuje nastavení pro zasílání zpráv WS-Reliable. Pokud tento prvek přidán na vlastní vazby, výsledný kanálu může podporovat přesně-jednou záruky doručení.  
  
 \<system.serviceModel>  
\<vazby >  
\<customBinding>  
\<Vytvoření vazby >  
\<reliableSession>  
  
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
|acknowledgementInterval|A <xref:System.TimeSpan> , která obsahuje maximální časový interval, bude kanál čekat na odeslání potvrzení zpráv až k danému bodu. Výchozí hodnota je 00:00:0.2.|  
|flowControlEnabled|Logická hodnota, která určuje, zda je aktivováno pokročilé řízení toku, specifické pro společnost Microsoft provádění řízení toku pro posílání WS-Reliable. Výchozí hodnota je `true`.|  
|InactivityTimeout|A <xref:System.TimeSpan> , která určuje maximální dobu, po kterou se bude kanál povolí druhé strany komunikace nechcete poslat žádnou zprávu před přerušením kanálu. Výchozí hodnota je 00:10:00.<br /><br /> Aktivita v kanálu je definován jako přijímající aplikace nebo zprávy infrastruktury. Tato vlastnost určuje maximální množství času, aby neaktivní relace udrželo aktivní. Pokud se žádná aktivita úspěšně projde delší dobu, relace přerušil infrastruktury a chyb kanálu. **Poznámka:**  Není nutné pro aplikaci pravidelně odesílat zprávy, aby se připojení udrželo aktivní.|  
|maxPendingChannels|Celé číslo určující maximální počet kanálů, které mohou čekat na straně posluchače na přijetí. Tato hodnota by měla být mezi 1 do 16384. Výchozí hodnota je 4.<br /><br /> Kanály představují čekající při čekání na přijetí. Po dosažení tohoto limitu jsou vytvořeny žádné kanály. Místo toho jsou umístěny do čekající režimu až tento počet přejde (tak, že přijímá čekajících kanálů). Jedná se o limit za factory.<br /><br /> Když je dosaženo prahové hodnoty a vzdálené aplikace se pokusí vytvořit nová stabilní relaci, požadavek se zamítne a operace otevření, která byla příčinou této chyby. Toto omezení se nevztahuje na počet čekajících odchozí kanály.|  
|maxRetryCount|Celé číslo, které určuje maximální počet pokusů o bezpečný kanál pokusí znovu poslat zprávu, že neobdržel potvrzení, voláním Poslat na svém základním kanálu.<br /><br /> Tato hodnota by měla být větší než nula. Výchozí hodnota je 8.<br /><br /> Tato hodnota by měla být celé číslo větší než nula. Pokud po poslední přenosu, k poruchám kanál neobdrží potvrzení.<br /><br /> Zpráva se považuje za které se mají přenést, pokud jeho doručení na straně příjemce byla potvrzena příjemce.<br /><br /> Pokud během určité doby pro zprávu, která bylo přeneseno nebyl přijat potvrzení, infrastruktury automaticky odešle zprávu. Infrastrukturu se pokusí znovu poslat zprávu pro maximální počet, kolikrát této vlastnosti. Pokud po poslední přenosu, k poruchám kanál neobdrží potvrzení.<br /><br /> Infrastruktura používá exponenciální regresní algoritmus, který určuje, kdy k opětovnému přenosu, podle vypočítaná průměrná doba odezvy. Čas začátku začíná na 1 sekundu před opakovaný přenos zpráv a zpoždění s všechny pokusy o jeho, což vede k přibližně 8,5 minut předávání mezi první pokus o přenos a poslední pokus o opakovaný přenos zdvojnásobení. Čas potřebný pro první pokus o opakovaný přenos zpráv je upraven podle počítané dobu odezvy a výsledné stretch času, které využívají tyto pokusy se liší odpovídajícím způsobem. To umožňuje dynamicky adaptovat na různých síťových podmínkách čas opakovaný přenos zpráv.|  
|maxTransferWindowSize|Celé číslo, které určuje maximální velikost vyrovnávací paměti. Platné hodnoty jsou od 1 do 4096 (včetně).<br /><br /> Na straně klienta tento atribut definuje maximální velikost vyrovnávací paměti používané stabilní kanál pro uložení zpráv ještě nebyla potvrzena příjemce. Jednotka kvóty je zpráva. Pokud vyrovnávací paměť je plná, zablokuje se další operace odeslání.<br /><br /> Na straně příjmu tento atribut definuje maximální velikost vyrovnávací paměti používané kanál k ukládání příchozích zpráv do aplikace ještě nebyla odeslána. Pokud vyrovnávací paměť je plná, další zprávy zařazují tiše příjemce a odesílaných klientem.|  
|ordered|Logická hodnota, která určuje, zda je zaručená zprávy doručeny v pořadí, v jakém byly odeslány. Pokud je toto nastavení `false`, můžete k doručování zpráv mimo pořadí. Výchozí hodnota je `true`.|  
|reliableMessagingVersion|Platná hodnota z <xref:System.ServiceModel.ReliableMessagingVersion> , který určuje verzi WS-ReliableMessaging, který se má použít.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádná  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vázání pro vlastní vazbu.|  
  
## <a name="remarks"></a>Poznámky  
 Spolehlivé relace poskytují funkce pro spolehlivé zasílání zpráv a relací. Spolehlivé zasílání zpráv pokusí znovu navázat komunikaci s selhání a umožňuje záruky doručení, jako je například v pořadí doručení zpráv zadání. Relace uchování stavu pro klienty mezi voláními. Tento element poskytuje také v případě potřeby doručování objednané zprávy. Tato implementované relace můžete různé zprostředkovatele protokolu SOAP a přenosu.  
  
 Každý prvek vazby představuje krok zpracování při odesílání nebo přijímání zpráv. Za běhu elementy vazby vytvářet objekty pro vytváření kanálů a naslouchacích procesů, které jsou potřebné k vývoji odchozí a příchozí kanál zásobníky potřebné pro odesílání a příjem zpráv. `reliableSession` Poskytuje volitelný vrstvy v zásobníku, který můžete vytvořit stabilní relaci mezi koncovými body a konfigurovat chování této relace.  
  
 Další informace najdete v tématu [spolehlivé relace](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat vlastní vazby s různými přenosu a zpráva kódování prvků, zejména povolení spolehlivé relace, která udržuje stavu klienta a určuje záruky doručení v daném pořadí. Tato funkce je nakonfigurován v konfiguračních souborech aplikace pro klienta a služby. Zobrazit příklad konfigurace služby.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc -->
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
          <textMessageEncoding messageVersion="Soap12WSAddressing10"
                               writeEncoding="utf-8" />
          <httpTransport authenticationScheme="Anonymous"
                         bypassProxyOnLocal="false"
                         hostNameComparisonMode="StrongWildcard"
                         proxyAuthenticationScheme="Anonymous"
                         realm=""
                         useDefaultWebProxy="true" />
        </binding>
      </customBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.ReliableSessionElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
- [Spolehlivé relace](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
