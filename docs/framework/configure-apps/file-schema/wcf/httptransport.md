---
title: '&lt;httpTransport&gt;'
ms.date: 03/30/2017
ms.assetid: 8b30c065-b32a-4fa3-8eb4-5537a9c6b897
ms.openlocfilehash: ddce1053a7494a84d0266c7ad14f6b1937365fa5
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2018
ms.locfileid: "49316425"
---
# <a name="lthttptransportgt"></a>&lt;httpTransport&gt;
Určuje přenos pomocí protokolu HTTP při odesílání zpráv SOAP pro vlastní vazbu.  
  
 \<system.serviceModel>  
\<vazby >  
\<třídě customBinding >  
\<Vytvoření vazby >  
\<httpTransport>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<httpTransport  
    allowCookies=Boolean"  
    authenticationScheme="Digest/Negotiate/Ntlm/Basic/Anonymous"  
    bypassProxyOnLocal=Boolean"  
    hostnameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
    keepAliveEnabled="Boolean"  
    maxBufferSize="Integer"  
    proxyAddress="Uri"  
    proxyAuthenticationScheme="None/Digest/Negotiate/Ntlm/Basic/Anonymous"  
IntegratedWindowsAuthentication: Specifies Windows authentication"  
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
|allowCookies|Logická hodnota určující, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích. Výchozí hodnota je `false`.<br /><br /> Tento atribut lze použít při interakci s ASMX webovými službami, které používají soubory cookie. Tímto způsobem máte jistotu, že soubory cookie vrácený ze serveru se automaticky zkopírují do všechny budoucí požadavky za danou službu.|  
|AuthenticationScheme|Určuje protokol použitý pro ověřování požadavků klientů, jenž jsou zpracovány při naslouchání protokolu HTTP. Platné hodnoty patří:<br /><br /> -Algoritmus Digest: Určuje ověřování hodnotou hash.<br />-Vyjednat: Vyjedná s klientem nástroje k určení schéma ověřování. Pokud klient i server podporovat protokol Kerberos, je použit. v opačném případě je použit protokol NTLM.<br />– Protokol Ntlm: Určuje ověřování protokolem NTLM.<br />-Basic: Určuje základní ověřování.<br />-Anonymní: Určuje anonymní ověřování.<br /><br /> Výchozí hodnota je Anonymous. Tento atribut je typu <xref:System.Net.AuthenticationSchemes>. Tento atribut lze nastavit pouze jednou.|  
|bypassProxyOnLocal|Logická hodnota určující, zda obejít proxy server pro místní adresy. Výchozí hodnota je `false`.<br /><br /> Místní adresa je ten, který je v místní síti LAN nebo intranet.<br /><br /> Pokud začíná adresu služby Windows Communication Foundation (WCF) vždy ignoruje proxy `http://localhost`.<br /><br /> Pokud chcete klientům přejít přes proxy server, když mluvíme ke službám ve stejném počítači, se musí používat název hostitele místo localhost.|  
|hostnameComparisonMode|Určuje režim porovnání jména hostitele HTTP použít k analýze identifikátoru URI. Platné hodnoty jsou,<br /><br /> -StrongWildcard: ("+") odpovídá všechny možné názvy hostitelů v rámci zadané schéma, port a relativní identifikátor URI.<br />-Přesné: žádné zástupné znaky<br />-WeakWildcard: ("\*") shoduje s názvem všech možných hostitele v rámci zadané schéma, port a relativní UIR, nebyly explicitně odpovídající nebo mechanismem silný zástupný znak.<br /><br /> Výchozí hodnota je StrongWildcard. Tento atribut je typu `System.ServiceModel.HostnameComparisonMode`.|  
|keepAliveEnabled|Logická hodnota určující, zda má být trvalé připojení k internetového zdroji.|  
|Třída maxBufferSize|Kladné celé číslo, které určuje maximální velikost vyrovnávací paměti. Výchozí hodnota je 524288|  
|proxyAddress|Identifikátor URI, který určuje adresu proxy serveru HTTP. Pokud `useSystemWebProxy` je `true`, toto nastavení musí být `null`. Výchozí hodnota je `null`.|  
|proxyAuthenticationScheme|Určuje protokol použitý pro ověřování požadavků klientů zpracovávaných HTTP proxy. Platné hodnoty patří:<br /><br /> -Žádný: Neprobíhá žádné ověřování.<br />-Algoritmus Digest: Určuje ověřování hodnotou hash.<br />-Vyjednat: Vyjedná s klientem nástroje k určení schéma ověřování. Pokud klient i server podporovat protokol Kerberos, je použit. v opačném případě je použit protokol NTLM.<br />– Protokol Ntlm: Určuje ověřování protokolem NTLM.<br />-Basic: Určuje základní ověřování.<br />-Anonymní: Určuje anonymní ověřování.<br />-IntegratedWindowsAuthentication: Určuje ověřování Windows.<br /><br /> Výchozí hodnota je Anonymous. Tento atribut je typu <xref:System.Net.AuthenticationSchemes>.|  
|Sféra|Řetězec určující sféru na serveru nebo proxy serveru. Výchozí hodnota je prázdný řetězec.<br /><br /> Servery používají sféry při vytváření oddílů chráněným prostředkům. Každý oddíl může mít vlastní databázi schéma a/nebo povolení ověřování. Sféry se používají pouze pro základní a ověřování algoritmem digest. Po klienta úspěšně ověřen, je platný pro všechny prostředky v danou sféru ověřování. Podrobný popis sféry, naleznete v tématu RFC 2617 na [IETF webu](https://www.ietf.org).|  
|režim přenosu|Určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo prostřednictvím datového proudu nebo požadavek nebo odpověď. Platné hodnoty patří:<br /><br /> -Ukládány do vyrovnávací paměti: Zpráv požadavků a odpovědí jsou ukládány do vyrovnávací paměti.<br />-Streamování: Se streamují zprávy požadavků a odpovědí.<br />-StreamedRequest: Streamuje zprávy požadavku a odpovědi do vyrovnávací paměti.<br />-StreamedResponse: Zprávy s požadavkem je uložená do vyrovnávací paměti a Streamovat zprávy s odpovědí.<br /><br /> Výchozí hodnota je uložená do vyrovnávací paměti. Tento atribut je typu <xref:System.ServiceModel.TransferMode> .|  
|unsafeConnectionNtlmAuthentication|Logická hodnota určující, zda je na serveru povoleno nezabezpečené sdílení připojení. Výchozí hodnota je `false`. Pokud je povoleno, ověřování protokolem NTLM se provádí jednou pro každé připojení TCP.|  
|useDefaultWebProxy|Logická hodnota, která určuje, jestli uživatelovo specifické nastavení jsou upřednostňována nastavení proxy pro celý počítač. Výchozí hodnota je `true`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vázání pro vlastní vazbu.|  
  
## <a name="remarks"></a>Poznámky  
 `httpTransport` Element je výchozí bod pro vytvoření vlastní vazby, který implementuje přenosový protokol HTTP. HTTP je primární přenosu používá pro účely vzájemná funkční spolupráce. Tento přenos je podporována v Windows Communication Foundation (WCF) k zajištění interoperability s další balíčky služeb WCF Web.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.HttpTransportElement>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Přenosy](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Volba přenosu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<třídě customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
