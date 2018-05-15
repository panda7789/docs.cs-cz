---
title: '&lt;authenticationModules –&gt; – Element (nastavení sítě)'
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
manager: markl
ms.openlocfilehash: 6d7f811a5746fa07264a192efdc4c5c02323e1f4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltauthenticationmodulesgt-element-network-settings"></a><span data-ttu-id="021bd-102">&lt;authenticationModules –&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="021bd-102">&lt;authenticationModules&gt; Element (Network Settings)</span></span>
<span data-ttu-id="021bd-103">Určuje moduly používané k ověřování žádostí o síti.</span><span class="sxs-lookup"><span data-stu-id="021bd-103">Specifies modules used to authenticate network requests.</span></span>  
  
 <span data-ttu-id="021bd-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="021bd-104">\<configuration></span></span>  
<span data-ttu-id="021bd-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="021bd-105">\<system.net></span></span>  
<span data-ttu-id="021bd-106">\<authenticationModules – ></span><span class="sxs-lookup"><span data-stu-id="021bd-106">\<authenticationModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="021bd-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="021bd-107">Syntax</span></span>  
  
```xml  
<authenticationModules>   
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="021bd-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="021bd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="021bd-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="021bd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="021bd-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="021bd-110">Attributes</span></span>  
 <span data-ttu-id="021bd-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="021bd-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="021bd-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="021bd-112">Child Elements</span></span>  
  
|<span data-ttu-id="021bd-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="021bd-113">**Element**</span></span>|<span data-ttu-id="021bd-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="021bd-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="021bd-115">add</span><span class="sxs-lookup"><span data-stu-id="021bd-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="021bd-116">Modul ověřování přidává k aplikaci.</span><span class="sxs-lookup"><span data-stu-id="021bd-116">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="021bd-117">Zrušte zaškrtnutí</span><span class="sxs-lookup"><span data-stu-id="021bd-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="021bd-118">Vymaže všechny moduly ověřování z aplikace.</span><span class="sxs-lookup"><span data-stu-id="021bd-118">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="021bd-119">remove</span><span class="sxs-lookup"><span data-stu-id="021bd-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="021bd-120">Odebere modul ověřování z aplikace.</span><span class="sxs-lookup"><span data-stu-id="021bd-120">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="021bd-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="021bd-121">Parent Elements</span></span>  
  
|<span data-ttu-id="021bd-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="021bd-122">**Element**</span></span>|<span data-ttu-id="021bd-123">**Popis**</span><span class="sxs-lookup"><span data-stu-id="021bd-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="021bd-124">System.NET</span><span class="sxs-lookup"><span data-stu-id="021bd-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="021bd-125">Obsahuje nastavení, které určují, jak rozhraní .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="021bd-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="021bd-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="021bd-126">Remarks</span></span>  
 <span data-ttu-id="021bd-127">`authenticationModule` Element určuje ověřování moduly, které provedení procesu ověřování se serverem.</span><span class="sxs-lookup"><span data-stu-id="021bd-127">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="021bd-128">Modul ověřování musí implementovat <xref:System.Net.IAuthenticationModule> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="021bd-128">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="021bd-129">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="021bd-129">Configuration Files</span></span>  
 <span data-ttu-id="021bd-130">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="021bd-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="021bd-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="021bd-131">Example</span></span>  
 <span data-ttu-id="021bd-132">Následující příklad povolí modul ověřování.</span><span class="sxs-lookup"><span data-stu-id="021bd-132">The following example enables an authentication module.</span></span> <span data-ttu-id="021bd-133">Měli byste nahradit hodnoty verze a PublicKeyToken správné hodnoty pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="021bd-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="021bd-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="021bd-134">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="021bd-135">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="021bd-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
