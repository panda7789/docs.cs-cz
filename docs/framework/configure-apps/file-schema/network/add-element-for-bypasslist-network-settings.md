---
title: '&lt;Přidat&gt; Element pro bypasslist – (nastavení sítě)'
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d786d4fd7e6663649408b36fb518db06063ef916
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-element-for-bypasslist-network-settings"></a><span data-ttu-id="f9b4d-102">&lt;Přidat&gt; Element pro bypasslist – (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="f9b4d-102">&lt;add&gt; Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="f9b4d-103">Přidá IP adresy nebo názvu DNS na seznam obcházení proxy.</span><span class="sxs-lookup"><span data-stu-id="f9b4d-103">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
 <span data-ttu-id="f9b4d-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="f9b4d-104">\<configuration></span></span>  
<span data-ttu-id="f9b4d-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="f9b4d-105">\<system.net></span></span>  
<span data-ttu-id="f9b4d-106">\<defaultProxy – ></span><span class="sxs-lookup"><span data-stu-id="f9b4d-106">\<defaultProxy></span></span>  
<span data-ttu-id="f9b4d-107">\<bypasslist – ></span><span class="sxs-lookup"><span data-stu-id="f9b4d-107">\<bypasslist></span></span>  
<span data-ttu-id="f9b4d-108">\<add></span><span class="sxs-lookup"><span data-stu-id="f9b4d-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9b4d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9b4d-109">Syntax</span></span>  
  
```xml  
<add   
  address="regular expression"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9b4d-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f9b4d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f9b4d-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f9b4d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9b4d-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="f9b4d-112">Attributes</span></span>  
  
|<span data-ttu-id="f9b4d-113">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="f9b4d-113">**Attribute**</span></span>|<span data-ttu-id="f9b4d-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="f9b4d-114">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="f9b4d-115">**Adresa**</span><span class="sxs-lookup"><span data-stu-id="f9b4d-115">**address**</span></span>|<span data-ttu-id="f9b4d-116">Regulární výraz popisující IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="f9b4d-116">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9b4d-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f9b4d-117">Child Elements</span></span>  
 <span data-ttu-id="f9b4d-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="f9b4d-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f9b4d-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f9b4d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f9b4d-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="f9b4d-120">**Element**</span></span>|<span data-ttu-id="f9b4d-121">**Popis**</span><span class="sxs-lookup"><span data-stu-id="f9b4d-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f9b4d-122">bypasslist –</span><span class="sxs-lookup"><span data-stu-id="f9b4d-122">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="f9b4d-123">Poskytuje sadu regulární výrazy, které popisují adresy, které se nedoporučuje používat proxy server.</span><span class="sxs-lookup"><span data-stu-id="f9b4d-123">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9b4d-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f9b4d-124">Remarks</span></span>  
 <span data-ttu-id="f9b4d-125">`add` Element vloží regulární výrazy, které popisují IP adresy nebo názvy serverů DNS do seznamu adres, které Nepoužívat proxy server.</span><span class="sxs-lookup"><span data-stu-id="f9b4d-125">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="f9b4d-126">Hodnota `address` atribut by měl mít regulární výraz, který popisuje sadu IP adres nebo názvů hostitelů.</span><span class="sxs-lookup"><span data-stu-id="f9b4d-126">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="f9b4d-127">Buďte opatrní při zadávání regulární výraz pro tento element.</span><span class="sxs-lookup"><span data-stu-id="f9b4d-127">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="f9b4d-128">Regulární výraz "[-z] +\\.contoso\\.com" odpovídá všechny hostitele v doméně contoso.com, ale také odpovídající libovolného hostitele v doméně contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="f9b4d-128">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="f9b4d-129">Vyhledat pouze na hostiteli v doméně contoso.com, použijte element anchor ("$"): "[-z] +\\.contoso\\.com$".</span><span class="sxs-lookup"><span data-stu-id="f9b4d-129">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="f9b4d-130">Další informace o regulárních výrazech najdete v tématu. [Regulární výrazy rozhraní .NET framework](../../../../../docs/standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="f9b4d-130">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f9b4d-131">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="f9b4d-131">Configuration Files</span></span>  
 <span data-ttu-id="f9b4d-132">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="f9b4d-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9b4d-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9b4d-133">Example</span></span>  
 <span data-ttu-id="f9b4d-134">Následující příklad přidá dvě adresy do seznamu jednorázové přihlášení.</span><span class="sxs-lookup"><span data-stu-id="f9b4d-134">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="f9b4d-135">První obchází proxy server pro všechny servery v doméně contoso.com; druhý obchází proxy server pro všechny servery jehož IP adresa začíná s 192.168.</span><span class="sxs-lookup"><span data-stu-id="f9b4d-135">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f9b4d-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9b4d-136">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="f9b4d-137">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="f9b4d-137">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
