---
title: <authenticationModules> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
ms.openlocfilehash: 6488bfcd97e27a184b4a8cd1498d1c60f32babda
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659489"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="3fcc3-102">\<authenticationModules – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="3fcc3-102">\<authenticationModules> Element (Network Settings)</span></span>
<span data-ttu-id="3fcc3-103">Určuje moduly používané pro ověřování síťových požadavků.</span><span class="sxs-lookup"><span data-stu-id="3fcc3-103">Specifies modules used to authenticate network requests.</span></span>  
  
 <span data-ttu-id="3fcc3-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="3fcc3-104">\<configuration></span></span>  
<span data-ttu-id="3fcc3-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="3fcc3-105">\<system.net></span></span>  
<span data-ttu-id="3fcc3-106">\<authenticationModules></span><span class="sxs-lookup"><span data-stu-id="3fcc3-106">\<authenticationModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fcc3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fcc3-107">Syntax</span></span>  
  
```xml  
<authenticationModules>   
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3fcc3-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3fcc3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3fcc3-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3fcc3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3fcc3-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="3fcc3-110">Attributes</span></span>  
 <span data-ttu-id="3fcc3-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="3fcc3-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3fcc3-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3fcc3-112">Child Elements</span></span>  
  
|<span data-ttu-id="3fcc3-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="3fcc3-113">**Element**</span></span>|<span data-ttu-id="3fcc3-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="3fcc3-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3fcc3-115">add</span><span class="sxs-lookup"><span data-stu-id="3fcc3-115">add</span></span>](add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="3fcc3-116">Přidá do aplikace modul ověřování.</span><span class="sxs-lookup"><span data-stu-id="3fcc3-116">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="3fcc3-117">jejich</span><span class="sxs-lookup"><span data-stu-id="3fcc3-117">clear</span></span>](clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="3fcc3-118">Vymaže všechny moduly ověřování z aplikace.</span><span class="sxs-lookup"><span data-stu-id="3fcc3-118">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="3fcc3-119">remove</span><span class="sxs-lookup"><span data-stu-id="3fcc3-119">remove</span></span>](remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="3fcc3-120">Odebere ověřovací modul z aplikace.</span><span class="sxs-lookup"><span data-stu-id="3fcc3-120">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3fcc3-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3fcc3-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3fcc3-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="3fcc3-122">**Element**</span></span>|<span data-ttu-id="3fcc3-123">**Popis**</span><span class="sxs-lookup"><span data-stu-id="3fcc3-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3fcc3-124">system.net</span><span class="sxs-lookup"><span data-stu-id="3fcc3-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="3fcc3-125">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="3fcc3-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fcc3-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3fcc3-126">Remarks</span></span>  
 <span data-ttu-id="3fcc3-127">`authenticationModule` Element určuje moduly ověřování, které provádí proces ověřování se serverem.</span><span class="sxs-lookup"><span data-stu-id="3fcc3-127">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="3fcc3-128">Modul ověřování musí implementovat <xref:System.Net.IAuthenticationModule> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3fcc3-128">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3fcc3-129">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="3fcc3-129">Configuration Files</span></span>  
 <span data-ttu-id="3fcc3-130">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="3fcc3-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fcc3-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="3fcc3-131">Example</span></span>  
 <span data-ttu-id="3fcc3-132">Následující příklad povoluje ověřovací modul.</span><span class="sxs-lookup"><span data-stu-id="3fcc3-132">The following example enables an authentication module.</span></span> <span data-ttu-id="3fcc3-133">Hodnoty pro Version a PublicKeyToken byste měli nahradit správnými hodnotami pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="3fcc3-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3fcc3-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3fcc3-134">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="3fcc3-135">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="3fcc3-135">Network Settings Schema</span></span>](index.md)
