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
ms.openlocfilehash: 696aeb619f14a5ebe9a760cbd78a0d0fa876edc0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a><span data-ttu-id="8a366-102">Postupy: Upravte konfigurační soubor počítače. Chcete-li povolit podporu IPv6</span><span class="sxs-lookup"><span data-stu-id="8a366-102">How to: Modify the Computer Configuration File to Enable IPv6 Support</span></span>
<span data-ttu-id="8a366-103">Následující příklad kódu ukazuje, jak upravit konfigurační soubor na počítači, *machine.config*, chcete-li povolit podporu IPv6.</span><span class="sxs-lookup"><span data-stu-id="8a366-103">The following code example shows how to modify the computer configuration file, *machine.config*, to enable IPv6 support.</span></span> <span data-ttu-id="8a366-104">*Machine.config* soubor je uložen v *%Windir%\Microsoft.NET\Framework* složku v adresáři, kde byl nainstalován systém Windows.</span><span class="sxs-lookup"><span data-stu-id="8a366-104">The *machine.config* file is stored in the *%Windir%\Microsoft.NET\Framework* folder in the directory where Windows was installed.</span></span> <span data-ttu-id="8a366-105">Je samostatný *machine.config* ze souborů v části *%Windir%\Microsoft.NET\Framework* pro každou verzi rozhraní .NET Framework na počítači nainstalovaná (třeba *C:\ WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span><span class="sxs-lookup"><span data-stu-id="8a366-105">There is a separate *machine.config* file in the folders under *%Windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer (for example, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span></span>  
  
 <span data-ttu-id="8a366-106">Tato nastavení lze provést také v konfiguračním souboru aplikace, který má vyšší prioritu než konfigurační soubor počítače.</span><span class="sxs-lookup"><span data-stu-id="8a366-106">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="8a366-107">Pro rozhraní .NET Framework verze 1.1 a starší se hodnota **pro protokol ipv6** konfigurace přepínače určuje zda členy <xref:System.Net.Dns?displayProperty=nameWithType> třída vrátit adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="8a366-107">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="8a366-108">Pro rozhraní .NET Framework verze 2.0 nebo novější, pokud systém Windows podporuje protokol IPv6, pak všechny členy <xref:System.Net.Dns?displayProperty=nameWithType> – třída (například <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> metoda), vrátí adresy IPv6 s jedním z omezení.</span><span class="sxs-lookup"><span data-stu-id="8a366-108">For .NET Framework version 2.0 and later, if Windows supports IPv6, then all members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="8a366-109">Zastaralé členy <xref:System.Net.Dns?displayProperty=nameWithType> – třída (například <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> metoda) bude číst a rozpoznat hodnota v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="8a366-109">Obsolete members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a366-110">Pro rozhraní .NET Framework verze 2.0 nebo novější je ve výchozím nastavení povolen protokol IPv6.</span><span class="sxs-lookup"><span data-stu-id="8a366-110">For .NET Framework version 2.0 and later, IPv6 is enabled by default.</span></span> <span data-ttu-id="8a366-111">Pro rozhraní .NET Framework verze 1.1 a starší je ve výchozím nastavení zakázán protokol IPv6.</span><span class="sxs-lookup"><span data-stu-id="8a366-111">For .NET Framework version 1.1 and earlier, IPv6 is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a366-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="8a366-112">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8a366-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="8a366-113">See Also</span></span>  
 [<span data-ttu-id="8a366-114">IPv6 adresy</span><span class="sxs-lookup"><span data-stu-id="8a366-114">IPv6 Addressing</span></span>](../../../docs/framework/network-programming/ipv6-addressing.md)  
 [<span data-ttu-id="8a366-115">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="8a366-115">Network Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [<span data-ttu-id="8a366-116">\<IPv6 > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="8a366-116">\<ipv6> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
