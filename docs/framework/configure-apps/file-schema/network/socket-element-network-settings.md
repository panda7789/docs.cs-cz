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
ms.openlocfilehash: 0e2b369eccfbc658a790ef61a961315a88361669
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089093"
---
# <a name="socket-element-network-settings"></a><span data-ttu-id="c0836-102">\<socket> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="c0836-102">\<socket> Element (Network Settings)</span></span>
<span data-ttu-id="c0836-103">Určuje, jestli operace soketu používají porty dokončení.</span><span class="sxs-lookup"><span data-stu-id="c0836-103">Specifies whether socket operations use completion ports.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<socket>**

## <a name="syntax"></a><span data-ttu-id="c0836-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0836-104">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0836-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c0836-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c0836-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c0836-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0836-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="c0836-107">Attributes</span></span>  
  
|<span data-ttu-id="c0836-108">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="c0836-108">**Attribute**</span></span>|<span data-ttu-id="c0836-109">**Popis**</span><span class="sxs-lookup"><span data-stu-id="c0836-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="c0836-110">Určuje, zda má soket vždy používat porty dokončení pro volání metody Accept.</span><span class="sxs-lookup"><span data-stu-id="c0836-110">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="c0836-111">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="c0836-111">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="c0836-112">Určuje, zda má soket vždy používat porty dokončení pro volání metody připojení.</span><span class="sxs-lookup"><span data-stu-id="c0836-112">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="c0836-113">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="c0836-113">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="c0836-114">Určuje výchozí hodnotu <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> , která se má použít pro soket.</span><span class="sxs-lookup"><span data-stu-id="c0836-114">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="c0836-115">Výchozí hodnota závisí na verzi systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c0836-115">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0836-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c0836-116">Child Elements</span></span>  
 <span data-ttu-id="c0836-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="c0836-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0836-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c0836-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c0836-119">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="c0836-119">**Element**</span></span>|<span data-ttu-id="c0836-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="c0836-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c0836-121">zdroje dat</span><span class="sxs-lookup"><span data-stu-id="c0836-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="c0836-122">Nakonfiguruje základní možnosti sítě pro <xref:System.Net> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="c0836-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0836-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c0836-123">Remarks</span></span>  
 <span data-ttu-id="c0836-124">`alwaysUseCompletionPortsForAccept`Atributy a `alwaysUseCompletionPortsForConnect` se používají k určení výchozího chování týkající se použití portů dokončení třídami v <xref:System.Net.Sockets?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c0836-124">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="c0836-125">Pro vysoce výkonné serverové aplikace se doporučují porty pro dokončení.</span><span class="sxs-lookup"><span data-stu-id="c0836-125">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="c0836-126">Výchozí hodnota `alwaysUseCompletionPortsForAccept` `alwaysUseCompletionPortsForConnect` atributů a je **false**.</span><span class="sxs-lookup"><span data-stu-id="c0836-126">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="c0836-127"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A>Lze použít k získání aktuální hodnoty `alwaysUseCompletionPortsForAccept` atributu z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="c0836-127">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="c0836-128"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A>Lze použít k získání aktuální hodnoty `alwaysUseCompletionPortsForConnect` atributu z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="c0836-128">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="c0836-129">`ipProtectionLevel`Atribut určuje výchozí hodnotu, <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> která se má použít pro soket.</span><span class="sxs-lookup"><span data-stu-id="c0836-129">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="c0836-130"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>Vlastnost umožňuje konfiguraci omezení pro soket IPv6 do zadaného oboru, jako jsou adresy se stejným místní předponou nebo místní předponou webu.</span><span class="sxs-lookup"><span data-stu-id="c0836-130">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="c0836-131">Tato možnost umožňuje aplikacím umístit omezení přístupu na sokety IPv6.</span><span class="sxs-lookup"><span data-stu-id="c0836-131">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="c0836-132">Taková omezení umožňují aplikacím běžícím v privátní síti LAN jednoduše a robustní zabezpečení proti externím útokům.</span><span class="sxs-lookup"><span data-stu-id="c0836-132">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="c0836-133">Tato možnost rozšiřuje nebo zužuje rozsah naslouchajícího soketu a umožňuje tak neomezený přístup k veřejným a soukromým uživatelům, pokud je to vhodné, nebo omezuje přístup jenom na stejnou lokalitu, jak je potřeba.</span><span class="sxs-lookup"><span data-stu-id="c0836-133">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="c0836-134">`ipProtectionLevel`Nastavení tohoto atributu má vliv jenom na počáteční příchozí provoz:</span><span class="sxs-lookup"><span data-stu-id="c0836-134">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
- <span data-ttu-id="c0836-135">Server TCP naslouchá příchozím připojením na soketu.</span><span class="sxs-lookup"><span data-stu-id="c0836-135">A TCP server listening for incoming connections on a socket.</span></span>  
  
- <span data-ttu-id="c0836-136">Aplikace UDP, která přijímá paket na soketu.</span><span class="sxs-lookup"><span data-stu-id="c0836-136">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="c0836-137">Toto nastavení konfigurace neovlivňuje již zavedené připojení TCP (provoz není v obou směrech omezený) a nemá vliv na aplikaci, která odesílá pakety UDP.</span><span class="sxs-lookup"><span data-stu-id="c0836-137">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="c0836-138">Možné hodnoty pro `ipProtectionLevel` nastavení atributů odpovídají definovaným úrovním ochrany zadaným ve <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> výčtu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="c0836-138">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="c0836-139">**Hodnota atributu**</span><span class="sxs-lookup"><span data-stu-id="c0836-139">**Attribute Value**</span></span>|<span data-ttu-id="c0836-140">**Popis**</span><span class="sxs-lookup"><span data-stu-id="c0836-140">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="c0836-141">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="c0836-141">EdgeRestricted</span></span>|<span data-ttu-id="c0836-142">Úroveň ochrany protokolu IP je omezena na hranici.</span><span class="sxs-lookup"><span data-stu-id="c0836-142">The IP protection level is edge restricted.</span></span> <span data-ttu-id="c0836-143">Tuto hodnotu budou používat aplikace navržené pro provoz přes Internet.</span><span class="sxs-lookup"><span data-stu-id="c0836-143">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="c0836-144">Toto nastavení nepovoluje procházení síťových adres (NAT) pomocí implementace Windows Teredo.</span><span class="sxs-lookup"><span data-stu-id="c0836-144">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="c0836-145">Tyto aplikace můžou obejít brány firewall IPv4, takže aplikace musí být posílené proti útokům na Internet, které jsou směrovány na otevřený port.</span><span class="sxs-lookup"><span data-stu-id="c0836-145">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="c0836-146">V systémech Windows Server 2003 a Windows XP je výchozí hodnota pro úroveň ochrany protokolu IP na soketu omezena na hranici.</span><span class="sxs-lookup"><span data-stu-id="c0836-146">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="c0836-147">S omezeným přístupem</span><span class="sxs-lookup"><span data-stu-id="c0836-147">Restricted</span></span>|<span data-ttu-id="c0836-148">Úroveň ochrany protokolu IP je omezená.</span><span class="sxs-lookup"><span data-stu-id="c0836-148">The IP protection level is restricted.</span></span> <span data-ttu-id="c0836-149">Tuto hodnotu budou používat intranetové aplikace, které neimplementují internetové scénáře.</span><span class="sxs-lookup"><span data-stu-id="c0836-149">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="c0836-150">Tyto aplikace jsou obecně netestovány ani posíleny proti útokům pomocí internetového stylu.</span><span class="sxs-lookup"><span data-stu-id="c0836-150">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="c0836-151">Toto nastavení omezí přijatý provoz jenom na místní připojení.</span><span class="sxs-lookup"><span data-stu-id="c0836-151">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="c0836-152">Neomezené</span><span class="sxs-lookup"><span data-stu-id="c0836-152">Unrestricted</span></span>|<span data-ttu-id="c0836-153">Úroveň ochrany IP je neomezená.</span><span class="sxs-lookup"><span data-stu-id="c0836-153">The IP protection level is unrestricted.</span></span> <span data-ttu-id="c0836-154">Tuto hodnotu budou používat aplikace navržené pro provoz přes Internet, včetně aplikací využívajících možnosti přecházení IPv6 NAT integrované do Windows (například Teredo).</span><span class="sxs-lookup"><span data-stu-id="c0836-154">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="c0836-155">Tyto aplikace můžou obejít brány firewall IPv4, takže aplikace musí být posílené proti útokům na Internet, které jsou směrovány na otevřený port.</span><span class="sxs-lookup"><span data-stu-id="c0836-155">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="c0836-156">V systémech Windows Server 2008 R2 a Windows Vista není výchozí hodnota pro úroveň ochrany IP adres na soketu omezená.</span><span class="sxs-lookup"><span data-stu-id="c0836-156">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="c0836-157">Unspecified</span><span class="sxs-lookup"><span data-stu-id="c0836-157">Unspecified</span></span>|<span data-ttu-id="c0836-158">Úroveň ochrany protokolu IP není určena.</span><span class="sxs-lookup"><span data-stu-id="c0836-158">The IP protection level is unspecified.</span></span> <span data-ttu-id="c0836-159">V systémech Windows 7 a Windows Server 2008 R2 není určena výchozí hodnota pro úroveň ochrany IP adres na soketu.</span><span class="sxs-lookup"><span data-stu-id="c0836-159">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="c0836-160">Výchozí hodnota pro `ipProtectionLevel` atribut není **specifikována**.</span><span class="sxs-lookup"><span data-stu-id="c0836-160">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="c0836-161"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>Vlastnost lze použít k získání aktuální hodnoty `ipProtectionLevel` atributu z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="c0836-161">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c0836-162">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="c0836-162">Configuration Files</span></span>  
 <span data-ttu-id="c0836-163">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="c0836-163">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0836-164">Příklad</span><span class="sxs-lookup"><span data-stu-id="c0836-164">Example</span></span>  
 <span data-ttu-id="c0836-165">Následující příklad ukazuje, jak určit, zda mají být použity porty dokončení a že výchozí hodnota <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> by měla být neomezená.</span><span class="sxs-lookup"><span data-stu-id="c0836-165">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c0836-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0836-166">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [<span data-ttu-id="c0836-167">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="c0836-167">Network Settings Schema</span></span>](index.md)
