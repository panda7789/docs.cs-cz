---
title: 'Postupy: Úprava konfiguračního souboru počítače na povolení podpory IPv6'
ms.date: 03/30/2017
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 77ad110a4f087ff21395fe4330793f8a1928b275
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075720"
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a>Postupy: Úprava konfiguračního souboru počítače na povolení podpory IPv6
Následující příklad kódu ukazuje, jak upravit konfigurační soubor počítače *machine.config*k povolení podpory pro IPv6. *Machine.config* soubor je uložen v *%Windir%\Microsoft.NET\Framework* složky v adresáři, kam se nainstaloval Windows. Neexistuje samostatné *machine.config* souborů ve složkách v rámci *%Windir%\Microsoft.NET\Framework* pro každou verzi rozhraní .NET Framework nainstalované v počítači (například *C:\ WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).  
  
 Tato nastavení lze provést také v konfiguračním souboru aplikace, který má vyšší prioritu než konfigurační soubor počítače.  
  
 Pro rozhraní .NET Framework verze 1.1 nebo starší, hodnota **podporuje protokol ipv6** konfigurační přepínač určuje, zda členové <xref:System.Net.Dns?displayProperty=nameWithType> třídy zpáteční adresu IPv6.  
  
 Pro rozhraní .NET Framework verze 2.0 nebo novější, pokud Windows podporuje protokol IPv6, pak všichni členové <xref:System.Net.Dns?displayProperty=nameWithType> třídy (například <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> metoda), vrátí adresy IPv6 s jediným omezením. Zastaralé členy <xref:System.Net.Dns?displayProperty=nameWithType> třídy (například <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> metoda) přečte a rozpoznat hodnotu v konfiguračním souboru.  
  
> [!NOTE]
>  Pro rozhraní .NET Framework verze 2.0 nebo novější je ve výchozím nastavení povolen protokol IPv6. Pro rozhraní .NET Framework verze 1.1 nebo starší je ve výchozím nastavení zakázán protokol IPv6.  
  
## <a name="example"></a>Příklad  
  
```xml  
<system.net>  
    …………  
    <settings>  
        …………  
        <ipv6 enabled="true"/>   
    ……………  
    </settings>  
    ………………  
<system.net>  
```  
  
## <a name="see-also"></a>Viz také  
 [Adresování IPv6](../../../docs/framework/network-programming/ipv6-addressing.md)  
 [Schéma nastavení sítě](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [\<IPv6 > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
