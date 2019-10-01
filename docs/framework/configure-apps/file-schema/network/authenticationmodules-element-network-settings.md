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
ms.openlocfilehash: 4fe44deba951e5302518ed855589ad1b0ca75343
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699536"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="07242-102">@no__t – element > 0authenticationModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="07242-102">\<authenticationModules> Element (Network Settings)</span></span>
<span data-ttu-id="07242-103">Určuje moduly používané pro ověřování síťových požadavků.</span><span class="sxs-lookup"><span data-stu-id="07242-103">Specifies modules used to authenticate network requests.</span></span>  
  
[<span data-ttu-id="07242-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="07242-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="07242-105">&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="07242-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="07242-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<authenticationModules >**</span><span class="sxs-lookup"><span data-stu-id="07242-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<authenticationModules>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07242-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07242-107">Syntax</span></span>  
  
```xml  
<authenticationModules>   
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07242-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="07242-108">Attributes and Elements</span></span>  
 <span data-ttu-id="07242-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="07242-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07242-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="07242-110">Attributes</span></span>  
 <span data-ttu-id="07242-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="07242-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="07242-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="07242-112">Child Elements</span></span>  
  
|<span data-ttu-id="07242-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="07242-113">**Element**</span></span>|<span data-ttu-id="07242-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="07242-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="07242-115">add</span><span class="sxs-lookup"><span data-stu-id="07242-115">add</span></span>](add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="07242-116">Přidá do aplikace modul ověřování.</span><span class="sxs-lookup"><span data-stu-id="07242-116">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="07242-117">jejich</span><span class="sxs-lookup"><span data-stu-id="07242-117">clear</span></span>](clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="07242-118">Vymaže všechny moduly ověřování z aplikace.</span><span class="sxs-lookup"><span data-stu-id="07242-118">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="07242-119">remove</span><span class="sxs-lookup"><span data-stu-id="07242-119">remove</span></span>](remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="07242-120">Odebere ověřovací modul z aplikace.</span><span class="sxs-lookup"><span data-stu-id="07242-120">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="07242-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="07242-121">Parent Elements</span></span>  
  
|<span data-ttu-id="07242-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="07242-122">**Element**</span></span>|<span data-ttu-id="07242-123">**Popis**</span><span class="sxs-lookup"><span data-stu-id="07242-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="07242-124">system.net</span><span class="sxs-lookup"><span data-stu-id="07242-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="07242-125">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="07242-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07242-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="07242-126">Remarks</span></span>  
 <span data-ttu-id="07242-127">Element `authenticationModule` určuje moduly ověřování, které provádí proces ověřování se serverem.</span><span class="sxs-lookup"><span data-stu-id="07242-127">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="07242-128">Ověřovací modul musí implementovat rozhraní <xref:System.Net.IAuthenticationModule>.</span><span class="sxs-lookup"><span data-stu-id="07242-128">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="07242-129">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="07242-129">Configuration Files</span></span>  
 <span data-ttu-id="07242-130">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="07242-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="07242-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="07242-131">Example</span></span>  
 <span data-ttu-id="07242-132">Následující příklad povoluje ověřovací modul.</span><span class="sxs-lookup"><span data-stu-id="07242-132">The following example enables an authentication module.</span></span> <span data-ttu-id="07242-133">Hodnoty pro Version a PublicKeyToken byste měli nahradit správnými hodnotami pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="07242-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="07242-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="07242-134">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="07242-135">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="07242-135">Network Settings Schema</span></span>](index.md)
