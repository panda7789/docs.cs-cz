---
title: '&lt;httpsTransport&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f6ed4bc0-7e38-4348-9259-30bf61eb9435
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 78b0cc2dd260b773c29b8684ab94bfaa0afffff2
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="lthttpstransportgt"></a>&lt;httpsTransport&gt;
Určuje přenosového protokolu HTTP pro přenos protokolu SOAP zprávy pro vlastní vazby.  
  
 \<system.serviceModel>  
\<vazby >  
\<customBinding>  
\<Vazba >  
\<httpsTransport>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<httpsTransport  
    allowCookies=Boolean"  
    authenticationScheme="Digest/Negotiate/Ntlm/Basic/Anonymous"  
    bypassProxyOnLocal=Boolean"  
    hostnameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
    manualAddressing="Boolean"  
    maxBufferPoolSize="Integer"  
    maxBufferSize="Integer"  
    maxReceivedMessageSize="Integer"  
    proxyAddress="Uri"  
    proxyAuthenticationScheme="None/Digest/Negotiate/Ntlm/Basic/Anonymous"        realm="String"  
    requireClientCertificate=Boolean"  
    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
        unsafeConnectionNtlmAuthentication="Boolean"  
....useDefaultWebProxy="Boolean"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|allowCookies|Logická hodnota, která určuje, zda klient přijímá soubory cookie a rozšiřuje je na dalších požadavků. Výchozí hodnota je `false`.<br /><br /> Tento atribut můžete použít při používání ASMX webové služby, které používají soubory cookie. Tímto způsobem mohou být jisti, že soubory cookie, kterou vrátil server se automaticky zkopírují do všechny budoucí požadavky pro tuto službu.|  
|AuthenticationScheme|Určuje protokol, používá k ověření klientských požadavků zpracovávaných naslouchací proces protokolu HTTP. Platné hodnoty patří:<br /><br /> -Digest: Určuje ověřování hodnotou hash.<br />-Vyjednávání: Vyjedná s klientem nástroje k určení schéma ověřování. Pokud klient i server podporovat protokolu Kerberos, použije se; jinak se používá protokol NTLM.<br />– Protokol Ntlm: Určuje ověřování NTLM.<br />– Základní: Určuje základní ověřování.<br />-Anonymní: Určuje anonymní ověřování.<br /><br /> Výchozí hodnota je anonymní. Tento atribut je typu <xref:System.Net.AuthenticationSchemes>. Tento atribut lze nastavit pouze jednou.|  
|bypassProxyOnLocal|Logická hodnota, která označuje, zda Nepoužívat proxy server pro místní adresy. Výchozí hodnota je `false`.<br /><br /> Místní adresa je ten, který je v místní síti LAN nebo intranet.<br /><br /> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Pokud adresu služby začíná http://localhost vždy ignoruje proxy serveru.<br /><br /> Pokud chcete klientům jít přes proxy server při posuzování ke službám ve stejném počítači, se musí používat název hostitele místo localhost.|  
|hostnameComparisonMode|Určuje režim porovnání hostname HTTP použitá k analýze identifikátory URI. Platné hodnoty jsou,<br /><br /> -StrongWildcard: ("+") odpovídá všechny možné názvy hostitelů v rámci zadané schéma, port a relativní identifikátor URI.<br />-Přesnou: žádné zástupné znaky<br />-WeakWildcard: ("*") shoduje s názvem všechny možné hostitele zadané schéma, port a relativní UIR, která nejsou explicitně shoduje nebo přes mechanismus silné zástupný znak v kontextu.<br /><br /> Výchozí hodnota je StrongWildcard. Tento atribut je typu `System.ServiceModel.HostnameComparison`.|  
|manualAddressing|Logická hodnota, která umožňuje uživatelům převzít kontrolu nad adresování zprávy. Tato vlastnost se obvykle používá ve scénářích směrovače, kde aplikace určuje, které jeden z několika cílů odeslat zprávu na.<br /><br /> Pokud nastavíte hodnotu `true`, kanál předpokládá zpráva již splněna a k němu nepřidává žádné další informace. Uživatel pak může jednotlivě adres každou zprávu.<br /><br /> Pokud nastavíte hodnotu `false`, výchozího mechanismu adresování Windows Communication Foundation (WCF) automaticky vytvoří adresy pro všechny zprávy.<br /><br /> Výchozí hodnota je `false`.|  
|maxBufferPoolSize|Kladné celé číslo, které určuje maximální velikost fondu vyrovnávací paměti. Výchozí hodnota je 524288.<br /><br /> Mnoho části služby WCF pomocí vyrovnávací paměti. Vytváření a zničení pokaždé, když se používají vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné. S fondy vyrovnávací paměti můžete provést vyrovnávací paměti z fondu, ho použít a po dokončení se vraťte do fondu. Proto je předejde režijní náklady v vytváření a zničení vyrovnávací paměti.|  
|maxBufferSize|Kladné celé číslo, které určuje maximální velikost vyrovnávací paměti. Výchozí hodnota je 524288|  
|MaxReceivedMessageSize|Kladné celé číslo, které určuje maximální povolená velikost zprávy, bude moci přijmout. Výchozí hodnota je 65536.|  
|proxyAddress|Identifikátor URI, který určuje adresu proxy serveru HTTP. Pokud `useSystemWebProxy` je `true`, toto nastavení musí být `null`. Výchozí hodnota je `null`.|  
|ProxyAuthenticationScheme|Určuje protokol použitý pro ověřování proxy serveru HTTP zpracovává požadavky klienta. Platné hodnoty patří:<br /><br /> -None: Neprobíhá žádné ověřování.<br />-Digest: Určuje ověřování hodnotou hash.<br />-Vyjednávání: Vyjedná s klientem nástroje k určení schéma ověřování. Pokud klient i server podporovat protokolu Kerberos, použije se; jinak se používá protokol NTLM.<br />– Protokol Ntlm: Určuje ověřování NTLM.<br />– Základní: Určuje základní ověřování.<br />-Anonymní: Určuje anonymní ověřování.<br />-IntegratedWindowsAuthentication: Určuje ověřování systému Windows.<br /><br /> Výchozí hodnota je anonymní. Tento atribut je typu <xref:System.Net.AuthenticationSchemes>.|  
|sféry|Řetězec, který určuje sféry, použijte na proxy serveru. Výchozí hodnota je prázdný řetězec.<br /><br /> Servery používají sfér k oddílu chráněným prostředkům. Každý oddíl může mít svou vlastní databázi schéma nebo autorizace ověřování. Sfér se používají pouze pro základní a ověřování algoritmem digest. Jakmile klient úspěšně ověří, je platný pro všechny prostředky v dané sféry ověřování. Podrobný popis sfér, najdete v dokumentu RFC 2617 na http://www.ietf.org.|  
|requireClientCertificate|Logická hodnota, která určuje, pokud server vyžaduje, aby klient zajistit certifikát klienta v rámci metody handshake pro protokol HTTPS. Výchozí hodnota je `false`.|  
|transferMode|Určuje, zda jsou zprávy do vyrovnávací paměti nebo prostřednictvím datového proudu nebo požadavku nebo odpovědi. Platné hodnoty patří:<br /><br /> -Uložená do vyrovnávací paměti: Zprávy požadavku a odpovědi jsou uložená do vyrovnávací paměti.<br />-Streamování: Streamovaných zprávy požadavku a odpovědi.<br />-StreamedRequest: Zprávu požadavku je streamování a zprávu odpovědi do vyrovnávací paměti.<br />-StreamedResponse: Zprávu požadavku do vyrovnávací paměti a je streamování zprávu odpovědi.<br /><br /> Výchozí hodnota je uložená do vyrovnávací paměti. Tento atribut je typu <xref:System.ServiceModel.TransferMode>.|  
|unsafeConnectionNtlmAuthentication|Logická hodnota, která určuje, zda je na serveru povoleno Unsafe sdílení připojení. Výchozí hodnota je `false`. Pokud je povoleno, ověřování protokolem NTLM se provádí jednou v každé připojení TCP.|  
|useDefaultWebProxy|Logická hodnota, která určuje, jestli jsou nastavení proxy serveru celého systému použít místo nastavení specifická pro uživatele. Výchozí hodnota je `true`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vazba >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vazba vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 `httpsTransport` Element je výchozím bodem pro vytvoření vlastní vazby, který implementuje přenosový protokol HTTPS. HTTPS je primární přenosu použitý pro zajištění zabezpečené spolupráce. Podporuje protokol HTTPS [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] zajistit interoperabilitu s dalších webových služeb zásobníky.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.HttpsTransportElement>  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Přenosy](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Volba přenosu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
