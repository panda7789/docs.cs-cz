---
title: <httpsTransport>
ms.date: 03/30/2017
ms.assetid: f6ed4bc0-7e38-4348-9259-30bf61eb9435
ms.openlocfilehash: 09b0b8500ca93649c814c00739210343bfe1424c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739022"
---
# <a name="httpstransport"></a>\<httpsTransport >
Určuje přenos HTTP pro přenos zpráv SOAP pro vlastní vazbu.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<httpsTransport >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<httpsTransport allowCookies="Boolean"
                authenticationScheme="Digest/Negotiate/Ntlm/Basic/Anonymous"
                bypassProxyOnLocal="Boolean"
                hostnameComparisonMode="StrongWildcard/Exact/WeakWildcard"
                manualAddressing="Boolean"
                maxBufferPoolSize="Integer"
                maxBufferSize="Integer"
                maxReceivedMessageSize="Integer"
                proxyAddress="Uri"
                proxyAuthenticationScheme="None/Digest/Negotiate/Ntlm/Basic/Anonymous"
                realm="String"
                requireClientCertificate="Boolean"
                transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
                unsafeConnectionNtlmAuthentication="Boolean"
                useDefaultWebProxy="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|allowCookies|Logická hodnota určující, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích. Výchozí hodnota je `false`.<br /><br /> Tento atribut lze použít při interakci s webovými službami ASMX, které používají soubory cookie. Tímto způsobem si můžete ověřit, že soubory cookie vrácené ze serveru se automaticky zkopírují do všech budoucích požadavků klientů pro danou službu.|  
|authenticationScheme|Určuje protokol použitý pro ověřování požadavků klientů zpracovávaných naslouchacím programem HTTP. Platné hodnoty jsou následující:<br /><br /> -Digest: Určuje ověřování algoritmem Digest.<br />-Negotiate: vyjednává klienta, aby určil schéma ověřování. Pokud klient i server podporují Kerberos, používá se. v opačném případě se použije NTLM.<br />-NTLM: Určuje ověřování NTLM.<br />-Basic: Určuje základní ověřování.<br />-Anonymous: Určuje anonymní přístup.<br /><br /> Výchozí hodnota je anonymní. Tento atribut je typu <xref:System.Net.AuthenticationSchemes>. Tento atribut lze nastavit pouze jednou.|  
|bypassProxyOnLocal|Logická hodnota, která označuje, zda se má pro místní adresy obejít proxy server. Výchozí hodnota je `false`.<br /><br /> Místní adresa je jedna z místních sítí LAN nebo intranetu.<br /><br /> Windows Communication Foundation (WCF) vždycky ignoruje proxy, pokud adresa služby začíná na `http://localhost`.<br /><br /> Pokud chcete, aby klienti při komunikaci se službami ve stejném počítači přešli přes proxy server, měli byste použít název hostitele místo na localhost.|  
|hostnameComparisonMode|Určuje režim porovnání názvu hostitele HTTP, který se používá k analýze identifikátorů URI. Platné hodnoty jsou,<br /><br /> -StrongWildcard: ("+") odpovídá všem možným názvům hostitelů v kontextu zadaného schématu, portu a relativního identifikátoru URI.<br />-Přesný: žádné zástupné znaky<br />-WeakWildcard: ("\*") odpovídá veškerému možnému názvu hostitele v kontextu zadaného schématu, portu a relativních UIR, které nebyly explicitně spárovány nebo prostřednictvím mechanismu silných zástupných znaků.<br /><br /> Výchozí hodnota je StrongWildcard. Tento atribut je typu `System.ServiceModel.HostnameComparison`.|  
|Jeho|Logická hodnota, která umožňuje uživateli převzít kontrolu nad adresováním zpráv. Tato vlastnost se obvykle používá ve scénářích směrovačů, kde aplikace určuje, do kterého jednoho z několika míst má poslat zprávu.<br /><br /> Při nastavení `true`kanál předpokládá, že zpráva již byla adresována a do ní nepřidá žádné další informace. Uživatel pak může každou zprávu adresovat jednotlivě.<br /><br /> Když nastavíte `false`, výchozí mechanismus pro adresování Windows Communication Foundation (WCF) automaticky vytvoří adresy pro všechny zprávy.<br /><br /> Výchozí hodnota je `false`.|  
|maxBufferPoolSize|Kladné celé číslo, které určuje maximální velikost fondu vyrovnávací paměti. Výchozí hodnota je 524288.<br /><br /> Mnoho částí služby WCF používá vyrovnávací paměti. Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné. Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu. Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.|  
|Třída|Kladné celé číslo, které určuje maximální velikost vyrovnávací paměti. Výchozí hodnota je 524288.|  
|maxReceivedMessageSize|Celé kladné číslo určující maximální povolenou velikost zprávy, kterou lze přijmout. Výchozí hodnota je 65536.|  
|proxyAddress|Identifikátor URI, který určuje adresu proxy serveru HTTP. Pokud je `true``useSystemWebProxy`, musí být toto nastavení `null`. Výchozí hodnota je `null`.|  
|proxyAuthenticationScheme|Určuje protokol, který se používá pro ověřování požadavků klientů zpracovávaných proxy HTTP. Platné hodnoty jsou následující:<br /><br /> -None: není provedeno žádné ověřování.<br />-Digest: Určuje ověřování algoritmem Digest.<br />-Negotiate: vyjednává klienta, aby určil schéma ověřování. Pokud klient i server podporují Kerberos, používá se. v opačném případě se použije NTLM.<br />-NTLM: Určuje ověřování NTLM.<br />-Basic: Určuje základní ověřování.<br />-Anonymous: Určuje anonymní přístup.<br /><br /> Výchozí hodnota je anonymní. Tento atribut je typu <xref:System.Net.AuthenticationSchemes>. Všimněte si, že <xref:System.Net.AuthenticationSchemes.IntegratedWindowsAuthentication?displayProperty=nameWithType> není podporována.|  
|sféry|Řetězec, který určuje sféru, která se má použít na proxy nebo serveru. Výchozí hodnota je prázdný řetězec.<br /><br /> Servery používají ke dělení chráněných prostředků sféry. Každý oddíl může mít vlastní schéma ověřování a/nebo autorizační databázi. Sféry se používají jenom pro základní ověřování a ověřování algoritmem Digest. Po úspěšném ověření klienta je ověřování platné pro všechny prostředky v dané sféře. Podrobný popis sfér najdete v dokumentu RFC 2617 na [webu IETF](https://www.ietf.org).|  
|requireClientCertificate|Logická hodnota určující, zda server vyžaduje, aby klient poskytoval klientský certifikát jako součást metody handshake protokolu HTTPS. Výchozí hodnota je `false`.|  
|Třídy TransferMode|Určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo zpracovány nebo jsou požadavkem či odpovědí. Platné hodnoty jsou následující:<br /><br /> – Vyrovnávací paměť: zprávy žádosti a odpovědi jsou ve vyrovnávací paměti.<br />-Streamování: zprávy žádosti a odpovědi jsou streamované.<br />-StreamedRequest: zpráva požadavku je streamovaná a zpráva odpovědi je uložená do vyrovnávací paměti.<br />-StreamedResponse: zpráva požadavku je ukládána do vyrovnávací paměti a zpráva odpovědi je streamovaná.<br /><br /> Výchozím nastavením je ukládání do vyrovnávací paměti. Tento atribut je typu <xref:System.ServiceModel.TransferMode>.|  
|unsafeConnectionNtlmAuthentication|Logická hodnota, která určuje, zda je na serveru povoleno nezabezpečené sdílení připojení. Výchozí hodnota je `false`. V případě povolení se ověřování NTLM provádí jednou při každém připojení TCP.|  
|useDefaultWebProxy|Logická hodnota určující, zda jsou použita nastavení proxy serveru na úrovni počítače, nikoli nastavení specifická pro uživatele. Výchozí hodnota je `true`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[vazba \<](bindings.md)|Definuje všechny schopnosti vazby vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 `httpsTransport` element je výchozím bodem pro vytvoření vlastní vazby, která implementuje transportní protokol HTTPS. HTTPS je primární přenos, který se používá pro účely zabezpečené interoperability. Protokol HTTPS podporuje Windows Communication Foundation (WCF), aby se zajistila interoperabilita s ostatními zásobníky webových služeb.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.HttpsTransportElement>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Přenosy](../../../wcf/feature-details/transports.md)
- [Volba přenosu](../../../wcf/feature-details/choosing-a-transport.md)
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
