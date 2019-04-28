---
title: <clear> – element pro bypasslist (nastavení sítě)
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
ms.openlocfilehash: 7499d15f1d57887ffc3e78b83ed686c0c0f46cf4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674633"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="26f34-102">\<Vymazat > – Element pro bypasslist (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="26f34-102">\<clear> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="26f34-103">Vymaže seznam obcházení proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="26f34-103">Clears the proxy bypass list.</span></span>  
  
 <span data-ttu-id="26f34-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="26f34-104">\<configuration></span></span>  
<span data-ttu-id="26f34-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="26f34-105">\<system.net></span></span>  
<span data-ttu-id="26f34-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="26f34-106">\<defaultProxy></span></span>  
<span data-ttu-id="26f34-107">\<bypasslist – ></span><span class="sxs-lookup"><span data-stu-id="26f34-107">\<bypasslist></span></span>  
<span data-ttu-id="26f34-108">\<clear></span><span class="sxs-lookup"><span data-stu-id="26f34-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26f34-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26f34-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26f34-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="26f34-110">Attributes and Elements</span></span>  
 <span data-ttu-id="26f34-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="26f34-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26f34-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="26f34-112">Attributes</span></span>  
 <span data-ttu-id="26f34-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="26f34-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="26f34-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="26f34-114">Child Elements</span></span>  
 <span data-ttu-id="26f34-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="26f34-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="26f34-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="26f34-116">Parent Elements</span></span>  
  
|<span data-ttu-id="26f34-117">**Element**</span><span class="sxs-lookup"><span data-stu-id="26f34-117">**Element**</span></span>|<span data-ttu-id="26f34-118">**Popis**</span><span class="sxs-lookup"><span data-stu-id="26f34-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="26f34-119">bypasslist</span><span class="sxs-lookup"><span data-stu-id="26f34-119">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="26f34-120">Poskytuje sadu regulární výrazy, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="26f34-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26f34-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="26f34-121">Remarks</span></span>  
 <span data-ttu-id="26f34-122">`clear` Element vymaže všechny položky ze seznamu jednorázové přihlášení.</span><span class="sxs-lookup"><span data-stu-id="26f34-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="26f34-123">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="26f34-123">Configuration Files</span></span>  
 <span data-ttu-id="26f34-124">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="26f34-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="26f34-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="26f34-125">Example</span></span>  
 <span data-ttu-id="26f34-126">Následující příklad vymaže seznamu obcházení a přidá do seznamu obcházení dvě adresy.</span><span class="sxs-lookup"><span data-stu-id="26f34-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="26f34-127">První obcházejí proxy serveru pro všechny servery v doméně contoso.com; druhý vynechá proxy serveru pro všechny servery, IP adresa začíná s 192.168.</span><span class="sxs-lookup"><span data-stu-id="26f34-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="26f34-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="26f34-128">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="26f34-129">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="26f34-129">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
