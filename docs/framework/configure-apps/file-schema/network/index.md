---
title: Schéma nastavení sítě
ms.date: 03/30/2017
helpviewer_keywords:
- elements [.NET Framework], network configuration elements
- sending data, network configuration elements
- receiving data, network configuration elements
- configuration settings [.NET Framework], networks
- Internet, network configuration elements
- network configuration elements
- network settings
- connections [.NET Framework], network configuration elements
- network resources, network configuration elements
ms.assetid: f1de5a0f-76c5-4833-819f-5222b8146340
ms.openlocfilehash: 71d945e6046a8648a812de939f197429bc695808
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148288"
---
# <a name="network-settings-schema"></a>Schéma nastavení sítě
Nastavení sítě určete, jak rozhraní .NET Framework připojí k Internetu. Následující tabulka popisuje funkce každý podřízený element konfigurace v rámci [ \<system.Net > – Element (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md).  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<authenticationModules – > – Element (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|Určuje moduly používané k ověření požadavků na Internetu.|  
|[\<connectionManagement – > – Element (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|Určuje maximální počet připojení k hostiteli v síti Internet.|  
|[\<defaultProxy > – Element (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Určuje proxy server používá pro požadavky HTTP na Internetu.|  
|[\<mailSettings – > – Element (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|Obsahuje nastavení pro možnosti pro odesílání pošty.|  
|[\<requestCaching – > – Element (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Určuje mechanismus ukládání do mezipaměti pro síťové požadavky.|  
|[\<webRequestModules – > – Element (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Určuje moduly používaná pro požádání o informace z hostitelů v Internetu.|  
  
 Nastavení URI zadejte způsob, jakým rozhraní .NET Framework zpracovává webové adresy vyjádřena pomocí uniform resource Identifier (identifikátory URI). Následující tabulka popisuje funkce každý podřízený element konfigurace v rámci [ \<Uri > – Element (nastavení Uri)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md).  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<IDN > – Element (nastavení Uri)](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|Určuje, pokud analýza mezinárodních názvů domén (IDN) platí pro názvy domén.|  
|[\<iriParsing > – Element (nastavení Uri)](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|Určuje, pokud analýze International Resource Identifier (IRI) se použije k <xref:System.Uri> a určuje, zda by měl použít IRI pravidel pro analýzu.|  
|[\<schemeSettings > – Element (nastavení Uri)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|Určuje, jak <xref:System.Uri> pro konkrétní schémata, bude analyzována.|  
  
## <a name="see-also"></a>Viz také:

- [Konfigurace internetových aplikací](../../../../../docs/framework/network-programming/configuring-internet-applications.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
