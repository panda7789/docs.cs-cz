---
title: "Postupy: Upravte konfigurační soubor počítače. Chcete-li povolit podporu IPv6"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
caps.latest.revision: "18"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: df0281d3be467309d2ee7a44af8f897885a8b2bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a>Postupy: Upravte konfigurační soubor počítače. Chcete-li povolit podporu IPv6
Následující příklad kódu ukazuje, jak upravit konfigurační soubor na počítači, *machine.config*, chcete-li povolit podporu IPv6. *Machine.config* soubor je uložen v *%Windir%\Microsoft.NET\Framework* složku v adresáři, kde byl nainstalován systém Windows. Je samostatný *machine.config* ze souborů v části *%Windir%\Microsoft.NET\Framework* pro každou verzi rozhraní .NET Framework na počítači nainstalovaná (třeba *C:\ WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).  
  
 Tato nastavení lze provést také v konfiguračním souboru aplikace, který má vyšší prioritu než konfigurační soubor počítače.  
  
 Pro rozhraní .NET Framework verze 1.1 a starší se hodnota **pro protokol ipv6** konfigurace přepínače určuje zda členy <xref:System.Net.Dns?displayProperty=nameWithType> třída vrátit adresy IPv6.  
  
 Pro rozhraní .NET Framework verze 2.0 nebo novější, pokud systém Windows podporuje protokol IPv6, pak všechny členy <xref:System.Net.Dns?displayProperty=nameWithType> – třída (například <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> metoda), vrátí adresy IPv6 s jedním z omezení. Zastaralé členy <xref:System.Net.Dns?displayProperty=nameWithType> – třída (například <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> metoda) bude číst a rozpoznat hodnota v konfiguračním souboru.  
  
> [!NOTE]
>  Pro rozhraní .NET Framework verze 2.0 nebo novější je ve výchozím nastavení povolen protokol IPv6. Pro rozhraní .NET Framework verze 1.1 a starší je ve výchozím nastavení zakázán protokol IPv6.  
  
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
 [\<IPv6 > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
