---
title: <reliableSession>
ms.date: 03/30/2017
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
ms.openlocfilehash: 548c4884ecd2f4b9a71fcc9d6647a9e258b183c1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934252"
---
# <a name="reliablesession"></a>\<reliableSession>
Definuje nastavení pro zasílání zpráv WS-Reliable. Když se tento prvek přidá do vlastní vazby, může výsledný kanál podporovat pouze zajištění doručení právě jednou.  
  
 \<system.serviceModel>  
\<> vazeb  
\<customBinding >  
\<> vazby  
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
|acknowledgementInterval|A <xref:System.TimeSpan> který obsahuje maximální časový interval, po který bude kanál čekat na odeslání potvrzení pro zprávy přijaté do tohoto okamžiku. Výchozí hodnota je 00:00:0,2.|  
|flowControlEnabled|Logická hodnota, která označuje, zda je aktivováno pokročilé řízení toku, což je implementace řízení toku pro zasílání zpráv WS-Reliable specifická pro společnost Microsoft. Výchozí hodnota je `true`.|  
|inactivityTimeout|A <xref:System.TimeSpan> určuje maximální dobu, po kterou kanál povolí druhé straně komunikace, aby před chybou kanálu neodesílala žádné zprávy. Výchozí hodnota je 00:10:00.<br /><br /> Aktivita na kanálu je definována jako příjem zpráv aplikace nebo infrastruktury. Tato vlastnost určuje maximální dobu, po kterou může zůstat neaktivní relace aktivní. Pokud delší doba projde bez aktivity, je relace přerušená infrastrukturou a chybami kanálu. **Poznámka:**  Není nutné, aby aplikace pravidelně odesílala zprávy pro zachování připojení.|  
|maxPendingChannels|Celé číslo, které určuje maximální počet kanálů, které mohou čekat na přijetí naslouchacího procesu. Tato hodnota by měla být mezi 1 a 16384 včetně. Výchozí hodnota je 4.<br /><br /> Kanály čekají na vyřízení, když čekají na přijetí. Po dosažení tohoto limitu se nevytvoří žádné kanály. Místo toho jsou vloženy do režimu čekání, dokud tento počet nezmizí (přijetím nevyřízených kanálů). Toto je omezení podle továrny.<br /><br /> Když je dosaženo prahové hodnoty a Vzdálená aplikace se pokusí vytvořit novou spolehlivou relaci, je žádost zamítnuta a operace otevření, která se zobrazí po zobrazení této chyby. Toto omezení se nevztahuje na počet nevyřízených odchozích kanálů.|  
|maxRetryCount|Celé číslo, které určuje maximální počet pokusů, kolikrát se spolehlivý kanál pokusí znovu přenést zprávu, pro kterou neobdržel potvrzení, voláním Send na svém základním kanálu.<br /><br /> Tato hodnota by měla být větší než nula. Výchozí hodnota je 8.<br /><br /> Tato hodnota by měla být celé číslo větší než nula. Pokud po posledním opětovném přenosu neobdrží potvrzení, dojde k chybám kanálu.<br /><br /> Zpráva se považuje za přenesenou, pokud příjemce vaši dodávku od příjemce potvrdí.<br /><br /> Pokud se u zprávy, která byla přenesena do určité doby, nedostalo potvrzení, infrastruktura tuto zprávu automaticky znovu odešle. Infrastruktura se pokusí zprávu znovu odeslat maximálně v počtu pokusů určených touto vlastností. Pokud po posledním opětovném přenosu neobdrží potvrzení, dojde k chybám kanálu.<br /><br /> Infrastruktura používá exponenciální back-vypnutý algoritmus k určení, kdy se má znovu přenést na základě vypočtené průměrné doby odezvy. Čas zpočátku začíná 1 sekundou před opakovaným přenosem a zdvojnásobuje se při každém pokusu, což má za následek přibližně 8,5 minut předávání mezi prvním pokusem o přenos a posledním pokusem o opakování přenosu. Čas při prvním pokusu o opakování přenosu se upraví podle vypočtené doby odezvy a výsledným roztažením času se tyto pokusy budou měnit. To umožňuje, aby se čas opětovného přenosu dynamicky přizpůsobil různým podmínkám sítě.|  
|maxTransferWindowSize|Celé číslo, které určuje maximální velikost vyrovnávací paměti. Platné hodnoty jsou od 1 do 4096 včetně.<br /><br /> V klientovi tento atribut definuje maximální velikost vyrovnávací paměti používané spolehlivým kanálem pro uchovávání zpráv, které příjemce ještě nepřijal. Jednotka kvóty je zpráva. Pokud je vyrovnávací paměť plná, zablokují se další operace odeslání.<br /><br /> Tento atribut na přijímači definuje maximální velikost vyrovnávací paměti, kterou kanál používá k ukládání příchozích zpráv, které ještě nebyly odeslány do aplikace. Pokud je vyrovnávací paměť plná, může příjemce tiše vyřadit další zprávy a vyžadovat opětovné odeslání klientem.|  
|ordered|Logická hodnota určující, zda mají být zprávy zaručeny pro doručení v pořadí, v jakém byly odeslány. Pokud je `false`toto nastavení, zprávy mohou být doručeny mimo pořadí. Výchozí hodnota je `true`.|  
|reliableMessagingVersion|Platná hodnota z <xref:System.ServiceModel.ReliableMessagingVersion> , která určuje verzi WS-ReliableMessaging, která se má použít.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> vazby](../../../misc/binding.md)|Definuje všechny schopnosti vazby vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Spolehlivé relace poskytují funkce pro spolehlivé zasílání zpráv a relací. Spolehlivé zasílání zpráv zopakuje komunikaci při selhání a umožňuje zasílat záruky doručování, jako je doručení zpráv v daném pořadí. Relace uchovávají stav pro klienty mezi voláními. Tento prvek také volitelně poskytuje objednané doručování zpráv. Tato implementovaná relace může vzájemně přenášet zprostředkovatele SOAP a přenosu.  
  
 Každý prvek vazby představuje krok zpracování při posílání nebo přijímání zpráv. V době běhu vytvoří vazby prvky vytváření kanálů a naslouchací procesy, které jsou nezbytné pro vytváření odchozích a příchozích zásobníků kanálů potřebných pro odesílání a příjem zpráv. `reliableSession` Poskytuje volitelnou vrstvu v zásobníku, která může navázat spolehlivou relaci mezi koncovými body a nakonfigurovat chování této relace.  
  
 Další informace najdete v tématu [spolehlivé relace](../../../wcf/feature-details/reliable-sessions.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat vlastní vazbu s různými prvky transportu a kódování zpráv, zejména povolením spolehlivých relací, které udržují stav klienta a určují záruku doručení v daném pořadí. Tato funkce je nakonfigurovaná v konfiguračních souborech aplikací pro klienta a službu. V příkladu se zobrazuje konfigurace služby.  
  
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
- [Spolehlivé relace](../../../wcf/feature-details/reliable-sessions.md)
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
