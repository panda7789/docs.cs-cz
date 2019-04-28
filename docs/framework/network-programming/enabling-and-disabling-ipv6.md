---
title: Povolení a zákaz IPv6
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 73dee0cb57674c8a2fa4ba2246162870ab1e3a10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643098"
---
# <a name="enabling-and-disabling-ipv6"></a>Povolení a zákaz IPv6
Pokud chcete použít protokol IPv6, ujistěte se, že používáte verzi operačního systému, který podporuje protokol IPv6 a zajistit správnou konfiguraci operačního systému a síťové třídy.  
  
## <a name="configuration-steps"></a>Postup konfigurace  
 V následující tabulce jsou uvedeny různé konfigurace  
  
|Operační systém podporující protokol IPv6?|Síťové třídy povolen protokol IPv6?|Popis|  
|-------------------------------------|---------------------------------------|-----------------|  
|Ne|Ne|Můžete analyzovat adresy IPv6.|  
|Ne|Ano|Můžete analyzovat adresy IPv6.|  
|Ano|Ne|Můžete analyzovat adresy IPv6 a překládat adresy IPv6 pomocí metody rozlišování názvů není označená jako zastaralá.|  
|Ano|Ano|Můžete analyzovat a řešit adres IPv6 pomocí všech metod, včetně těch, které označená jako zastaralá.|  
  
 Mějte na paměti, že pokud chcete povolit podporu protokolu IPv6 pro všechny třídy v oboru názvů System.Net, je třeba upravit konfigurační soubor počítače nebo konfiguračního souboru aplikace. Konfigurační soubor aplikace má vyšší prioritu než konfigurační soubor počítače.  
  
 Příklad toho, jak upravit konfigurační soubor počítače *machine.config*k povolení podpory naleznete v protokolu Ipv6, [jak: Upravte konfigurační soubor počítače na povolení podpory Ipv6](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md). Také se ujistěte, že je povolena podpora protokolu IPv6 pro operační systém.  
  
 Rozhraní .NET Framework obsahuje konfigurační přepínač, nastavte v konfiguračním souboru následujícím způsobem  
  
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
  
 Pro rozhraní .NET Framework verze 1.1 nebo starší, hodnota **podporuje protokol ipv6** konfigurační přepínač určuje, zda členové <xref:System.Net.Dns?displayProperty=nameWithType> třídy zpáteční adresu IPv6.  
  
 Pro rozhraní .NET Framework verze 2.0 nebo novější, pokud Windows podporuje protokol IPv6 a členy <xref:System.Net.Dns?displayProperty=nameWithType> třídy, (například <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> metoda), vrátí adresy IPv6 s jediným omezením. Zastaralé členy DNS <xref:System.Net.Dns?displayProperty=nameWithType> (například <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> metoda) přečte a rozpoznat hodnotu v konfiguračním souboru pro nastavení podporuje protokol ipv6.  
  
## <a name="see-also"></a>Viz také:

- [Protokol IP (Internet Protocol) verze 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)
- [Sokety](../../../docs/framework/network-programming/sockets.md)
- [Schéma nastavení sítě](../../../docs/framework/configure-apps/file-schema/network/index.md)
- [\<IPv6 > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
