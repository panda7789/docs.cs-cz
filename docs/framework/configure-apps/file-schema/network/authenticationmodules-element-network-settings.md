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
ms.openlocfilehash: b502cc4a0958f074018d4b0ce6b3fb118b811c2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154969"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="2fc0e-102">\<authenticationModuly> element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="2fc0e-102">\<authenticationModules> Element (Network Settings)</span></span>
<span data-ttu-id="2fc0e-103">Určuje moduly používané k ověřování síťových požadavků.</span><span class="sxs-lookup"><span data-stu-id="2fc0e-103">Specifies modules used to authenticate network requests.</span></span>  

<span data-ttu-id="2fc0e-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2fc0e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2fc0e-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="2fc0e-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="2fc0e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<autentizační moduly>**</span><span class="sxs-lookup"><span data-stu-id="2fc0e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<authenticationModules>**</span></span>

## <a name="syntax"></a><span data-ttu-id="2fc0e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fc0e-107">Syntax</span></span>  
  
```xml  
<authenticationModules>
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2fc0e-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2fc0e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2fc0e-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2fc0e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2fc0e-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="2fc0e-110">Attributes</span></span>  
 <span data-ttu-id="2fc0e-111">Žádné.</span><span class="sxs-lookup"><span data-stu-id="2fc0e-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2fc0e-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2fc0e-112">Child Elements</span></span>  
  
|<span data-ttu-id="2fc0e-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="2fc0e-113">**Element**</span></span>|<span data-ttu-id="2fc0e-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="2fc0e-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2fc0e-115">Přidat</span><span class="sxs-lookup"><span data-stu-id="2fc0e-115">add</span></span>](add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="2fc0e-116">Přidá do aplikace ověřovací modul.</span><span class="sxs-lookup"><span data-stu-id="2fc0e-116">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="2fc0e-117">Jasné</span><span class="sxs-lookup"><span data-stu-id="2fc0e-117">clear</span></span>](clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="2fc0e-118">Vymaže všechny ověřovací moduly z aplikace.</span><span class="sxs-lookup"><span data-stu-id="2fc0e-118">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="2fc0e-119">Odebrat</span><span class="sxs-lookup"><span data-stu-id="2fc0e-119">remove</span></span>](remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="2fc0e-120">Odebere ověřovací modul z aplikace.</span><span class="sxs-lookup"><span data-stu-id="2fc0e-120">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2fc0e-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2fc0e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2fc0e-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="2fc0e-122">**Element**</span></span>|<span data-ttu-id="2fc0e-123">**Popis**</span><span class="sxs-lookup"><span data-stu-id="2fc0e-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2fc0e-124">system.net</span><span class="sxs-lookup"><span data-stu-id="2fc0e-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="2fc0e-125">Obsahuje nastavení, která určují, jak se rozhraní .NET Framework připojuje k síti.</span><span class="sxs-lookup"><span data-stu-id="2fc0e-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2fc0e-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2fc0e-126">Remarks</span></span>  
 <span data-ttu-id="2fc0e-127">Prvek `authenticationModule` určuje ověřovací moduly, které provádějí proces ověřování se serverem.</span><span class="sxs-lookup"><span data-stu-id="2fc0e-127">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="2fc0e-128">Ověřovací modul musí <xref:System.Net.IAuthenticationModule> implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2fc0e-128">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2fc0e-129">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="2fc0e-129">Configuration Files</span></span>  
 <span data-ttu-id="2fc0e-130">Tento prvek lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="2fc0e-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fc0e-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="2fc0e-131">Example</span></span>  
 <span data-ttu-id="2fc0e-132">Následující příklad umožňuje ověřovací modul.</span><span class="sxs-lookup"><span data-stu-id="2fc0e-132">The following example enables an authentication module.</span></span> <span data-ttu-id="2fc0e-133">Hodnoty Version a PublicKeyToken byste měli nahradit správnými hodnotami pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="2fc0e-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2fc0e-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="2fc0e-134">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="2fc0e-135">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="2fc0e-135">Network Settings Schema</span></span>](index.md)
