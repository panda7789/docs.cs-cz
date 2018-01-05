---
title: "&lt;Vymazat&gt; Element pro bypasslist – (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, bypasslist
- <clear> element, bypasslist
- <bypasslist>, clear element
- bypasslist, clear element
ms.assetid: 301584ca-a914-4100-b180-3b288d3b099e
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 620197065a8e689997b4081b3d90169aa0e3c6c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-element-for-bypasslist-network-settings"></a><span data-ttu-id="c7e02-102">&lt;Vymazat&gt; Element pro bypasslist – (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="c7e02-102">&lt;clear&gt; Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="c7e02-103">Vymaže seznam obcházení proxy.</span><span class="sxs-lookup"><span data-stu-id="c7e02-103">Clears the proxy bypass list.</span></span>  
  
 <span data-ttu-id="c7e02-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="c7e02-104">\<configuration></span></span>  
<span data-ttu-id="c7e02-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="c7e02-105">\<system.net></span></span>  
<span data-ttu-id="c7e02-106">\<defaultProxy – ></span><span class="sxs-lookup"><span data-stu-id="c7e02-106">\<defaultProxy></span></span>  
<span data-ttu-id="c7e02-107">\<bypasslist – ></span><span class="sxs-lookup"><span data-stu-id="c7e02-107">\<bypasslist></span></span>  
<span data-ttu-id="c7e02-108">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="c7e02-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7e02-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7e02-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7e02-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c7e02-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c7e02-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c7e02-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c7e02-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="c7e02-112">Attributes</span></span>  
 <span data-ttu-id="c7e02-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="c7e02-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c7e02-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c7e02-114">Child Elements</span></span>  
 <span data-ttu-id="c7e02-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="c7e02-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c7e02-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c7e02-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c7e02-117">**Element**</span><span class="sxs-lookup"><span data-stu-id="c7e02-117">**Element**</span></span>|<span data-ttu-id="c7e02-118">**Popis**</span><span class="sxs-lookup"><span data-stu-id="c7e02-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c7e02-119">bypasslist –</span><span class="sxs-lookup"><span data-stu-id="c7e02-119">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="c7e02-120">Poskytuje sadu regulární výrazy, které popisují adresy, které se nedoporučuje používat proxy server.</span><span class="sxs-lookup"><span data-stu-id="c7e02-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7e02-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c7e02-121">Remarks</span></span>  
 <span data-ttu-id="c7e02-122">`clear` Element vymaže všechny položky ze seznamu jednorázové přihlášení.</span><span class="sxs-lookup"><span data-stu-id="c7e02-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c7e02-123">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="c7e02-123">Configuration Files</span></span>  
 <span data-ttu-id="c7e02-124">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="c7e02-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7e02-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="c7e02-125">Example</span></span>  
 <span data-ttu-id="c7e02-126">Následující příklad vymaže seznam obcházení a potom přidá dvě adresy do seznamu jednorázové přihlášení.</span><span class="sxs-lookup"><span data-stu-id="c7e02-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="c7e02-127">První obchází proxy server pro všechny servery v doméně contoso.com; druhý obchází proxy server pro všechny servery jehož IP adresa začíná s 192.168.</span><span class="sxs-lookup"><span data-stu-id="c7e02-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
         <clear/>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="c7e02-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7e02-128">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="c7e02-129">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="c7e02-129">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
