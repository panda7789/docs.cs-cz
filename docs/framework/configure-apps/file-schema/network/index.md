---
title: Schéma nastavení sítě
description: Přečtěte si o schématu nastavení sítě, které určuje, jak se .NET Framework připojuje k Internetu a zpracovává identifikátory URI.
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
ms.openlocfilehash: 6a22d7f1608db2e8909d0ead11e9110ec8a8a2c5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504573"
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
  
## <a name="see-also"></a>Viz také:

- [Konfigurace internetových aplikací](../../../network-programming/configuring-internet-applications.md)
- [Schéma konfiguračního souboru](../index.md)
