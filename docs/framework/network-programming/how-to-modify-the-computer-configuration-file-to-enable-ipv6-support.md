---
title: 'Postupy: Úpravy konfiguračního souboru počítače na povolení podpory IPv6'
description: Naučte se, jak upravit konfigurační soubor počítače, Machine. config a povolit podporu protokolu IPv6 v .NET Framework.
ms.date: 03/30/2017
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
ms.openlocfilehash: eb7b3665c0dbcf0edefa8c48a9e69297d7259067
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502519"
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a>Postupy: Úpravy konfiguračního souboru počítače na povolení podpory IPv6
Následující příklad kódu ukazuje, jak upravit konfigurační soubor počítače, *Machine. config*, aby byla povolena podpora protokolu IPv6. Soubor *Machine. config* je uložen ve složce *%windir%\Microsoft.NET\Framework* v adresáři, ve kterém byl nainstalován systém Windows. Ve složkách v *%windir%\Microsoft.NET\Framework* je k dispozici samostatný soubor *Machine. config* pro každou verzi .NET Framework nainstalovanou v počítači (například *C:\Windows\Microsoft.NET\Framework\v2.0.50727\machine.config*).  
  
 Tato nastavení lze provést také v konfiguračním souboru aplikace, který má vyšší prioritu než konfigurační soubor počítače.  
  
 U .NET Framework verze 1,1 a starší určuje hodnota přepínače konfigurace s **povoleným protokolem IPv6** , zda členové <xref:System.Net.Dns?displayProperty=nameWithType> třídy vrací IPv6 adresy.  
  
 Pro .NET Framework verze 2,0 a novější, pokud systém Windows podporuje protokol IPv6, pak všichni členové <xref:System.Net.Dns?displayProperty=nameWithType> třídy (například <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> Metoda) vrátí adresy IPv6 s jediným omezením. Zastaralí členové <xref:System.Net.Dns?displayProperty=nameWithType> třídy (například <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> Metoda) přečtou a rozpoznají hodnotu v konfiguračním souboru.  
  
> [!NOTE]
> Pro .NET Framework verze 2,0 a novější je ve výchozím nastavení povolen protokol IPv6. Pro .NET Framework verze 1,1 a starší je protokol IPv6 ve výchozím nastavení zakázaný.  
  
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
</system.net>  
```  
  
## <a name="see-also"></a>Viz také:

- [Adresování IPv6](ipv6-addressing.md)
- [Schéma nastavení sítě](../configure-apps/file-schema/network/index.md)
- [\<ipv6>– Element (nastavení sítě)](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
