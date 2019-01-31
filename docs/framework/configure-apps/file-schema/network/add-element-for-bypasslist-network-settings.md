---
title: <add> – element pro element bypasslist (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
ms.openlocfilehash: 702aa8ccefcdddee1ffc5a7519a4f955b1dc5dfb
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55265659"
---
# <a name="add-element-for-bypasslist-network-settings"></a><span data-ttu-id="cd4bb-102">\<Přidat > – Element pro bypasslist (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="cd4bb-102">\<add> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="cd4bb-103">Přidá do seznamu obcházení proxy IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="cd4bb-103">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
 <span data-ttu-id="cd4bb-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="cd4bb-104">\<configuration></span></span>  
<span data-ttu-id="cd4bb-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="cd4bb-105">\<system.net></span></span>  
<span data-ttu-id="cd4bb-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="cd4bb-106">\<defaultProxy></span></span>  
<span data-ttu-id="cd4bb-107">\<bypasslist – ></span><span class="sxs-lookup"><span data-stu-id="cd4bb-107">\<bypasslist></span></span>  
<span data-ttu-id="cd4bb-108">\<add></span><span class="sxs-lookup"><span data-stu-id="cd4bb-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd4bb-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd4bb-109">Syntax</span></span>  
  
```xml  
<add   
  address="regular expression"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd4bb-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cd4bb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cd4bb-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cd4bb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd4bb-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="cd4bb-112">Attributes</span></span>  
  
|<span data-ttu-id="cd4bb-113">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="cd4bb-113">**Attribute**</span></span>|<span data-ttu-id="cd4bb-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="cd4bb-114">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="cd4bb-115">**address**</span><span class="sxs-lookup"><span data-stu-id="cd4bb-115">**address**</span></span>|<span data-ttu-id="cd4bb-116">Regulární výraz popisující IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="cd4bb-116">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd4bb-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cd4bb-117">Child Elements</span></span>  
 <span data-ttu-id="cd4bb-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="cd4bb-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cd4bb-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cd4bb-119">Parent Elements</span></span>  
  
|<span data-ttu-id="cd4bb-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="cd4bb-120">**Element**</span></span>|<span data-ttu-id="cd4bb-121">**Popis**</span><span class="sxs-lookup"><span data-stu-id="cd4bb-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="cd4bb-122">bypasslist</span><span class="sxs-lookup"><span data-stu-id="cd4bb-122">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="cd4bb-123">Poskytuje sadu regulární výrazy, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="cd4bb-123">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd4bb-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cd4bb-124">Remarks</span></span>  
 <span data-ttu-id="cd4bb-125">`add` Element vloží regulární výrazy popisující IP adresy nebo názvy serverů DNS do seznamu adres, které obcházejí proxy server.</span><span class="sxs-lookup"><span data-stu-id="cd4bb-125">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="cd4bb-126">Hodnota `address` atribut musí být regulární výraz, který popisuje sadu IP adres nebo názvů hostitele.</span><span class="sxs-lookup"><span data-stu-id="cd4bb-126">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="cd4bb-127">Buďte opatrní při zadávání regulární výraz pro tento element.</span><span class="sxs-lookup"><span data-stu-id="cd4bb-127">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="cd4bb-128">Regulární výraz "[-z] +\\.contoso\\.com" odpovídá některé hostovat v doméně contoso.com, ale také odpovídající libovolného hostitele v doméně contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="cd4bb-128">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="cd4bb-129">Tak, aby odpovídaly pouze na hostiteli v doméně contoso.com, použijte ukotvení ("$"): "[-z] +\\.contoso\\.com$".</span><span class="sxs-lookup"><span data-stu-id="cd4bb-129">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="cd4bb-130">Další informace o formátování regulárních výrazů naleznete v tématu. [Regulárních výrazech .NET Frameworku](../../../../../docs/standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="cd4bb-130">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="cd4bb-131">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="cd4bb-131">Configuration Files</span></span>  
 <span data-ttu-id="cd4bb-132">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="cd4bb-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd4bb-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd4bb-133">Example</span></span>  
 <span data-ttu-id="cd4bb-134">Následující příklad přidá do seznamu obcházení dvě adresy.</span><span class="sxs-lookup"><span data-stu-id="cd4bb-134">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="cd4bb-135">První obcházejí proxy serveru pro všechny servery v doméně contoso.com; druhý vynechá proxy serveru pro všechny servery, IP adresa začíná s 192.168.</span><span class="sxs-lookup"><span data-stu-id="cd4bb-135">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cd4bb-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd4bb-136">See also</span></span>
- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="cd4bb-137">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="cd4bb-137">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
