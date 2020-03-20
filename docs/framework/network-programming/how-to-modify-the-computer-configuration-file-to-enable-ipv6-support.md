---
title: 'Postupy: Úpravy konfiguračního souboru počítače na povolení podpory IPv6'
ms.date: 03/30/2017
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
ms.openlocfilehash: 73408afe9fcb35daa898c08b087a3411a6cb342b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180806"
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a>Postupy: Úpravy konfiguračního souboru počítače na povolení podpory IPv6
Následující příklad kódu ukazuje, jak upravit konfigurační soubor počítače *machine.config*, aby byla povolena podpora Protokolu IPv6. Soubor *Machine.config* je uložen ve složce *%Windir%\Microsoft.NET\Framework* v adresáři, ve kterém byl nainstalován systém Windows. Ve složkách pod položkou *%Windir%\Microsoft.NET\Framework* je samostatný soubor *machine.config* pro každou verzi rozhraní .NET Framework nainstalovanou v počítači (například *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).  
  
 Tato nastavení lze provést také v konfiguračním souboru aplikace, který má vyšší prioritu než konfigurační soubor počítače.  
  
 Pro rozhraní .NET Framework verze 1.1 a starší hodnota konfiguračního <xref:System.Net.Dns?displayProperty=nameWithType> přepínače **s povolenou protokolem ipv6** určuje, zda členové třídy vrátí adresy IPv6.  
  
 Pro rozhraní .NET Framework verze 2.0 a novější, pokud systém <xref:System.Net.Dns?displayProperty=nameWithType> Windows podporuje Protokol <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> IPv6, vrátí všichni členové třídy (například metoda) adresy IPv6 s jedním omezením. Zastaralé členy <xref:System.Net.Dns?displayProperty=nameWithType> třídy (například <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> metoda) budou číst a rozpoznávat hodnotu v konfiguračním souboru.  
  
> [!NOTE]
> Pro rozhraní .NET Framework verze 2.0 a novější je protokol IPv6 ve výchozím nastavení povolen. U rozhraní .NET Framework verze 1.1 a starší je standardně zakázán systém IPv6.  
  
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
  
## <a name="see-also"></a>Viz také

- [Adresování IPv6](ipv6-addressing.md)
- [Schéma nastavení sítě](../configure-apps/file-schema/network/index.md)
- [\<Ipv6> Element (Nastavení sítě)](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
