---
title: '&lt;msmqIntegrationBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: msmqIntegrationBinding Element
ms.assetid: edf277f3-e3bf-4ed8-9f55-83b5788430a7
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0715952077db755386a0381f68ccc6e33705a031
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltmsmqintegrationbindinggt"></a>&lt;msmqIntegrationBinding&gt;
Definuje vazbu, která poskytuje služby Řízení front podporu tím, že směrování zpráv prostřednictvím služby MSMQ.  
  
 \<system.ServiceModel>  
\<vazby >  
msmqIntegrationBinding  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<msmqIntegrationBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       customDeadLetterQueue="Uri"  
       deadLetterQueue="Uri"  
       durable="Boolean"  
       exactlyOnce="Boolean"   
       maxReceivedMessageSize"Integer"  
       maxRetryCycles="Integer"   
       name="string"   
       openTimeout="TimeSpan"        receiveContextEnabled="Boolean"  
       receiveErrorHandling="Drop/Fault/Move/Reject"  
       receiveTimeout="TimeSpan"   
       receiveRetryCount="Integer"  
       retryCycleDelay="TimeSpan"    
       sendTimeout="TimeSpan"   
       serializationFormat="XML/Binary/ActiveX/ByteArray/Stream">  
       timeToLive="TimeSpan"    
       useMsmqTracing="Boolean  
       useSourceJournal="Boolean"  
   </binding>  
</msmqIntegrationBinding>   
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Intervalu|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|customDeadLetterQueue|Identifikátor URI, která obsahuje umístění fronty nedoručených zpráv jednotlivých aplikací, kde jsou umístěny zprávy, jejichž platnost vypršela nebo které selhaly přenos nebo doručení.<br /><br /> Fronta nedoručených zpráv je do fronty v správce front odeslání žádosti o zprávy s vypršenou platností, které se nepodařilo doručit.<br /><br /> Identifikátor URI, která je zadána <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> musí používat schéma net.msmq.|  
|deadLetterQueue|A <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>.value zadání typu frontu nedoručených zpráv, pokud chcete použít, pokud existuje<br /><br /> Frontu nedoručených zpráv je umístění, že se bude přenášet zprávy, které se nepodařilo doručit do aplikace.<br /><br /> Pro zprávy, které vyžadují Kontrola ExactlyOnce (tj, `exactlyOnce` je atribut nastaven na `true`), použije se výchozí hodnota tohoto atributu do fronty transakcí nedoručených zpráv systémové služby MSMQ.<br /><br /> Pro zprávy, které vyžadují žádné záruky, tento atribut výchozí `null`.|  
|trvanlivý|Logická hodnota, která určuje, zda je zpráva trvalé nebo přechodné ve frontě. Trvanlivý zprávu odolává fronty manager havárie, při volatile zpráva neexistuje. Volatile zprávy jsou užitečné, když aplikace vyžadují nižší latenci a tolerovat příležitostně ztrátě zpráv. Pokud `exactlyOnce` je atribut nastaven na `true`, zprávy musí být odolné. Výchozí hodnota je `true`.|  
|exactlyOnce|Logická hodnota, která určuje, zda je každá zpráva doručena pouze jednou. Odesílatel pak budou informováni o selhání doručení. Když `durable` je `false`, tento atribut je ignorován a přenosu zpráv bez záruky doručení. Výchozí hodnota je `true`. Další informace naleznete v tématu <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.|  
|MaxReceivedMessageSize|Kladné celé číslo, který definuje maximální velikost zprávy, v bajtech, včetně hlavičky, které je zpracovávané touto vazbou. Odesílatel zprávy překročení tohoto limitu obdrží chybu protokolu SOAP. Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování. Výchozí hodnota je 65536. Vázaný na velikost zprávy se má omezit riziko napadení útok na dostupnost služby (DoS).|  
|maxRetryCycles|Celé číslo určující počet cyklů opakování používané funkce rozpoznávání poison zprávy. Zprávu stane nezpracovatelná zpráva, pokud se nezdaří všechny pokusy o doručení všech cyklů. Výchozí hodnota je 2. Další informace naleznete v tématu <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.|  
|name|Řetězec, který obsahuje název konfigurace vazby. Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|receiveErrorHandling|A <xref:System.ServiceModel.ReceiveErrorHandling> hodnotu, která určuje způsob zpracování zprávy poison a nondispatchable.|  
|receiveRetryCount|Celé číslo, které určuje maximální počet opakování, okamžitou správce front mají pokusit o, pokud selže přenos zpráv z fronty aplikace do aplikace.<br /><br /> Pokud je dosaženo maximálního počtu pokusů o doručení a zpráva není získat přístup k aplikaci, zpráva se pak odešlou do fronty pro opakované dodání opakovat později. Množství času, než se přenáší zprávy zpět do fronty odesílání řídí `retryCycleDelay`. Pokud opakování cyklů reach `maxRetryCycles` hodnotu, pak je zpráva odeslána do fronty zpráv poison buď nebo záporné potvrzení budou odeslána zpět do odesílatele.|  
|receiveTimeout|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:10:00.|  
|receiveContextEnabled|Logická hodnota, která určuje, pokud obdrží kontext pro zpracování zpráv do front je povoleno. Pokud je nastavena v `true`, služby můžete "prohlížet" zprávu ve frontě zahájíte zpracování, a když se něco pokazí a je vyvolána výjimka, zůstane ve frontě. Služby lze také "zamknout" zprávy, aby bylo možné opakovat zpracování později v čase. ReceiveContext poskytuje mechanismus pro "dokončení" zprávu po zpracování, může být odebrán z fronty. Zprávy jsou už je pro čtení a znovu zapsaný na fronty přes síť a jednotlivé zprávy nejsou skákání napříč instancemi jinou službu během zpracování.|  
|retryCycleDelay|Hodnota časového rozpětí, který určuje prodlevu mezi opakování cyklů při pokusu o doručení zprávy, která nelze doručit okamžitě. Hodnota definuje jen minimální doba čekání, protože skutečná čekací dobu může být delší. Výchozí hodnota je 00:30:00. Další informace naleznete v tématu <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.|  
|sendTimeout|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|serializationFormat|Definuje formát použitý pro serializaci textu zprávy. Tento atribut je typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat>.|  
|timeToLive|Hodnota časového rozpětí, která určuje, jak dlouho zprávy jsou platné předtím, než se platnost a zařazena do fronty nedoručených zpráv. Výchozí hodnota je 1.00:00:00.<br /><br /> Tento atribut nastavený zajistit, že zprávy dobou nepřestali být zastaralé dříve, než je přijímací aplikace. Zprávy ve frontě, který není přijímající aplikace v rámci zadaného časového intervalu říká, že je mít skončenou platnost. Zprávy s vypršenou platností se odesílají do speciální fronty názvem fronty nedoručených zpráv. Umístění fronty nedoručených zpráv nastavena `DeadLetterQueue` atribut, nebo odpovídající výchozí, aby na základě záruky.|  
|useMsmqTracing|Logická hodnota, která určuje, zda zprávy zpracovávané touto vazbou má trasovat. Výchozí hodnota je `false`. Pokud je povoleno sledování, sestava zprávy se vytváří a odesílají do fronty hlášení pokaždé, když opustí zpráva nebo zpráva dorazí na počítači služby Řízení front zpráv.|  
|useSourceJournal|Logická hodnota, která určuje kopie zprávy zpracovávané touto vazbou by měl být uložen v deníku zdroje. Výchozí hodnota je `false`.<br /><br /> Ve frontě aplikací, které chcete zachovat záznam zprávy, které mají zbývající počítače fronty odesílaných zpráv můžete zkopírovat do deníku fronty zpráv. Jakmile zprávu opustí fronty odesílaných zpráv a je obdržena potvrzení, že zpráva byla přijata v cílovém počítači, je udržováno kopie zprávy ve frontě deníku odesílající počítač systému.|  
  
## <a name="serializationformat-attribute"></a>{serializationFormat} Atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|XML|Formát XML|  
|binární|Binární formát|  
|ActiveX|Formát ActiveX|  
|ByteArray|Serializuje objekt, který má pole bajtů.|  
|Stream|Formátovaný text jako datový proud|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-msmqintegrationbinding.md)|Definuje nastavení zabezpečení pro vazbu. Tento element je typu <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<vazby >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Tento prvek obsahuje kolekci standardní a vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element vazby lze umožnit aplikacím zprávy odesílat a přijímat zprávy z existující aplikace služby MSMQ, které používají COM, nativních rozhraní API MSMQ nebo typy definované v systému Windows Communication Foundation (WCF) <xref:System.Messaging?displayProperty=nameWithType> oboru názvů můžete můžete použít tento element konfigurace k určení způsoby, jak vyřešit fronty přenosu záruky, zda musí spolehlivě ukládat zprávy a jak by měla chránit a ověření zprávy. Další informace najdete v tématu [postup: Exchange zpráv pomocí koncových bodů WCF a aplikace služby Řízení front zpráv](../../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md).  
  
## <a name="example"></a>Příklad  
  
```xml  
<configuration>  
<system.ServiceModel>  
    <bindings>  
       <msmqIntegrationBinding>  
           <binding   
                    closeTimeout="00:00:10"   
                    openTimeout="00:00:20"   
                    receiveTimeout="00:00:30"   
                    sendTimeout="00:00:40"   
                    deadLetterQueue="net.msmq://localhost/blah"   
                    durable="true"   
                    exactlyOnce="true"   
                    maxReceivedMessageSize="1000"   
                    maxImmediateRetries="11"   
                    maxRetryCycles="12"  
                    poisonMessageHandling="Disabled"   
                    rejectAfterLastRetry="false"   
                    retryCycleDelay="00:05:55"   
                    timeToLive="00:11:11"   
                    useSourceJournal="true"   
                    useMsmqTracing="true"   
                    serializationFormat="Binary">  
                    <security mode="None" />  
           </binding>  
       </msmqIntegrationBinding  
   </bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [Fronty ve WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
