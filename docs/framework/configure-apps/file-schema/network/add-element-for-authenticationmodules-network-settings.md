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
ms.openlocfilehash: 4181a045079bdb455a63ebda722dd6b0daf33c4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155112"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="d1a83-102">\<přidat prvek> pro autentizační moduly (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="d1a83-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="d1a83-103">Přidá do aplikace ověřovací modul.</span><span class="sxs-lookup"><span data-stu-id="d1a83-103">Adds an authentication module to the application.</span></span>  

<span data-ttu-id="d1a83-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d1a83-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d1a83-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="d1a83-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="d1a83-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<autentizační moduly>**](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="d1a83-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="d1a83-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<přidat>**</span><span class="sxs-lookup"><span data-stu-id="d1a83-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d1a83-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1a83-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1a83-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d1a83-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d1a83-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d1a83-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1a83-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="d1a83-111">Attributes</span></span>  
  
|<span data-ttu-id="d1a83-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="d1a83-112">**Attribute**</span></span>|<span data-ttu-id="d1a83-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="d1a83-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="d1a83-114">Plně kvalifikovaný název typu (označený <xref:System.Type.FullName%2A> vlastností) a název sestavení <xref:System.Reflection.Assembly.FullName%2A> (označený vlastností), oddělený čárkou.</span><span class="sxs-lookup"><span data-stu-id="d1a83-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1a83-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d1a83-115">Child Elements</span></span>  
 <span data-ttu-id="d1a83-116">Žádné.</span><span class="sxs-lookup"><span data-stu-id="d1a83-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1a83-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d1a83-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d1a83-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="d1a83-118">**Element**</span></span>|<span data-ttu-id="d1a83-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="d1a83-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d1a83-120">autentizační moduly</span><span class="sxs-lookup"><span data-stu-id="d1a83-120">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="d1a83-121">Určuje moduly používané k ověřování síťových požadavků.</span><span class="sxs-lookup"><span data-stu-id="d1a83-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1a83-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d1a83-122">Remarks</span></span>  
 <span data-ttu-id="d1a83-123">Prvek `add` přidá ověřovací modul na konec seznamu registrovaných ověřovacích modulů.</span><span class="sxs-lookup"><span data-stu-id="d1a83-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="d1a83-124">Ověřovací moduly jsou volány v pořadí, ve kterém byly přidány do seznamu.</span><span class="sxs-lookup"><span data-stu-id="d1a83-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="d1a83-125">Hodnota atributu `type` by měla být platný název typu a odpovídající název sestavení oddělený čárkou.</span><span class="sxs-lookup"><span data-stu-id="d1a83-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d1a83-126">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="d1a83-126">Configuration Files</span></span>  
 <span data-ttu-id="d1a83-127">Tento prvek lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="d1a83-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1a83-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="d1a83-128">Example</span></span>  
 <span data-ttu-id="d1a83-129">Následující příklad umožňuje výchozí ověřovací moduly.</span><span class="sxs-lookup"><span data-stu-id="d1a83-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="d1a83-130">Hodnoty Version a PublicKeyToken byste měli nahradit správnými hodnotami pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="d1a83-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d1a83-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1a83-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="d1a83-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="d1a83-132">Network Settings Schema</span></span>](index.md)
