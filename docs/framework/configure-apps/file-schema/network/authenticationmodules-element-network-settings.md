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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154969"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="46261-102">\<authenticationModules> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="46261-102">\<authenticationModules> Element (Network Settings)</span></span>
<span data-ttu-id="46261-103">Určuje moduly používané pro ověřování síťových požadavků.</span><span class="sxs-lookup"><span data-stu-id="46261-103">Specifies modules used to authenticate network requests.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<authenticationModules>**

## <a name="syntax"></a><span data-ttu-id="46261-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46261-104">Syntax</span></span>  
  
```xml  
<authenticationModules>
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46261-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="46261-105">Attributes and Elements</span></span>  
 <span data-ttu-id="46261-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="46261-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46261-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="46261-107">Attributes</span></span>  
 <span data-ttu-id="46261-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="46261-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="46261-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="46261-109">Child Elements</span></span>  
  
|<span data-ttu-id="46261-110">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="46261-110">**Element**</span></span>|<span data-ttu-id="46261-111">**Popis**</span><span class="sxs-lookup"><span data-stu-id="46261-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="46261-112">add</span><span class="sxs-lookup"><span data-stu-id="46261-112">add</span></span>](add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="46261-113">Přidá do aplikace modul ověřování.</span><span class="sxs-lookup"><span data-stu-id="46261-113">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="46261-114">jejich</span><span class="sxs-lookup"><span data-stu-id="46261-114">clear</span></span>](clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="46261-115">Vymaže všechny moduly ověřování z aplikace.</span><span class="sxs-lookup"><span data-stu-id="46261-115">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="46261-116">odebrány</span><span class="sxs-lookup"><span data-stu-id="46261-116">remove</span></span>](remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="46261-117">Odebere ověřovací modul z aplikace.</span><span class="sxs-lookup"><span data-stu-id="46261-117">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="46261-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="46261-118">Parent Elements</span></span>  
  
|<span data-ttu-id="46261-119">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="46261-119">**Element**</span></span>|<span data-ttu-id="46261-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="46261-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="46261-121">system.net</span><span class="sxs-lookup"><span data-stu-id="46261-121">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="46261-122">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="46261-122">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46261-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="46261-123">Remarks</span></span>  
 <span data-ttu-id="46261-124">`authenticationModule`Element určuje moduly ověřování, které provádí proces ověřování se serverem.</span><span class="sxs-lookup"><span data-stu-id="46261-124">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="46261-125">Modul ověřování musí implementovat <xref:System.Net.IAuthenticationModule> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="46261-125">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="46261-126">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="46261-126">Configuration Files</span></span>  
 <span data-ttu-id="46261-127">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="46261-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="46261-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="46261-128">Example</span></span>  
 <span data-ttu-id="46261-129">Následující příklad povoluje ověřovací modul.</span><span class="sxs-lookup"><span data-stu-id="46261-129">The following example enables an authentication module.</span></span> <span data-ttu-id="46261-130">Hodnoty pro Version a PublicKeyToken byste měli nahradit správnými hodnotami pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="46261-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="46261-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="46261-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="46261-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="46261-132">Network Settings Schema</span></span>](index.md)
