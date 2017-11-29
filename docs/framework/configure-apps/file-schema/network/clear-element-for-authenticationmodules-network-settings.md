---
title: "&lt;Vymazat&gt; Element pro authenticationModules – (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, authenticationModules
- <authenticationModules>, clear element
- <clear> element, authenticationModules
- authenticationModules, clear element
ms.assetid: dc522c45-4a80-4831-8955-f7b68a47edfd
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f056894148177e6b540fd45569140a996b6b888f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltcleargt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="989af-102">&lt;Vymazat&gt; Element pro authenticationModules – (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="989af-102">&lt;clear&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="989af-103">Vymaže všechny moduly ověřování z aplikace.</span><span class="sxs-lookup"><span data-stu-id="989af-103">Clears all authentication modules from the application.</span></span>  
  
 <span data-ttu-id="989af-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="989af-104">\<configuration></span></span>  
<span data-ttu-id="989af-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="989af-105">\<system.net></span></span>  
<span data-ttu-id="989af-106">\<authenticationModules – ></span><span class="sxs-lookup"><span data-stu-id="989af-106">\<authenticationModules></span></span>  
<span data-ttu-id="989af-107">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="989af-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="989af-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="989af-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="989af-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="989af-109">Attributes and Elements</span></span>  
 <span data-ttu-id="989af-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="989af-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="989af-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="989af-111">Attributes</span></span>  
 <span data-ttu-id="989af-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="989af-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="989af-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="989af-113">Child Elements</span></span>  
 <span data-ttu-id="989af-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="989af-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="989af-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="989af-115">Parent Elements</span></span>  
  
|<span data-ttu-id="989af-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="989af-116">**Element**</span></span>|<span data-ttu-id="989af-117">**Popis**</span><span class="sxs-lookup"><span data-stu-id="989af-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="989af-118">authenticationModules –</span><span class="sxs-lookup"><span data-stu-id="989af-118">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="989af-119">Určuje moduly používané k ověřování žádostí o síti.</span><span class="sxs-lookup"><span data-stu-id="989af-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="989af-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="989af-120">Remarks</span></span>  
 <span data-ttu-id="989af-121">`clear` Element odebere všechny ověřovací moduly, které byly dříve definované v konfiguračním souboru nebo na vyšší úrovni v hierarchii konfigurace.</span><span class="sxs-lookup"><span data-stu-id="989af-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="989af-122">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="989af-122">Configuration Files</span></span>  
 <span data-ttu-id="989af-123">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="989af-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="989af-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="989af-124">Example</span></span>  
 <span data-ttu-id="989af-125">Následující příklad odebere všechny moduly nakonfigurované ověřování.</span><span class="sxs-lookup"><span data-stu-id="989af-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="989af-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="989af-126">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="989af-127">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="989af-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
