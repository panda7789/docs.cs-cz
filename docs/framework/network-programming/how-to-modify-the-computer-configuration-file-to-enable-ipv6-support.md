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
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a><span data-ttu-id="a2b87-103">Postupy: Úpravy konfiguračního souboru počítače na povolení podpory IPv6</span><span class="sxs-lookup"><span data-stu-id="a2b87-103">How to: Modify the Computer Configuration File to Enable IPv6 Support</span></span>
<span data-ttu-id="a2b87-104">Následující příklad kódu ukazuje, jak upravit konfigurační soubor počítače, *Machine. config*, aby byla povolena podpora protokolu IPv6.</span><span class="sxs-lookup"><span data-stu-id="a2b87-104">The following code example shows how to modify the computer configuration file, *machine.config*, to enable IPv6 support.</span></span> <span data-ttu-id="a2b87-105">Soubor *Machine. config* je uložen ve složce *%windir%\Microsoft.NET\Framework* v adresáři, ve kterém byl nainstalován systém Windows.</span><span class="sxs-lookup"><span data-stu-id="a2b87-105">The *machine.config* file is stored in the *%Windir%\Microsoft.NET\Framework* folder in the directory where Windows was installed.</span></span> <span data-ttu-id="a2b87-106">Ve složkách v *%windir%\Microsoft.NET\Framework* je k dispozici samostatný soubor *Machine. config* pro každou verzi .NET Framework nainstalovanou v počítači (například *C:\Windows\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span><span class="sxs-lookup"><span data-stu-id="a2b87-106">There is a separate *machine.config* file in the folders under *%Windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer (for example, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span></span>  
  
 <span data-ttu-id="a2b87-107">Tato nastavení lze provést také v konfiguračním souboru aplikace, který má vyšší prioritu než konfigurační soubor počítače.</span><span class="sxs-lookup"><span data-stu-id="a2b87-107">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="a2b87-108">U .NET Framework verze 1,1 a starší určuje hodnota přepínače konfigurace s **povoleným protokolem IPv6** , zda členové <xref:System.Net.Dns?displayProperty=nameWithType> třídy vrací IPv6 adresy.</span><span class="sxs-lookup"><span data-stu-id="a2b87-108">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="a2b87-109">Pro .NET Framework verze 2,0 a novější, pokud systém Windows podporuje protokol IPv6, pak všichni členové <xref:System.Net.Dns?displayProperty=nameWithType> třídy (například <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> Metoda) vrátí adresy IPv6 s jediným omezením.</span><span class="sxs-lookup"><span data-stu-id="a2b87-109">For .NET Framework version 2.0 and later, if Windows supports IPv6, then all members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="a2b87-110">Zastaralí členové <xref:System.Net.Dns?displayProperty=nameWithType> třídy (například <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> Metoda) přečtou a rozpoznají hodnotu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="a2b87-110">Obsolete members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2b87-111">Pro .NET Framework verze 2,0 a novější je ve výchozím nastavení povolen protokol IPv6.</span><span class="sxs-lookup"><span data-stu-id="a2b87-111">For .NET Framework version 2.0 and later, IPv6 is enabled by default.</span></span> <span data-ttu-id="a2b87-112">Pro .NET Framework verze 1,1 a starší je protokol IPv6 ve výchozím nastavení zakázaný.</span><span class="sxs-lookup"><span data-stu-id="a2b87-112">For .NET Framework version 1.1 and earlier, IPv6 is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2b87-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="a2b87-113">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a2b87-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a2b87-114">See also</span></span>

- [<span data-ttu-id="a2b87-115">Adresování IPv6</span><span class="sxs-lookup"><span data-stu-id="a2b87-115">IPv6 Addressing</span></span>](ipv6-addressing.md)
- [<span data-ttu-id="a2b87-116">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="a2b87-116">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="a2b87-117">\<ipv6>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="a2b87-117">\<ipv6> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
