---
title: <webRequestModules> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: e119d9ce1f8bb6f07f8050612550db459a2f065c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697466"
---
# <a name="webrequestmodules-element-network-settings"></a><span data-ttu-id="b545e-102">\<element > webRequestModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="b545e-102">\<webRequestModules> Element (Network Settings)</span></span>
<span data-ttu-id="b545e-103">Určuje moduly, které se použijí k vyžádání informací od hostitelů v síti.</span><span class="sxs-lookup"><span data-stu-id="b545e-103">Specifies modules to use to request information from network hosts.</span></span>  
  
[<span data-ttu-id="b545e-104">**Konfigurace \<>** </span><span class="sxs-lookup"><span data-stu-id="b545e-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="b545e-105">&nbsp;&nbsp;[ **\<System. NET >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b545e-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="b545e-106">&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="b545e-106">&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b545e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b545e-107">Syntax</span></span>  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b545e-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b545e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b545e-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b545e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b545e-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="b545e-110">Attributes</span></span>  
 <span data-ttu-id="b545e-111">Žádné.</span><span class="sxs-lookup"><span data-stu-id="b545e-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b545e-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b545e-112">Child Elements</span></span>  
  
|<span data-ttu-id="b545e-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="b545e-113">**Element**</span></span>|<span data-ttu-id="b545e-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="b545e-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b545e-115">add</span><span class="sxs-lookup"><span data-stu-id="b545e-115">add</span></span>](add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="b545e-116">Přidá do aplikace vlastní modul webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="b545e-116">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="b545e-117">jejich</span><span class="sxs-lookup"><span data-stu-id="b545e-117">clear</span></span>](clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="b545e-118">Odebere z aplikace všechny registrované moduly webových požadavků.</span><span class="sxs-lookup"><span data-stu-id="b545e-118">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="b545e-119">remove</span><span class="sxs-lookup"><span data-stu-id="b545e-119">remove</span></span>](remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="b545e-120">Odebere z aplikace vlastní modul webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="b545e-120">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b545e-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b545e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b545e-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="b545e-122">**Element**</span></span>|<span data-ttu-id="b545e-123">**Popis**</span><span class="sxs-lookup"><span data-stu-id="b545e-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b545e-124">system.net</span><span class="sxs-lookup"><span data-stu-id="b545e-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="b545e-125">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="b545e-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b545e-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b545e-126">Remarks</span></span>  
 <span data-ttu-id="b545e-127">Element `webRequestModules` registruje následníky <xref:System.Net.WebRequest> třídy za účelem zpracování žádostí o informace na síťové hostitele.</span><span class="sxs-lookup"><span data-stu-id="b545e-127">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="b545e-128">Moduly webových požadavků musí implementovat rozhraní <xref:System.Net.IWebRequestCreate>.</span><span class="sxs-lookup"><span data-stu-id="b545e-128">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="b545e-129">.NET Framework obsahuje moduly webových požadavků pro identifikátory URI, které začínají `http://`, `https://`a `file://`.</span><span class="sxs-lookup"><span data-stu-id="b545e-129">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="b545e-130">Výchozí moduly můžete přepsat pouze tím, že do konfiguračního souboru zaregistrujete vlastní modul.</span><span class="sxs-lookup"><span data-stu-id="b545e-130">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b545e-131">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="b545e-131">Configuration Files</span></span>  
 <span data-ttu-id="b545e-132">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="b545e-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b545e-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="b545e-133">Example</span></span>  
 <span data-ttu-id="b545e-134">Následující příklad registruje výchozí modul HTTP.</span><span class="sxs-lookup"><span data-stu-id="b545e-134">The following example registers the default HTTP module.</span></span> <span data-ttu-id="b545e-135">Hodnoty pro Version a PublicKeyToken byste měli nahradit správnými hodnotami pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="b545e-135">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b545e-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b545e-136">See also</span></span>

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [<span data-ttu-id="b545e-137">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="b545e-137">Network Settings Schema</span></span>](index.md)
