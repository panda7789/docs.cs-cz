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
ms.openlocfilehash: 0f5d762a2b688bebcb7c027be6c639b6d64c069d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664108"
---
# <a name="network-settings-schema"></a>Schéma nastavení sítě
Nastavení sítě určují, jak se .NET Framework připojí k Internetu. Následující tabulka popisuje funkci každého podřízeného prvku konfigurace pod [ \<prvkem System .NET > (nastavení sítě)](system-net-element-network-settings.md).  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<authenticationModules – element > (nastavení sítě)](authenticationmodules-element-network-settings.md)|Určuje moduly používané pro ověřování internetových požadavků.|  
|[\<connectionManagement – element > (nastavení sítě)](connectionmanagement-element-network-settings.md)|Určuje maximální počet připojení k hostitelům v Internetu.|  
|[\<defaultProxy – element > (nastavení sítě)](defaultproxy-element-network-settings.md)|Určuje proxy server, který se používá pro požadavky HTTP na Internet.|  
|[\<mailSettings – element > (nastavení sítě)](mailsettings-element-network-settings.md)|Obsahuje nastavení pro možnosti odesílání pošty.|  
|[\<requestCaching – element > (nastavení sítě)](requestcaching-element-network-settings.md)|Řídí mechanismus ukládání do mezipaměti pro síťové požadavky.|  
|[\<webRequestModules – element > (nastavení sítě)](webrequestmodules-element-network-settings.md)|Určuje moduly, které se používají k vyžádání informací od hostitelů v Internetu.|  
  
 Nastavení identifikátoru URI určuje způsob, jakým .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů URI (Uniform Resource Identifier). Následující tabulka popisuje funkci každého podřízeného prvku konfigurace pod [ \<identifikátorem URI > element (nastavení URI)](uri-element-uri-settings.md).  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Element > IDN (nastavení URI)](idn-element-uri-settings.md)|Určuje, jestli se pro názvy domén použije analýza v mezinárodním názvu domény (IDN).|  
|[\<iriParsing – element > (nastavení URI)](iriparsing-element-uri-settings.md)|Určuje, jestli se <xref:System.Uri> má použít analýza mezinárodní identifikátoru prostředků (IRI) a jestli se mají použít pravidla analýzy IRI.|  
|[\<schemeSettings – element > (nastavení URI)](schemesettings-element-uri-settings.md)|Určuje, jak <xref:System.Uri> se bude analyzovat pro konkrétní schémata.|  
  
## <a name="see-also"></a>Viz také:

- [Konfigurace internetových aplikací](../../../network-programming/configuring-internet-applications.md)
- [Schéma konfiguračního souboru](../index.md)
