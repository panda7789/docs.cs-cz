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
ms.openlocfilehash: 683c4c5e3f3f62d947ce244c66cc590eabe64f17
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195785"
---
# <a name="ltwebproxyscriptgt-element-network-settings"></a><span data-ttu-id="c43cc-102">&lt;webproxyscript –&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="c43cc-102">&lt;webProxyScript&gt; Element (Network Settings)</span></span>
<span data-ttu-id="c43cc-103">Konfiguruje vlastnosti souboru, který používá ke zjišťování webové proxy servery.</span><span class="sxs-lookup"><span data-stu-id="c43cc-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="c43cc-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="c43cc-104">\<configuration></span></span>  
<span data-ttu-id="c43cc-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="c43cc-105">\<system.net></span></span>  
<span data-ttu-id="c43cc-106">\<Nastavení ></span><span class="sxs-lookup"><span data-stu-id="c43cc-106">\<settings></span></span>  
<span data-ttu-id="c43cc-107">\<webproxyscript – ></span><span class="sxs-lookup"><span data-stu-id="c43cc-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c43cc-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c43cc-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c43cc-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c43cc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c43cc-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c43cc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c43cc-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="c43cc-111">Attributes</span></span>  
  
|<span data-ttu-id="c43cc-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="c43cc-112">Attribute</span></span>|<span data-ttu-id="c43cc-113">Popis</span><span class="sxs-lookup"><span data-stu-id="c43cc-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="c43cc-114">Určuje maximální dobu se stáhnout skript do hodiny, minuty a sekundy.</span><span class="sxs-lookup"><span data-stu-id="c43cc-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="c43cc-115">Výchozí hodnota je jedna minuta.</span><span class="sxs-lookup"><span data-stu-id="c43cc-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c43cc-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c43cc-116">Child Elements</span></span>  
 <span data-ttu-id="c43cc-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="c43cc-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c43cc-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c43cc-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c43cc-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="c43cc-119">Element</span></span>|<span data-ttu-id="c43cc-120">Popis</span><span class="sxs-lookup"><span data-stu-id="c43cc-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c43cc-121">Nastavení</span><span class="sxs-lookup"><span data-stu-id="c43cc-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="c43cc-122">Nakonfiguruje možnosti základní sítě pro <xref:System.Net> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c43cc-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c43cc-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c43cc-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c43cc-124">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="c43cc-124">Configuration Files</span></span>  
 <span data-ttu-id="c43cc-125">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="c43cc-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c43cc-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="c43cc-126">See Also</span></span>  
- [<span data-ttu-id="c43cc-127">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="c43cc-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
