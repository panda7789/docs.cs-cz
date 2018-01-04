---
title: "&lt;Odebrat&gt; Element pro bypasslist – (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove elemment, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
caps.latest.revision: "16"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: a385401217c10a316268f48757e46e3d0cfea09c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt-element-for-bypasslist-network-settings"></a><span data-ttu-id="23a63-102">&lt;Odebrat&gt; Element pro bypasslist – (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="23a63-102">&lt;remove&gt; Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="23a63-103">Odebere seznam obcházení proxy adresy IP nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="23a63-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>  
  
 <span data-ttu-id="23a63-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="23a63-104">\<configuration></span></span>  
<span data-ttu-id="23a63-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="23a63-105">\<system.net></span></span>  
<span data-ttu-id="23a63-106">\<defaultProxy – ></span><span class="sxs-lookup"><span data-stu-id="23a63-106">\<defaultProxy></span></span>  
<span data-ttu-id="23a63-107">\<bypasslist – ></span><span class="sxs-lookup"><span data-stu-id="23a63-107">\<bypasslist></span></span>  
<span data-ttu-id="23a63-108">\<Odebrat ></span><span class="sxs-lookup"><span data-stu-id="23a63-108">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23a63-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23a63-109">Syntax</span></span>  
  
```xml  
<remove   
  address="regular expression"   
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23a63-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="23a63-110">Attributes and Elements</span></span>  
 <span data-ttu-id="23a63-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="23a63-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23a63-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="23a63-112">Attributes</span></span>  
  
|<span data-ttu-id="23a63-113">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="23a63-113">**Attribute**</span></span>|<span data-ttu-id="23a63-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="23a63-114">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="23a63-115">Regulární výraz popisující IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="23a63-115">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23a63-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="23a63-116">Child Elements</span></span>  
 <span data-ttu-id="23a63-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="23a63-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="23a63-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="23a63-118">Parent Elements</span></span>  
  
|<span data-ttu-id="23a63-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="23a63-119">**Element**</span></span>|<span data-ttu-id="23a63-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="23a63-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="23a63-121">bypasslist –</span><span class="sxs-lookup"><span data-stu-id="23a63-121">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="23a63-122">Poskytuje sadu regulární výrazy, které popisují adresy, které se nedoporučuje používat proxy server.</span><span class="sxs-lookup"><span data-stu-id="23a63-122">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23a63-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="23a63-123">Remarks</span></span>  
 <span data-ttu-id="23a63-124">`remove` Element odebere regulární výrazy, které popisují IP adresy nebo názvy serverů DNS ze seznamu adres, které Nepoužívat proxy server.</span><span class="sxs-lookup"><span data-stu-id="23a63-124">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="23a63-125">Adresy byly dříve definovány v konfiguračním souboru nebo na vyšší úrovni v hierarchii konfigurace.</span><span class="sxs-lookup"><span data-stu-id="23a63-125">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="23a63-126">Hodnota `address` atribut by měl mít regulární výraz, který popisuje sadu IP adres nebo názvů hostitelů.</span><span class="sxs-lookup"><span data-stu-id="23a63-126">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="23a63-127">Další informace o regulárních výrazech najdete v tématu. [Regulární výrazy rozhraní .NET framework](../../../../../docs/standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="23a63-127">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="23a63-128">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="23a63-128">Configuration Files</span></span>  
 <span data-ttu-id="23a63-129">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="23a63-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23a63-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="23a63-130">Example</span></span>  
 <span data-ttu-id="23a63-131">Následující příklad odebere všechny předchozí definice pro doménu společnosti adventure-works.com a pak přidá do seznamu jednorázové přihlášení k doméně contoso.com.</span><span class="sxs-lookup"><span data-stu-id="23a63-131">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <remove address="[a-z]+\.adventure-works\.com$" />  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="23a63-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="23a63-132">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="23a63-133">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="23a63-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
