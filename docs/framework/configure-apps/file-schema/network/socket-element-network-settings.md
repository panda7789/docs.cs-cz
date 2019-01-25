---
title: '&lt;soket&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
ms.openlocfilehash: 01e4b5ef4583d30114720ffe559a342b45fe2b98
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640014"
---
# <a name="ltsocketgt-element-network-settings"></a><span data-ttu-id="4d019-102">&lt;soket&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="4d019-102">&lt;socket&gt; Element (Network Settings)</span></span>
<span data-ttu-id="4d019-103">Určuje, zda operace soketu používat porty dokončení.</span><span class="sxs-lookup"><span data-stu-id="4d019-103">Specifies whether socket operations use completion ports.</span></span>  
  
 <span data-ttu-id="4d019-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="4d019-104">\<configuration></span></span>  
<span data-ttu-id="4d019-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="4d019-105">\<system.net></span></span>  
<span data-ttu-id="4d019-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="4d019-106">\<settings></span></span>  
<span data-ttu-id="4d019-107">\<socket></span><span class="sxs-lookup"><span data-stu-id="4d019-107">\<socket></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d019-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d019-108">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d019-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4d019-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4d019-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4d019-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d019-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="4d019-111">Attributes</span></span>  
  
|<span data-ttu-id="4d019-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="4d019-112">**Attribute**</span></span>|<span data-ttu-id="4d019-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="4d019-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="4d019-114">Označuje, zda soketu měli vždy používat porty dokončení pro volání metody přijmout.</span><span class="sxs-lookup"><span data-stu-id="4d019-114">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="4d019-115">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="4d019-115">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="4d019-116">Označuje, zda soketu by měla vždy používat porty dokončení pro volání metody připojení.</span><span class="sxs-lookup"><span data-stu-id="4d019-116">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="4d019-117">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="4d019-117">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="4d019-118">Určuje výchozí <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> pro soket.</span><span class="sxs-lookup"><span data-stu-id="4d019-118">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="4d019-119">Výchozí hodnota závisí na verzi Windows.</span><span class="sxs-lookup"><span data-stu-id="4d019-119">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d019-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4d019-120">Child Elements</span></span>  
 <span data-ttu-id="4d019-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="4d019-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4d019-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4d019-122">Parent Elements</span></span>  
  
|<span data-ttu-id="4d019-123">**Element**</span><span class="sxs-lookup"><span data-stu-id="4d019-123">**Element**</span></span>|<span data-ttu-id="4d019-124">**Popis**</span><span class="sxs-lookup"><span data-stu-id="4d019-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4d019-125">settings</span><span class="sxs-lookup"><span data-stu-id="4d019-125">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="4d019-126">Nakonfiguruje možnosti základní sítě pro <xref:System.Net> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4d019-126">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d019-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d019-127">Remarks</span></span>  
 <span data-ttu-id="4d019-128">`alwaysUseCompletionPortsForAccept` a `alwaysUseCompletionPortsForConnect` atributy se používají k určení výchozí chování týkající se použití portů dokončení třídy v <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span><span class="sxs-lookup"><span data-stu-id="4d019-128">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="4d019-129">Dokončení porty se doporučuje pro aplikace s vysokým výkonem serveru.</span><span class="sxs-lookup"><span data-stu-id="4d019-129">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="4d019-130">Výchozí hodnota `alwaysUseCompletionPortsForAccept` a `alwaysUseCompletionPortsForConnect` atributy je **false**.</span><span class="sxs-lookup"><span data-stu-id="4d019-130">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="4d019-131"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> Lze použít k získání aktuální hodnoty `alwaysUseCompletionPortsForAccept` atribut z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="4d019-131">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="4d019-132"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> Lze použít k získání aktuální hodnoty `alwaysUseCompletionPortsForConnect` atribut z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="4d019-132">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="4d019-133">`ipProtectionLevel` Atribut specifikuje výchozí <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> pro soket.</span><span class="sxs-lookup"><span data-stu-id="4d019-133">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="4d019-134"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Vlastnost umožňuje konfiguraci toho, omezení pro soket IPv6 do zadaného oboru, například adresy se stejným propojit místní nebo lokality místní předponu.</span><span class="sxs-lookup"><span data-stu-id="4d019-134">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="4d019-135">Tato možnost umožňuje aplikacím umístit omezení přístupu pro sokety IPv6.</span><span class="sxs-lookup"><span data-stu-id="4d019-135">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="4d019-136">Taková omezení povolit aplikaci spuštěnou v privátní síti LAN jednoduše a robustně Posilte zabezpečení samotného externí útoky.</span><span class="sxs-lookup"><span data-stu-id="4d019-136">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="4d019-137">Tato možnost rozšiřuje nebo rozsahu oboru naslouchání soketu, takže neomezený přístup z veřejné a soukromé uživatele v případě potřeby nebo omezení přístupu jenom ke stejné lokalitě, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="4d019-137">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="4d019-138">To `ipProtectionLevel` atribut nastavení má vliv počáteční příchozí provoz:</span><span class="sxs-lookup"><span data-stu-id="4d019-138">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
-   <span data-ttu-id="4d019-139">Server TCP naslouchání pro příchozí spojení na soket.</span><span class="sxs-lookup"><span data-stu-id="4d019-139">A TCP server listening for incoming connections on a socket.</span></span>  
  
-   <span data-ttu-id="4d019-140">Aplikace UDP příjem paketů pro soket.</span><span class="sxs-lookup"><span data-stu-id="4d019-140">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="4d019-141">Toto nastavení nemá vliv na už navázané připojení TCP (v obou směrech je neomezený přenos) a nemá vliv na aplikace odešle pakety UDP.</span><span class="sxs-lookup"><span data-stu-id="4d019-141">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="4d019-142">Možné hodnoty parametru `ipProtectionLevel` nastavení atributu nekorespondují s definovanou úrovní podle <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> výčet následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="4d019-142">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="4d019-143">**Hodnota atributu**</span><span class="sxs-lookup"><span data-stu-id="4d019-143">**Attribute Value**</span></span>|<span data-ttu-id="4d019-144">**Popis**</span><span class="sxs-lookup"><span data-stu-id="4d019-144">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="4d019-145">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="4d019-145">EdgeRestricted</span></span>|<span data-ttu-id="4d019-146">Úroveň ochrany IP je edge s omezením pomocí specifikátoru.</span><span class="sxs-lookup"><span data-stu-id="4d019-146">The IP protection level is edge restricted.</span></span> <span data-ttu-id="4d019-147">Tato hodnota se použije u aplikací, které jsou navržené tak, aby provoz přes Internet.</span><span class="sxs-lookup"><span data-stu-id="4d019-147">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="4d019-148">Toto nastavení není povoleno procházení překladu adres (NAT) pomocí implementace Windows Teredo.</span><span class="sxs-lookup"><span data-stu-id="4d019-148">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="4d019-149">Tyto aplikace mohou obejít brány firewall protokolu IPv4, takže aplikace musí být posílené už před útoky z Internetu zaslaných je otevřený port.</span><span class="sxs-lookup"><span data-stu-id="4d019-149">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="4d019-150">V systému Windows Server 2003 a Windows XP je výchozí hodnotu pro úroveň ochrany IP na soketu edge s omezením pomocí specifikátoru.</span><span class="sxs-lookup"><span data-stu-id="4d019-150">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="4d019-151">s omezením pomocí specifikátoru</span><span class="sxs-lookup"><span data-stu-id="4d019-151">Restricted</span></span>|<span data-ttu-id="4d019-152">Úroveň ochrany IP je omezen.</span><span class="sxs-lookup"><span data-stu-id="4d019-152">The IP protection level is restricted.</span></span> <span data-ttu-id="4d019-153">Tato hodnota se použije ve intranetové aplikace, které neimplementují scénáře Internetu.</span><span class="sxs-lookup"><span data-stu-id="4d019-153">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="4d019-154">Tyto aplikace nejsou obecně testovat nebo posílené už před útoky na Internetu – vizuální styl.</span><span class="sxs-lookup"><span data-stu-id="4d019-154">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="4d019-155">Toto nastavení omezí přijaté přenosy do link-local pouze.</span><span class="sxs-lookup"><span data-stu-id="4d019-155">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="4d019-156">Neomezená</span><span class="sxs-lookup"><span data-stu-id="4d019-156">Unrestricted</span></span>|<span data-ttu-id="4d019-157">Úroveň ochrany IP neomezený.</span><span class="sxs-lookup"><span data-stu-id="4d019-157">The IP protection level is unrestricted.</span></span> <span data-ttu-id="4d019-158">Tato hodnota se použije aplikace, které jsou navržené tak, aby provoz přes Internet, jako jsou třeba aplikace s využitím integrované možnosti procházení překladu adres IPv6 do Windows (například Teredo).</span><span class="sxs-lookup"><span data-stu-id="4d019-158">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="4d019-159">Tyto aplikace mohou obejít brány firewall protokolu IPv4, takže aplikace musí být posílené už před útoky z Internetu zaslaných je otevřený port.</span><span class="sxs-lookup"><span data-stu-id="4d019-159">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="4d019-160">V systému Windows Server 2008 R2 a Windows Vista je výchozí hodnotu pro úroveň ochrany IP na soketu neomezený.</span><span class="sxs-lookup"><span data-stu-id="4d019-160">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="4d019-161">Tento parametr zadán</span><span class="sxs-lookup"><span data-stu-id="4d019-161">Unspecified</span></span>|<span data-ttu-id="4d019-162">Úroveň ochrany IP není zadána.</span><span class="sxs-lookup"><span data-stu-id="4d019-162">The IP protection level is unspecified.</span></span> <span data-ttu-id="4d019-163">Ve Windows 7 a Windows Server 2008 R2 neurčená výchozí hodnotu pro úroveň ochrany IP pro soket.</span><span class="sxs-lookup"><span data-stu-id="4d019-163">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="4d019-164">Výchozí hodnota `ipProtectionLevel` atribut je **nespecifikovaný**.</span><span class="sxs-lookup"><span data-stu-id="4d019-164">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="4d019-165"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Vlastnost lze použít k získání aktuální hodnoty `ipProtectionLevel` atribut z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="4d019-165">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4d019-166">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="4d019-166">Configuration Files</span></span>  
 <span data-ttu-id="4d019-167">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="4d019-167">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d019-168">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d019-168">Example</span></span>  
 <span data-ttu-id="4d019-169">Následující příklad ukazuje, jak zadat, že má být použita portů dokončení a že výchozí <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> by měl neomezená.</span><span class="sxs-lookup"><span data-stu-id="4d019-169">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4d019-170">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d019-170">See also</span></span>
- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [<span data-ttu-id="4d019-171">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="4d019-171">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
