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
ms.openlocfilehash: 7f2805283f89e6165d336b3e593d34054e02115d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154540"
---
# <a name="webrequestmodules-element-network-settings"></a><span data-ttu-id="ccd05-102">\<webRequestModules> Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="ccd05-102">\<webRequestModules> Element (Network Settings)</span></span>
<span data-ttu-id="ccd05-103">Určuje moduly, které mají být používány k vyžádání informací od síťových hostitelů.</span><span class="sxs-lookup"><span data-stu-id="ccd05-103">Specifies modules to use to request information from network hosts.</span></span>  
  
[<span data-ttu-id="ccd05-104">**\<>konfigurace**</span><span class="sxs-lookup"><span data-stu-id="ccd05-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="ccd05-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="ccd05-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="ccd05-106">&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="ccd05-106">&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccd05-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccd05-107">Syntax</span></span>  
  
```xml  
<webRequestModules>
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ccd05-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ccd05-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ccd05-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ccd05-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ccd05-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="ccd05-110">Attributes</span></span>  
 <span data-ttu-id="ccd05-111">Žádné.</span><span class="sxs-lookup"><span data-stu-id="ccd05-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ccd05-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ccd05-112">Child Elements</span></span>  
  
|<span data-ttu-id="ccd05-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="ccd05-113">**Element**</span></span>|<span data-ttu-id="ccd05-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="ccd05-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ccd05-115">Přidat</span><span class="sxs-lookup"><span data-stu-id="ccd05-115">add</span></span>](add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="ccd05-116">Přidá do aplikace vlastní modul webového požadavku.</span><span class="sxs-lookup"><span data-stu-id="ccd05-116">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="ccd05-117">Jasné</span><span class="sxs-lookup"><span data-stu-id="ccd05-117">clear</span></span>](clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="ccd05-118">Odebere z aplikace všechny registrované moduly webových požadavků.</span><span class="sxs-lookup"><span data-stu-id="ccd05-118">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="ccd05-119">Odebrat</span><span class="sxs-lookup"><span data-stu-id="ccd05-119">remove</span></span>](remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="ccd05-120">Odebere z aplikace vlastní modul webového požadavku.</span><span class="sxs-lookup"><span data-stu-id="ccd05-120">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ccd05-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ccd05-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ccd05-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="ccd05-122">**Element**</span></span>|<span data-ttu-id="ccd05-123">**Popis**</span><span class="sxs-lookup"><span data-stu-id="ccd05-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ccd05-124">system.net</span><span class="sxs-lookup"><span data-stu-id="ccd05-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="ccd05-125">Obsahuje nastavení, která určují, jak se rozhraní .NET Framework připojuje k síti.</span><span class="sxs-lookup"><span data-stu-id="ccd05-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ccd05-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ccd05-126">Remarks</span></span>  
 <span data-ttu-id="ccd05-127">Prvek `webRequestModules` registruje následníky <xref:System.Net.WebRequest> třídy pro zpracování požadavků na informace pro síťové hostitele.</span><span class="sxs-lookup"><span data-stu-id="ccd05-127">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="ccd05-128">Moduly webových požadavků <xref:System.Net.IWebRequestCreate> musí implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ccd05-128">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="ccd05-129">Rozhraní .NET Framework obsahuje moduly webových `http://`požadavků `https://`pro `file://`identifikátory URI, které začínají na rozhraní , a .</span><span class="sxs-lookup"><span data-stu-id="ccd05-129">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="ccd05-130">Výchozí moduly můžete přepsat pouze registrací vlastního modulu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="ccd05-130">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ccd05-131">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="ccd05-131">Configuration Files</span></span>  
 <span data-ttu-id="ccd05-132">Tento prvek lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="ccd05-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccd05-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="ccd05-133">Example</span></span>  
 <span data-ttu-id="ccd05-134">Následující příklad registruje výchozí modul HTTP.</span><span class="sxs-lookup"><span data-stu-id="ccd05-134">The following example registers the default HTTP module.</span></span> <span data-ttu-id="ccd05-135">Hodnoty Version a PublicKeyToken byste měli nahradit správnými hodnotami pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="ccd05-135">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ccd05-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccd05-136">See also</span></span>

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [<span data-ttu-id="ccd05-137">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="ccd05-137">Network Settings Schema</span></span>](index.md)
