---
title: <httpTransport>
ms.date: 03/30/2017
ms.assetid: 8b30c065-b32a-4fa3-8eb4-5537a9c6b897
ms.openlocfilehash: b3558db6018d79f0fad27ff28657bfadb5637467
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736763"
---
# \<httpTransport>
Určuje přenos HTTP pro přenos zpráv SOAP pro vlastní vazbu.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpTransport>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<httpTransport allowCookies="Boolean"
               authenticationScheme="Digest/Negotiate/Ntlm/Basic/Anonymous"
               bypassProxyOnLocal="Boolean"
               hostnameComparisonMode="StrongWildcard/Exact/WeakWildcard"
               keepAliveEnabled="Boolean"
               maxBufferSize="Integer"
               proxyAddress="Uri"
               proxyAuthenticationScheme="None/Digest/Negotiate/Ntlm/Basic/Anonymous"
               realm="String"
               transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
               unsafeConnectionNtlmAuthentication="Boolean"
               useDefaultWebProxy="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|allowCookies|Logická hodnota určující, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích. Výchozí formát je `false`.<br /><br /> Tento atribut lze použít při interakci s webovými službami ASMX, které používají soubory cookie. Tímto způsobem si můžete ověřit, že soubory cookie vrácené ze serveru se automaticky zkopírují do všech budoucích požadavků klientů pro danou službu.|  
|authenticationScheme|Určuje protokol použitý pro ověřování požadavků klientů zpracovávaných naslouchacím programem HTTP. Platné hodnoty jsou následující:<br /><br /> -Digest: Určuje ověřování algoritmem Digest.<br />-Negotiate: vyjednává klienta, aby určil schéma ověřování. Pokud klient i server podporují Kerberos, používá se. v opačném případě se použije NTLM.<br />-NTLM: Určuje ověřování NTLM.<br />-Basic: Určuje základní ověřování.<br />-Anonymous: Určuje anonymní přístup.<br /><br /> Výchozí hodnota je anonymní. Tento atribut je typu <xref:System.Net.AuthenticationSchemes> . Tento atribut lze nastavit pouze jednou.|  
|bypassProxyOnLocal|Logická hodnota, která označuje, zda se má pro místní adresy obejít proxy server. Výchozí formát je `false`.<br /><br /> Místní adresa je jedna z místních sítí LAN nebo intranetu.<br /><br /> Windows Communication Foundation (WCF) vždycky ignoruje proxy, pokud adresa služby začíná na `http://localhost` .<br /><br /> Pokud chcete, aby klienti při komunikaci se službami ve stejném počítači přešli přes proxy server, měli byste použít název hostitele místo na localhost.|  
|hostnameComparisonMode|Určuje režim porovnání názvu hostitele HTTP, který se používá k analýze identifikátorů URI. Platné hodnoty jsou,<br /><br /> -StrongWildcard: ("+") odpovídá všem možným názvům hostitelů v kontextu zadaného schématu, portu a relativního identifikátoru URI.<br />-Přesný: žádné zástupné znaky<br />-WeakWildcard: (" \* ") odpovídá veškerému možnému názvu hostitele v kontextu zadaného schématu, portu a relativních UIR, které nebyly explicitně spárovány nebo prostřednictvím mechanismu silných zástupných znaků.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode> . Výchozí formát je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>.|  
|keepAliveEnabled|Logická hodnota, která určuje, zda má být trvalé připojení k internetovému prostředku.|  
|Třída|Kladné celé číslo, které určuje maximální velikost vyrovnávací paměti. Výchozí hodnota je 524288.|  
|proxyAddress|Identifikátor URI, který určuje adresu proxy serveru HTTP. Pokud `useSystemWebProxy` má `true` parametr hodnotu, musí být toto nastavení `null` . Výchozí formát je `null`.|  
|proxyAuthenticationScheme|Určuje protokol, který se používá pro ověřování požadavků klientů zpracovávaných proxy HTTP. Platné hodnoty jsou následující:<br /><br /> -None: není provedeno žádné ověřování.<br />-Digest: Určuje ověřování algoritmem Digest.<br />-Negotiate: vyjednává klienta, aby určil schéma ověřování. Pokud klient i server podporují Kerberos, používá se. v opačném případě se použije NTLM.<br />-NTLM: Určuje ověřování NTLM.<br />-Basic: Určuje základní ověřování.<br />-Anonymous: Určuje anonymní přístup.<br /><br /> Výchozí hodnota je anonymní. Tento atribut je typu <xref:System.Net.AuthenticationSchemes> . Všimněte si, že <xref:System.Net.AuthenticationSchemes.IntegratedWindowsAuthentication?displayProperty=nameWithType> se nepodporuje.|  
|sféry|Řetězec, který určuje sféru, která se má použít na proxy nebo serveru. Výchozí hodnota je prázdný řetězec.<br /><br /> Servery používají ke dělení chráněných prostředků sféry. Každý oddíl může mít vlastní schéma ověřování a/nebo autorizační databázi. Sféry se používají jenom pro základní ověřování a ověřování algoritmem Digest. Po úspěšném ověření klienta je ověřování platné pro všechny prostředky v dané sféře. Podrobný popis sfér najdete v dokumentu RFC 2617 na [webu IETF](https://www.ietf.org).|  
|Třídy TransferMode|Určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo zpracovány nebo jsou požadavkem či odpovědí. Platné hodnoty jsou následující:<br /><br /> – Vyrovnávací paměť: zprávy žádosti a odpovědi jsou ve vyrovnávací paměti.<br />-Streamování: zprávy žádosti a odpovědi jsou streamované.<br />-StreamedRequest: zpráva požadavku je streamovaná a zpráva odpovědi je uložená do vyrovnávací paměti.<br />-StreamedResponse: zpráva požadavku je ukládána do vyrovnávací paměti a zpráva odpovědi je streamovaná.<br /><br /> Výchozím nastavením je ukládání do vyrovnávací paměti. Tento atribut je typu <xref:System.ServiceModel.TransferMode> .|  
|unsafeConnectionNtlmAuthentication|Logická hodnota, která určuje, zda je na serveru povoleno nezabezpečené sdílení připojení. Výchozí formát je `false`. V případě povolení se ověřování NTLM provádí jednou při každém připojení TCP.|  
|useDefaultWebProxy|Logická hodnota určující, zda jsou použita nastavení proxy serveru na úrovni počítače, nikoli nastavení specifická pro uživatele. Výchozí formát je `true`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|Definuje všechny schopnosti vazby vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 `httpTransport`Element je výchozím bodem pro vytvoření vlastní vazby, která implementuje protokol HTTP Transport. HTTP je primární přenos používaný pro účely interoperability. Tento přenos podporuje Windows Communication Foundation (WCF), aby se zajistila interoperabilita s jinými zásobníky webových služeb, které nepatří do WCF.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.HttpTransportElement>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Přenosy](../../../wcf/feature-details/transports.md)
- [Volba přenosu](../../../wcf/feature-details/choosing-a-transport.md)
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
