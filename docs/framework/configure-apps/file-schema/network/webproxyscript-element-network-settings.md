---
title: '&lt;webproxyscript –&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6843662b73f6b7d45dd12616f5118569a2d19975
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltwebproxyscriptgt-element-network-settings"></a><span data-ttu-id="74f4d-102">&lt;webproxyscript –&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="74f4d-102">&lt;webProxyScript&gt; Element (Network Settings)</span></span>
<span data-ttu-id="74f4d-103">Nakonfiguruje charakteristiky skript používá ke zjišťování webové proxy servery.</span><span class="sxs-lookup"><span data-stu-id="74f4d-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="74f4d-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="74f4d-104">\<configuration></span></span>  
<span data-ttu-id="74f4d-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="74f4d-105">\<system.net></span></span>  
<span data-ttu-id="74f4d-106">\<Nastavení ></span><span class="sxs-lookup"><span data-stu-id="74f4d-106">\<settings></span></span>  
<span data-ttu-id="74f4d-107">\<webproxyscript – ></span><span class="sxs-lookup"><span data-stu-id="74f4d-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74f4d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74f4d-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74f4d-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="74f4d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="74f4d-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="74f4d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74f4d-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="74f4d-111">Attributes</span></span>  
  
|<span data-ttu-id="74f4d-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="74f4d-112">Attribute</span></span>|<span data-ttu-id="74f4d-113">Popis</span><span class="sxs-lookup"><span data-stu-id="74f4d-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="74f4d-114">Určuje maximální dobu se stáhnout skript v hodiny, minuty a sekundy.</span><span class="sxs-lookup"><span data-stu-id="74f4d-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="74f4d-115">Výchozí hodnota je jedna minuta.</span><span class="sxs-lookup"><span data-stu-id="74f4d-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74f4d-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="74f4d-116">Child Elements</span></span>  
 <span data-ttu-id="74f4d-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="74f4d-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="74f4d-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="74f4d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="74f4d-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="74f4d-119">Element</span></span>|<span data-ttu-id="74f4d-120">Popis</span><span class="sxs-lookup"><span data-stu-id="74f4d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74f4d-121">Nastavení</span><span class="sxs-lookup"><span data-stu-id="74f4d-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="74f4d-122">Nakonfiguruje možnosti základní sítě <xref:System.Net> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="74f4d-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74f4d-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74f4d-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="74f4d-124">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="74f4d-124">Configuration Files</span></span>  
 <span data-ttu-id="74f4d-125">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="74f4d-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74f4d-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="74f4d-126">See Also</span></span>  
 [<span data-ttu-id="74f4d-127">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="74f4d-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
