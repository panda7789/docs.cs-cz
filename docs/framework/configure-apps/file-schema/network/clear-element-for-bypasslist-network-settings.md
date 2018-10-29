---
title: '&lt;Vymazat&gt; – Element pro bypasslist (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, bypasslist
- <clear> element, bypasslist
- <bypasslist>, clear element
- bypasslist, clear element
ms.assetid: 301584ca-a914-4100-b180-3b288d3b099e
ms.openlocfilehash: 5c26857496d52f9fb98ef76a72cb72fe8d852349
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201410"
---
# <a name="ltcleargt-element-for-bypasslist-network-settings"></a><span data-ttu-id="4971a-102">&lt;Vymazat&gt; – Element pro bypasslist (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="4971a-102">&lt;clear&gt; Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="4971a-103">Vymaže seznam obcházení proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="4971a-103">Clears the proxy bypass list.</span></span>  
  
 <span data-ttu-id="4971a-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="4971a-104">\<configuration></span></span>  
<span data-ttu-id="4971a-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="4971a-105">\<system.net></span></span>  
<span data-ttu-id="4971a-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="4971a-106">\<defaultProxy></span></span>  
<span data-ttu-id="4971a-107">\<bypasslist – ></span><span class="sxs-lookup"><span data-stu-id="4971a-107">\<bypasslist></span></span>  
<span data-ttu-id="4971a-108">\<Vymazat ></span><span class="sxs-lookup"><span data-stu-id="4971a-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4971a-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4971a-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4971a-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4971a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4971a-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4971a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4971a-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="4971a-112">Attributes</span></span>  
 <span data-ttu-id="4971a-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="4971a-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4971a-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4971a-114">Child Elements</span></span>  
 <span data-ttu-id="4971a-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="4971a-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4971a-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4971a-116">Parent Elements</span></span>  
  
|<span data-ttu-id="4971a-117">**Element**</span><span class="sxs-lookup"><span data-stu-id="4971a-117">**Element**</span></span>|<span data-ttu-id="4971a-118">**Popis**</span><span class="sxs-lookup"><span data-stu-id="4971a-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4971a-119">atribut bypasslist bude</span><span class="sxs-lookup"><span data-stu-id="4971a-119">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="4971a-120">Poskytuje sadu regulární výrazy, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="4971a-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4971a-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4971a-121">Remarks</span></span>  
 <span data-ttu-id="4971a-122">`clear` Element vymaže všechny položky ze seznamu jednorázové přihlášení.</span><span class="sxs-lookup"><span data-stu-id="4971a-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4971a-123">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="4971a-123">Configuration Files</span></span>  
 <span data-ttu-id="4971a-124">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="4971a-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4971a-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="4971a-125">Example</span></span>  
 <span data-ttu-id="4971a-126">Následující příklad vymaže seznamu obcházení a přidá do seznamu obcházení dvě adresy.</span><span class="sxs-lookup"><span data-stu-id="4971a-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="4971a-127">První obcházejí proxy serveru pro všechny servery v doméně contoso.com; druhý vynechá proxy serveru pro všechny servery, IP adresa začíná s 192.168.</span><span class="sxs-lookup"><span data-stu-id="4971a-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4971a-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="4971a-128">See Also</span></span>  
- <xref:System.Net.WebProxy?displayProperty=nameWithType>  
- [<span data-ttu-id="4971a-129">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="4971a-129">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
