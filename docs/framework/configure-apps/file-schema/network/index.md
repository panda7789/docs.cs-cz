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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c080ff7ebef680712581d1f77fd4eb1ec99c6a86
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742611"
---
# <a name="network-settings-schema"></a>Schéma nastavení sítě
Nastavení sítě určete, jak rozhraní .NET Framework připojuje k Internetu. Následující tabulka popisuje funkci jednotlivých podřízených prvků konfigurace v části [ \<system.Net > elementu (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md).  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<authenticationModules – > elementu (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|Určuje moduly používané k ověřování žádostí o Internetu.|  
|[\<connectionManagement – > elementu (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|Určuje maximální počet připojení k hostiteli v síti Internet.|  
|[\<defaultProxy – > elementu (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Určuje proxy server používá pro požadavky HTTP na Internetu.|  
|[\<mailSettings – > elementu (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|Obsahuje nastavení pro e-mailu odesílání možnosti.|  
|[\<requestCaching – > elementu (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Určuje moduly používané pro vyžádání informací z Internetu hostitelů.|  
|[\<requestCaching – > elementu (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Nakonfiguruje možnosti základní sítě <xref:System.Net?displayProperty=nameWithType> oboru názvů.|  
|[\<webRequestModules – > elementu (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Určuje moduly používané pro vyžádání informací z Internetu hostitelů.|  
  
 Identifikátor URI nastavení určují, jak rozhraní .NET Framework zpracovává webové adresy vyjádřit pomocí identifikátorů URI (URI). Následující tabulka popisuje funkci jednotlivých podřízených prvků konfigurace v části [ \<Uri > elementu (nastavení Uri)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md).  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<IDN > elementu (nastavení Uri)](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|Určuje, pokud analýza mezinárodní název domény (IDN) se použijí pro názvy domén.|  
|[\<iriParsing > – Element (nastavení Uri)](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|Určuje, zda analýza mezinárodní prostředků identifikátor (IRI) je použita k <xref:System.Uri> a zda má být použita IRI Analýza pravidla.|  
|[\<schemeSettings > – Element (nastavení Uri)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|Určuje, jak <xref:System.Uri> bude analyzovat pro konkrétní schémat.|  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace internetových aplikací](../../../../../docs/framework/network-programming/configuring-internet-applications.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
