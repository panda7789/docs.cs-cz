---
title: <add> – element pro authenticationModules (nastavení sítě)
description: <add>Prvek nastavení sítě pro connectionManagement přidá IP adresu nebo název DNS do seznamu správy připojení v .NET Framework.
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
ms.openlocfilehash: 1a6d0f79f076a69cec33ac14f0e0f33f7c3c6577
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504638"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="e4f42-103">\<add> – element pro authenticationModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="e4f42-103">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="e4f42-104">Přidá do aplikace modul ověřování.</span><span class="sxs-lookup"><span data-stu-id="e4f42-104">Adds an authentication module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="e4f42-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4f42-105">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4f42-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e4f42-106">Attributes and Elements</span></span>  
 <span data-ttu-id="e4f42-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e4f42-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4f42-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="e4f42-108">Attributes</span></span>  
  
|<span data-ttu-id="e4f42-109">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="e4f42-109">**Attribute**</span></span>|<span data-ttu-id="e4f42-110">**Popis**</span><span class="sxs-lookup"><span data-stu-id="e4f42-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="e4f42-111">Plně kvalifikovaný název typu (uvedený <xref:System.Type.FullName%2A> vlastností) a název sestavení (označeno <xref:System.Reflection.Assembly.FullName%2A> vlastností), oddělené čárkou.</span><span class="sxs-lookup"><span data-stu-id="e4f42-111">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4f42-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e4f42-112">Child Elements</span></span>  
 <span data-ttu-id="e4f42-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="e4f42-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4f42-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e4f42-114">Parent Elements</span></span>  
  
|<span data-ttu-id="e4f42-115">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="e4f42-115">**Element**</span></span>|<span data-ttu-id="e4f42-116">**Popis**</span><span class="sxs-lookup"><span data-stu-id="e4f42-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e4f42-117">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="e4f42-117">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="e4f42-118">Určuje moduly používané pro ověřování síťových požadavků.</span><span class="sxs-lookup"><span data-stu-id="e4f42-118">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4f42-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e4f42-119">Remarks</span></span>  
 <span data-ttu-id="e4f42-120">`add`Element přidá ověřovací modul na konec seznamu registrovaných ověřovacích modulů.</span><span class="sxs-lookup"><span data-stu-id="e4f42-120">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="e4f42-121">Moduly ověřování jsou volány v pořadí, ve kterém byly přidány do seznamu.</span><span class="sxs-lookup"><span data-stu-id="e4f42-121">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="e4f42-122">Hodnota `type` atributu by měla být platný název typu a odpovídající název sestavení oddělený čárkou.</span><span class="sxs-lookup"><span data-stu-id="e4f42-122">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e4f42-123">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="e4f42-123">Configuration Files</span></span>  
 <span data-ttu-id="e4f42-124">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="e4f42-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4f42-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4f42-125">Example</span></span>  
 <span data-ttu-id="e4f42-126">Následující příklad povoluje výchozí moduly ověřování.</span><span class="sxs-lookup"><span data-stu-id="e4f42-126">The following example enables the default authentication modules.</span></span> <span data-ttu-id="e4f42-127">Hodnoty pro Version a PublicKeyToken byste měli nahradit správnými hodnotami pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="e4f42-127">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e4f42-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4f42-128">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="e4f42-129">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="e4f42-129">Network Settings Schema</span></span>](index.md)
