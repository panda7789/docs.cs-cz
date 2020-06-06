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
ms.openlocfilehash: 5e3bd1b1734fc7fba50b72785531a8b001d6d741
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "71698154"
---
# <a name="network-settings-schema"></a>Schéma nastavení sítě
Nastavení sítě určují, jak se .NET Framework připojí k Internetu.

\<system.net>Nastavení určuje, jak se .NET Framework připojí k síti. Následující tabulka popisuje funkci každého podřízeného elementu konfigurace pod [ \<system.Net> elementem (nastavení sítě)](system-net-element-network-settings.md).  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<authenticationModules>– Element (nastavení sítě)](authenticationmodules-element-network-settings.md)|Určuje moduly používané pro ověřování internetových požadavků.|  
|[\<connectionManagement>– Element (nastavení sítě)](connectionmanagement-element-network-settings.md)|Určuje maximální počet připojení k hostitelům v Internetu.|  
|[\<defaultProxy>– Element (nastavení sítě)](defaultproxy-element-network-settings.md)|Určuje proxy server, který se používá pro požadavky HTTP na Internet.|  
|[\<mailSettings>– Element (nastavení sítě)](mailsettings-element-network-settings.md)|Obsahuje nastavení pro možnosti odesílání pošty.|  
|[\<requestCaching>– Element (nastavení sítě)](requestcaching-element-network-settings.md)|Řídí mechanismus ukládání do mezipaměti pro síťové požadavky.|  
|[\<webRequestModules>– Element (nastavení sítě)](webrequestmodules-element-network-settings.md)|Určuje moduly, které se používají k vyžádání informací od hostitelů v Internetu.|  
  
\<uri>Nastavení určuje způsob, jakým .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů URI (Uniform Resource Identifier). Následující tabulka popisuje funkci každého podřízeného elementu konfigurace pod [ \<uri> elementem (nastavení URI)](uri-element-uri-settings.md).  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<idn>– Element (nastavení URI)](idn-element-uri-settings.md)|Určuje, jestli se pro názvy domén použije analýza v mezinárodním názvu domény (IDN).|  
|[\<iriParsing>– Element (nastavení URI)](iriparsing-element-uri-settings.md)|Určuje, jestli se má použít analýza mezinárodní identifikátoru prostředků (IRI) <xref:System.Uri> a jestli se mají použít pravidla analýzy IRI.|  
|[\<schemeSettings>– Element (nastavení URI)](schemesettings-element-uri-settings.md)|Určuje, jak se <xref:System.Uri> bude analyzovat pro konkrétní schémata.|  
  
## <a name="see-also"></a>Viz také

- [Konfigurace internetových aplikací](../../../network-programming/configuring-internet-applications.md)
- [Schéma konfiguračního souboru](../index.md)
