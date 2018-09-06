---
title: '&lt;basicHttpContextBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 39b16b82-4ec6-4eff-8031-67e026870961
ms.openlocfilehash: 6a53251f9c5bc828fde1e2cc21cc9d06c477f1d6
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43803441"
---
# <a name="ltbasichttpcontextbindinggt"></a>&lt;basicHttpContextBinding&gt;
Určení vazby, která poskytuje kontext pro <xref:System.ServiceModel.BasicHttpBinding> jenž bude vyměněn povolením souborů cookie protokolu HTTP, coby mechanismem výměny.  
  
 \<system.ServiceModel>  
\<vazby >  
\<basicHttpContextBinding>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<basicHttpContextBinding>  
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
           <message  algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"  
                                    clientCredentialType="UserName/Certificate"/>  
       </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />   </binding>  
</basicHttpContextBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`allowCookies`|Logická hodnota určující, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích. Výchozí hodnota je `false`.<br /><br /> Tuto vlastnost můžete použít, když pracujete s ASMX webovými službami, které používají soubory cookie. Tímto způsobem máte jistotu, že soubory cookie vrácený ze serveru se automaticky zkopírují do všechny budoucí požadavky za danou službu.|  
|`bypassProxyOnLocal`|Logická hodnota určující, zda obejít proxy server pro místní adresy. Výchozí hodnota je `false`.<br /><br /> Je místní, pokud má místní adresu internetového zdroji. Místní adresa je ten, který je na stejném počítači, místní síti LAN nebo intranetu a identifikuje, syntakticky, absenci tečkou (.) jako identifikátory URI "http://webserver/" a "http://localhost/".<br /><br /> Nastavení tohoto atributu určuje, zda se BasicHttpBinding nakonfigurované koncové body používat proxy server při přístupu k místním prostředkům. Pokud tento atribut je `true`, požadavky na místní internetové prostředky Nepoužívat proxy server. Název hostitele (místo místního hostitele), pokud chcete klientům přejít přes proxy server, když mluvíme ke službám ve stejném počítači, když tento atribut je nastaven na použití `true`.<br /><br /> Pokud tento atribut je `false`, všechny požadavky na Internetu se provádějí přes proxy server.|  
|`closeTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`envelopeVersion`|Určuje verzi modulu protokolu SOAP, která se používá pro zprávy zpracovávané touto vazbou. Jediná platná hodnota je Soap11.|  
|`hostnameComparisonMode`|Určuje režim porovnání jména hostitele HTTP použít k analýze identifikátoru URI. Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což znamená, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele. Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, které ignoruje jako název hostitele v porovnávání.|  
|`maxBufferPoolSize`|Celočíselná hodnota, která určuje maximální množství paměti přidělené správci vyrovnávacích pamětí zpráv, které přijímají zprávy z tohoto kanálu pamětí. Výchozí hodnota je 524288 (0x80000) bajtů.<br /><br /> Správce vyrovnávací paměti minimalizuje náklady na použití vyrovnávací paměti pomocí fondu vyrovnávací paměti. Vyrovnávací paměti jsou potřeba ke zpracování zpráv ve službě, když pocházejí z kanálu. Pokud ve fondu vyrovnávací paměti pro zpracování zátěže zpráva není dostatek paměti, musí správce vyrovnávací paměti přidělit další paměti z haldy CLR, což zvyšuje úroveň režie uvolňování paměti. Rozsáhlé přidělení v haldě uvolňování paměti modulu CLR slouží jako ukazatel toho, že je příliš malá velikost fondu vyrovnávací paměti a že výkon lze zvýšit pomocí větší přidělení zvýšením limit specifikovaný pro tento atribut.|  
|`maxBufferSize`|Celočíselná hodnota, která určuje maximální velikost v bajtech, vyrovnávací paměti, která ukládá zprávy při jejich zpracování pro koncovým bodem nakonfigurovaným s touto vazbou. Výchozí hodnota je 65 536 bajtů.|  
|`maxReceivedMessageSize`|Kladné celé číslo, které definuje maximální velikost zprávy, v bajtech, včetně záhlaví zprávy, která může být přijata v kanálu nakonfigurovaným s touto vazbou. Odesílatel obdrží chybu protokolu SOAP, pokud zpráva je moc velká pro příjemce. Příjemce zahodí a vytvoří záznam události v protokolu trasování. Výchozí hodnota je 65 536 bajty.|  
|`messageEncoding`|Definuje kodér použít ke kódování zprávy protokolu SOAP. Platné hodnoty patří:<br /><br /> -Text: Použijte kodér textu zprávy.<br />-Mtom: Pomocí kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).<br /><br /> Výchozí hodnota je Text. Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.|  
|`messageVersion`|Určuje verzi zprávy používají klienti a služba nakonfigurovaná pomocí této vazby. Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion>.|  
|`name`|Řetězec, který obsahuje konfigurační název vazby. Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu. Má každá vazba `name` a `namespace` atributů, které dohromady jedinečně identifikovat v metadatech služby. Kromě toho tento název je jedinečný mezi vazby stejného typu. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`namespace`|Určuje obor názvů XML vazby. Výchozí hodnota je " http://tempuri.org/Bindings". Má každá vazba `name` a `namespace` atributů, které dohromady jedinečně identifikovat v metadatech služby.|  
|`openTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`proxyAddress`|Identifikátor URI, který obsahuje adresu proxy serveru HTTP. Pokud `useSystemWebProxy` je nastavena na `true`, toto nastavení musí být `null`. Výchozí hodnota je `null`.|  
|`receiveTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:10:00.|  
|`sendTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`textEncoding`|Nastaví znakovou sadu kódování, které má být použito pro vysílání zpráv z vazby. Platné hodnoty patří:<br /><br /> -BigEndianUnicode: BigEndian kódování Unicode kódování.<br />-Unicode: kódování 16 bitů.<br />– UTF8: kódování 8bitové<br /><br /> Použije se UTF8. Tento atribut je typu <xref:System.Text.Encoding>.|  
|`transferMode`|Platný <xref:System.ServiceModel.TransferMode> hodnota, která určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo prostřednictvím datového proudu na požadavku nebo odpovědi.|  
|`useDefaultWebProxy`|Logická hodnota, která určuje, zda má být použita automaticky nakonfigurovaný proxy HTTP systému, pokud je k dispozici. Výchozí hodnota je `true`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|Definuje nastavení zabezpečení pro vazbu. Tento prvek je typu <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.|  
|[\<readerQuotas>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou. Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<vazby >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Tento prvek obsahuje sadu standardních a vlastních vazeb.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element vazby poskytuje úroveň ochrany a mechanismus exchange v rámci kontextu pro `BasicHttpBinding`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.BasicHttpContextBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpContextBindingElement>  
 <xref:System.ServiceModel.Channels.ContextBindingElement>  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)  
 [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
