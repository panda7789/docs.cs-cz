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
ms.openlocfilehash: 2abab3de2965c31c11d9acaf7b78f3a668563506
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697454"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="f43ad-102">@no__t – element > 0webProxyScript (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="f43ad-102">\<webProxyScript> Element (Network Settings)</span></span>
<span data-ttu-id="f43ad-103">Konfiguruje charakteristiky skriptu používaného pro zjišťování webových proxy serverů.</span><span class="sxs-lookup"><span data-stu-id="f43ad-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
[<span data-ttu-id="f43ad-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="f43ad-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="f43ad-105">&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f43ad-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="f43ad-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f43ad-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>  
<span data-ttu-id="f43ad-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<webProxyScript >**</span><span class="sxs-lookup"><span data-stu-id="f43ad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webProxyScript>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f43ad-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f43ad-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f43ad-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f43ad-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f43ad-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f43ad-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f43ad-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="f43ad-111">Attributes</span></span>  
  
|<span data-ttu-id="f43ad-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="f43ad-112">Attribute</span></span>|<span data-ttu-id="f43ad-113">Popis</span><span class="sxs-lookup"><span data-stu-id="f43ad-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="f43ad-114">Určuje maximální dobu, po kterou se má skript stáhnout v hodinách, minutách a sekundách.</span><span class="sxs-lookup"><span data-stu-id="f43ad-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="f43ad-115">Výchozí hodnota je jedna minuta.</span><span class="sxs-lookup"><span data-stu-id="f43ad-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f43ad-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f43ad-116">Child Elements</span></span>  
 <span data-ttu-id="f43ad-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="f43ad-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f43ad-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f43ad-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f43ad-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="f43ad-119">Element</span></span>|<span data-ttu-id="f43ad-120">Popis</span><span class="sxs-lookup"><span data-stu-id="f43ad-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f43ad-121">možnost</span><span class="sxs-lookup"><span data-stu-id="f43ad-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="f43ad-122">Konfiguruje základní možnosti sítě pro obor názvů <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="f43ad-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f43ad-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f43ad-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f43ad-124">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="f43ad-124">Configuration Files</span></span>  
 <span data-ttu-id="f43ad-125">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="f43ad-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f43ad-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f43ad-126">See also</span></span>

- [<span data-ttu-id="f43ad-127">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="f43ad-127">Network Settings Schema</span></span>](index.md)
