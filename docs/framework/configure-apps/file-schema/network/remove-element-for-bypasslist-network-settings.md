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
ms.openlocfilehash: 99c18bd5b779845d52831b4a9591eaf4d5e5530b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920966"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="0b52a-102">\<Remove – element > pro BypassList (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="0b52a-102">\<remove> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="0b52a-103">Odebere IP adresu nebo název DNS ze seznamu obcházení proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="0b52a-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>

<span data-ttu-id="0b52a-104">\<> Konfigurace </span><span class="sxs-lookup"><span data-stu-id="0b52a-104">\<configuration></span></span>\
<span data-ttu-id="0b52a-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="0b52a-105">\<system.net></span></span>\
<span data-ttu-id="0b52a-106">\<defaultProxy > </span><span class="sxs-lookup"><span data-stu-id="0b52a-106">\<defaultProxy></span></span>\
<span data-ttu-id="0b52a-107">\<BypassList > </span><span class="sxs-lookup"><span data-stu-id="0b52a-107">\<bypasslist></span></span>\
<span data-ttu-id="0b52a-108">\<odebrat ></span><span class="sxs-lookup"><span data-stu-id="0b52a-108">\<remove></span></span>

## <a name="syntax"></a><span data-ttu-id="0b52a-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b52a-109">Syntax</span></span>

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0b52a-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0b52a-110">Attributes and Elements</span></span>

<span data-ttu-id="0b52a-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0b52a-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0b52a-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="0b52a-112">Attributes</span></span>

|<span data-ttu-id="0b52a-113">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="0b52a-113">**Attribute**</span></span>|<span data-ttu-id="0b52a-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="0b52a-114">**Description**</span></span>|
|-------------------|---------------------|
|`address`|<span data-ttu-id="0b52a-115">Regulární výraz popisující IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="0b52a-115">A regular expression describing an IP address or DNS name.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="0b52a-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0b52a-116">Child Elements</span></span>

<span data-ttu-id="0b52a-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="0b52a-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0b52a-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0b52a-118">Parent Elements</span></span>

|<span data-ttu-id="0b52a-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="0b52a-119">**Element**</span></span>|<span data-ttu-id="0b52a-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="0b52a-120">**Description**</span></span>|
|-----------------|---------------------|
|[<span data-ttu-id="0b52a-121">bypasslist</span><span class="sxs-lookup"><span data-stu-id="0b52a-121">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="0b52a-122">Poskytuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="0b52a-122">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0b52a-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b52a-123">Remarks</span></span>

<span data-ttu-id="0b52a-124">`remove` Element odstraní regulární výrazy popisující IP adresy nebo názvy serverů DNS ze seznamu adres, které obcházejí proxy server.</span><span class="sxs-lookup"><span data-stu-id="0b52a-124">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="0b52a-125">Adresy byly definovány dříve v konfiguračním souboru nebo na vyšší úrovni v konfigurační hierarchii.</span><span class="sxs-lookup"><span data-stu-id="0b52a-125">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>

<span data-ttu-id="0b52a-126">Hodnota `address` atributu by měla být regulární výraz, který popisuje sadu IP adres nebo názvů hostitelů.</span><span class="sxs-lookup"><span data-stu-id="0b52a-126">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>

<span data-ttu-id="0b52a-127">Další informace o regulárních výrazech naleznete v tématu. [.NET Framework regulární výrazy](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="0b52a-127">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="0b52a-128">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="0b52a-128">Configuration Files</span></span>

<span data-ttu-id="0b52a-129">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="0b52a-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="0b52a-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b52a-130">Example</span></span>

<span data-ttu-id="0b52a-131">Následující příklad odebere předchozí definici pro doménu adventure-works.com a pak do seznamu pro obejití přidá doménu contoso.com.</span><span class="sxs-lookup"><span data-stu-id="0b52a-131">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0b52a-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b52a-132">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="0b52a-133">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="0b52a-133">Network Settings Schema</span></span>](index.md)
