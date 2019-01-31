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
ms.openlocfilehash: e823d6065ea23f3a47dad6853a1b9e1237a616c9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257821"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="70e07-102">\<webproxyscript – > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="70e07-102">\<webProxyScript> Element (Network Settings)</span></span>
<span data-ttu-id="70e07-103">Konfiguruje vlastnosti souboru, který používá ke zjišťování webové proxy servery.</span><span class="sxs-lookup"><span data-stu-id="70e07-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="70e07-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="70e07-104">\<configuration></span></span>  
<span data-ttu-id="70e07-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="70e07-105">\<system.net></span></span>  
<span data-ttu-id="70e07-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="70e07-106">\<settings></span></span>  
<span data-ttu-id="70e07-107">\<webProxyScript></span><span class="sxs-lookup"><span data-stu-id="70e07-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70e07-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70e07-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70e07-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="70e07-109">Attributes and Elements</span></span>  
 <span data-ttu-id="70e07-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="70e07-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70e07-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="70e07-111">Attributes</span></span>  
  
|<span data-ttu-id="70e07-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="70e07-112">Attribute</span></span>|<span data-ttu-id="70e07-113">Popis</span><span class="sxs-lookup"><span data-stu-id="70e07-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="70e07-114">Určuje maximální dobu se stáhnout skript do hodiny, minuty a sekundy.</span><span class="sxs-lookup"><span data-stu-id="70e07-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="70e07-115">Výchozí hodnota je jedna minuta.</span><span class="sxs-lookup"><span data-stu-id="70e07-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70e07-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="70e07-116">Child Elements</span></span>  
 <span data-ttu-id="70e07-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="70e07-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="70e07-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="70e07-118">Parent Elements</span></span>  
  
|<span data-ttu-id="70e07-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="70e07-119">Element</span></span>|<span data-ttu-id="70e07-120">Popis</span><span class="sxs-lookup"><span data-stu-id="70e07-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70e07-121">settings</span><span class="sxs-lookup"><span data-stu-id="70e07-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="70e07-122">Nakonfiguruje možnosti základní sítě pro <xref:System.Net> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="70e07-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70e07-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70e07-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="70e07-124">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="70e07-124">Configuration Files</span></span>  
 <span data-ttu-id="70e07-125">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="70e07-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70e07-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70e07-126">See also</span></span>
- [<span data-ttu-id="70e07-127">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="70e07-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
