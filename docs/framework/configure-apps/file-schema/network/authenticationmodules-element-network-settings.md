---
title: '&lt;Element authenticationModules&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 394a686fe07036d6c3ac2bc51fb3503e1ee4a9e6
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873346"
---
# <a name="ltauthenticationmodulesgt-element-network-settings"></a><span data-ttu-id="0789d-102">&lt;Element authenticationModules&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="0789d-102">&lt;authenticationModules&gt; Element (Network Settings)</span></span>
<span data-ttu-id="0789d-103">Určuje moduly používané k ověření síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="0789d-103">Specifies modules used to authenticate network requests.</span></span>  
  
 <span data-ttu-id="0789d-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="0789d-104">\<configuration></span></span>  
<span data-ttu-id="0789d-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="0789d-105">\<system.net></span></span>  
<span data-ttu-id="0789d-106">\<authenticationModules – ></span><span class="sxs-lookup"><span data-stu-id="0789d-106">\<authenticationModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0789d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0789d-107">Syntax</span></span>  
  
```xml  
<authenticationModules>   
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0789d-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0789d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0789d-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0789d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0789d-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="0789d-110">Attributes</span></span>  
 <span data-ttu-id="0789d-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="0789d-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0789d-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0789d-112">Child Elements</span></span>  
  
|<span data-ttu-id="0789d-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="0789d-113">**Element**</span></span>|<span data-ttu-id="0789d-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="0789d-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0789d-115">add</span><span class="sxs-lookup"><span data-stu-id="0789d-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="0789d-116">Přidá modul ověřování do aplikace.</span><span class="sxs-lookup"><span data-stu-id="0789d-116">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="0789d-117">Vymazat</span><span class="sxs-lookup"><span data-stu-id="0789d-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="0789d-118">Vymaže všechny moduly ověřování z aplikace.</span><span class="sxs-lookup"><span data-stu-id="0789d-118">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="0789d-119">remove</span><span class="sxs-lookup"><span data-stu-id="0789d-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="0789d-120">Odebere ověřovací modul z aplikace.</span><span class="sxs-lookup"><span data-stu-id="0789d-120">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0789d-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0789d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0789d-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="0789d-122">**Element**</span></span>|<span data-ttu-id="0789d-123">**Popis**</span><span class="sxs-lookup"><span data-stu-id="0789d-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0789d-124">System.NET</span><span class="sxs-lookup"><span data-stu-id="0789d-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="0789d-125">Obsahuje nastavení, která určují, jak rozhraní .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="0789d-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0789d-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0789d-126">Remarks</span></span>  
 <span data-ttu-id="0789d-127">`authenticationModule` Prvek určuje moduly ověřování, které provádí proces ověřování se serverem.</span><span class="sxs-lookup"><span data-stu-id="0789d-127">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="0789d-128">Ověřovací modul musí implementovat <xref:System.Net.IAuthenticationModule> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0789d-128">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0789d-129">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="0789d-129">Configuration Files</span></span>  
 <span data-ttu-id="0789d-130">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="0789d-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0789d-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="0789d-131">Example</span></span>  
 <span data-ttu-id="0789d-132">Následující příklad povolí ověřovací modul.</span><span class="sxs-lookup"><span data-stu-id="0789d-132">The following example enables an authentication module.</span></span> <span data-ttu-id="0789d-133">Měli byste nahradit hodnoty pro verzi a PublicKeyToken správné hodnoty pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="0789d-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0789d-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="0789d-134">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="0789d-135">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="0789d-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
