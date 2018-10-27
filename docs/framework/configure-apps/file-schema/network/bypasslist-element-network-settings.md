---
title: '&lt;atribut bypasslist bude&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: c696017c153b63ba6f2d485855c969b2b45ba0ab
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188525"
---
# <a name="ltbypasslistgt-element-network-settings"></a><span data-ttu-id="c3a3a-102">&lt;atribut bypasslist bude&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="c3a3a-102">&lt;bypasslist&gt; Element (Network Settings)</span></span>
<span data-ttu-id="c3a3a-103">Poskytuje sadu regulární výrazy, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="c3a3a-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  
  
 <span data-ttu-id="c3a3a-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="c3a3a-104">\<configuration></span></span>  
<span data-ttu-id="c3a3a-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="c3a3a-105">\<system.net></span></span>  
<span data-ttu-id="c3a3a-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="c3a3a-106">\<defaultProxy></span></span>  
<span data-ttu-id="c3a3a-107">\<bypasslist – ></span><span class="sxs-lookup"><span data-stu-id="c3a3a-107">\<bypasslist></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3a3a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3a3a-108">Syntax</span></span>  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3a3a-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c3a3a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c3a3a-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c3a3a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3a3a-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="c3a3a-111">Attributes</span></span>  
 <span data-ttu-id="c3a3a-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="c3a3a-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c3a3a-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c3a3a-113">Child Elements</span></span>  
  
|<span data-ttu-id="c3a3a-114">**Element**</span><span class="sxs-lookup"><span data-stu-id="c3a3a-114">**Element**</span></span>|<span data-ttu-id="c3a3a-115">**Popis**</span><span class="sxs-lookup"><span data-stu-id="c3a3a-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c3a3a-116">add</span><span class="sxs-lookup"><span data-stu-id="c3a3a-116">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="c3a3a-117">Přidá do seznamu obcházení proxy IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="c3a3a-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="c3a3a-118">Vymazat</span><span class="sxs-lookup"><span data-stu-id="c3a3a-118">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="c3a3a-119">Seznam obcházení vymaže.</span><span class="sxs-lookup"><span data-stu-id="c3a3a-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="c3a3a-120">remove</span><span class="sxs-lookup"><span data-stu-id="c3a3a-120">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="c3a3a-121">Odebere ze seznamu obcházení proxy IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="c3a3a-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c3a3a-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c3a3a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c3a3a-123">**Element**</span><span class="sxs-lookup"><span data-stu-id="c3a3a-123">**Element**</span></span>|<span data-ttu-id="c3a3a-124">**Popis**</span><span class="sxs-lookup"><span data-stu-id="c3a3a-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c3a3a-125">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="c3a3a-125">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="c3a3a-126">Konfiguruje server proxy protokolu HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="c3a3a-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3a3a-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c3a3a-127">Remarks</span></span>  
 <span data-ttu-id="c3a3a-128">Seznam obcházení obsahuje regulárních výrazů, které popisují identifikátory URI, který <xref:System.Net.WebRequest> instancí k datům přímo namísto prostřednictvím proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="c3a3a-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="c3a3a-129">Buďte opatrní při zadávání regulární výraz pro tento element.</span><span class="sxs-lookup"><span data-stu-id="c3a3a-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="c3a3a-130">Regulární výraz "[-z] +\\.contoso\\.com" odpovídá některé hostovat v doméně contoso.com, ale také odpovídající libovolného hostitele v doméně contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="c3a3a-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="c3a3a-131">Tak, aby odpovídaly pouze na hostiteli v doméně contoso.com, použijte ukotvení ("$"): "[-z] +\\.contoso\\.com$".</span><span class="sxs-lookup"><span data-stu-id="c3a3a-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="c3a3a-132">Další informace o formátování regulárních výrazů naleznete v tématu. [Regulárních výrazech .NET Frameworku](../../../../../docs/standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="c3a3a-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c3a3a-133">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="c3a3a-133">Configuration Files</span></span>  
 <span data-ttu-id="c3a3a-134">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="c3a3a-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3a3a-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="c3a3a-135">Example</span></span>  
 <span data-ttu-id="c3a3a-136">Následující příklad přidá do seznamu obcházení dvě adresy.</span><span class="sxs-lookup"><span data-stu-id="c3a3a-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="c3a3a-137">První obcházejí proxy serveru pro všechny servery v doméně contoso.com; druhý vynechá proxy serveru pro všechny servery jehož IP adres začít s 192.168.</span><span class="sxs-lookup"><span data-stu-id="c3a3a-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3a3a-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3a3a-138">See Also</span></span>  
- <xref:System.Net.WebProxy?displayProperty=nameWithType>  
- [<span data-ttu-id="c3a3a-139">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="c3a3a-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
