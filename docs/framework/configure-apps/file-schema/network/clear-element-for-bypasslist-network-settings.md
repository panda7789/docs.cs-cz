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
ms.openlocfilehash: e5305d9aed09b6c4d1ad4201e5e08e007a14c7c0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664189"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="8d05b-102">\<Clear – element > pro BypassList (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="8d05b-102">\<clear> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="8d05b-103">Vymaže seznam obcházení proxy serverů.</span><span class="sxs-lookup"><span data-stu-id="8d05b-103">Clears the proxy bypass list.</span></span>  
  
 <span data-ttu-id="8d05b-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="8d05b-104">\<configuration></span></span>  
<span data-ttu-id="8d05b-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="8d05b-105">\<system.net></span></span>  
<span data-ttu-id="8d05b-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="8d05b-106">\<defaultProxy></span></span>  
<span data-ttu-id="8d05b-107">\<BypassList ></span><span class="sxs-lookup"><span data-stu-id="8d05b-107">\<bypasslist></span></span>  
<span data-ttu-id="8d05b-108">\<Vymazat ></span><span class="sxs-lookup"><span data-stu-id="8d05b-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d05b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d05b-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d05b-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8d05b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8d05b-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8d05b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d05b-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="8d05b-112">Attributes</span></span>  
 <span data-ttu-id="8d05b-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="8d05b-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8d05b-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8d05b-114">Child Elements</span></span>  
 <span data-ttu-id="8d05b-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="8d05b-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8d05b-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8d05b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="8d05b-117">**Element**</span><span class="sxs-lookup"><span data-stu-id="8d05b-117">**Element**</span></span>|<span data-ttu-id="8d05b-118">**Popis**</span><span class="sxs-lookup"><span data-stu-id="8d05b-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8d05b-119">bypasslist</span><span class="sxs-lookup"><span data-stu-id="8d05b-119">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="8d05b-120">Poskytuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="8d05b-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d05b-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d05b-121">Remarks</span></span>  
 <span data-ttu-id="8d05b-122">`clear` Prvek vymaže všechny položky ze seznamu pro obejití.</span><span class="sxs-lookup"><span data-stu-id="8d05b-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8d05b-123">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="8d05b-123">Configuration Files</span></span>  
 <span data-ttu-id="8d05b-124">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="8d05b-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d05b-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d05b-125">Example</span></span>  
 <span data-ttu-id="8d05b-126">Následující příklad vymaže seznam obcházení a potom přidá dvě adresy do seznamu pro obejití.</span><span class="sxs-lookup"><span data-stu-id="8d05b-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="8d05b-127">První obchází proxy server pro všechny servery v doméně contoso.com; Druhá obchází proxy server pro všechny servery, jejichž IP adresa začíná 192,168.</span><span class="sxs-lookup"><span data-stu-id="8d05b-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8d05b-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d05b-128">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="8d05b-129">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="8d05b-129">Network Settings Schema</span></span>](index.md)
