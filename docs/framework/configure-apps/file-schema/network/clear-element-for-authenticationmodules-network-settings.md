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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087503"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="a0d91-102">\<clear> – element pro authenticationModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="a0d91-102">\<clear> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="a0d91-103">Vymaže všechny moduly ověřování z aplikace.</span><span class="sxs-lookup"><span data-stu-id="a0d91-103">Clears all authentication modules from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="a0d91-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0d91-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0d91-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a0d91-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a0d91-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a0d91-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0d91-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="a0d91-107">Attributes</span></span>  
 <span data-ttu-id="a0d91-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="a0d91-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a0d91-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a0d91-109">Child Elements</span></span>  
 <span data-ttu-id="a0d91-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="a0d91-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a0d91-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a0d91-111">Parent Elements</span></span>  
  
|<span data-ttu-id="a0d91-112">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="a0d91-112">**Element**</span></span>|<span data-ttu-id="a0d91-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="a0d91-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a0d91-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="a0d91-114">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="a0d91-115">Určuje moduly používané pro ověřování síťových požadavků.</span><span class="sxs-lookup"><span data-stu-id="a0d91-115">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0d91-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0d91-116">Remarks</span></span>  
 <span data-ttu-id="a0d91-117">`clear`Element odebere všechny moduly ověřování definované dříve v konfiguračním souboru nebo na vyšší úrovni v konfigurační hierarchii.</span><span class="sxs-lookup"><span data-stu-id="a0d91-117">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a0d91-118">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="a0d91-118">Configuration Files</span></span>  
 <span data-ttu-id="a0d91-119">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="a0d91-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0d91-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0d91-120">Example</span></span>  
 <span data-ttu-id="a0d91-121">Následující příklad odebere všechny nakonfigurované ověřovací moduly.</span><span class="sxs-lookup"><span data-stu-id="a0d91-121">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0d91-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0d91-122">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="a0d91-123">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="a0d91-123">Network Settings Schema</span></span>](index.md)
