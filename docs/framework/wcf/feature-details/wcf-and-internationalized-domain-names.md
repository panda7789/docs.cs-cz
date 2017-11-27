---
title: "WCF a mezinárodní názvy domén"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ab9346e7826fcef5151ef976b6ca7f25120fa5a3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="wcf-and-internationalized-domain-names"></a><span data-ttu-id="2131a-102">WCF a mezinárodní názvy domén</span><span class="sxs-lookup"><span data-stu-id="2131a-102">WCF and Internationalized Domain Names</span></span>
<span data-ttu-id="2131a-103">Byla přidána podpora pro služby WCF s mezinárodní názvy domén (IDN).</span><span class="sxs-lookup"><span data-stu-id="2131a-103">Support has been added to allow for WCF services with Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="2131a-104">Mezinárodní název domény je název domény, který obsahuje jiné znaky než ASCII.</span><span class="sxs-lookup"><span data-stu-id="2131a-104">An internationalized domain name is a domain name that contains non-ASCII characters.</span></span> <span data-ttu-id="2131a-105">Tato podpora zahrnuje možnost k hostování služby WCF s názvu IDN a klienta WCF ke komunikaci s webovou službu pomocí názvu IDN.</span><span class="sxs-lookup"><span data-stu-id="2131a-105">This support includes both the ability to host a WCF service with an IDN name and a WCF client to talk to a web service with an IDN name.</span></span>  
  
## <a name="systemuri-and-idn"></a><span data-ttu-id="2131a-106">System.Uri a IDN.</span><span class="sxs-lookup"><span data-stu-id="2131a-106">System.Uri and IDN</span></span>  
 <span data-ttu-id="2131a-107"><xref:System.Uri>má dvě vlastnosti <xref:System.Uri.Host%2A> a <xref:System.Uri.DnsSafeHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="2131a-107"><xref:System.Uri> has two properties <xref:System.Uri.Host%2A> and <xref:System.Uri.DnsSafeHost%2A>.</span></span> <span data-ttu-id="2131a-108">Tyto vlastnosti obsahovat Unicode nebo Punycode hodnoty v závislosti na nastavení konfigurace IDN.</span><span class="sxs-lookup"><span data-stu-id="2131a-108">These properties contain Unicode or Punycode values depending upon the IDN configuration settings.</span></span>  
  
 <span data-ttu-id="2131a-109">V konfiguračním souboru aplikace pomocí následující kód XML je povoleno IDN.</span><span class="sxs-lookup"><span data-stu-id="2131a-109">IDN is enabled in an application’s configuration file using the following XML</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 <span data-ttu-id="2131a-110">\<Idn > element obsahuje povoleno atribut, který můžete nastavit na jedno z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="2131a-110">The \<idn> element contains the enabled attribute which can be set to one of the following values:</span></span>  
  
1.  <span data-ttu-id="2131a-111">"Žádný"</span><span class="sxs-lookup"><span data-stu-id="2131a-111">"None"</span></span>  
  
2.  <span data-ttu-id="2131a-112">"AllExceptIntranet"</span><span class="sxs-lookup"><span data-stu-id="2131a-112">"AllExceptIntranet"</span></span>  
  
3.  <span data-ttu-id="2131a-113">"Vše"</span><span class="sxs-lookup"><span data-stu-id="2131a-113">"All"</span></span>  
  
 <span data-ttu-id="2131a-114">Pokud je na "Žádný" nastavení IDN žádné převody se provádí Uri.Host nebo Uri.DnsSafeHost.</span><span class="sxs-lookup"><span data-stu-id="2131a-114">When the IDN setting is set to "None", no conversions are performed by Uri.Host or Uri.DnsSafeHost.</span></span> <span data-ttu-id="2131a-115">Pokud nastavení IDN nastavená na "Vše", identifikátor uri. Hostitel zůstává kódování Unicode a identifikátoru uri. DnsSafeHost je převede na kódování Punycode.</span><span class="sxs-lookup"><span data-stu-id="2131a-115">When the IDN setting is set to "All", uri.Host remains Unicode and uri.DnsSafeHost is converted to Punycode.</span></span> <span data-ttu-id="2131a-116">Pokud nastavení IDN nastavená na "AllExceptIntranet", identifikátor uri. DnsSafeHost je převede na kódování Punycode pro internetové adresy a zůstane Unicode adres v podnikové síti.</span><span class="sxs-lookup"><span data-stu-id="2131a-116">When the IDN setting is set to "AllExceptIntranet", uri.DnsSafeHost is converted to Punycode for internet addresses, and remains Unicode for intranet addresses.</span></span> <span data-ttu-id="2131a-117">Toto nastavení je důležité pro správný překlad názvů DNS.</span><span class="sxs-lookup"><span data-stu-id="2131a-117">This setting is important for correct DNS name resolution.</span></span> <span data-ttu-id="2131a-118">Poznámka: Toto nastavení nemusí být konfigurované pro Windows 8 a novější verze.</span><span class="sxs-lookup"><span data-stu-id="2131a-118">Note this setting is not required to be configured for Windows 8 and newer versions.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="2131a-119">Měli byste nikdy pevný kód adresu pomocí kódování Punycode.</span><span class="sxs-lookup"><span data-stu-id="2131a-119">You should never hard-code an address using Punycode.</span></span> <span data-ttu-id="2131a-120">WCF ji převést vám na základě nastavení konfigurace, které použijete.</span><span class="sxs-lookup"><span data-stu-id="2131a-120">WCF will convert it for you based on the configuration settings you apply.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="2131a-121">Při přidávání znaky Unicode do applicationHost.exe.config, uložte soubor pomocí kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="2131a-121">When adding Unicode characters to applicationHost.exe.config, save the file using the UTF-8 encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2131a-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="2131a-122">See Also</span></span>  
 [<span data-ttu-id="2131a-123">System.Uri</span><span class="sxs-lookup"><span data-stu-id="2131a-123">System.Uri</span></span>](http://msdn.microsoft.com/library/system.uri.aspx)
