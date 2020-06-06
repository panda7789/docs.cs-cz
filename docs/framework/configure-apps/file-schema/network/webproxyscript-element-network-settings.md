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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089063"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="62220-102">\<webProxyScript> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="62220-102">\<webProxyScript> Element (Network Settings)</span></span>
<span data-ttu-id="62220-103">Konfiguruje charakteristiky skriptu používaného pro zjišťování webových proxy serverů.</span><span class="sxs-lookup"><span data-stu-id="62220-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webProxyScript>**

## <a name="syntax"></a><span data-ttu-id="62220-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62220-104">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62220-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="62220-105">Attributes and Elements</span></span>  
 <span data-ttu-id="62220-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="62220-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62220-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="62220-107">Attributes</span></span>  
  
|<span data-ttu-id="62220-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="62220-108">Attribute</span></span>|<span data-ttu-id="62220-109">Popis</span><span class="sxs-lookup"><span data-stu-id="62220-109">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="62220-110">Určuje maximální dobu, po kterou se má skript stáhnout v hodinách, minutách a sekundách.</span><span class="sxs-lookup"><span data-stu-id="62220-110">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="62220-111">Výchozí hodnota je jedna minuta.</span><span class="sxs-lookup"><span data-stu-id="62220-111">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62220-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="62220-112">Child Elements</span></span>  
 <span data-ttu-id="62220-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="62220-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62220-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="62220-114">Parent Elements</span></span>  
  
|<span data-ttu-id="62220-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="62220-115">Element</span></span>|<span data-ttu-id="62220-116">Description</span><span class="sxs-lookup"><span data-stu-id="62220-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62220-117">zdroje dat</span><span class="sxs-lookup"><span data-stu-id="62220-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="62220-118">Nakonfiguruje základní možnosti sítě pro <xref:System.Net> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="62220-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62220-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="62220-119">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="62220-120">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="62220-120">Configuration Files</span></span>  
 <span data-ttu-id="62220-121">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="62220-121">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62220-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="62220-122">See also</span></span>

- [<span data-ttu-id="62220-123">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="62220-123">Network Settings Schema</span></span>](index.md)
