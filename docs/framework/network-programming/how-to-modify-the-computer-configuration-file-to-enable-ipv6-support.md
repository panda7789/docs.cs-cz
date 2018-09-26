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
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a><span data-ttu-id="2f20e-102">Postupy: Úprava konfiguračního souboru počítače na povolení podpory IPv6</span><span class="sxs-lookup"><span data-stu-id="2f20e-102">How to: Modify the Computer Configuration File to Enable IPv6 Support</span></span>
<span data-ttu-id="2f20e-103">Následující příklad kódu ukazuje, jak upravit konfigurační soubor počítače *machine.config*k povolení podpory pro IPv6.</span><span class="sxs-lookup"><span data-stu-id="2f20e-103">The following code example shows how to modify the computer configuration file, *machine.config*, to enable IPv6 support.</span></span> <span data-ttu-id="2f20e-104">*Machine.config* soubor je uložen v *%Windir%\Microsoft.NET\Framework* složky v adresáři, kam se nainstaloval Windows.</span><span class="sxs-lookup"><span data-stu-id="2f20e-104">The *machine.config* file is stored in the *%Windir%\Microsoft.NET\Framework* folder in the directory where Windows was installed.</span></span> <span data-ttu-id="2f20e-105">Neexistuje samostatné *machine.config* souborů ve složkách v rámci *%Windir%\Microsoft.NET\Framework* pro každou verzi rozhraní .NET Framework nainstalované v počítači (například *C:\ WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span><span class="sxs-lookup"><span data-stu-id="2f20e-105">There is a separate *machine.config* file in the folders under *%Windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer (for example, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span></span>  
  
 <span data-ttu-id="2f20e-106">Tato nastavení lze provést také v konfiguračním souboru aplikace, který má vyšší prioritu než konfigurační soubor počítače.</span><span class="sxs-lookup"><span data-stu-id="2f20e-106">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="2f20e-107">Pro rozhraní .NET Framework verze 1.1 nebo starší, hodnota **podporuje protokol ipv6** konfigurační přepínač určuje, zda členové <xref:System.Net.Dns?displayProperty=nameWithType> třídy zpáteční adresu IPv6.</span><span class="sxs-lookup"><span data-stu-id="2f20e-107">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="2f20e-108">Pro rozhraní .NET Framework verze 2.0 nebo novější, pokud Windows podporuje protokol IPv6, pak všichni členové <xref:System.Net.Dns?displayProperty=nameWithType> třídy (například <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> metoda), vrátí adresy IPv6 s jediným omezením.</span><span class="sxs-lookup"><span data-stu-id="2f20e-108">For .NET Framework version 2.0 and later, if Windows supports IPv6, then all members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="2f20e-109">Zastaralé členy <xref:System.Net.Dns?displayProperty=nameWithType> třídy (například <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> metoda) přečte a rozpoznat hodnotu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="2f20e-109">Obsolete members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f20e-110">Pro rozhraní .NET Framework verze 2.0 nebo novější je ve výchozím nastavení povolen protokol IPv6.</span><span class="sxs-lookup"><span data-stu-id="2f20e-110">For .NET Framework version 2.0 and later, IPv6 is enabled by default.</span></span> <span data-ttu-id="2f20e-111">Pro rozhraní .NET Framework verze 1.1 nebo starší je ve výchozím nastavení zakázán protokol IPv6.</span><span class="sxs-lookup"><span data-stu-id="2f20e-111">For .NET Framework version 1.1 and earlier, IPv6 is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f20e-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="2f20e-112">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2f20e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f20e-113">See Also</span></span>  
 [<span data-ttu-id="2f20e-114">Adresování IPv6</span><span class="sxs-lookup"><span data-stu-id="2f20e-114">IPv6 Addressing</span></span>](../../../docs/framework/network-programming/ipv6-addressing.md)  
 [<span data-ttu-id="2f20e-115">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="2f20e-115">Network Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [<span data-ttu-id="2f20e-116">\<IPv6 > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="2f20e-116">\<ipv6> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
