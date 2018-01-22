---
title: '&lt;basicHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: basicHttpBinding Element
ms.assetid: 85cf1a4f-26c2-48c7-bda6-6c960d5d3fb3
caps.latest.revision: "43"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 80494dd0050c7a3a873e6885a8001a55171ffc8e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltbasichttpbindinggt"></a>&lt;basicHttpBinding&gt;
Představuje vazbu, [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] služby můžete použít ke konfiguraci a vystavit koncové body, které jsou schopni komunikovat se na základě ASMX webových služeb a klientů a dalším službám, které odpovídají WS-I Basic Profile 1.1.  
  
 \<system.ServiceModel>  
\<vazby >  
\<basicHttpBinding>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<basicHttpBinding>  
   <binding   
       allowCookies="Boolean"  
       bypassProxyOnLocal="Boolean"  
       closeTimeout="TimeSpan"   
       envelopeVersion="None/Soap11/Soap12"  
       hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
       maxBufferPoolSize="Integer"  
       maxBufferSize="Integer"  
       maxReceivedMessageSize="Integer"  
       messageEncoding="Text/Mtom"  
              name="string"   
       openTimeout="TimeSpan"   
       proxyAddress="URI"  
        receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan"  
              textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
              transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
       useDefaultWebProxy="Boolean"  
       <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">  
           <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"  
                  proxyCredentialType="None/Basic/Digest/Ntlm/Windows"  
                                    realm="string" />  
           <message   
                 algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                            clientCredentialType="UserName/Certificate"/>  
       </security>  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"             maxNameTableCharCount="Integer"                maxStringContentLength="Integer" />  
   </binding>  
</basicHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`allowCookies`|Logická hodnota, která určuje, zda klient přijímá soubory cookie a rozšiřuje je na dalších požadavků. Výchozí hodnota je `false`.<br /><br /> Tuto vlastnost lze použít při používání ASMX webové služby, které používají soubory cookie. Tímto způsobem mohou být jisti, že soubory cookie, kterou vrátil server se automaticky zkopírují do všechny budoucí požadavky pro tuto službu.|  
|`bypassProxyOnLocal`|Logická hodnota, která označuje, zda Nepoužívat proxy server pro místní adresy. Výchozí hodnota je `false`.<br /><br /> Internetových prostředků je místní, pokud má místní adresy. Místní adresa je ten, který je na stejném počítači, místní síti LAN nebo intranetu a identifikuje, syntakticky, absenci tečkou (.) jako identifikátory URI "http://webserver/" a "http://localhost/".<br /><br /> Nastavení tento atribut určuje, zda koncové body nakonfigurované BasicHttpBinding používat proxy server při přístupu k místním prostředkům. Pokud tento atribut je `true`, požadavky k místním prostředkům Internetu Nepoužívat proxy server. Použijte název hostitele (místo localhost), pokud chcete klientům jít přes proxy server při posuzování ke službám ve stejném počítači, když tento atribut je nastaven na `true`.<br /><br /> Když tento atribut je `false`, jsou vytvářeny všechny požadavky Internetu prostřednictvím proxy serveru.|  
|`closeTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`envelopeVersion`|Určuje verzi protokolu SOAP, která se používá pro zprávy zpracovávané touto vazbou. Jediná platná hodnota je Soap11.|  
|`hostnameComparisonMode`|Určuje režim porovnání hostname HTTP použitá k analýze identifikátory URI. Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což naznačuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele. Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, který ignoruje název hostitele se shodují.|  
|`maxBufferPoolSize`|Celočíselná hodnota, která určuje maximální množství paměti přidělené pro použití správcem vyrovnávacích pamětí zpráv, které přijímají zprávy z tohoto kanálu. Výchozí hodnota je 524288 (0x80000) bajtů.<br /><br /> Správci vyrovnávacích minimalizuje náklady na používání vyrovnávací paměti pomocí fondu vyrovnávací paměti. Vyrovnávací paměti se vyžadují zpracování zpráv službou, při které pocházejí z kanálu. Pokud ve fondu vyrovnávací paměti při zpracování zprávy zatížení není dostatek paměti, musí správce vyrovnávací paměť přidělit další paměť z haldy CLR, což zvyšuje režii kolekce paměti. Rozsáhlé přidělení z paměti haldy CLR je jako ukazatel toho, že je příliš malá velikost fondu vyrovnávací paměti a že výkon lze zvýšit pomocí větší přidělení zvýšením limit určený tento atribut.|  
|`maxBufferSize`|Celočíselná hodnota, která určuje maximální velikost v bajtech vyrovnávací paměti, která ukládá zprávy, když jsou zpracovávány pro koncovým bodem nakonfigurovaným s touto vazbou. Výchozí hodnota je 65 536 bajtů.|  
|`maxReceivedMessageSize`|Kladné celé číslo, které definuje maximální velikost zprávy, v bajtech, včetně záhlaví zprávy, která lze přijímat pomocí kanálu nakonfigurovaným s touto vazbou. Odesílatel obdrží chybu protokolu SOAP, pokud zpráva je příliš velké vzhledem k příjemce. Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování. Výchozí hodnota je 65 536 bajtů.|  
|`messageEncoding`|Definuje kodér použitá ke kódování zprávu protokolu SOAP. Platné hodnoty patří:<br /><br /> -Text: Pomocí kodéru text zprávy.<br />-Mtom: Pomocí kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).<br /><br /> Výchozí hodnota je Text. Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.|  
|`name`|Řetězec, který obsahuje název konfigurace vazby. Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu. Má každou vazbu `name` a `namespace` atributů, které společně jednoznačně identifikovat v metadatech služby. Kromě toho je tento název jedinečný mezi vazby stejného typu. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`namespace`|Určuje obor názvů XML vazby. Výchozí hodnota je "http://tempuri.org/Bindings". Má každou vazbu `name` a `namespace` atributů, které společně jednoznačně identifikovat v metadatech služby.|  
|`openTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`proxyAddress`|Identifikátor URI, který obsahuje adresu proxy serveru HTTP. Pokud `useSystemWebProxy` je nastaven na `true`, toto nastavení musí být `null`. Výchozí hodnota je `null`.|  
|`receiveTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:10:00.|  
|`sendTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`textEncoding`|Nastaví znak, nastavení kódování, který se má použít pro vysílání zpráv v vazby. Platné hodnoty patří:<br /><br /> -BigEndianUnicode: Unicode BigEndian kódování.<br />-Unicode: 16bitové kódování.<br />-UTF8: kódování 8bitové<br /><br /> Výchozí hodnota je UTF8. Tento atribut je typu <xref:System.Text.Encoding>.|  
|`transferMode`|Platná <xref:System.ServiceModel.TransferMode> hodnotu, která určuje, zda jsou zprávy do vyrovnávací paměti nebo prostřednictvím datového proudu na požadavek nebo odpověď.|  
|`useDefaultWebProxy`|Logická hodnota, která určuje, zda má být použita automatické konfigurace proxy serveru HTTP systému, pokud je k dispozici. Výchozí hodnota je `true`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|Definuje nastavení zabezpečení pro vazbu. Tento element je typu <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.|  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby. Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<vazby >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Tento prvek obsahuje kolekci standardní a vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 BasicHttpBinding využívá protokol HTTP jako přenosu pro odesílání zpráv SOAP 1.1. Službu můžete použít tuto vazbu ke zveřejnění koncové body, které odpovídají WS-I BP 1.1, jako jsou ty, které využívají klienti ASMX. Podobně, může klient používat BasicHttpBinding komunikovat se službami vystavení koncové body, které odpovídají WS-I BP 1.1, jako je například ASMX webové služby nebo služby, které jsou nakonfigurované BasicHttpBinding.  
  
 Zabezpečení je ve výchozím nastavení vypnuté, ale můžete přidat nastavení atribut režimu [ \<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) podřízený element hodnotu jinou než `None`. "Text" kódování a UTF-8 text zprávy kódování ve výchozím nastavení používá.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití <xref:System.ServiceModel.BasicHttpBinding> , poskytuje HTTP komunikace a maximální vzájemnou funkční spolupráci s první - a second - generation webové služby. Vazba je zadána v konfiguračních souborech pro klienta a služby. Typ vazby je zadán pomocí `binding` atribut `<endpoint>` elementu. Pokud chcete nakonfigurovat základní vazby a některá z jeho nastavení změnit, je nutné definovat Konfigurace vazeb. Koncový bod musí odkazovat Konfigurace vazeb podle názvu pomocí `bindingConfiguration` atribut `<endpoint>` elementu, jak je znázorněno v následujícím kódu konfigurace pro službu.  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="basicHttpBinding"  
             bindingConfiguration="Binding1"   
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <basicHttpBinding>  
        <binding name="Binding1"   
               hostNameComparisonMode="StrongWildcard"   
               receiveTimeout="00:10:00"  
               sendTimeout="00:10:00"  
               openTimeout="00:10:00"  
               closeTimeout="00:10:00"  
               maxReceivedMessageSize="65536"   
               maxBufferSize="65536"   
               maxBufferPoolSize="524288"   
               transferMode="Buffered"   
               messageEncoding="Text"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </basicHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="example"></a>Příklad  
 Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Funkce z předchozího příkladu můžete provést bindingConfiguration odebráním adresa koncového bodu a název frm vazby.  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="basicHttpBinding"  
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <basicHttpBinding>  
        <binding   
               hostNameComparisonMode="StrongWildcard"   
               receiveTimeout="00:10:00"  
               sendTimeout="00:10:00"  
               openTimeout="00:10:00"  
               closeTimeout="00:10:00"  
               maxReceivedMessageSize="65536"   
               maxBufferSize="65536"   
               maxBufferPoolSize="524288"   
               transferMode="Buffered"   
               messageEncoding="Text"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </basicHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)
