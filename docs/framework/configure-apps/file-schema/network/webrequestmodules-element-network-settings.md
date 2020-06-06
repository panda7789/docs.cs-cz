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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154540"
---
# <a name="webrequestmodules-element-network-settings"></a><span data-ttu-id="ca1c6-102">\<webRequestModules> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="ca1c6-102">\<webRequestModules> Element (Network Settings)</span></span>
<span data-ttu-id="ca1c6-103">Určuje moduly, které se použijí k vyžádání informací od hostitelů v síti.</span><span class="sxs-lookup"><span data-stu-id="ca1c6-103">Specifies modules to use to request information from network hosts.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules>  
  
## <a name="syntax"></a><span data-ttu-id="ca1c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca1c6-104">Syntax</span></span>  
  
```xml  
<webRequestModules>
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca1c6-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ca1c6-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ca1c6-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ca1c6-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca1c6-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="ca1c6-107">Attributes</span></span>  
 <span data-ttu-id="ca1c6-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="ca1c6-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ca1c6-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ca1c6-109">Child Elements</span></span>  
  
|<span data-ttu-id="ca1c6-110">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="ca1c6-110">**Element**</span></span>|<span data-ttu-id="ca1c6-111">**Popis**</span><span class="sxs-lookup"><span data-stu-id="ca1c6-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ca1c6-112">add</span><span class="sxs-lookup"><span data-stu-id="ca1c6-112">add</span></span>](add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="ca1c6-113">Přidá do aplikace vlastní modul webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="ca1c6-113">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="ca1c6-114">jejich</span><span class="sxs-lookup"><span data-stu-id="ca1c6-114">clear</span></span>](clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="ca1c6-115">Odebere z aplikace všechny registrované moduly webových požadavků.</span><span class="sxs-lookup"><span data-stu-id="ca1c6-115">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="ca1c6-116">odebrány</span><span class="sxs-lookup"><span data-stu-id="ca1c6-116">remove</span></span>](remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="ca1c6-117">Odebere z aplikace vlastní modul webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="ca1c6-117">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca1c6-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ca1c6-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ca1c6-119">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="ca1c6-119">**Element**</span></span>|<span data-ttu-id="ca1c6-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="ca1c6-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ca1c6-121">system.net</span><span class="sxs-lookup"><span data-stu-id="ca1c6-121">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="ca1c6-122">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="ca1c6-122">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca1c6-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ca1c6-123">Remarks</span></span>  
 <span data-ttu-id="ca1c6-124">`webRequestModules`Element registruje následníky <xref:System.Net.WebRequest> třídy pro zpracování žádostí o informace na síťové hostitele.</span><span class="sxs-lookup"><span data-stu-id="ca1c6-124">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="ca1c6-125">Moduly webových požadavků musí implementovat <xref:System.Net.IWebRequestCreate> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ca1c6-125">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="ca1c6-126">.NET Framework obsahuje moduly webových požadavků pro identifikátory URI, které začínají `http://` na, `https://` a `file://` .</span><span class="sxs-lookup"><span data-stu-id="ca1c6-126">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="ca1c6-127">Výchozí moduly můžete přepsat pouze tím, že do konfiguračního souboru zaregistrujete vlastní modul.</span><span class="sxs-lookup"><span data-stu-id="ca1c6-127">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ca1c6-128">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="ca1c6-128">Configuration Files</span></span>  
 <span data-ttu-id="ca1c6-129">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="ca1c6-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca1c6-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="ca1c6-130">Example</span></span>  
 <span data-ttu-id="ca1c6-131">Následující příklad registruje výchozí modul HTTP.</span><span class="sxs-lookup"><span data-stu-id="ca1c6-131">The following example registers the default HTTP module.</span></span> <span data-ttu-id="ca1c6-132">Hodnoty pro Version a PublicKeyToken byste měli nahradit správnými hodnotami pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="ca1c6-132">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ca1c6-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca1c6-133">See also</span></span>

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [<span data-ttu-id="ca1c6-134">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="ca1c6-134">Network Settings Schema</span></span>](index.md)
