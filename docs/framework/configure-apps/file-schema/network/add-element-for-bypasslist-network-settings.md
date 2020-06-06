---
title: <add> – element pro bypasslist (nastavení sítě)
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
ms.openlocfilehash: 652b8738a201aaa98fa2c5c435fee1a6da91673b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155074"
---
# <a name="add-element-for-bypasslist-network-settings"></a><span data-ttu-id="f5d0f-102">\<add> – element pro bypasslist (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="f5d0f-102">\<add> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="f5d0f-103">Přidá IP adresu nebo název DNS do seznamu obcházení proxy serverů.</span><span class="sxs-lookup"><span data-stu-id="f5d0f-103">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="f5d0f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5d0f-104">Syntax</span></span>  
  
```xml  
<add
  address="regular expression"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5d0f-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f5d0f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f5d0f-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f5d0f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5d0f-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="f5d0f-107">Attributes</span></span>  
  
|<span data-ttu-id="f5d0f-108">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="f5d0f-108">**Attribute**</span></span>|<span data-ttu-id="f5d0f-109">**Popis**</span><span class="sxs-lookup"><span data-stu-id="f5d0f-109">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="f5d0f-110">**adresáře**</span><span class="sxs-lookup"><span data-stu-id="f5d0f-110">**address**</span></span>|<span data-ttu-id="f5d0f-111">Regulární výraz popisující IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="f5d0f-111">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f5d0f-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f5d0f-112">Child Elements</span></span>  
 <span data-ttu-id="f5d0f-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="f5d0f-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f5d0f-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f5d0f-114">Parent Elements</span></span>  
  
|<span data-ttu-id="f5d0f-115">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="f5d0f-115">**Element**</span></span>|<span data-ttu-id="f5d0f-116">**Popis**</span><span class="sxs-lookup"><span data-stu-id="f5d0f-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f5d0f-117">bypasslist</span><span class="sxs-lookup"><span data-stu-id="f5d0f-117">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="f5d0f-118">Poskytuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="f5d0f-118">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5d0f-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f5d0f-119">Remarks</span></span>  
 <span data-ttu-id="f5d0f-120">`add`Element vloží regulární výrazy POPISUJÍCÍ IP adresy nebo názvy serverů DNS na seznam adres, které obcházejí proxy server.</span><span class="sxs-lookup"><span data-stu-id="f5d0f-120">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="f5d0f-121">Hodnota `address` atributu by měla být regulární výraz, který popisuje sadu IP adres nebo názvů hostitelů.</span><span class="sxs-lookup"><span data-stu-id="f5d0f-121">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="f5d0f-122">Při zadávání regulárního výrazu pro tento prvek byste měli použít upozornění.</span><span class="sxs-lookup"><span data-stu-id="f5d0f-122">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="f5d0f-123">Regulární výraz "[a-z] + \\ . contoso \\ . com" odpovídá jakémukoli hostiteli v doméně contoso.com, ale také odpovídá jakémukoli hostiteli v doméně contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="f5d0f-123">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="f5d0f-124">Chcete-li spárovat pouze hostitele v doméně contoso.com, použijte kotvu ("$"): "[a-z] + \\ . contoso \\ . com $".</span><span class="sxs-lookup"><span data-stu-id="f5d0f-124">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="f5d0f-125">Další informace o regulárních výrazech naleznete v tématu. [.NET Framework regulární výrazy](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="f5d0f-125">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f5d0f-126">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="f5d0f-126">Configuration Files</span></span>  
 <span data-ttu-id="f5d0f-127">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="f5d0f-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5d0f-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5d0f-128">Example</span></span>  
 <span data-ttu-id="f5d0f-129">Následující příklad přidá dvě adresy do seznamu pro obejití.</span><span class="sxs-lookup"><span data-stu-id="f5d0f-129">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="f5d0f-130">První obchází proxy server pro všechny servery v doméně contoso.com; Druhá obchází proxy server pro všechny servery, jejichž IP adresa začíná 192,168.</span><span class="sxs-lookup"><span data-stu-id="f5d0f-130">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f5d0f-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5d0f-131">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="f5d0f-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="f5d0f-132">Network Settings Schema</span></span>](index.md)
