---
title: "&lt;bypasslist –&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 20e3676e69357dc73433876275cb2737ee235552
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltbypasslistgt-element-network-settings"></a><span data-ttu-id="89fe9-102">&lt;bypasslist –&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="89fe9-102">&lt;bypasslist&gt; Element (Network Settings)</span></span>
<span data-ttu-id="89fe9-103">Poskytuje sadu regulární výrazy, které popisují adresy, které se nedoporučuje používat proxy server.</span><span class="sxs-lookup"><span data-stu-id="89fe9-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  
  
 <span data-ttu-id="89fe9-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="89fe9-104">\<configuration></span></span>  
<span data-ttu-id="89fe9-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="89fe9-105">\<system.net></span></span>  
<span data-ttu-id="89fe9-106">\<defaultProxy – ></span><span class="sxs-lookup"><span data-stu-id="89fe9-106">\<defaultProxy></span></span>  
<span data-ttu-id="89fe9-107">\<bypasslist – ></span><span class="sxs-lookup"><span data-stu-id="89fe9-107">\<bypasslist></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89fe9-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89fe9-108">Syntax</span></span>  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89fe9-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="89fe9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="89fe9-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="89fe9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89fe9-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="89fe9-111">Attributes</span></span>  
 <span data-ttu-id="89fe9-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="89fe9-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="89fe9-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="89fe9-113">Child Elements</span></span>  
  
|<span data-ttu-id="89fe9-114">**Element**</span><span class="sxs-lookup"><span data-stu-id="89fe9-114">**Element**</span></span>|<span data-ttu-id="89fe9-115">**Popis**</span><span class="sxs-lookup"><span data-stu-id="89fe9-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="89fe9-116">add</span><span class="sxs-lookup"><span data-stu-id="89fe9-116">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="89fe9-117">Přidá IP adresy nebo názvu DNS na seznam obcházení proxy.</span><span class="sxs-lookup"><span data-stu-id="89fe9-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="89fe9-118">Vymazat</span><span class="sxs-lookup"><span data-stu-id="89fe9-118">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="89fe9-119">Vymaže seznam obcházení.</span><span class="sxs-lookup"><span data-stu-id="89fe9-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="89fe9-120">remove</span><span class="sxs-lookup"><span data-stu-id="89fe9-120">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="89fe9-121">Odebere seznam obcházení proxy adresy IP nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="89fe9-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="89fe9-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="89fe9-122">Parent Elements</span></span>  
  
|<span data-ttu-id="89fe9-123">**Element**</span><span class="sxs-lookup"><span data-stu-id="89fe9-123">**Element**</span></span>|<span data-ttu-id="89fe9-124">**Popis**</span><span class="sxs-lookup"><span data-stu-id="89fe9-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="89fe9-125">defaultProxy –</span><span class="sxs-lookup"><span data-stu-id="89fe9-125">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="89fe9-126">Nakonfiguruje server proxy protokolu HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="89fe9-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89fe9-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89fe9-127">Remarks</span></span>  
 <span data-ttu-id="89fe9-128">Seznam obcházení obsahuje regulární výrazy, které popisují identifikátory URI, <xref:System.Net.WebRequest> instance přístup přímo místo z prostřednictvím proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="89fe9-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="89fe9-129">Buďte opatrní při zadávání regulární výraz pro tento element.</span><span class="sxs-lookup"><span data-stu-id="89fe9-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="89fe9-130">Regulární výraz "[-z] +\\.contoso\\.com" odpovídá všechny hostitele v doméně contoso.com, ale také odpovídající libovolného hostitele v doméně contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="89fe9-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="89fe9-131">Vyhledat pouze na hostiteli v doméně contoso.com, použijte element anchor ("$"): "[-z] +\\.contoso\\.com$".</span><span class="sxs-lookup"><span data-stu-id="89fe9-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="89fe9-132">Další informace o regulárních výrazech najdete v tématu. [Regulární výrazy rozhraní .NET framework](../../../../../docs/standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="89fe9-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="89fe9-133">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="89fe9-133">Configuration Files</span></span>  
 <span data-ttu-id="89fe9-134">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="89fe9-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="89fe9-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="89fe9-135">Example</span></span>  
 <span data-ttu-id="89fe9-136">Následující příklad přidá dvě adresy do seznamu jednorázové přihlášení.</span><span class="sxs-lookup"><span data-stu-id="89fe9-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="89fe9-137">První obchází proxy server pro všechny servery v doméně contoso.com; druhý obchází proxy server pro všechny servery začít jejichž IP adresy s 192.168.</span><span class="sxs-lookup"><span data-stu-id="89fe9-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="89fe9-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="89fe9-138">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="89fe9-139">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="89fe9-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
