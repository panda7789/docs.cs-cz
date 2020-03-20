---
title: <remove> – element pro webRequestModules (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
ms.openlocfilehash: afa1aef8ea71f43a136987ec5b6e1925c6d9fb40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154722"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="33cf9-102">\<odebrat> element pro webRequestModules (Nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="33cf9-102">\<remove> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="33cf9-103">Odebere z aplikace vlastní modul webového požadavku.</span><span class="sxs-lookup"><span data-stu-id="33cf9-103">Removes a custom Web request module from the application.</span></span>  
  
<span data-ttu-id="33cf9-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="33cf9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="33cf9-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="33cf9-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="33cf9-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="33cf9-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="33cf9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<odebrat>**</span><span class="sxs-lookup"><span data-stu-id="33cf9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="33cf9-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33cf9-108">Syntax</span></span>  
  
```xml  
<remove
  prefix="URI prefix"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="33cf9-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="33cf9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="33cf9-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="33cf9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="33cf9-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="33cf9-111">Attributes</span></span>  
  
|<span data-ttu-id="33cf9-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="33cf9-112">**Attribute**</span></span>|<span data-ttu-id="33cf9-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="33cf9-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="33cf9-114">Předpona identifikátoru URI pro požadavky zpracovávané tímto modulem webového požadavku.</span><span class="sxs-lookup"><span data-stu-id="33cf9-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="33cf9-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="33cf9-115">Child Elements</span></span>  
 <span data-ttu-id="33cf9-116">Žádné.</span><span class="sxs-lookup"><span data-stu-id="33cf9-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="33cf9-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="33cf9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="33cf9-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="33cf9-118">**Element**</span></span>|<span data-ttu-id="33cf9-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="33cf9-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="33cf9-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="33cf9-120">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="33cf9-121">Určuje moduly, které mají být používány k vyžádání informací od síťových hostitelů.</span><span class="sxs-lookup"><span data-stu-id="33cf9-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33cf9-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="33cf9-122">Remarks</span></span>  
 <span data-ttu-id="33cf9-123">Prvek `remove` odebere registrovaný modul webového požadavku pro zadanou předponu URI.</span><span class="sxs-lookup"><span data-stu-id="33cf9-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="33cf9-124">Hodnota atributu `prefix` by měla být úvodníznaky platného identifikátoru`http`URI –`http://www.contoso.com`například " ", nebo " ".</span><span class="sxs-lookup"><span data-stu-id="33cf9-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="33cf9-125">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="33cf9-125">Configuration Files</span></span>  
 <span data-ttu-id="33cf9-126">Tento prvek lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="33cf9-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="33cf9-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="33cf9-127">Example</span></span>  

<span data-ttu-id="33cf9-128">Následující příklad odebere existující modul webového požadavku pro protokol HTTP a poté zaregistruje nový vlastní modul webových požadavků pro požadavky HTTP. `www.contoso.com`</span><span class="sxs-lookup"><span data-stu-id="33cf9-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix="http">  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="33cf9-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="33cf9-129">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="33cf9-130">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="33cf9-130">Network Settings Schema</span></span>](index.md)
