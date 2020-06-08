---
title: Povolení a zákaz IPv6
description: Pomocí těchto kroků konfigurace povolte použití protokolu IPv6, včetně úprav konfiguračního souboru pro počítač nebo aplikaci.
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 7729647b09df20a98d5d639a641cb0a31f557330
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502610"
---
# <a name="enabling-and-disabling-ipv6"></a>Povolení a zákaz IPv6
Chcete-li použít protokol IPv6, ujistěte se, že používáte verzi operačního systému, která podporuje protokol IPv6, a ujistěte se, že jsou správně nakonfigurovány operační systém a síťové třídy.  
  
## <a name="configuration-steps"></a>Kroky konfigurace  
 V následující tabulce jsou uvedeny různé konfigurace  
  
|Je povolený protokol IPv6 operačního systému?|Síťové třídy podporující protokol IPv6?|Description|  
|-------------------------------------|---------------------------------------|-----------------|  
|Ne|Ne|Může analyzovat adresy IPv6.|  
|No|Ano|Může analyzovat adresy IPv6.|  
|Ano|Ne|Dokáže analyzovat adresy IPv6 a překládat adresy IPv6 pomocí metod překladu názvů, které nejsou označené jako zastaralé.|  
|Ano|Ano|Může analyzovat a řešit adresy IPv6 pomocí všech metod, včetně těch, které jsou označené jako zastaralé.|  
  
 Uvědomte si, že pokud chcete povolit podporu IPv6 pro všechny třídy v oboru názvů System.Net, musíte upravit konfigurační soubor počítače nebo konfigurační soubor pro aplikaci. Konfigurační soubor aplikace má přednost před konfiguračním souborem počítače.  
  
 Příklad úprav konfiguračního souboru počítače *Machine. config*, který umožňuje podporu protokolu IPv6, najdete v tématu [Postupy: Změna konfiguračního souboru počítače pro povolení podpory protokolu IPv6](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md). Také se ujistěte, že je pro operační systém povolena podpora protokolu IPv6.  
  
 .NET Framework má konfigurační přepínač nastavený v konfiguračním souboru následujícím způsobem.  
  
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
  
 U .NET Framework verze 1,1 a starší určuje hodnota přepínače konfigurace s **povoleným protokolem IPv6** , zda členové <xref:System.Net.Dns?displayProperty=nameWithType> třídy vrací IPv6 adresy.  
  
 Pro .NET Framework verze 2,0 a novější, pokud systém Windows podporuje protokol IPv6, pak členové <xref:System.Net.Dns?displayProperty=nameWithType> třídy (například <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> Metoda) vrátí adresy IPv6 s jedním omezením. Zastaralí členové DNS <xref:System.Net.Dns?displayProperty=nameWithType> (například <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> Metoda) přečtou a rozpoznají hodnotu v konfiguračním souboru pro nastavení s povoleným protokolem IPv6.  
  
## <a name="see-also"></a>Viz také:

- [Protokol IP (Internet Protocol) verze 6](internet-protocol-version-6.md)
- [Sokety](sockets.md)
- [Schéma nastavení sítě](../configure-apps/file-schema/network/index.md)
- [\<ipv6>– Element (nastavení sítě)](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
