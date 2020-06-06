---
title: <remove> – element pro bypasslist (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove element, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
ms.openlocfilehash: 97b49a8a520d6a4f72945366874991d2deb18710
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697895"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="e5ca3-102">\<remove> – element pro bypasslist (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="e5ca3-102">\<remove> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="e5ca3-103">Odebere IP adresu nebo název DNS ze seznamu obcházení proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="e5ca3-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  

## <a name="syntax"></a><span data-ttu-id="e5ca3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5ca3-104">Syntax</span></span>

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5ca3-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e5ca3-105">Attributes and Elements</span></span>

<span data-ttu-id="e5ca3-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e5ca3-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5ca3-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="e5ca3-107">Attributes</span></span>

|<span data-ttu-id="e5ca3-108">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="e5ca3-108">**Attribute**</span></span>|<span data-ttu-id="e5ca3-109">**Popis**</span><span class="sxs-lookup"><span data-stu-id="e5ca3-109">**Description**</span></span>|
|-------------------|---------------------|
|`address`|<span data-ttu-id="e5ca3-110">Regulární výraz popisující IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="e5ca3-110">A regular expression describing an IP address or DNS name.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e5ca3-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e5ca3-111">Child Elements</span></span>

<span data-ttu-id="e5ca3-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="e5ca3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e5ca3-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e5ca3-113">Parent Elements</span></span>

|<span data-ttu-id="e5ca3-114">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="e5ca3-114">**Element**</span></span>|<span data-ttu-id="e5ca3-115">**Popis**</span><span class="sxs-lookup"><span data-stu-id="e5ca3-115">**Description**</span></span>|
|-----------------|---------------------|
|[<span data-ttu-id="e5ca3-116">bypasslist</span><span class="sxs-lookup"><span data-stu-id="e5ca3-116">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="e5ca3-117">Poskytuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="e5ca3-117">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e5ca3-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e5ca3-118">Remarks</span></span>

<span data-ttu-id="e5ca3-119">`remove`Element odstraní regulární výrazy POPISUJÍCÍ IP adresy nebo názvy serverů DNS ze seznamu adres, které obcházejí proxy server.</span><span class="sxs-lookup"><span data-stu-id="e5ca3-119">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="e5ca3-120">Adresy byly definovány dříve v konfiguračním souboru nebo na vyšší úrovni v konfigurační hierarchii.</span><span class="sxs-lookup"><span data-stu-id="e5ca3-120">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>

<span data-ttu-id="e5ca3-121">Hodnota `address` atributu by měla být regulární výraz, který popisuje sadu IP adres nebo názvů hostitelů.</span><span class="sxs-lookup"><span data-stu-id="e5ca3-121">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>

<span data-ttu-id="e5ca3-122">Další informace o regulárních výrazech naleznete v tématu. [.NET Framework regulární výrazy](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e5ca3-122">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="e5ca3-123">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="e5ca3-123">Configuration Files</span></span>

<span data-ttu-id="e5ca3-124">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="e5ca3-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="e5ca3-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5ca3-125">Example</span></span>

<span data-ttu-id="e5ca3-126">Následující příklad odebere předchozí definici pro doménu adventure-works.com a pak do seznamu pro obejití přidá doménu contoso.com.</span><span class="sxs-lookup"><span data-stu-id="e5ca3-126">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e5ca3-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5ca3-127">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="e5ca3-128">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="e5ca3-128">Network Settings Schema</span></span>](index.md)
