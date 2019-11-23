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
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698154"
---
# <a name="network-settings-schema"></a>Schéma nastavení sítě
Nastavení sítě určují, jak se .NET Framework připojí k Internetu.

Nastavení \<System. NET > určují, jak se .NET Framework připojí k síti. Následující tabulka popisuje funkci každého podřízeného prvku konfigurace pod [prvkem\<System .net > elementu (nastavení sítě)](system-net-element-network-settings.md).  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<element > authenticationModules (nastavení sítě)](authenticationmodules-element-network-settings.md)|Určuje moduly používané pro ověřování internetových požadavků.|  
|[\<element > connectionManagement (nastavení sítě)](connectionmanagement-element-network-settings.md)|Určuje maximální počet připojení k hostitelům v Internetu.|  
|[\<element > defaultProxy (nastavení sítě)](defaultproxy-element-network-settings.md)|Určuje proxy server, který se používá pro požadavky HTTP na Internet.|  
|[\<element > mailSettings (nastavení sítě)](mailsettings-element-network-settings.md)|Obsahuje nastavení pro možnosti odesílání pošty.|  
|[\<element > requestCaching (nastavení sítě)](requestcaching-element-network-settings.md)|Řídí mechanismus ukládání do mezipaměti pro síťové požadavky.|  
|[\<element > webRequestModules (nastavení sítě)](webrequestmodules-element-network-settings.md)|Určuje moduly, které se používají k vyžádání informací od hostitelů v Internetu.|  
  
Nastavení > identifikátoru URI \<určují, jak .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů URI (Uniform Resource Identifier). Následující tabulka popisuje funkci každého podřízeného prvku konfigurace pod [\<identifikátor uri > elementu (nastavení URI)](uri-element-uri-settings.md).  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<element IDN > (nastavení URI)](idn-element-uri-settings.md)|Určuje, jestli se pro názvy domén použije analýza v mezinárodním názvu domény (IDN).|  
|[\<element > iriParsing (nastavení URI)](iriparsing-element-uri-settings.md)|Určuje, jestli se má u <xref:System.Uri> použít analýza mezinárodního identifikátoru prostředků (IRI) a jestli se mají použít pravidla analýzy IRI.|  
|[\<element > schemeSettings (nastavení URI)](schemesettings-element-uri-settings.md)|Určuje, jak se bude <xref:System.Uri> analyzovat pro konkrétní schémata.|  
  
## <a name="see-also"></a>Viz také:

- [Konfigurace internetových aplikací](../../../network-programming/configuring-internet-applications.md)
- [Schéma konfiguračního souboru](../index.md)
