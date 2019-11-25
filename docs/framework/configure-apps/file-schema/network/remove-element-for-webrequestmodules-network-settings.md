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
ms.openlocfilehash: ca3a78a491c61b6e23dab0f96eebceb3157706ae
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089139"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="b1326-102">\<odebrat element > pro webRequestModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="b1326-102">\<remove> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="b1326-103">Odebere z aplikace vlastní modul webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="b1326-103">Removes a custom Web request module from the application.</span></span>  
  
<span data-ttu-id="b1326-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="b1326-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b1326-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b1326-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="b1326-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<webRequestModules >** ](webrequestmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b1326-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="b1326-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<odebrat >**</span><span class="sxs-lookup"><span data-stu-id="b1326-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="b1326-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1326-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1326-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b1326-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b1326-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b1326-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1326-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="b1326-111">Attributes</span></span>  
  
|<span data-ttu-id="b1326-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="b1326-112">**Attribute**</span></span>|<span data-ttu-id="b1326-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="b1326-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="b1326-114">Předpona identifikátoru URI pro požadavky zpracovávané tímto modulem webového požadavku.</span><span class="sxs-lookup"><span data-stu-id="b1326-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1326-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b1326-115">Child Elements</span></span>  
 <span data-ttu-id="b1326-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="b1326-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1326-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b1326-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b1326-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="b1326-118">**Element**</span></span>|<span data-ttu-id="b1326-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="b1326-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b1326-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="b1326-120">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="b1326-121">Určuje moduly, které se použijí k vyžádání informací od hostitelů v síti.</span><span class="sxs-lookup"><span data-stu-id="b1326-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1326-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1326-122">Remarks</span></span>  
 <span data-ttu-id="b1326-123">Element `remove` odebere registrovaný modul webové žádosti pro zadanou předponu identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="b1326-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="b1326-124">Hodnota atributu `prefix` by měla být úvodními znaky platného identifikátoru URI, například "`http`" nebo "`http://www.contoso.com`".</span><span class="sxs-lookup"><span data-stu-id="b1326-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b1326-125">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="b1326-125">Configuration Files</span></span>  
 <span data-ttu-id="b1326-126">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="b1326-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1326-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="b1326-127">Example</span></span>  

<span data-ttu-id="b1326-128">Následující příklad odebere existující modul webové žádosti pro protokol HTTP a pak zaregistruje nový vlastní modul webové žádosti o požadavky HTTP na `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="b1326-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="b1326-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1326-129">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="b1326-130">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="b1326-130">Network Settings Schema</span></span>](index.md)
