---
title: <clear> – element pro authenticationModules (nastavení sítě)
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
ms.openlocfilehash: e3abd1b4c76ebda885703ccf961d58657b582f19
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087503"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="6cb5f-102">\<Clear > element pro authenticationModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="6cb5f-102">\<clear> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="6cb5f-103">Vymaže všechny moduly ověřování z aplikace.</span><span class="sxs-lookup"><span data-stu-id="6cb5f-103">Clears all authentication modules from the application.</span></span>  

<span data-ttu-id="6cb5f-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="6cb5f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6cb5f-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6cb5f-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="6cb5f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<authenticationModules >** ](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6cb5f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="6cb5f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vymazat >**</span><span class="sxs-lookup"><span data-stu-id="6cb5f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6cb5f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cb5f-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6cb5f-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6cb5f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6cb5f-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6cb5f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6cb5f-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="6cb5f-111">Attributes</span></span>  
 <span data-ttu-id="6cb5f-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="6cb5f-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6cb5f-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6cb5f-113">Child Elements</span></span>  
 <span data-ttu-id="6cb5f-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="6cb5f-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6cb5f-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6cb5f-115">Parent Elements</span></span>  
  
|<span data-ttu-id="6cb5f-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="6cb5f-116">**Element**</span></span>|<span data-ttu-id="6cb5f-117">**Popis**</span><span class="sxs-lookup"><span data-stu-id="6cb5f-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6cb5f-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="6cb5f-118">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="6cb5f-119">Určuje moduly používané pro ověřování síťových požadavků.</span><span class="sxs-lookup"><span data-stu-id="6cb5f-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cb5f-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6cb5f-120">Remarks</span></span>  
 <span data-ttu-id="6cb5f-121">Element `clear` odebere všechny moduly ověřování definované dříve v konfiguračním souboru nebo na vyšší úrovni v konfigurační hierarchii.</span><span class="sxs-lookup"><span data-stu-id="6cb5f-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6cb5f-122">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="6cb5f-122">Configuration Files</span></span>  
 <span data-ttu-id="6cb5f-123">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="6cb5f-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cb5f-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="6cb5f-124">Example</span></span>  
 <span data-ttu-id="6cb5f-125">Následující příklad odebere všechny nakonfigurované ověřovací moduly.</span><span class="sxs-lookup"><span data-stu-id="6cb5f-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6cb5f-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6cb5f-126">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="6cb5f-127">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="6cb5f-127">Network Settings Schema</span></span>](index.md)
