---
title: <webProxyScript> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
ms.openlocfilehash: 8a77c2567401fd80e355bb7fcee17b6684653ebe
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659036"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="01626-102">\<webProxyScript – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="01626-102">\<webProxyScript> Element (Network Settings)</span></span>
<span data-ttu-id="01626-103">Konfiguruje charakteristiky skriptu používaného pro zjišťování webových proxy serverů.</span><span class="sxs-lookup"><span data-stu-id="01626-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="01626-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="01626-104">\<configuration></span></span>  
<span data-ttu-id="01626-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="01626-105">\<system.net></span></span>  
<span data-ttu-id="01626-106">\<Nastavení ></span><span class="sxs-lookup"><span data-stu-id="01626-106">\<settings></span></span>  
<span data-ttu-id="01626-107">\<webProxyScript></span><span class="sxs-lookup"><span data-stu-id="01626-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01626-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01626-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01626-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="01626-109">Attributes and Elements</span></span>  
 <span data-ttu-id="01626-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="01626-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01626-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="01626-111">Attributes</span></span>  
  
|<span data-ttu-id="01626-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="01626-112">Attribute</span></span>|<span data-ttu-id="01626-113">Popis</span><span class="sxs-lookup"><span data-stu-id="01626-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="01626-114">Určuje maximální dobu, po kterou se má skript stáhnout v hodinách, minutách a sekundách.</span><span class="sxs-lookup"><span data-stu-id="01626-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="01626-115">Výchozí hodnota je jedna minuta.</span><span class="sxs-lookup"><span data-stu-id="01626-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="01626-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="01626-116">Child Elements</span></span>  
 <span data-ttu-id="01626-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="01626-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="01626-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="01626-118">Parent Elements</span></span>  
  
|<span data-ttu-id="01626-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="01626-119">Element</span></span>|<span data-ttu-id="01626-120">Popis</span><span class="sxs-lookup"><span data-stu-id="01626-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01626-121">možnost</span><span class="sxs-lookup"><span data-stu-id="01626-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="01626-122">Nakonfiguruje základní možnosti sítě pro <xref:System.Net> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="01626-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01626-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01626-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="01626-124">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="01626-124">Configuration Files</span></span>  
 <span data-ttu-id="01626-125">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="01626-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01626-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01626-126">See also</span></span>

- [<span data-ttu-id="01626-127">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="01626-127">Network Settings Schema</span></span>](index.md)
