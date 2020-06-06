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
ms.openlocfilehash: 5832d120824df75d374fc94cb0aa4e08189cb965
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088490"
---
# <a name="clear-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="879a5-102">\<clear> – element pro webRequestModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="879a5-102">\<clear> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="879a5-103">Odebere z aplikace všechny registrované moduly webových požadavků.</span><span class="sxs-lookup"><span data-stu-id="879a5-103">Removes all registered Web request modules from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="879a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="879a5-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="879a5-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="879a5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="879a5-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="879a5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="879a5-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="879a5-107">Attributes</span></span>  
 <span data-ttu-id="879a5-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="879a5-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="879a5-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="879a5-109">Child Elements</span></span>  
 <span data-ttu-id="879a5-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="879a5-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="879a5-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="879a5-111">Parent Elements</span></span>  
  
|<span data-ttu-id="879a5-112">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="879a5-112">**Element**</span></span>|<span data-ttu-id="879a5-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="879a5-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="879a5-114">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="879a5-114">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="879a5-115">Určuje moduly, které se použijí k vyžádání informací od hostitelů v síti.</span><span class="sxs-lookup"><span data-stu-id="879a5-115">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="879a5-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="879a5-116">Remarks</span></span>  
 <span data-ttu-id="879a5-117">`clear`Element odebere všechny registrované moduly webových požadavků, které byly definovány dříve v konfiguračním souboru nebo na vyšší úrovni v konfigurační hierarchii.</span><span class="sxs-lookup"><span data-stu-id="879a5-117">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="879a5-118">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="879a5-118">Configuration Files</span></span>  
 <span data-ttu-id="879a5-119">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="879a5-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="879a5-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="879a5-120">Example</span></span>  
 <span data-ttu-id="879a5-121">Následující příklad zruší všechny moduly webových požadavků a pak zaregistruje modul webové žádosti pro protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="879a5-121">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="879a5-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="879a5-122">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="879a5-123">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="879a5-123">Network Settings Schema</span></span>](index.md)
