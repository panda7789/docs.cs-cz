---
title: WCF a mezinárodní názvy domén
ms.date: 03/30/2017
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
ms.openlocfilehash: 1db62f3e7d073fd1bf9bf9d4d0e17703310f2e69
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988586"
---
# <a name="wcf-and-internationalized-domain-names"></a><span data-ttu-id="5a449-102">WCF a mezinárodní názvy domén</span><span class="sxs-lookup"><span data-stu-id="5a449-102">WCF and Internationalized Domain Names</span></span>
<span data-ttu-id="5a449-103">Přidala se podpora, aby služba WCF mohla používat mezinárodní názvy domén (IDN).</span><span class="sxs-lookup"><span data-stu-id="5a449-103">Support has been added to allow for WCF services with Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="5a449-104">Mezinárodní název domény je název domény, který obsahuje jiné znaky než ASCII.</span><span class="sxs-lookup"><span data-stu-id="5a449-104">An internationalized domain name is a domain name that contains non-ASCII characters.</span></span> <span data-ttu-id="5a449-105">Tato podpora zahrnuje možnost hostování služby WCF s názvem IDN a klientem WCF pro komunikaci s webovou službou s názvem IDN.</span><span class="sxs-lookup"><span data-stu-id="5a449-105">This support includes both the ability to host a WCF service with an IDN name and a WCF client to talk to a web service with an IDN name.</span></span>  
  
## <a name="systemuri-and-idn"></a><span data-ttu-id="5a449-106">System. URI a IDN</span><span class="sxs-lookup"><span data-stu-id="5a449-106">System.Uri and IDN</span></span>  
 <span data-ttu-id="5a449-107"><xref:System.Uri>má dvě vlastnosti <xref:System.Uri.Host%2A> a <xref:System.Uri.DnsSafeHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="5a449-107"><xref:System.Uri> has two properties <xref:System.Uri.Host%2A> and <xref:System.Uri.DnsSafeHost%2A>.</span></span> <span data-ttu-id="5a449-108">Tyto vlastnosti obsahují hodnoty Unicode nebo Punycode v závislosti na nastavení konfigurace IDN.</span><span class="sxs-lookup"><span data-stu-id="5a449-108">These properties contain Unicode or Punycode values depending upon the IDN configuration settings.</span></span>  
  
 <span data-ttu-id="5a449-109">V konfiguračním souboru aplikace je povoleno IDN s použitím následujícího kódu XML.</span><span class="sxs-lookup"><span data-stu-id="5a449-109">IDN is enabled in an application’s configuration file using the following XML</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 <span data-ttu-id="5a449-110">Element \<IDN > obsahuje atribut Enabled, který může být nastaven na jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="5a449-110">The \<idn> element contains the enabled attribute which can be set to one of the following values:</span></span>  
  
1. <span data-ttu-id="5a449-111">"None"</span><span class="sxs-lookup"><span data-stu-id="5a449-111">"None"</span></span>  
  
2. <span data-ttu-id="5a449-112">"AllExceptIntranet"</span><span class="sxs-lookup"><span data-stu-id="5a449-112">"AllExceptIntranet"</span></span>  
  
3. <span data-ttu-id="5a449-113">Všem</span><span class="sxs-lookup"><span data-stu-id="5a449-113">"All"</span></span>  
  
 <span data-ttu-id="5a449-114">Pokud je nastavení IDN nastaveno na hodnotu žádné, neprovede se převody pomocí identifikátoru URI. Host nebo URI. DnsSafeHost.</span><span class="sxs-lookup"><span data-stu-id="5a449-114">When the IDN setting is set to "None", no conversions are performed by Uri.Host or Uri.DnsSafeHost.</span></span> <span data-ttu-id="5a449-115">Pokud je nastavení IDN nastaveno na hodnotu "vše", identifikátor URI. Hostitel zůstává v kódu Unicode a v identifikátoru URI. DnsSafeHost se převede na Punycode.</span><span class="sxs-lookup"><span data-stu-id="5a449-115">When the IDN setting is set to "All", uri.Host remains Unicode and uri.DnsSafeHost is converted to Punycode.</span></span> <span data-ttu-id="5a449-116">Pokud je nastavení IDN nastaveno na hodnotu "AllExceptIntranet", identifikátor URI. DnsSafeHost se převede na Punycode pro internetové adresy a zůstane Unicode pro intranetové adresy.</span><span class="sxs-lookup"><span data-stu-id="5a449-116">When the IDN setting is set to "AllExceptIntranet", uri.DnsSafeHost is converted to Punycode for internet addresses, and remains Unicode for intranet addresses.</span></span> <span data-ttu-id="5a449-117">Toto nastavení je důležité pro správné rozlišení názvů DNS.</span><span class="sxs-lookup"><span data-stu-id="5a449-117">This setting is important for correct DNS name resolution.</span></span> <span data-ttu-id="5a449-118">Poznámka: Toto nastavení není nutné konfigurovat pro systém Windows 8 a novější verze.</span><span class="sxs-lookup"><span data-stu-id="5a449-118">Note this setting is not required to be configured for Windows 8 and newer versions.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="5a449-119">Adresu byste nikdy neměli pevně zakódovat pomocí Punycode.</span><span class="sxs-lookup"><span data-stu-id="5a449-119">You should never hard-code an address using Punycode.</span></span> <span data-ttu-id="5a449-120">WCF je převede na základě nastavení konfigurace, které použijete.</span><span class="sxs-lookup"><span data-stu-id="5a449-120">WCF will convert it for you based on the configuration settings you apply.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="5a449-121">Při přidávání znaků Unicode do souboru applicationHost. exe. config uložte soubor pomocí kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="5a449-121">When adding Unicode characters to applicationHost.exe.config, save the file using the UTF-8 encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a449-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a449-122">See also</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
