---
title: Povolení a zákaz IPv6
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 66c802dd5feb865faf7469cb7da04fbffcb4a2d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048566"
---
# <a name="enabling-and-disabling-ipv6"></a>Povolení a zákaz IPv6
Chcete-li použít protokol IPv6, ujistěte se, že používáte verzi operačního systému, která podporuje protokol IPv6, a ujistěte se, že jsou správně nakonfigurovány třídy operačního systému a sítě.  
  
## <a name="configuration-steps"></a>Kroky konfigurace  
 V následující tabulce jsou uvedeny různé konfigurace  
  
|Operační systém s podporou IPv6?|Síťové třídy s podporou IPv6?|Popis|  
|-------------------------------------|---------------------------------------|-----------------|  
|Ne|Ne|Může analyzovat adresy IPv6.|  
|Ne|Ano|Může analyzovat adresy IPv6.|  
|Ano|Ne|Může analyzovat adresy IPv6 a vyřešit adresy IPv6 pomocí metod překladu názvů, které nejsou označeny jako zastaralé.|  
|Ano|Ano|Může analyzovat a vyřešit adresy IPv6 pomocí všech metod, včetně těch, které jsou označeny jako zastaralé.|  
  
 Uvědomte si, že chcete-li povolit podporu Protokolu IPv6 pro všechny třídy v oboru názvů System.Net, je nutné upravit konfigurační soubor počítače nebo konfigurační soubor aplikace. Konfigurační soubor aplikace má přednost před konfiguračním souborem počítače.  
  
 Příklad úpravy konfiguračního souboru počítače *machine.config*, který umožňuje podporu protokolu Ipv6, naleznete v [tématu Jak: Úprava konfiguračního souboru počítače pro povolení podpory ipv6](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md). Také se ujistěte, že je povolena podpora IPv6 pro operační systém.  
  
 Rozhraní .NET Framework má konfigurační přepínač nastavený v konfiguračním souboru následujícím způsobem  
  
```xml  
<system.net>  
  ...  
  <settings>  
    ...  
    <ipv6 enabled="true"/>  
    ...  
  </settings>  
  ...  
</system.net>  
```  
  
 Pro rozhraní .NET Framework verze 1.1 a starší hodnota konfiguračního <xref:System.Net.Dns?displayProperty=nameWithType> přepínače **s povolenou protokolem ipv6** určuje, zda členové třídy vrátí adresy IPv6.  
  
 Pro rozhraní .NET Framework verze 2.0 a novější, pokud systém <xref:System.Net.Dns?displayProperty=nameWithType> Windows podporuje Protokol <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> IPv6, vrátí členové třídy (například metoda) adresy IPv6 s jedním omezením. Zastaralé členy služby DNS <xref:System.Net.Dns?displayProperty=nameWithType> (například <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> metoda) přečtou a rozpozná hodnotu v konfiguračním souboru pro nastavení s povolenou službou ipv6.  
  
## <a name="see-also"></a>Viz také

- [Protokol IP (Internet Protocol) verze 6](internet-protocol-version-6.md)
- [Sokety](sockets.md)
- [Schéma nastavení sítě](../configure-apps/file-schema/network/index.md)
- [\<Ipv6> Element (Nastavení sítě)](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
