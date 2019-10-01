---
title: <socket> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
ms.openlocfilehash: ec2c8388411e24940041dc9dcb7f6a6755e89805
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697577"
---
# <a name="socket-element-network-settings"></a><span data-ttu-id="36962-102">@no__t – element > 0socket (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="36962-102">\<socket> Element (Network Settings)</span></span>
<span data-ttu-id="36962-103">Určuje, jestli operace soketu používají porty dokončení.</span><span class="sxs-lookup"><span data-stu-id="36962-103">Specifies whether socket operations use completion ports.</span></span>  
  
[<span data-ttu-id="36962-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="36962-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="36962-105">&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="36962-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="36962-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="36962-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>  
<span data-ttu-id="36962-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<socket >**</span><span class="sxs-lookup"><span data-stu-id="36962-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<socket>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36962-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36962-108">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36962-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="36962-109">Attributes and Elements</span></span>  
 <span data-ttu-id="36962-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="36962-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36962-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="36962-111">Attributes</span></span>  
  
|<span data-ttu-id="36962-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="36962-112">**Attribute**</span></span>|<span data-ttu-id="36962-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="36962-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="36962-114">Určuje, zda má soket vždy používat porty dokončení pro volání metody Accept.</span><span class="sxs-lookup"><span data-stu-id="36962-114">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="36962-115">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="36962-115">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="36962-116">Určuje, zda má soket vždy používat porty dokončení pro volání metody připojení.</span><span class="sxs-lookup"><span data-stu-id="36962-116">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="36962-117">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="36962-117">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="36962-118">Určuje výchozí <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> pro použití pro soket.</span><span class="sxs-lookup"><span data-stu-id="36962-118">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="36962-119">Výchozí hodnota závisí na verzi systému Windows.</span><span class="sxs-lookup"><span data-stu-id="36962-119">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="36962-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="36962-120">Child Elements</span></span>  
 <span data-ttu-id="36962-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="36962-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="36962-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="36962-122">Parent Elements</span></span>  
  
|<span data-ttu-id="36962-123">**Element**</span><span class="sxs-lookup"><span data-stu-id="36962-123">**Element**</span></span>|<span data-ttu-id="36962-124">**Popis**</span><span class="sxs-lookup"><span data-stu-id="36962-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="36962-125">možnost</span><span class="sxs-lookup"><span data-stu-id="36962-125">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="36962-126">Konfiguruje základní možnosti sítě pro obor názvů <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="36962-126">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36962-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36962-127">Remarks</span></span>  
 <span data-ttu-id="36962-128">Atributy `alwaysUseCompletionPortsForAccept` a `alwaysUseCompletionPortsForConnect` slouží k určení výchozího chování týkající se použití portů dokončení třídami v @no__t -2. Namespace.</span><span class="sxs-lookup"><span data-stu-id="36962-128">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="36962-129">Pro vysoce výkonné serverové aplikace se doporučují porty pro dokončení.</span><span class="sxs-lookup"><span data-stu-id="36962-129">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="36962-130">Výchozí hodnota pro atributy `alwaysUseCompletionPortsForAccept` a `alwaysUseCompletionPortsForConnect` je **false**.</span><span class="sxs-lookup"><span data-stu-id="36962-130">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="36962-131">@No__t-0 lze použít k získání aktuální hodnoty atributu `alwaysUseCompletionPortsForAccept` z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="36962-131">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="36962-132">@No__t-0 lze použít k získání aktuální hodnoty atributu `alwaysUseCompletionPortsForConnect` z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="36962-132">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="36962-133">Atribut `ipProtectionLevel` určuje výchozí <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>, který se má použít pro soket.</span><span class="sxs-lookup"><span data-stu-id="36962-133">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="36962-134">Vlastnost <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> umožňuje konfiguraci omezení pro soket IPv6 do zadaného oboru, například adresy se stejnou místní předponou nebo místní předponou webu.</span><span class="sxs-lookup"><span data-stu-id="36962-134">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="36962-135">Tato možnost umožňuje aplikacím umístit omezení přístupu na sokety IPv6.</span><span class="sxs-lookup"><span data-stu-id="36962-135">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="36962-136">Taková omezení umožňují aplikacím běžícím v privátní síti LAN jednoduše a robustní zabezpečení proti externím útokům.</span><span class="sxs-lookup"><span data-stu-id="36962-136">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="36962-137">Tato možnost rozšiřuje nebo zužuje rozsah naslouchajícího soketu a umožňuje tak neomezený přístup k veřejným a soukromým uživatelům, pokud je to vhodné, nebo omezuje přístup jenom na stejnou lokalitu, jak je potřeba.</span><span class="sxs-lookup"><span data-stu-id="36962-137">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="36962-138">Toto nastavení atributu `ipProtectionLevel` má vliv jenom na počáteční příchozí provoz:</span><span class="sxs-lookup"><span data-stu-id="36962-138">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
- <span data-ttu-id="36962-139">Server TCP naslouchá příchozím připojením na soketu.</span><span class="sxs-lookup"><span data-stu-id="36962-139">A TCP server listening for incoming connections on a socket.</span></span>  
  
- <span data-ttu-id="36962-140">Aplikace UDP, která přijímá paket na soketu.</span><span class="sxs-lookup"><span data-stu-id="36962-140">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="36962-141">Toto nastavení konfigurace neovlivňuje již zavedené připojení TCP (provoz není v obou směrech omezený) a nemá vliv na aplikaci, která odesílá pakety UDP.</span><span class="sxs-lookup"><span data-stu-id="36962-141">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="36962-142">Možné hodnoty pro nastavení atributu `ipProtectionLevel` odpovídají definovaným úrovním ochrany zadaným ve výčtu <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="36962-142">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="36962-143">**Hodnota atributu**</span><span class="sxs-lookup"><span data-stu-id="36962-143">**Attribute Value**</span></span>|<span data-ttu-id="36962-144">**Popis**</span><span class="sxs-lookup"><span data-stu-id="36962-144">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="36962-145">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="36962-145">EdgeRestricted</span></span>|<span data-ttu-id="36962-146">Úroveň ochrany protokolu IP je omezena na hranici.</span><span class="sxs-lookup"><span data-stu-id="36962-146">The IP protection level is edge restricted.</span></span> <span data-ttu-id="36962-147">Tuto hodnotu budou používat aplikace navržené pro provoz přes Internet.</span><span class="sxs-lookup"><span data-stu-id="36962-147">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="36962-148">Toto nastavení nepovoluje procházení síťových adres (NAT) pomocí implementace Windows Teredo.</span><span class="sxs-lookup"><span data-stu-id="36962-148">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="36962-149">Tyto aplikace můžou obejít brány firewall IPv4, takže aplikace musí být posílené proti útokům na Internet, které jsou směrovány na otevřený port.</span><span class="sxs-lookup"><span data-stu-id="36962-149">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="36962-150">V systémech Windows Server 2003 a Windows XP je výchozí hodnota pro úroveň ochrany protokolu IP na soketu omezena na hranici.</span><span class="sxs-lookup"><span data-stu-id="36962-150">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="36962-151">S omezeným přístupem</span><span class="sxs-lookup"><span data-stu-id="36962-151">Restricted</span></span>|<span data-ttu-id="36962-152">Úroveň ochrany protokolu IP je omezená.</span><span class="sxs-lookup"><span data-stu-id="36962-152">The IP protection level is restricted.</span></span> <span data-ttu-id="36962-153">Tuto hodnotu budou používat intranetové aplikace, které neimplementují internetové scénáře.</span><span class="sxs-lookup"><span data-stu-id="36962-153">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="36962-154">Tyto aplikace jsou obecně netestovány ani posíleny proti útokům pomocí internetového stylu.</span><span class="sxs-lookup"><span data-stu-id="36962-154">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="36962-155">Toto nastavení omezí přijatý provoz jenom na místní připojení.</span><span class="sxs-lookup"><span data-stu-id="36962-155">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="36962-156">Neomezený</span><span class="sxs-lookup"><span data-stu-id="36962-156">Unrestricted</span></span>|<span data-ttu-id="36962-157">Úroveň ochrany IP je neomezená.</span><span class="sxs-lookup"><span data-stu-id="36962-157">The IP protection level is unrestricted.</span></span> <span data-ttu-id="36962-158">Tuto hodnotu budou používat aplikace navržené pro provoz přes Internet, včetně aplikací využívajících možnosti přecházení IPv6 NAT integrované do Windows (například Teredo).</span><span class="sxs-lookup"><span data-stu-id="36962-158">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="36962-159">Tyto aplikace můžou obejít brány firewall IPv4, takže aplikace musí být posílené proti útokům na Internet, které jsou směrovány na otevřený port.</span><span class="sxs-lookup"><span data-stu-id="36962-159">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="36962-160">V systémech Windows Server 2008 R2 a Windows Vista není výchozí hodnota pro úroveň ochrany IP adres na soketu omezená.</span><span class="sxs-lookup"><span data-stu-id="36962-160">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="36962-161">Neurčené</span><span class="sxs-lookup"><span data-stu-id="36962-161">Unspecified</span></span>|<span data-ttu-id="36962-162">Úroveň ochrany protokolu IP není určena.</span><span class="sxs-lookup"><span data-stu-id="36962-162">The IP protection level is unspecified.</span></span> <span data-ttu-id="36962-163">V systémech Windows 7 a Windows Server 2008 R2 není určena výchozí hodnota pro úroveň ochrany IP adres na soketu.</span><span class="sxs-lookup"><span data-stu-id="36962-163">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="36962-164">Výchozí hodnota pro atribut `ipProtectionLevel` není **specifikována**.</span><span class="sxs-lookup"><span data-stu-id="36962-164">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="36962-165">Vlastnost <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> lze použít k získání aktuální hodnoty atributu `ipProtectionLevel` z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="36962-165">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="36962-166">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="36962-166">Configuration Files</span></span>  
 <span data-ttu-id="36962-167">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="36962-167">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="36962-168">Příklad</span><span class="sxs-lookup"><span data-stu-id="36962-168">Example</span></span>  
 <span data-ttu-id="36962-169">Následující příklad ukazuje, jak určit, že se mají použít porty dokončení a že výchozí <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> by mělo být neomezené.</span><span class="sxs-lookup"><span data-stu-id="36962-169">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <socket  
        alwaysUseCompletionPortsForAccept="true"  
        alwaysUseCompletionPortsForConnect="true"  
        ipProtectionLevel="Unrestricted"  
       />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="36962-170">Viz také:</span><span class="sxs-lookup"><span data-stu-id="36962-170">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [<span data-ttu-id="36962-171">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="36962-171">Network Settings Schema</span></span>](index.md)
