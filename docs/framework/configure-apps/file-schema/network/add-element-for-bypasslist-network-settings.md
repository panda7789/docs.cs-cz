---
title: "&lt;Přidat&gt; Element pro bypasslist – (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: bed3abd5522b748a2bd24ba03c7be5d991deae9a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-bypasslist-network-settings"></a><span data-ttu-id="da126-102">&lt;Přidat&gt; Element pro bypasslist – (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="da126-102">&lt;add&gt; Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="da126-103">Přidá IP adresy nebo názvu DNS na seznam obcházení proxy.</span><span class="sxs-lookup"><span data-stu-id="da126-103">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
 <span data-ttu-id="da126-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="da126-104">\<configuration></span></span>  
<span data-ttu-id="da126-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="da126-105">\<system.net></span></span>  
<span data-ttu-id="da126-106">\<defaultProxy – ></span><span class="sxs-lookup"><span data-stu-id="da126-106">\<defaultProxy></span></span>  
<span data-ttu-id="da126-107">\<bypasslist – ></span><span class="sxs-lookup"><span data-stu-id="da126-107">\<bypasslist></span></span>  
<span data-ttu-id="da126-108">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="da126-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da126-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da126-109">Syntax</span></span>  
  
```xml  
<add   
  address="regular expression"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da126-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="da126-110">Attributes and Elements</span></span>  
 <span data-ttu-id="da126-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="da126-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da126-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="da126-112">Attributes</span></span>  
  
|<span data-ttu-id="da126-113">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="da126-113">**Attribute**</span></span>|<span data-ttu-id="da126-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="da126-114">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="da126-115">**Adresa**</span><span class="sxs-lookup"><span data-stu-id="da126-115">**address**</span></span>|<span data-ttu-id="da126-116">Regulární výraz popisující IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="da126-116">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="da126-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="da126-117">Child Elements</span></span>  
 <span data-ttu-id="da126-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="da126-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="da126-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="da126-119">Parent Elements</span></span>  
  
|<span data-ttu-id="da126-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="da126-120">**Element**</span></span>|<span data-ttu-id="da126-121">**Popis**</span><span class="sxs-lookup"><span data-stu-id="da126-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="da126-122">bypasslist –</span><span class="sxs-lookup"><span data-stu-id="da126-122">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="da126-123">Poskytuje sadu regulární výrazy, které popisují adresy, které se nedoporučuje používat proxy server.</span><span class="sxs-lookup"><span data-stu-id="da126-123">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da126-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da126-124">Remarks</span></span>  
 <span data-ttu-id="da126-125">`add` Element vloží regulární výrazy, které popisují IP adresy nebo názvy serverů DNS do seznamu adres, které Nepoužívat proxy server.</span><span class="sxs-lookup"><span data-stu-id="da126-125">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="da126-126">Hodnota `address` atribut by měl mít regulární výraz, který popisuje sadu IP adres nebo názvů hostitelů.</span><span class="sxs-lookup"><span data-stu-id="da126-126">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="da126-127">Buďte opatrní při zadávání regulární výraz pro tento element.</span><span class="sxs-lookup"><span data-stu-id="da126-127">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="da126-128">Regulární výraz "[-z] +\\.contoso\\.com" odpovídá všechny hostitele v doméně contoso.com, ale také odpovídající libovolného hostitele v doméně contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="da126-128">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="da126-129">Vyhledat pouze na hostiteli v doméně contoso.com, použijte element anchor ("$"): "[-z] +\\.contoso\\.com$".</span><span class="sxs-lookup"><span data-stu-id="da126-129">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="da126-130">Další informace o regulárních výrazech najdete v tématu. [Regulární výrazy rozhraní .NET framework](../../../../../docs/standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="da126-130">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="da126-131">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="da126-131">Configuration Files</span></span>  
 <span data-ttu-id="da126-132">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="da126-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="da126-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="da126-133">Example</span></span>  
 <span data-ttu-id="da126-134">Následující příklad přidá dvě adresy do seznamu jednorázové přihlášení.</span><span class="sxs-lookup"><span data-stu-id="da126-134">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="da126-135">První obchází proxy server pro všechny servery v doméně contoso.com; druhý obchází proxy server pro všechny servery jehož IP adresa začíná s 192.168.</span><span class="sxs-lookup"><span data-stu-id="da126-135">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="da126-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="da126-136">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="da126-137">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="da126-137">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
