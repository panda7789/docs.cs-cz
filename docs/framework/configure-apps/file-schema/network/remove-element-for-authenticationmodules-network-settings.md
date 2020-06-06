---
title: <remove> – element pro authenticationModules (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, authenticationModules
- <authenticationModules>, remove element
- <remove> element, authenticationModules
- authenticationModules, remove element
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
ms.openlocfilehash: d171fea193bbae068e69b8976abb8e56a5623f02
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154774"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="7ea4b-102">\<remove> – element pro authenticationModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="7ea4b-102">\<remove> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="7ea4b-103">Odebere ověřovací modul z aplikace.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-103">Removes an authentication module from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="7ea4b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ea4b-104">Syntax</span></span>  
  
```xml  
<remove
   type="authentication module name"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ea4b-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7ea4b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7ea4b-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ea4b-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="7ea4b-107">Attributes</span></span>  
  
|<span data-ttu-id="7ea4b-108">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="7ea4b-108">**Attribute**</span></span>|<span data-ttu-id="7ea4b-109">**Popis**</span><span class="sxs-lookup"><span data-stu-id="7ea4b-109">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="7ea4b-110">**textový**</span><span class="sxs-lookup"><span data-stu-id="7ea4b-110">**type**</span></span>|<span data-ttu-id="7ea4b-111">Název modulu ověřování, který se má odebrat</span><span class="sxs-lookup"><span data-stu-id="7ea4b-111">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7ea4b-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7ea4b-112">Child Elements</span></span>  
 <span data-ttu-id="7ea4b-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="7ea4b-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7ea4b-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7ea4b-114">Parent Elements</span></span>  
  
|<span data-ttu-id="7ea4b-115">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="7ea4b-115">**Element**</span></span>|<span data-ttu-id="7ea4b-116">**Popis**</span><span class="sxs-lookup"><span data-stu-id="7ea4b-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7ea4b-117">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="7ea4b-117">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="7ea4b-118">Určuje moduly používané pro ověřování síťových požadavků.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-118">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ea4b-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7ea4b-119">Remarks</span></span>  
 <span data-ttu-id="7ea4b-120">`remove`Element odebere moduly ověřování definované dříve v konfiguračním souboru nebo na vyšší úrovni v konfigurační hierarchii.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-120">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="7ea4b-121">Hodnota `type` atributu by měla být platný název třídy.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-121">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="7ea4b-122">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="7ea4b-122">Configuration Files</span></span>  
 <span data-ttu-id="7ea4b-123">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="7ea4b-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ea4b-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="7ea4b-124">Example</span></span>  
 <span data-ttu-id="7ea4b-125">Následující příklad odebere ověřovací modul.</span><span class="sxs-lookup"><span data-stu-id="7ea4b-125">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ea4b-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ea4b-126">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="7ea4b-127">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="7ea4b-127">Network Settings Schema</span></span>](index.md)
