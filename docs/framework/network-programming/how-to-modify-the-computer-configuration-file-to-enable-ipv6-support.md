---
title: 'Postupy: Úpravy konfiguračního souboru počítače na povolení podpory IPv6'
ms.date: 03/30/2017
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
ms.openlocfilehash: af6eb8a334108c988967a555024b524e27d40f58
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959080"
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a><span data-ttu-id="25c03-102">Postupy: Úpravy konfiguračního souboru počítače na povolení podpory IPv6</span><span class="sxs-lookup"><span data-stu-id="25c03-102">How to: Modify the Computer Configuration File to Enable IPv6 Support</span></span>
<span data-ttu-id="25c03-103">Následující příklad kódu ukazuje, jak upravit konfigurační soubor počítače, *Machine. config*, aby byla povolena podpora protokolu IPv6.</span><span class="sxs-lookup"><span data-stu-id="25c03-103">The following code example shows how to modify the computer configuration file, *machine.config*, to enable IPv6 support.</span></span> <span data-ttu-id="25c03-104">Soubor *Machine. config* je uložen ve složce *%windir%\Microsoft.NET\Framework* v adresáři, ve kterém byl nainstalován systém Windows.</span><span class="sxs-lookup"><span data-stu-id="25c03-104">The *machine.config* file is stored in the *%Windir%\Microsoft.NET\Framework* folder in the directory where Windows was installed.</span></span> <span data-ttu-id="25c03-105">Ve složkách v *%windir%\Microsoft.NET\Framework* je k dispozici samostatný soubor *Machine. config* pro každou verzi .NET Framework nainstalovanou v počítači (například *C:\Windows\Microsoft.NET\Framework\v2.0.50727\ Machine. config*).</span><span class="sxs-lookup"><span data-stu-id="25c03-105">There is a separate *machine.config* file in the folders under *%Windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer (for example, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span></span>  
  
 <span data-ttu-id="25c03-106">Tato nastavení lze provést také v konfiguračním souboru aplikace, který má vyšší prioritu než konfigurační soubor počítače.</span><span class="sxs-lookup"><span data-stu-id="25c03-106">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="25c03-107">U .NET Framework verze 1,1 a starší určuje hodnota přepínače konfigurace s **povoleným protokolem IPv6** , zda členové <xref:System.Net.Dns?displayProperty=nameWithType> třídy vrací IPv6 adresy.</span><span class="sxs-lookup"><span data-stu-id="25c03-107">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="25c03-108">Pro .NET Framework verze 2,0 a novější, pokud systém Windows podporuje protokol IPv6, pak všichni členové <xref:System.Net.Dns?displayProperty=nameWithType> třídy (například <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> Metoda) vrátí adresy IPv6 s jediným omezením.</span><span class="sxs-lookup"><span data-stu-id="25c03-108">For .NET Framework version 2.0 and later, if Windows supports IPv6, then all members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="25c03-109">Zastaralí členové <xref:System.Net.Dns?displayProperty=nameWithType> třídy (například <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> Metoda) přečtou a rozpoznají hodnotu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="25c03-109">Obsolete members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25c03-110">Pro .NET Framework verze 2,0 a novější je ve výchozím nastavení povolen protokol IPv6.</span><span class="sxs-lookup"><span data-stu-id="25c03-110">For .NET Framework version 2.0 and later, IPv6 is enabled by default.</span></span> <span data-ttu-id="25c03-111">Pro .NET Framework verze 1,1 a starší je protokol IPv6 ve výchozím nastavení zakázaný.</span><span class="sxs-lookup"><span data-stu-id="25c03-111">For .NET Framework version 1.1 and earlier, IPv6 is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25c03-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="25c03-112">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="25c03-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25c03-113">See also</span></span>

- [<span data-ttu-id="25c03-114">Adresování IPv6</span><span class="sxs-lookup"><span data-stu-id="25c03-114">IPv6 Addressing</span></span>](../../../docs/framework/network-programming/ipv6-addressing.md)
- [<span data-ttu-id="25c03-115">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="25c03-115">Network Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="25c03-116">\<> – element IPv6 (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="25c03-116">\<ipv6> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
