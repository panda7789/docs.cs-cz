---
title: <clear> – Element pro authenticationModules (nastavení sítě)
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
ms.openlocfilehash: 3c018c7d474286f7a9cde2d070e4b54d164b5b40
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094369"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="8cb64-102">\<Vymazat > – Element pro authenticationModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="8cb64-102">\<clear> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="8cb64-103">Vymaže všechny moduly ověřování z aplikace.</span><span class="sxs-lookup"><span data-stu-id="8cb64-103">Clears all authentication modules from the application.</span></span>  
  
 <span data-ttu-id="8cb64-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="8cb64-104">\<configuration></span></span>  
<span data-ttu-id="8cb64-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="8cb64-105">\<system.net></span></span>  
<span data-ttu-id="8cb64-106">\<authenticationModules></span><span class="sxs-lookup"><span data-stu-id="8cb64-106">\<authenticationModules></span></span>  
<span data-ttu-id="8cb64-107">\<clear></span><span class="sxs-lookup"><span data-stu-id="8cb64-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cb64-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8cb64-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8cb64-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8cb64-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8cb64-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8cb64-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8cb64-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="8cb64-111">Attributes</span></span>  
 <span data-ttu-id="8cb64-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="8cb64-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8cb64-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8cb64-113">Child Elements</span></span>  
 <span data-ttu-id="8cb64-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="8cb64-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8cb64-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8cb64-115">Parent Elements</span></span>  
  
|**<span data-ttu-id="8cb64-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="8cb64-116">Element</span></span>**|**<span data-ttu-id="8cb64-117">Popis</span><span class="sxs-lookup"><span data-stu-id="8cb64-117">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="8cb64-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="8cb64-118">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="8cb64-119">Určuje moduly používané k ověření síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="8cb64-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8cb64-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8cb64-120">Remarks</span></span>  
 <span data-ttu-id="8cb64-121">`clear` Element odebere všechny moduly ověřování, které byly dříve definovány v konfiguračním souboru nebo na vyšší úrovni v hierarchii konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8cb64-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8cb64-122">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="8cb64-122">Configuration Files</span></span>  
 <span data-ttu-id="8cb64-123">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="8cb64-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8cb64-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="8cb64-124">Example</span></span>  
 <span data-ttu-id="8cb64-125">Následující příklad odebere všechny moduly nakonfigurované ověřování.</span><span class="sxs-lookup"><span data-stu-id="8cb64-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8cb64-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8cb64-126">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="8cb64-127">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="8cb64-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
