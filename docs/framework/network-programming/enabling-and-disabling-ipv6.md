---
title: Povolení a zakázání IPv6
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b018d646816bda96945a440a890da20b81b1cbbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393929"
---
# <a name="enabling-and-disabling-ipv6"></a>Povolení a zakázání IPv6
Chcete-li používat protokol IPv6, ujistěte se, že používáte verzi operačního systému, který podporuje protokol IPv6 a ujistěte se, že operační systém a síťové třídy jsou konfigurována správně.  
  
## <a name="configuration-steps"></a>Kroky konfigurace  
 Následující tabulka uvádí různé konfigurace  
  
|Operační systém podporující protokol IPv6?|Sítě třídy povolen protokol IPv6?|Popis|  
|-------------------------------------|---------------------------------------|-----------------|  
|Ne|Ne|Můžete analyzovat adresy IPv6.|  
|Ne|Ano|Můžete analyzovat adresy IPv6.|  
|Ano|Ne|Můžete analyzovat adresy IPv6 a překládat adresy IPv6 pomocí metody rozlišování názvů není označena jako zastaralá.|  
|Ano|Ano|Můžete analyzovat a řešit pomocí všech metod, včetně těch, které označeny jako zastaralé adresy IPv6.|  
  
 Upozorňujeme, že pokud chcete povolit podporu IPv6 pro všechny třídy v oboru názvů System.Net, je třeba upravit konfiguračního souboru počítače nebo konfiguračního souboru pro aplikaci. Konfigurační soubor pro aplikaci, má přednost před konfiguračního souboru počítače.  
  
 Příklad toho, jak upravit konfigurační soubor na počítači *machine.config*, aby Ipv6 podpory najdete [postup: Upravte konfigurační soubor počítače. Chcete-li povolit podporu Ipv6](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md). Ujistěte se také, že je povolena podpora protokolu IPv6 pro operační systém.  
  
 Rozhraní .NET Framework má přepínač konfigurace následujícím způsobem nastavit v konfiguračním souboru  
  
```xml  
<system.net>…  
    <settings>…  
        <ipv6 enabled="true"/>…  
    </settings>…  
</system.net>  
```  
  
 Pro rozhraní .NET Framework verze 1.1 a starší se hodnota **pro protokol ipv6** konfigurace přepínače určuje zda členy <xref:System.Net.Dns?displayProperty=nameWithType> třída vrátit adresy IPv6.  
  
 Pro rozhraní .NET Framework verze 2.0 nebo novější, pokud systém Windows podporuje protokol IPv6 a potom členy <xref:System.Net.Dns?displayProperty=nameWithType> třídy (například <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> metoda), vrátí adresy IPv6 s jedním z omezení. Zastaralé členy DNS <xref:System.Net.Dns?displayProperty=nameWithType> (například <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> metoda) bude číst a rozpoznat hodnota v konfiguračním souboru pro nastavení pro protokol ipv6.  
  
## <a name="see-also"></a>Viz také  
 [Protokol IP (Internet Protocol) verze 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [Sokety](../../../docs/framework/network-programming/sockets.md)  
 [Schéma nastavení sítě](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [\<IPv6 > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
