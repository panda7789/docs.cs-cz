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
ms.openlocfilehash: 20a586e945a889d1fd8a8d4c5c09c8b790c56fc3
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664020"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="413d4-102">\<Remove – element > pro webRequestModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="413d4-102">\<remove> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="413d4-103">Odebere z aplikace vlastní modul webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="413d4-103">Removes a custom Web request module from the application.</span></span>  
  
 <span data-ttu-id="413d4-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="413d4-104">\<configuration></span></span>  
<span data-ttu-id="413d4-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="413d4-105">\<system.net></span></span>  
<span data-ttu-id="413d4-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="413d4-106">\<webRequestModules></span></span>  
<span data-ttu-id="413d4-107">\<odebrat ></span><span class="sxs-lookup"><span data-stu-id="413d4-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="413d4-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="413d4-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="413d4-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="413d4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="413d4-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="413d4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="413d4-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="413d4-111">Attributes</span></span>  
  
|<span data-ttu-id="413d4-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="413d4-112">**Attribute**</span></span>|<span data-ttu-id="413d4-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="413d4-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="413d4-114">Předpona identifikátoru URI pro požadavky zpracovávané tímto modulem webového požadavku.</span><span class="sxs-lookup"><span data-stu-id="413d4-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="413d4-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="413d4-115">Child Elements</span></span>  
 <span data-ttu-id="413d4-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="413d4-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="413d4-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="413d4-117">Parent Elements</span></span>  
  
|<span data-ttu-id="413d4-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="413d4-118">**Element**</span></span>|<span data-ttu-id="413d4-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="413d4-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="413d4-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="413d4-120">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="413d4-121">Určuje moduly, které se použijí k vyžádání informací od hostitelů v síti.</span><span class="sxs-lookup"><span data-stu-id="413d4-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="413d4-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="413d4-122">Remarks</span></span>  
 <span data-ttu-id="413d4-123">`remove` Prvek odebere registrovaný modul webové žádosti pro zadanou předponu identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="413d4-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="413d4-124">Hodnota `prefix` atributu by měla být předními znaky platného identifikátoru URI – například`http`"" nebo "`http://www.contoso.com`".</span><span class="sxs-lookup"><span data-stu-id="413d4-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="413d4-125">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="413d4-125">Configuration Files</span></span>  
 <span data-ttu-id="413d4-126">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="413d4-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="413d4-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="413d4-127">Example</span></span>  

<span data-ttu-id="413d4-128">Následující příklad odebere existující modul webové žádosti pro protokol HTTP a pak zaregistruje nový vlastní modul webové žádosti pro požadavky HTTP na `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="413d4-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="413d4-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="413d4-129">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="413d4-130">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="413d4-130">Network Settings Schema</span></span>](index.md)
