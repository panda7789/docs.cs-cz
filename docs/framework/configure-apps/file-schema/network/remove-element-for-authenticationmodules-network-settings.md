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
ms.openlocfilehash: 7f923ce73760fa42a2c435d346f9d1097a5ed82f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664040"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="51edf-102">\<Remove – element > pro authenticationModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="51edf-102">\<remove> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="51edf-103">Odebere ověřovací modul z aplikace.</span><span class="sxs-lookup"><span data-stu-id="51edf-103">Removes an authentication module from the application.</span></span>  
  
 <span data-ttu-id="51edf-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="51edf-104">\<configuration></span></span>  
<span data-ttu-id="51edf-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="51edf-105">\<system.net></span></span>  
<span data-ttu-id="51edf-106">\<authenticationModules></span><span class="sxs-lookup"><span data-stu-id="51edf-106">\<authenticationModules></span></span>  
<span data-ttu-id="51edf-107">\<odebrat ></span><span class="sxs-lookup"><span data-stu-id="51edf-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51edf-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51edf-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51edf-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="51edf-109">Attributes and Elements</span></span>  
 <span data-ttu-id="51edf-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="51edf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51edf-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="51edf-111">Attributes</span></span>  
  
|<span data-ttu-id="51edf-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="51edf-112">**Attribute**</span></span>|<span data-ttu-id="51edf-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="51edf-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="51edf-114">**type**</span><span class="sxs-lookup"><span data-stu-id="51edf-114">**type**</span></span>|<span data-ttu-id="51edf-115">Název modulu ověřování, který se má odebrat</span><span class="sxs-lookup"><span data-stu-id="51edf-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="51edf-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="51edf-116">Child Elements</span></span>  
 <span data-ttu-id="51edf-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="51edf-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="51edf-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="51edf-118">Parent Elements</span></span>  
  
|<span data-ttu-id="51edf-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="51edf-119">**Element**</span></span>|<span data-ttu-id="51edf-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="51edf-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="51edf-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="51edf-121">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="51edf-122">Určuje moduly používané pro ověřování síťových požadavků.</span><span class="sxs-lookup"><span data-stu-id="51edf-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51edf-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="51edf-123">Remarks</span></span>  
 <span data-ttu-id="51edf-124">`remove` Element odebere moduly ověřování definované dříve v konfiguračním souboru nebo na vyšší úrovni v konfigurační hierarchii.</span><span class="sxs-lookup"><span data-stu-id="51edf-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="51edf-125">Hodnota `type` atributu by měla být platný název třídy.</span><span class="sxs-lookup"><span data-stu-id="51edf-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="51edf-126">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="51edf-126">Configuration Files</span></span>  
 <span data-ttu-id="51edf-127">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="51edf-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="51edf-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="51edf-128">Example</span></span>  
 <span data-ttu-id="51edf-129">Následující příklad odebere ověřovací modul.</span><span class="sxs-lookup"><span data-stu-id="51edf-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="51edf-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51edf-130">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="51edf-131">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="51edf-131">Network Settings Schema</span></span>](index.md)
