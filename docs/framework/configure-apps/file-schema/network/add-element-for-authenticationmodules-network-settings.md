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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155112"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="c0e5c-102">\<add> – element pro authenticationModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="c0e5c-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="c0e5c-103">Přidá do aplikace modul ověřování.</span><span class="sxs-lookup"><span data-stu-id="c0e5c-103">Adds an authentication module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="c0e5c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0e5c-104">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0e5c-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c0e5c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c0e5c-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c0e5c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0e5c-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="c0e5c-107">Attributes</span></span>  
  
|<span data-ttu-id="c0e5c-108">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="c0e5c-108">**Attribute**</span></span>|<span data-ttu-id="c0e5c-109">**Popis**</span><span class="sxs-lookup"><span data-stu-id="c0e5c-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="c0e5c-110">Plně kvalifikovaný název typu (uvedený <xref:System.Type.FullName%2A> vlastností) a název sestavení (označeno <xref:System.Reflection.Assembly.FullName%2A> vlastností), oddělené čárkou.</span><span class="sxs-lookup"><span data-stu-id="c0e5c-110">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0e5c-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c0e5c-111">Child Elements</span></span>  
 <span data-ttu-id="c0e5c-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="c0e5c-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0e5c-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c0e5c-113">Parent Elements</span></span>  
  
|<span data-ttu-id="c0e5c-114">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="c0e5c-114">**Element**</span></span>|<span data-ttu-id="c0e5c-115">**Popis**</span><span class="sxs-lookup"><span data-stu-id="c0e5c-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c0e5c-116">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="c0e5c-116">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="c0e5c-117">Určuje moduly používané pro ověřování síťových požadavků.</span><span class="sxs-lookup"><span data-stu-id="c0e5c-117">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0e5c-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c0e5c-118">Remarks</span></span>  
 <span data-ttu-id="c0e5c-119">`add`Element přidá ověřovací modul na konec seznamu registrovaných ověřovacích modulů.</span><span class="sxs-lookup"><span data-stu-id="c0e5c-119">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="c0e5c-120">Moduly ověřování jsou volány v pořadí, ve kterém byly přidány do seznamu.</span><span class="sxs-lookup"><span data-stu-id="c0e5c-120">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="c0e5c-121">Hodnota `type` atributu by měla být platný název typu a odpovídající název sestavení oddělený čárkou.</span><span class="sxs-lookup"><span data-stu-id="c0e5c-121">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c0e5c-122">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="c0e5c-122">Configuration Files</span></span>  
 <span data-ttu-id="c0e5c-123">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="c0e5c-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0e5c-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="c0e5c-124">Example</span></span>  
 <span data-ttu-id="c0e5c-125">Následující příklad povoluje výchozí moduly ověřování.</span><span class="sxs-lookup"><span data-stu-id="c0e5c-125">The following example enables the default authentication modules.</span></span> <span data-ttu-id="c0e5c-126">Hodnoty pro Version a PublicKeyToken byste měli nahradit správnými hodnotami pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="c0e5c-126">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c0e5c-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0e5c-127">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="c0e5c-128">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="c0e5c-128">Network Settings Schema</span></span>](index.md)
