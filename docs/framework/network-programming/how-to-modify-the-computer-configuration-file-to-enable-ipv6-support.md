---
title: 'Postupy: Úpravy konfiguračního souboru počítače na povolení podpory IPv6'
ms.date: 03/30/2017
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
ms.openlocfilehash: 362e7af36d214df9f0454479e25a80af9d440b2b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048276"
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a>Postupy: Úpravy konfiguračního souboru počítače na povolení podpory IPv6
Následující příklad kódu ukazuje, jak upravit konfigurační soubor počítače, *Machine. config*, aby byla povolena podpora protokolu IPv6. Soubor *Machine. config* je uložen ve složce *%windir%\Microsoft.NET\Framework* v adresáři, ve kterém byl nainstalován systém Windows. Ve složkách v *%windir%\Microsoft.NET\Framework* je k dispozici samostatný soubor *Machine. config* pro každou verzi .NET Framework nainstalovanou v počítači (například *C:\Windows\Microsoft.NET\Framework\v2.0.50727\ Machine. config*).  
  
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
<system.net>  
```  
  
## <a name="see-also"></a>Viz také:

- [Adresování IPv6](ipv6-addressing.md)
- [Schéma nastavení sítě](../configure-apps/file-schema/network/index.md)
- [\<> – element IPv6 (nastavení sítě)](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
