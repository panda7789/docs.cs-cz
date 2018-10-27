---
title: WCF a mezinárodní názvy domén
ms.date: 03/30/2017
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
ms.openlocfilehash: a0d4a5b4fe5dd3bc7cf41c8c6ad320dd83861aec
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187920"
---
# <a name="wcf-and-internationalized-domain-names"></a><span data-ttu-id="32e24-102">WCF a mezinárodní názvy domén</span><span class="sxs-lookup"><span data-stu-id="32e24-102">WCF and Internationalized Domain Names</span></span>
<span data-ttu-id="32e24-103">Byla přidána podpora pro služby WCF s mezinárodní názvy domén (IDN).</span><span class="sxs-lookup"><span data-stu-id="32e24-103">Support has been added to allow for WCF services with Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="32e24-104">Mezinárodní název domény je název domény, který obsahuje jiné znaky než ASCII.</span><span class="sxs-lookup"><span data-stu-id="32e24-104">An internationalized domain name is a domain name that contains non-ASCII characters.</span></span> <span data-ttu-id="32e24-105">Tato podpora zahrnuje možnost pro hostování služby WCF pomocí názvu IDN a klienta WCF ke komunikaci s webovou službu s názvem IDN.</span><span class="sxs-lookup"><span data-stu-id="32e24-105">This support includes both the ability to host a WCF service with an IDN name and a WCF client to talk to a web service with an IDN name.</span></span>  
  
## <a name="systemuri-and-idn"></a><span data-ttu-id="32e24-106">System.Uri a IDN</span><span class="sxs-lookup"><span data-stu-id="32e24-106">System.Uri and IDN</span></span>  
 <span data-ttu-id="32e24-107"><xref:System.Uri> má dvě vlastnosti <xref:System.Uri.Host%2A> a <xref:System.Uri.DnsSafeHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="32e24-107"><xref:System.Uri> has two properties <xref:System.Uri.Host%2A> and <xref:System.Uri.DnsSafeHost%2A>.</span></span> <span data-ttu-id="32e24-108">Tyto vlastnosti obsahovat Unicode nebo kódování Punycode hodnoty v závislosti na nastavení konfigurace IDN.</span><span class="sxs-lookup"><span data-stu-id="32e24-108">These properties contain Unicode or Punycode values depending upon the IDN configuration settings.</span></span>  
  
 <span data-ttu-id="32e24-109">V konfiguračním souboru aplikace pomocí následující kód XML je povoleno IDN</span><span class="sxs-lookup"><span data-stu-id="32e24-109">IDN is enabled in an application’s configuration file using the following XML</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 <span data-ttu-id="32e24-110">\<Idn > prvku obsahuje atribut enabled, které můžete nastavit na jedno z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="32e24-110">The \<idn> element contains the enabled attribute which can be set to one of the following values:</span></span>  
  
1.  <span data-ttu-id="32e24-111">"None"</span><span class="sxs-lookup"><span data-stu-id="32e24-111">"None"</span></span>  
  
2.  <span data-ttu-id="32e24-112">"AllExceptIntranet"</span><span class="sxs-lookup"><span data-stu-id="32e24-112">"AllExceptIntranet"</span></span>  
  
3.  <span data-ttu-id="32e24-113">"Vše"</span><span class="sxs-lookup"><span data-stu-id="32e24-113">"All"</span></span>  
  
 <span data-ttu-id="32e24-114">Když je IDN nastavená na hodnotu "None", žádný převod se provádí Uri.Host nebo Uri.DnsSafeHost.</span><span class="sxs-lookup"><span data-stu-id="32e24-114">When the IDN setting is set to "None", no conversions are performed by Uri.Host or Uri.DnsSafeHost.</span></span> <span data-ttu-id="32e24-115">Když je IDN nastavená na "Vše", identifikátor uri. Hostitel zůstává kódování Unicode a identifikátor uri. DnsSafeHost je převede na kódování Punycode.</span><span class="sxs-lookup"><span data-stu-id="32e24-115">When the IDN setting is set to "All", uri.Host remains Unicode and uri.DnsSafeHost is converted to Punycode.</span></span> <span data-ttu-id="32e24-116">Když je IDN nastavená na "AllExceptIntranet", identifikátor uri. DnsSafeHost je převede na kódování Punycode u internetových adres a zůstane Unicode pro adres v podnikové síti.</span><span class="sxs-lookup"><span data-stu-id="32e24-116">When the IDN setting is set to "AllExceptIntranet", uri.DnsSafeHost is converted to Punycode for internet addresses, and remains Unicode for intranet addresses.</span></span> <span data-ttu-id="32e24-117">Toto nastavení je důležité pro správný překlad názvů DNS.</span><span class="sxs-lookup"><span data-stu-id="32e24-117">This setting is important for correct DNS name resolution.</span></span> <span data-ttu-id="32e24-118">Všimněte si, že toto nastavení není potřeba nakonfigurovat pro Windows 8 a novější verze.</span><span class="sxs-lookup"><span data-stu-id="32e24-118">Note this setting is not required to be configured for Windows 8 and newer versions.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="32e24-119">Měli byste nikdy pevně zakódovat adresu pomocí kódování Punycode.</span><span class="sxs-lookup"><span data-stu-id="32e24-119">You should never hard-code an address using Punycode.</span></span> <span data-ttu-id="32e24-120">WCF převede za vás na základě nastavení konfigurace, které použijete.</span><span class="sxs-lookup"><span data-stu-id="32e24-120">WCF will convert it for you based on the configuration settings you apply.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="32e24-121">Při přidávání znaky Unicode do applicationHost.exe.config, uložte soubor pomocí kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="32e24-121">When adding Unicode characters to applicationHost.exe.config, save the file using the UTF-8 encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32e24-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="32e24-122">See Also</span></span>  
 <xref:System.Uri?displayProperty=nameWithType>
