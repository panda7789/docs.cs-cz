---
title: '&lt;Vymazat&gt; Element pro authenticationModules – (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, authenticationModules
- <authenticationModules>, clear element
- <clear> element, authenticationModules
- authenticationModules, clear element
ms.assetid: dc522c45-4a80-4831-8955-f7b68a47edfd
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 94e0242ca685e8b0118a55ba44fb0569c13f10f3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltcleargt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="490f1-102">&lt;Vymazat&gt; Element pro authenticationModules – (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="490f1-102">&lt;clear&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="490f1-103">Vymaže všechny moduly ověřování z aplikace.</span><span class="sxs-lookup"><span data-stu-id="490f1-103">Clears all authentication modules from the application.</span></span>  
  
 <span data-ttu-id="490f1-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="490f1-104">\<configuration></span></span>  
<span data-ttu-id="490f1-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="490f1-105">\<system.net></span></span>  
<span data-ttu-id="490f1-106">\<authenticationModules – ></span><span class="sxs-lookup"><span data-stu-id="490f1-106">\<authenticationModules></span></span>  
<span data-ttu-id="490f1-107">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="490f1-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="490f1-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="490f1-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="490f1-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="490f1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="490f1-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="490f1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="490f1-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="490f1-111">Attributes</span></span>  
 <span data-ttu-id="490f1-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="490f1-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="490f1-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="490f1-113">Child Elements</span></span>  
 <span data-ttu-id="490f1-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="490f1-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="490f1-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="490f1-115">Parent Elements</span></span>  
  
|<span data-ttu-id="490f1-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="490f1-116">**Element**</span></span>|<span data-ttu-id="490f1-117">**Popis**</span><span class="sxs-lookup"><span data-stu-id="490f1-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="490f1-118">authenticationModules –</span><span class="sxs-lookup"><span data-stu-id="490f1-118">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="490f1-119">Určuje moduly používané k ověřování žádostí o síti.</span><span class="sxs-lookup"><span data-stu-id="490f1-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="490f1-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="490f1-120">Remarks</span></span>  
 <span data-ttu-id="490f1-121">`clear` Element odebere všechny ověřovací moduly, které byly dříve definované v konfiguračním souboru nebo na vyšší úrovni v hierarchii konfigurace.</span><span class="sxs-lookup"><span data-stu-id="490f1-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="490f1-122">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="490f1-122">Configuration Files</span></span>  
 <span data-ttu-id="490f1-123">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="490f1-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="490f1-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="490f1-124">Example</span></span>  
 <span data-ttu-id="490f1-125">Následující příklad odebere všechny moduly nakonfigurované ověřování.</span><span class="sxs-lookup"><span data-stu-id="490f1-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="490f1-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="490f1-126">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="490f1-127">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="490f1-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
