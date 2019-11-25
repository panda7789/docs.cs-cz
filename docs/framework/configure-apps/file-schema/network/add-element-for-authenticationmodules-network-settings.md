---
title: <add> – element pro authenticationModules (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/add
helpviewer_keywords:
- authenticationModules, add element
- add element, authenticationModules
- <authenticationModules>, add element
- <add> element, authenticationModules
ms.assetid: 333c5fb0-a2ab-4db8-8531-a7fe37bb9b5b
ms.openlocfilehash: 9c011cf1216b98fa20e330e185e4cf2c331b31d4
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087956"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="7782d-102">\<přidat > element pro authenticationModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="7782d-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="7782d-103">Přidá do aplikace modul ověřování.</span><span class="sxs-lookup"><span data-stu-id="7782d-103">Adds an authentication module to the application.</span></span>  

<span data-ttu-id="7782d-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="7782d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7782d-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7782d-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="7782d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<authenticationModules >** ](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7782d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="7782d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<přidat >**</span><span class="sxs-lookup"><span data-stu-id="7782d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="7782d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7782d-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7782d-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7782d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7782d-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7782d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7782d-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="7782d-111">Attributes</span></span>  
  
|<span data-ttu-id="7782d-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="7782d-112">**Attribute**</span></span>|<span data-ttu-id="7782d-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="7782d-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="7782d-114">Plně kvalifikovaný název typu (uvedený vlastností <xref:System.Type.FullName%2A>) a název sestavení (označeno vlastností <xref:System.Reflection.Assembly.FullName%2A>), které jsou odděleny čárkou.</span><span class="sxs-lookup"><span data-stu-id="7782d-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7782d-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7782d-115">Child Elements</span></span>  
 <span data-ttu-id="7782d-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="7782d-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7782d-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7782d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7782d-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="7782d-118">**Element**</span></span>|<span data-ttu-id="7782d-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="7782d-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7782d-120">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="7782d-120">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="7782d-121">Určuje moduly používané pro ověřování síťových požadavků.</span><span class="sxs-lookup"><span data-stu-id="7782d-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7782d-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7782d-122">Remarks</span></span>  
 <span data-ttu-id="7782d-123">Element `add` přidá na konec seznamu registrovaných ověřovacích modulů modul ověřování.</span><span class="sxs-lookup"><span data-stu-id="7782d-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="7782d-124">Moduly ověřování jsou volány v pořadí, ve kterém byly přidány do seznamu.</span><span class="sxs-lookup"><span data-stu-id="7782d-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="7782d-125">Hodnota atributu `type` musí být platný název typu a odpovídající název sestavení oddělený čárkou.</span><span class="sxs-lookup"><span data-stu-id="7782d-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="7782d-126">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="7782d-126">Configuration Files</span></span>  
 <span data-ttu-id="7782d-127">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="7782d-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7782d-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="7782d-128">Example</span></span>  
 <span data-ttu-id="7782d-129">Následující příklad povoluje výchozí moduly ověřování.</span><span class="sxs-lookup"><span data-stu-id="7782d-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="7782d-130">Hodnoty pro Version a PublicKeyToken byste měli nahradit správnými hodnotami pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="7782d-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
        <authenticationModules>  
            <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.NegotiateClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.KerberosClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.NtlmClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.BasicClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
        </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7782d-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7782d-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="7782d-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="7782d-132">Network Settings Schema</span></span>](index.md)
