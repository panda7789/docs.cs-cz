---
title: <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 84179d77-825d-44b9-895a-ab08e7aa044d
ms.openlocfilehash: 0bb6d1f40fe38cb13ed8ab07957de5db22d48fcc
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140499"
---
# <a name="webhttpbinding"></a>\<webHttpBinding >
Definuje prvek vazby, který se používá ke konfiguraci koncových bodů pro webové služby Windows Communication Foundation (WCF), které reagují na požadavky HTTP namísto zpráv SOAP.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webHttpBinding >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<webHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxBufferSize="integer"
           maxReceivedMessageSize="Integer"
           name="string"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
           useDefaultWebProxy="Boolean"
           writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding">
    <security mode="None/Transport/TransportCredentialOnly">
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 realm="string" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</webHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|allowCookies|Logická hodnota určující, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích. Výchozí hodnota je false.<br /><br /> Tuto vlastnost lze použít při práci s webovými službami ASMX, které používají soubory cookie. Tímto způsobem si můžete ověřit, že soubory cookie vrácené ze serveru se automaticky zkopírují do všech budoucích požadavků klientů pro danou službu.|  
|bypassProxyOnLocal|Logická hodnota, která označuje, zda se má pro místní adresy obejít proxy server. Výchozí hodnota je `false`.|  
|closeTimeout|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace ukončení. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|hostnameComparisonMode|Určuje režim porovnání názvu hostitele HTTP, který se používá k analýze identifikátorů URI. Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, který označuje, zda se k dosažení služby při shodě s identifikátorem URI používá název hostitele. Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, která ignoruje název hostitele v shodě.|  
|maxBufferPoolSize|Celé číslo, které určuje maximální velikost fondu vyrovnávací paměti pro tuto vazbu. Výchozí hodnota je 524 288 bajtů (512 * 1024). Mnoho částí Windows Communication Foundation (WCF) používá vyrovnávací paměti. Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné. Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu. Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.|  
|Třída|Celé číslo, které určuje maximální velikost paměti, která je přidělena pro použití správcem vyrovnávacích pamětí zpráv, které přijímají zprávy z kanálu. Výchozí hodnota je 524 288 (0x80000) bajtů.|  
|maxReceivedMessageSize|Celé kladné číslo určující maximální velikost zprávy v bajtech, včetně hlaviček, které lze přijmout na kanálu nakonfigurovaném pomocí této vazby. Odesílateli zprávy, která překračuje toto omezení, dostane chybu. Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování. Výchozí hodnota je 65536. **Poznámka:**  Zvýšení samotné hodnoty není dostatečné v režimu kompatibilním s ASP.NET. Měli byste také zvýšit hodnotu `httpRuntime` (viz [httpRuntime element (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e1f13641(v=vs.100))).|  
|name|Řetězec, který obsahuje název konfigurace vazby. Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby. Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název. Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace otevření. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|proxyAddress|Identifikátor URI, který určuje adresu proxy serveru HTTP. Pokud je `true``useSystemWebProxy`, musí být toto nastavení `null`. Výchozí hodnota je `null`.|  
|receiveTimeout|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace Receive. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|sendTimeout|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace odeslání. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|třídy TransferMode.|Hodnota <xref:System.ServiceModel.TransferMode>, která indikuje, jestli služba nakonfigurovaná s vazbou používá režimy přenosu zpráv streamování nebo ukládání do vyrovnávací paměti (nebo obojí). Výchozí hodnota je `Buffered`.|  
|useDefaultWebProxy|Logická hodnota, která určuje, zda se používá automaticky konfigurovaný proxy server HTTP systému. Výchozí hodnota je `true`.|  
|writeEncoding|Určuje kódování znaků, které se používá pro text zprávy. Platné hodnoty jsou následující:<br /><br /> UnicodeFffeTextEncoding: kódování Unicode BigEndian.<br /><br /> Utf16TextEncoding: 16bitové kódování.<br /><br /> Utf8TextEncoding: 8bitové kódování.<br /><br /> Výchozí hodnota je Utf8TextEncoding.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definuje omezení složitosti zpráv POX, které mohou být zpracovány koncovými body nakonfigurovanými pomocí této vazby. Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[> zabezpečení \<](security-of-webhttpbinding.md)|Definuje nastavení zabezpečení pro vazbu. Tento prvek je typu <xref:System.ServiceModel.Configuration.WebHttpSecurityElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[vazby\<](bindings.md)|Tento prvek obsahuje kolekci standardních a vlastních vazeb.|  
  
## <a name="remarks"></a>Poznámky  
 Model webového programování WCF umožňuje vývojářům vystavit webové služby WCF prostřednictvím požadavků HTTP, které místo zasílání zpráv založeného na protokolu SOAP používají zasílání zpráv ve stylu "obyčejného starého XML" (POX). Aby klienti mohli komunikovat se službou pomocí požadavků protokolu HTTP, je nutné nakonfigurovat koncový bod služby s [\<webHttpBinding >](webhttpbinding.md) , ke kterému je > připojeno \<WebHttpBehavior.  
  
 Podpora služby WCF pro syndikaci a ASP. Integrace s AJAX je postavená na modelu webového programování. Další informace o modelu naleznete v tématu [model programování webového HTTP WCF](../../../wcf/feature-details/wcf-web-http-programming-model.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- [Programovací model webových služeb HTTP WCF](../../../wcf/feature-details/wcf-web-http-programming-model.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [vazba \<](bindings.md)
