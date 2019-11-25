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
ms.openlocfilehash: 2113b2b81ae347b398b0f25028dc6c361aec8447
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089184"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="2d72c-102">\<odebrat element > pro authenticationModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="2d72c-102">\<remove> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="2d72c-103">Odebere ověřovací modul z aplikace.</span><span class="sxs-lookup"><span data-stu-id="2d72c-103">Removes an authentication module from the application.</span></span>  

<span data-ttu-id="2d72c-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="2d72c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2d72c-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="2d72c-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="2d72c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<authenticationModules >** ](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="2d72c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="2d72c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<odebrat >**</span><span class="sxs-lookup"><span data-stu-id="2d72c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="2d72c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d72c-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d72c-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2d72c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2d72c-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2d72c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d72c-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="2d72c-111">Attributes</span></span>  
  
|<span data-ttu-id="2d72c-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="2d72c-112">**Attribute**</span></span>|<span data-ttu-id="2d72c-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="2d72c-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="2d72c-114">**textový**</span><span class="sxs-lookup"><span data-stu-id="2d72c-114">**type**</span></span>|<span data-ttu-id="2d72c-115">Název modulu ověřování, který se má odebrat</span><span class="sxs-lookup"><span data-stu-id="2d72c-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d72c-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2d72c-116">Child Elements</span></span>  
 <span data-ttu-id="2d72c-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="2d72c-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d72c-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2d72c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2d72c-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="2d72c-119">**Element**</span></span>|<span data-ttu-id="2d72c-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="2d72c-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2d72c-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="2d72c-121">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="2d72c-122">Určuje moduly používané pro ověřování síťových požadavků.</span><span class="sxs-lookup"><span data-stu-id="2d72c-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d72c-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d72c-123">Remarks</span></span>  
 <span data-ttu-id="2d72c-124">Element `remove` odebere moduly ověřování definované dříve v konfiguračním souboru nebo na vyšší úrovni v konfigurační hierarchii.</span><span class="sxs-lookup"><span data-stu-id="2d72c-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="2d72c-125">Hodnota atributu `type` musí být platný název třídy.</span><span class="sxs-lookup"><span data-stu-id="2d72c-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2d72c-126">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="2d72c-126">Configuration Files</span></span>  
 <span data-ttu-id="2d72c-127">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="2d72c-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d72c-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d72c-128">Example</span></span>  
 <span data-ttu-id="2d72c-129">Následující příklad odebere ověřovací modul.</span><span class="sxs-lookup"><span data-stu-id="2d72c-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2d72c-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d72c-130">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="2d72c-131">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="2d72c-131">Network Settings Schema</span></span>](index.md)
