---
title: '&lt;Odebrat&gt; – Element pro authenticationModules (nastavení sítě)'
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 332f8eb4fb1a5a02df76c5745522037b029a2407
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48780645"
---
# <a name="ltremovegt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="10d7f-102">&lt;Odebrat&gt; – Element pro authenticationModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="10d7f-102">&lt;remove&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="10d7f-103">Odebere ověřovací modul z aplikace.</span><span class="sxs-lookup"><span data-stu-id="10d7f-103">Removes an authentication module from the application.</span></span>  
  
 <span data-ttu-id="10d7f-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="10d7f-104">\<configuration></span></span>  
<span data-ttu-id="10d7f-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="10d7f-105">\<system.net></span></span>  
<span data-ttu-id="10d7f-106">\<authenticationModules – ></span><span class="sxs-lookup"><span data-stu-id="10d7f-106">\<authenticationModules></span></span>  
<span data-ttu-id="10d7f-107">\<Odebrat ></span><span class="sxs-lookup"><span data-stu-id="10d7f-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10d7f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10d7f-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10d7f-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="10d7f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="10d7f-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="10d7f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10d7f-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="10d7f-111">Attributes</span></span>  
  
|<span data-ttu-id="10d7f-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="10d7f-112">**Attribute**</span></span>|<span data-ttu-id="10d7f-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="10d7f-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="10d7f-114">**Typ**</span><span class="sxs-lookup"><span data-stu-id="10d7f-114">**type**</span></span>|<span data-ttu-id="10d7f-115">Název modulu ověřování k odebrání.</span><span class="sxs-lookup"><span data-stu-id="10d7f-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10d7f-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="10d7f-116">Child Elements</span></span>  
 <span data-ttu-id="10d7f-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="10d7f-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="10d7f-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="10d7f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="10d7f-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="10d7f-119">**Element**</span></span>|<span data-ttu-id="10d7f-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="10d7f-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="10d7f-121">authenticationModules –</span><span class="sxs-lookup"><span data-stu-id="10d7f-121">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="10d7f-122">Určuje moduly používané k ověření síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="10d7f-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10d7f-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="10d7f-123">Remarks</span></span>  
 <span data-ttu-id="10d7f-124">`remove` Element odebere ověřovací moduly, které byly dříve definovány v konfiguračním souboru nebo na vyšší úrovni v hierarchii konfigurace.</span><span class="sxs-lookup"><span data-stu-id="10d7f-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="10d7f-125">Hodnota `type` atribut by měl být platný název třídy.</span><span class="sxs-lookup"><span data-stu-id="10d7f-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="10d7f-126">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="10d7f-126">Configuration Files</span></span>  
 <span data-ttu-id="10d7f-127">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="10d7f-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="10d7f-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="10d7f-128">Example</span></span>  
 <span data-ttu-id="10d7f-129">Následující příklad odebere ověřovací modul.</span><span class="sxs-lookup"><span data-stu-id="10d7f-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="10d7f-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="10d7f-130">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="10d7f-131">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="10d7f-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
