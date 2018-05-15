---
title: '&lt;Socket&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 995a89dd67664fd6a408f88f20f6837d2dbaaad4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltsocketgt-element-network-settings"></a><span data-ttu-id="dcd9f-102">&lt;Socket&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="dcd9f-102">&lt;socket&gt; Element (Network Settings)</span></span>
<span data-ttu-id="dcd9f-103">Určuje, zda operace soketu používat porty dokončení.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-103">Specifies whether socket operations use completion ports.</span></span>  
  
 <span data-ttu-id="dcd9f-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="dcd9f-104">\<configuration></span></span>  
<span data-ttu-id="dcd9f-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="dcd9f-105">\<system.net></span></span>  
<span data-ttu-id="dcd9f-106">\<Nastavení ></span><span class="sxs-lookup"><span data-stu-id="dcd9f-106">\<settings></span></span>  
<span data-ttu-id="dcd9f-107">\<Socket ></span><span class="sxs-lookup"><span data-stu-id="dcd9f-107">\<socket></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcd9f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcd9f-108">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dcd9f-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dcd9f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="dcd9f-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dcd9f-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="dcd9f-111">Attributes</span></span>  
  
|<span data-ttu-id="dcd9f-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="dcd9f-112">**Attribute**</span></span>|<span data-ttu-id="dcd9f-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="dcd9f-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="dcd9f-114">Označuje, zda soket měli vždycky používat dokončení porty pro volání metod přijmout.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-114">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="dcd9f-115">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-115">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="dcd9f-116">Označuje, zda soket měli vždycky používat dokončení porty pro volání metod připojit.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-116">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="dcd9f-117">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-117">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="dcd9f-118">Určuje výchozí <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> pro soket.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-118">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="dcd9f-119">Výchozí hodnota závisí na verzi systému Windows.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-119">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dcd9f-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dcd9f-120">Child Elements</span></span>  
 <span data-ttu-id="dcd9f-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="dcd9f-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dcd9f-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dcd9f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="dcd9f-123">**Element**</span><span class="sxs-lookup"><span data-stu-id="dcd9f-123">**Element**</span></span>|<span data-ttu-id="dcd9f-124">**Popis**</span><span class="sxs-lookup"><span data-stu-id="dcd9f-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="dcd9f-125">Nastavení</span><span class="sxs-lookup"><span data-stu-id="dcd9f-125">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="dcd9f-126">Nakonfiguruje možnosti základní sítě <xref:System.Net> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-126">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcd9f-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dcd9f-127">Remarks</span></span>  
 <span data-ttu-id="dcd9f-128">`alwaysUseCompletionPortsForAccept` a `alwaysUseCompletionPortsForConnect` atributy se používají k určení výchozího chování týkající se použití dokončení portů pomocí třídy v <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-128">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="dcd9f-129">Dokončení porty – se doporučují pro vysoký výkon serverových aplikací.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-129">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="dcd9f-130">Výchozí hodnota `alwaysUseCompletionPortsForAccept` a `alwaysUseCompletionPortsForConnect` atributy je **false**.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-130">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="dcd9f-131"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> Můžete použít k získání aktuální hodnota `alwaysUseCompletionPortsForAccept` atribut z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-131">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="dcd9f-132"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> Můžete použít k získání aktuální hodnota `alwaysUseCompletionPortsForConnect` atribut z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-132">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="dcd9f-133">`ipProtectionLevel` Atribut určuje výchozí <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> pro soket.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-133">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="dcd9f-134"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Vlastnost umožňuje konfigurovat omezení soketu IPv6 pro zadaný rozsah oboru, například adresy se stejným propojit místní nebo lokality místní předponu.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-134">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="dcd9f-135">Tato možnost umožňuje aplikacím umístit omezení přístupu na IPv6 sockets.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-135">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="dcd9f-136">Takové omezení povolit aplikace spuštěna v privátní síti LAN jednoduše a robustní posílení samotné proti útokům na externí.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-136">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="dcd9f-137">Tato možnost rozšiřuje nebo zužuje oblast naslouchání soketu a povolení neomezený přístup z veřejné a soukromé uživatele v případě nutnosti nebo omezení přístupu jenom do stejné lokality, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-137">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="dcd9f-138">To `ipProtectionLevel` atribut nastavení má vliv počáteční příchozí provoz:</span><span class="sxs-lookup"><span data-stu-id="dcd9f-138">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
-   <span data-ttu-id="dcd9f-139">Server TCP naslouchá pro příchozí spojení na soket.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-139">A TCP server listening for incoming connections on a socket.</span></span>  
  
-   <span data-ttu-id="dcd9f-140">UDP aplikace, který přijímá paket na soketu.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-140">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="dcd9f-141">Toto nastavení nemá vliv již navázáno připojení TCP (provoz je neomezený v obou směrech) a nemá vliv na aplikaci odesílání UDP paketů.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-141">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="dcd9f-142">Možné hodnoty `ipProtectionLevel` nastavení atributu odpovídají s úrovněmi ochrany definované zadané v <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> výčtu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="dcd9f-142">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="dcd9f-143">**Hodnota atributu**</span><span class="sxs-lookup"><span data-stu-id="dcd9f-143">**Attribute Value**</span></span>|<span data-ttu-id="dcd9f-144">**Popis**</span><span class="sxs-lookup"><span data-stu-id="dcd9f-144">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="dcd9f-145">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="dcd9f-145">EdgeRestricted</span></span>|<span data-ttu-id="dcd9f-146">Úroveň ochrany IP je hraniční omezený.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-146">The IP protection level is edge restricted.</span></span> <span data-ttu-id="dcd9f-147">Tato hodnota se použije aplikace navržené tak, aby provoz přes Internet.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-147">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="dcd9f-148">Toto nastavení neumožňuje traversal překlad adres (NAT) pomocí implementace Teredo systému Windows.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-148">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="dcd9f-149">Tyto aplikace mohou obejít brány firewall IPv4, takže aplikace musí být zesílené zabezpečení proti útokům na Internetu přesměrován na otevřen port.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-149">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="dcd9f-150">V systému Windows Server 2003 a Windows XP je výchozí hodnota pro úroveň ochrany IP na soket edge omezený.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-150">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="dcd9f-151">Omezený</span><span class="sxs-lookup"><span data-stu-id="dcd9f-151">Restricted</span></span>|<span data-ttu-id="dcd9f-152">Úroveň ochrany IP je omezen.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-152">The IP protection level is restricted.</span></span> <span data-ttu-id="dcd9f-153">Tato hodnota se použije intranetu aplikace, které neimplementují scénáře Internetu.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-153">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="dcd9f-154">Tyto aplikace nejsou obvykle testována nebo zesílené zabezpečení proti útokům na Internetu stylu.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-154">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="dcd9f-155">Toto nastavení omezí přijaté přenosy do link-local jenom.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-155">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="dcd9f-156">Bez omezení</span><span class="sxs-lookup"><span data-stu-id="dcd9f-156">Unrestricted</span></span>|<span data-ttu-id="dcd9f-157">Úroveň ochrany IP není omezeno.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-157">The IP protection level is unrestricted.</span></span> <span data-ttu-id="dcd9f-158">Tato hodnota se použije aplikace navržené tak, aby provoz přes Internet, včetně aplikací s využitím možnosti traversal IPv6 NAT do systému Windows (například Teredo).</span><span class="sxs-lookup"><span data-stu-id="dcd9f-158">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="dcd9f-159">Tyto aplikace mohou obejít brány firewall IPv4, takže aplikace musí být zesílené zabezpečení proti útokům na Internetu přesměrován na otevřen port.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-159">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="dcd9f-160">Na Windows Server 2008 R2 a Windows Vista je výchozí hodnota pro úroveň ochrany IP na soket bez omezení.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-160">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="dcd9f-161">Tento parametr</span><span class="sxs-lookup"><span data-stu-id="dcd9f-161">Unspecified</span></span>|<span data-ttu-id="dcd9f-162">Úroveň ochrany IP neurčená.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-162">The IP protection level is unspecified.</span></span> <span data-ttu-id="dcd9f-163">V systému Windows 7 a Windows Server 2008 R2 je výchozí hodnota pro úroveň ochrany IP na soket neurčené.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-163">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="dcd9f-164">Výchozí hodnota `ipProtectionLevel` atribut je **nespecifikovaný**.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-164">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="dcd9f-165"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Vlastnost lze použít k získání aktuální hodnota `ipProtectionLevel` atribut z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-165">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="dcd9f-166">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="dcd9f-166">Configuration Files</span></span>  
 <span data-ttu-id="dcd9f-167">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="dcd9f-167">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcd9f-168">Příklad</span><span class="sxs-lookup"><span data-stu-id="dcd9f-168">Example</span></span>  
 <span data-ttu-id="dcd9f-169">Následující příklad ukazuje, jak určit, že má být použita dokončení porty a že výchozí <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> by měl neomezený.</span><span class="sxs-lookup"><span data-stu-id="dcd9f-169">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dcd9f-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="dcd9f-170">See Also</span></span>  
 <xref:System.Net?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>  
 <xref:System.Net.Sockets?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>  
 [<span data-ttu-id="dcd9f-171">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="dcd9f-171">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
