---
title: <remove> – Element pro webRequestModules (nastavení sítě)
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
ms.openlocfilehash: c57e2849d608b1706c41beca91ff8026ebd9ca45
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085392"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="90d46-102">\<Odebrat > – Element pro webRequestModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="90d46-102">\<remove> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="90d46-103">Vlastní modul požadavku webového odstraní z aplikace.</span><span class="sxs-lookup"><span data-stu-id="90d46-103">Removes a custom Web request module from the application.</span></span>  
  
 <span data-ttu-id="90d46-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="90d46-104">\<configuration></span></span>  
<span data-ttu-id="90d46-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="90d46-105">\<system.net></span></span>  
<span data-ttu-id="90d46-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="90d46-106">\<webRequestModules></span></span>  
<span data-ttu-id="90d46-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="90d46-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90d46-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90d46-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90d46-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="90d46-109">Attributes and Elements</span></span>  
 <span data-ttu-id="90d46-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="90d46-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90d46-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="90d46-111">Attributes</span></span>  
  
|**<span data-ttu-id="90d46-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="90d46-112">Attribute</span></span>**|**<span data-ttu-id="90d46-113">Popis</span><span class="sxs-lookup"><span data-stu-id="90d46-113">Description</span></span>**|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="90d46-114">Předponu identifikátoru URI pro žádosti zpracovat tento modul webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="90d46-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90d46-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="90d46-115">Child Elements</span></span>  
 <span data-ttu-id="90d46-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="90d46-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="90d46-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="90d46-117">Parent Elements</span></span>  
  
|**<span data-ttu-id="90d46-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="90d46-118">Element</span></span>**|**<span data-ttu-id="90d46-119">Popis</span><span class="sxs-lookup"><span data-stu-id="90d46-119">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="90d46-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="90d46-120">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="90d46-121">Určuje moduly, které použijte k vyžádání informace z hostitelů v síti.</span><span class="sxs-lookup"><span data-stu-id="90d46-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90d46-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90d46-122">Remarks</span></span>  
 <span data-ttu-id="90d46-123">`remove` Element odebere registrovaný modul požadavku webového pro zadaný identifikátor URI předponu.</span><span class="sxs-lookup"><span data-stu-id="90d46-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="90d46-124">Hodnota `prefix` atribut by měl mít počáteční znaky platný identifikátor URI – například "`http`", nebo "`http://www.contoso.com`".</span><span class="sxs-lookup"><span data-stu-id="90d46-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="90d46-125">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="90d46-125">Configuration Files</span></span>  
 <span data-ttu-id="90d46-126">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="90d46-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="90d46-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="90d46-127">Example</span></span>  

<span data-ttu-id="90d46-128">Následující příklad odebere existující webový modul požadavku pro protokol HTTP a poté registrů nový modul vlastní webového požadavku pro protokol HTTP žádostí o `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="90d46-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="90d46-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90d46-129">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="90d46-130">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="90d46-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
