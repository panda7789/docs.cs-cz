---
title: <clear> – element pro webRequestModules (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, webRequestModules
- <webRequestModules>, clear element
- webRequestModules, clear element
- clear element, webRequestModules
ms.assetid: 48f38bcb-f30c-4b74-a8f0-1a3caf1aa96f
ms.openlocfilehash: e175c70bd4932d6a8f9428e8cd9159a47df52558
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659428"
---
# <a name="clear-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="0fbcf-102">\<Clear – element > pro webRequestModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="0fbcf-102">\<clear> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="0fbcf-103">Odebere z aplikace všechny registrované moduly webových požadavků.</span><span class="sxs-lookup"><span data-stu-id="0fbcf-103">Removes all registered Web request modules from the application.</span></span>  
  
 <span data-ttu-id="0fbcf-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="0fbcf-104">\<configuration></span></span>  
<span data-ttu-id="0fbcf-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="0fbcf-105">\<system.net></span></span>  
<span data-ttu-id="0fbcf-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="0fbcf-106">\<webRequestModules></span></span>  
<span data-ttu-id="0fbcf-107">\<Vymazat ></span><span class="sxs-lookup"><span data-stu-id="0fbcf-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fbcf-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fbcf-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fbcf-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0fbcf-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0fbcf-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0fbcf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fbcf-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="0fbcf-111">Attributes</span></span>  
 <span data-ttu-id="0fbcf-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="0fbcf-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0fbcf-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0fbcf-113">Child Elements</span></span>  
 <span data-ttu-id="0fbcf-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="0fbcf-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0fbcf-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0fbcf-115">Parent Elements</span></span>  
  
|<span data-ttu-id="0fbcf-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="0fbcf-116">**Element**</span></span>|<span data-ttu-id="0fbcf-117">**Popis**</span><span class="sxs-lookup"><span data-stu-id="0fbcf-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0fbcf-118">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="0fbcf-118">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="0fbcf-119">Určuje moduly, které se použijí k vyžádání informací od hostitelů v síti.</span><span class="sxs-lookup"><span data-stu-id="0fbcf-119">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fbcf-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0fbcf-120">Remarks</span></span>  
 <span data-ttu-id="0fbcf-121">`clear` Element odebere všechny registrované moduly webových požadavků, které byly definovány dříve v konfiguračním souboru nebo na vyšší úrovni v konfigurační hierarchii.</span><span class="sxs-lookup"><span data-stu-id="0fbcf-121">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0fbcf-122">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="0fbcf-122">Configuration Files</span></span>  
 <span data-ttu-id="0fbcf-123">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="0fbcf-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fbcf-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="0fbcf-124">Example</span></span>  
 <span data-ttu-id="0fbcf-125">Následující příklad zruší všechny moduly webových požadavků a pak zaregistruje modul webové žádosti pro protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="0fbcf-125">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <clear/>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0fbcf-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0fbcf-126">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="0fbcf-127">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="0fbcf-127">Network Settings Schema</span></span>](index.md)
