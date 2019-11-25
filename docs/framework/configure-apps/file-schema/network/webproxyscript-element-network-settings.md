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
ms.openlocfilehash: dbad888cd0537f63c09840ac1053f924db9ea9bc
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089063"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="5e01e-102">\<element > webProxyScript (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="5e01e-102">\<webProxyScript> Element (Network Settings)</span></span>
<span data-ttu-id="5e01e-103">Konfiguruje charakteristiky skriptu používaného pro zjišťování webových proxy serverů.</span><span class="sxs-lookup"><span data-stu-id="5e01e-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  

<span data-ttu-id="5e01e-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="5e01e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5e01e-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5e01e-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="5e01e-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<nastavení >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5e01e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>\
<span data-ttu-id="5e01e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webProxyScript >**</span><span class="sxs-lookup"><span data-stu-id="5e01e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webProxyScript>**</span></span>

## <a name="syntax"></a><span data-ttu-id="5e01e-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e01e-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e01e-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5e01e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5e01e-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5e01e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e01e-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="5e01e-111">Attributes</span></span>  
  
|<span data-ttu-id="5e01e-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="5e01e-112">Attribute</span></span>|<span data-ttu-id="5e01e-113">Popis</span><span class="sxs-lookup"><span data-stu-id="5e01e-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="5e01e-114">Určuje maximální dobu, po kterou se má skript stáhnout v hodinách, minutách a sekundách.</span><span class="sxs-lookup"><span data-stu-id="5e01e-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="5e01e-115">Výchozí hodnota je jedna minuta.</span><span class="sxs-lookup"><span data-stu-id="5e01e-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e01e-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5e01e-116">Child Elements</span></span>  
 <span data-ttu-id="5e01e-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="5e01e-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5e01e-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5e01e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5e01e-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="5e01e-119">Element</span></span>|<span data-ttu-id="5e01e-120">Popis</span><span class="sxs-lookup"><span data-stu-id="5e01e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e01e-121">možnost</span><span class="sxs-lookup"><span data-stu-id="5e01e-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="5e01e-122">Konfiguruje základní možnosti sítě pro obor názvů <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="5e01e-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e01e-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5e01e-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5e01e-124">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="5e01e-124">Configuration Files</span></span>  
 <span data-ttu-id="5e01e-125">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="5e01e-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e01e-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e01e-126">See also</span></span>

- [<span data-ttu-id="5e01e-127">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="5e01e-127">Network Settings Schema</span></span>](index.md)
