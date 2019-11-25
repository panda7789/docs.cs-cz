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
ms.openlocfilehash: bacaaf92464a355804a9ea8307f6e6f1caac1f05
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087616"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="29b61-102">\<element > authenticationModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="29b61-102">\<authenticationModules> Element (Network Settings)</span></span>
<span data-ttu-id="29b61-103">Určuje moduly používané pro ověřování síťových požadavků.</span><span class="sxs-lookup"><span data-stu-id="29b61-103">Specifies modules used to authenticate network requests.</span></span>  

<span data-ttu-id="29b61-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="29b61-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="29b61-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="29b61-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="29b61-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<authenticationModules >**</span><span class="sxs-lookup"><span data-stu-id="29b61-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<authenticationModules>**</span></span>

## <a name="syntax"></a><span data-ttu-id="29b61-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29b61-107">Syntax</span></span>  
  
```xml  
<authenticationModules>   
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29b61-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="29b61-108">Attributes and Elements</span></span>  
 <span data-ttu-id="29b61-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="29b61-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29b61-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="29b61-110">Attributes</span></span>  
 <span data-ttu-id="29b61-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="29b61-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="29b61-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="29b61-112">Child Elements</span></span>  
  
|<span data-ttu-id="29b61-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="29b61-113">**Element**</span></span>|<span data-ttu-id="29b61-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="29b61-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="29b61-115">add</span><span class="sxs-lookup"><span data-stu-id="29b61-115">add</span></span>](add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="29b61-116">Přidá do aplikace modul ověřování.</span><span class="sxs-lookup"><span data-stu-id="29b61-116">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="29b61-117">jejich</span><span class="sxs-lookup"><span data-stu-id="29b61-117">clear</span></span>](clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="29b61-118">Vymaže všechny moduly ověřování z aplikace.</span><span class="sxs-lookup"><span data-stu-id="29b61-118">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="29b61-119">remove</span><span class="sxs-lookup"><span data-stu-id="29b61-119">remove</span></span>](remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="29b61-120">Odebere ověřovací modul z aplikace.</span><span class="sxs-lookup"><span data-stu-id="29b61-120">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="29b61-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="29b61-121">Parent Elements</span></span>  
  
|<span data-ttu-id="29b61-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="29b61-122">**Element**</span></span>|<span data-ttu-id="29b61-123">**Popis**</span><span class="sxs-lookup"><span data-stu-id="29b61-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="29b61-124">system.net</span><span class="sxs-lookup"><span data-stu-id="29b61-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="29b61-125">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="29b61-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29b61-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29b61-126">Remarks</span></span>  
 <span data-ttu-id="29b61-127">Element `authenticationModule` Určuje moduly ověřování, které provádí proces ověřování se serverem.</span><span class="sxs-lookup"><span data-stu-id="29b61-127">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="29b61-128">Ověřovací modul musí implementovat rozhraní <xref:System.Net.IAuthenticationModule>.</span><span class="sxs-lookup"><span data-stu-id="29b61-128">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="29b61-129">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="29b61-129">Configuration Files</span></span>  
 <span data-ttu-id="29b61-130">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="29b61-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="29b61-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="29b61-131">Example</span></span>  
 <span data-ttu-id="29b61-132">Následující příklad povoluje ověřovací modul.</span><span class="sxs-lookup"><span data-stu-id="29b61-132">The following example enables an authentication module.</span></span> <span data-ttu-id="29b61-133">Hodnoty pro Version a PublicKeyToken byste měli nahradit správnými hodnotami pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="29b61-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="29b61-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29b61-134">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="29b61-135">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="29b61-135">Network Settings Schema</span></span>](index.md)
