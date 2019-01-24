---
title: '&lt;httpsTransport&gt;'
ms.date: 03/30/2017
ms.assetid: f6ed4bc0-7e38-4348-9259-30bf61eb9435
ms.openlocfilehash: 8a2c76fd6d657a4b86909469296e3b4c6b47a926
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624571"
---
# <a name="lthttpstransportgt"></a>&lt;httpsTransport&gt;
Určuje přenos pomocí protokolu HTTP při odesílání zpráv SOAP pro vlastní vazbu.  
  
 \<system.serviceModel>  
\<vazby >  
\<customBinding>  
\<Vytvoření vazby >  
\<httpsTransport>  
  
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
|allowCookies|Logická hodnota určující, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích. Výchozí hodnota je `false`.<br /><br /> Tento atribut lze použít při interakci s ASMX webovými službami, které používají soubory cookie. Tímto způsobem máte jistotu, že soubory cookie vrácený ze serveru se automaticky zkopírují do všechny budoucí požadavky za danou službu.|  
|authenticationScheme|Určuje protokol použitý pro ověřování požadavků klientů, jenž jsou zpracovány při naslouchání protokolu HTTP. Platné hodnoty patří:<br /><br /> -Algoritmus Digest: Určuje, ověřování hodnotou hash.<br />-Vyjednat: Vyjednává s klientem nástroje k určení schéma ověřování. Pokud klient i server podporovat protokol Kerberos, je použit. v opačném případě je použit protokol NTLM.<br />– Protokol Ntlm: Určuje ověřování protokolem NTLM.<br />-Základní: Určuje základní ověřování.<br />-Anonymní: Určuje anonymní ověřování.<br /><br /> Výchozí hodnota je Anonymous. Tento atribut je typu <xref:System.Net.AuthenticationSchemes>. Tento atribut lze nastavit pouze jednou.|  
|bypassProxyOnLocal|Logická hodnota určující, zda obejít proxy server pro místní adresy. Výchozí hodnota je `false`.<br /><br /> Místní adresa je ten, který je v místní síti LAN nebo intranet.<br /><br /> Pokud začíná adresu služby Windows Communication Foundation (WCF) vždy ignoruje proxy `http://localhost`.<br /><br /> Pokud chcete klientům přejít přes proxy server, když mluvíme ke službám ve stejném počítači, se musí používat název hostitele místo localhost.|  
|hostnameComparisonMode|Určuje režim porovnání jména hostitele HTTP použít k analýze identifikátoru URI. Platné hodnoty jsou,<br /><br /> -StrongWildcard: ("+") odpovídá všechny možné názvy hostitelů v rámci zadané schéma, port a relativní identifikátor URI.<br />-Přesné: žádné zástupné znaky<br />-WeakWildcard: ("\*") shoduje s názvem všech možných hostitele v rámci zadané schéma, port a relativní UIR, nebyly explicitně odpovídající nebo mechanismem silný zástupný znak.<br /><br /> Výchozí hodnota je StrongWildcard. Tento atribut je typu `System.ServiceModel.HostnameComparison`.|  
|Vlastnost manualAddressing|Logická hodnota, která umožňuje uživateli řídit adresování zpráv. Tato vlastnost se obvykle používá ve scénářích směrovače, kde aplikace určuje, který z nich několik cílů odeslat zprávu do.<br /><br /> Pokud je nastavena na `true`, kanál se předpokládá zprávu už nemá řešení a k němu nepřidává žádné další informace. Uživatel může pak Adresujte všechny zprávy jednotlivě.<br /><br /> Pokud je nastavena na `false`, výchozího mechanismu adresování Windows Communication Foundation (WCF) automaticky vytvoří adresy pro všechny zprávy.<br /><br /> Výchozí hodnota je `false`.|  
|maxBufferPoolSize|Kladné celé číslo, které určuje maximální velikost fondu vyrovnávacích pamětí. Výchozí hodnota je 524288.<br /><br /> Mnoho částí WCF pomocí vyrovnávací paměti. Vytváření a ničení pokaždé, když používají se vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměť je také náročné. S fondy vyrovnávací paměti může trvat vyrovnávací paměti z fondu, ho použít a vrátit do fondu, až budete hotovi. Proto je vyloučeno režie při vytváření a ničení vyrovnávací paměti.|  
|maxBufferSize|Kladné celé číslo, které určuje maximální velikost vyrovnávací paměti. Výchozí hodnota je 524288|  
|maxReceivedMessageSize|Kladné celé číslo, určující maximální povolenou velikost zprávy, která může být přijata. Výchozí hodnota je 65536.|  
|proxyAddress|Identifikátor URI, který určuje adresu proxy serveru HTTP. Pokud `useSystemWebProxy` je `true`, toto nastavení musí být `null`. Výchozí hodnota je `null`.|  
|proxyAuthenticationScheme|Určuje protokol použitý pro ověřování požadavků klientů zpracovávaných HTTP proxy. Platné hodnoty patří:<br /><br /> -Žádný: Neprobíhá žádné ověřování.<br />-Algoritmus Digest: Určuje, ověřování hodnotou hash.<br />-Vyjednat: Vyjednává s klientem nástroje k určení schéma ověřování. Pokud klient i server podporovat protokol Kerberos, je použit. v opačném případě je použit protokol NTLM.<br />– Protokol Ntlm: Určuje ověřování protokolem NTLM.<br />-Základní: Určuje základní ověřování.<br />-Anonymní: Určuje anonymní ověřování.<br /><br /> Výchozí hodnota je Anonymous. Tento atribut je typu <xref:System.Net.AuthenticationSchemes>. Všimněte si, že `IntegratedWindowsAuthentication` se nepodporuje.|  
|Sféra|Řetězec určující sféru na serveru nebo proxy serveru. Výchozí hodnota je prázdný řetězec.<br /><br /> Servery používají sféry při vytváření oddílů chráněným prostředkům. Každý oddíl může mít vlastní databázi schéma a/nebo povolení ověřování. Sféry se používají pouze pro základní a ověřování algoritmem digest. Po klienta úspěšně ověřen, je platný pro všechny prostředky v danou sféru ověřování. Podrobný popis sféry, naleznete v tématu RFC 2617 na [IETF webu](https://www.ietf.org).|  
|requireClientCertificate|Logická hodnota určující, zda server vyžaduje od klienta klientský certifikát jako součást metody handshake HTTPS. Výchozí hodnota je `false`.|  
|transferMode|Určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo prostřednictvím datového proudu nebo požadavek nebo odpověď. Platné hodnoty patří:<br /><br /> -Ukládány do vyrovnávací paměti: Zprávy požadavků a odpovědí jsou ukládány do vyrovnávací paměti.<br />-Streamování: Se streamují zprávy požadavků a odpovědí.<br />-StreamedRequest: Zprávy s požadavkem je streamování a zprávy s odpovědí do vyrovnávací paměti.<br />-StreamedResponse: Zpráva požadavku do vyrovnávací paměti a Streamovat zprávy s odpovědí.<br /><br /> Výchozí hodnota je uložená do vyrovnávací paměti. Tento atribut je typu <xref:System.ServiceModel.TransferMode>.|  
|unsafeConnectionNtlmAuthentication|Logická hodnota určující, zda je na serveru povoleno nezabezpečené sdílení připojení. Výchozí hodnota je `false`. Pokud je povoleno, ověřování protokolem NTLM se provádí jednou pro každé připojení TCP.|  
|useDefaultWebProxy|Logická hodnota, která určuje, jestli uživatelovo specifické nastavení jsou upřednostňována nastavení proxy pro celý počítač. Výchozí hodnota je `true`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vázání pro vlastní vazbu.|  
  
## <a name="remarks"></a>Poznámky  
 `httpsTransport` Element je výchozí bod pro vytvoření vlastní vazby, který implementuje přenosový protokol HTTPS. HTTPS je primární přenosu používá pro účely zabezpečenou spolupráci. HTTPS je podporována v Windows Communication Foundation (WCF) k zajištění interoperability s zásobníky jiné webové služby.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.HttpsTransportElement>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Přenosy](../../../../../docs/framework/wcf/feature-details/transports.md)
- [Volba přenosu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
