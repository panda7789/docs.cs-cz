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
ms.openlocfilehash: 0eb3ef7db422d5cbbe70bd5633798b8d3787452d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125250"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="6af18-102">\<Odebrat > – Element pro authenticationModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="6af18-102">\<remove> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="6af18-103">Odebere ověřovací modul z aplikace.</span><span class="sxs-lookup"><span data-stu-id="6af18-103">Removes an authentication module from the application.</span></span>  
  
 <span data-ttu-id="6af18-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="6af18-104">\<configuration></span></span>  
<span data-ttu-id="6af18-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="6af18-105">\<system.net></span></span>  
<span data-ttu-id="6af18-106">\<authenticationModules></span><span class="sxs-lookup"><span data-stu-id="6af18-106">\<authenticationModules></span></span>  
<span data-ttu-id="6af18-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="6af18-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6af18-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6af18-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6af18-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6af18-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6af18-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6af18-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6af18-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="6af18-111">Attributes</span></span>  
  
|<span data-ttu-id="6af18-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="6af18-112">**Attribute**</span></span>|<span data-ttu-id="6af18-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="6af18-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="6af18-114">**type**</span><span class="sxs-lookup"><span data-stu-id="6af18-114">**type**</span></span>|<span data-ttu-id="6af18-115">Název modulu ověřování k odebrání.</span><span class="sxs-lookup"><span data-stu-id="6af18-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6af18-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6af18-116">Child Elements</span></span>  
 <span data-ttu-id="6af18-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="6af18-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6af18-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6af18-118">Parent Elements</span></span>  
  
|<span data-ttu-id="6af18-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="6af18-119">**Element**</span></span>|<span data-ttu-id="6af18-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="6af18-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6af18-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="6af18-121">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="6af18-122">Určuje moduly používané k ověření síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="6af18-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6af18-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6af18-123">Remarks</span></span>  
 <span data-ttu-id="6af18-124">`remove` Element odebere ověřovací moduly, které byly dříve definovány v konfiguračním souboru nebo na vyšší úrovni v hierarchii konfigurace.</span><span class="sxs-lookup"><span data-stu-id="6af18-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="6af18-125">Hodnota `type` atribut by měl být platný název třídy.</span><span class="sxs-lookup"><span data-stu-id="6af18-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6af18-126">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="6af18-126">Configuration Files</span></span>  
 <span data-ttu-id="6af18-127">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="6af18-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6af18-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="6af18-128">Example</span></span>  
 <span data-ttu-id="6af18-129">Následující příklad odebere ověřovací modul.</span><span class="sxs-lookup"><span data-stu-id="6af18-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6af18-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6af18-130">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="6af18-131">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="6af18-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
