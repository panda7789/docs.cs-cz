---
title: "&lt;Odebrat&gt; Element pro authenticationModules – (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, authenticationModules
- <authenticationModules>, remove element
- <remove> element, authenticationModules
- authenticationModules, remove element
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 077a6f3cb7020d501978fa112a0c318efee27e27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="bd553-102">&lt;Odebrat&gt; Element pro authenticationModules – (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="bd553-102">&lt;remove&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="bd553-103">Odebere modul ověřování z aplikace.</span><span class="sxs-lookup"><span data-stu-id="bd553-103">Removes an authentication module from the application.</span></span>  
  
 <span data-ttu-id="bd553-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="bd553-104">\<configuration></span></span>  
<span data-ttu-id="bd553-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="bd553-105">\<system.net></span></span>  
<span data-ttu-id="bd553-106">\<authenticationModules – ></span><span class="sxs-lookup"><span data-stu-id="bd553-106">\<authenticationModules></span></span>  
<span data-ttu-id="bd553-107">\<Odebrat ></span><span class="sxs-lookup"><span data-stu-id="bd553-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd553-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd553-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd553-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bd553-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bd553-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bd553-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd553-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="bd553-111">Attributes</span></span>  
  
|<span data-ttu-id="bd553-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="bd553-112">**Attribute**</span></span>|<span data-ttu-id="bd553-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="bd553-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="bd553-114">**Typ**</span><span class="sxs-lookup"><span data-stu-id="bd553-114">**type**</span></span>|<span data-ttu-id="bd553-115">Název modulu ověřování odebrat.</span><span class="sxs-lookup"><span data-stu-id="bd553-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd553-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bd553-116">Child Elements</span></span>  
 <span data-ttu-id="bd553-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="bd553-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bd553-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bd553-118">Parent Elements</span></span>  
  
|<span data-ttu-id="bd553-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="bd553-119">**Element**</span></span>|<span data-ttu-id="bd553-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="bd553-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="bd553-121">authenticationModules –</span><span class="sxs-lookup"><span data-stu-id="bd553-121">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="bd553-122">Určuje moduly používané k ověřování žádostí o síti.</span><span class="sxs-lookup"><span data-stu-id="bd553-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd553-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bd553-123">Remarks</span></span>  
 <span data-ttu-id="bd553-124">`remove` Element odebere ověřovací moduly, které byly dříve definované v konfiguračním souboru nebo na vyšší úrovni v hierarchii konfigurace.</span><span class="sxs-lookup"><span data-stu-id="bd553-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="bd553-125">Hodnota `type` atribut by měl být platný název třídy.</span><span class="sxs-lookup"><span data-stu-id="bd553-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="bd553-126">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="bd553-126">Configuration Files</span></span>  
 <span data-ttu-id="bd553-127">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="bd553-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd553-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="bd553-128">Example</span></span>  
 <span data-ttu-id="bd553-129">Následující příklad odebere modul ověřování.</span><span class="sxs-lookup"><span data-stu-id="bd553-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd553-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd553-130">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="bd553-131">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="bd553-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
