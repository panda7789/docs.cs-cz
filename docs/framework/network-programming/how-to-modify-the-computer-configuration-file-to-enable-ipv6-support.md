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
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a><span data-ttu-id="edf94-102">Postupy: Úpravy konfiguračního souboru počítače na povolení podpory IPv6</span><span class="sxs-lookup"><span data-stu-id="edf94-102">How to: Modify the Computer Configuration File to Enable IPv6 Support</span></span>
<span data-ttu-id="edf94-103">Následující příklad kódu ukazuje, jak upravit konfigurační soubor počítače *machine.config*, aby byla povolena podpora Protokolu IPv6.</span><span class="sxs-lookup"><span data-stu-id="edf94-103">The following code example shows how to modify the computer configuration file, *machine.config*, to enable IPv6 support.</span></span> <span data-ttu-id="edf94-104">Soubor *Machine.config* je uložen ve složce *%Windir%\Microsoft.NET\Framework* v adresáři, ve kterém byl nainstalován systém Windows.</span><span class="sxs-lookup"><span data-stu-id="edf94-104">The *machine.config* file is stored in the *%Windir%\Microsoft.NET\Framework* folder in the directory where Windows was installed.</span></span> <span data-ttu-id="edf94-105">Ve složkách pod položkou *%Windir%\Microsoft.NET\Framework* je samostatný soubor *machine.config* pro každou verzi rozhraní .NET Framework nainstalovanou v počítači (například *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span><span class="sxs-lookup"><span data-stu-id="edf94-105">There is a separate *machine.config* file in the folders under *%Windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer (for example, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span></span>  
  
 <span data-ttu-id="edf94-106">Tato nastavení lze provést také v konfiguračním souboru aplikace, který má vyšší prioritu než konfigurační soubor počítače.</span><span class="sxs-lookup"><span data-stu-id="edf94-106">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="edf94-107">Pro rozhraní .NET Framework verze 1.1 a starší hodnota konfiguračního <xref:System.Net.Dns?displayProperty=nameWithType> přepínače **s povolenou protokolem ipv6** určuje, zda členové třídy vrátí adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="edf94-107">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="edf94-108">Pro rozhraní .NET Framework verze 2.0 a novější, pokud systém <xref:System.Net.Dns?displayProperty=nameWithType> Windows podporuje Protokol <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> IPv6, vrátí všichni členové třídy (například metoda) adresy IPv6 s jedním omezením.</span><span class="sxs-lookup"><span data-stu-id="edf94-108">For .NET Framework version 2.0 and later, if Windows supports IPv6, then all members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="edf94-109">Zastaralé členy <xref:System.Net.Dns?displayProperty=nameWithType> třídy (například <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> metoda) budou číst a rozpoznávat hodnotu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="edf94-109">Obsolete members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="edf94-110">Pro rozhraní .NET Framework verze 2.0 a novější je protokol IPv6 ve výchozím nastavení povolen.</span><span class="sxs-lookup"><span data-stu-id="edf94-110">For .NET Framework version 2.0 and later, IPv6 is enabled by default.</span></span> <span data-ttu-id="edf94-111">U rozhraní .NET Framework verze 1.1 a starší je standardně zakázán systém IPv6.</span><span class="sxs-lookup"><span data-stu-id="edf94-111">For .NET Framework version 1.1 and earlier, IPv6 is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edf94-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="edf94-112">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="edf94-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="edf94-113">See also</span></span>

- [<span data-ttu-id="edf94-114">Adresování IPv6</span><span class="sxs-lookup"><span data-stu-id="edf94-114">IPv6 Addressing</span></span>](ipv6-addressing.md)
- [<span data-ttu-id="edf94-115">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="edf94-115">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="edf94-116">\<Ipv6> Element (Nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="edf94-116">\<ipv6> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
