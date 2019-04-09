---
title: <add> – Element pro authenticationModules (nastavení sítě)
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
ms.openlocfilehash: a46e6af97f37974805812fb0d19801d618eee4d4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105869"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="ca67d-102">\<Přidat > – Element pro authenticationModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="ca67d-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="ca67d-103">Přidá modul ověřování do aplikace.</span><span class="sxs-lookup"><span data-stu-id="ca67d-103">Adds an authentication module to the application.</span></span>  
  
 <span data-ttu-id="ca67d-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="ca67d-104">\<configuration></span></span>  
<span data-ttu-id="ca67d-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="ca67d-105">\<system.net></span></span>  
<span data-ttu-id="ca67d-106">\<authenticationModules></span><span class="sxs-lookup"><span data-stu-id="ca67d-106">\<authenticationModules></span></span>  
<span data-ttu-id="ca67d-107">\<add></span><span class="sxs-lookup"><span data-stu-id="ca67d-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca67d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca67d-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca67d-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ca67d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ca67d-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ca67d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca67d-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="ca67d-111">Attributes</span></span>  
  
|**<span data-ttu-id="ca67d-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="ca67d-112">Attribute</span></span>**|**<span data-ttu-id="ca67d-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ca67d-113">Description</span></span>**|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="ca67d-114">Zadejte plně kvalifikovaný název (indikován <xref:System.Type.FullName%2A> vlastnost) a název sestavení (indikován <xref:System.Reflection.Assembly.FullName%2A> vlastnost), oddělená čárkou.</span><span class="sxs-lookup"><span data-stu-id="ca67d-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca67d-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ca67d-115">Child Elements</span></span>  
 <span data-ttu-id="ca67d-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="ca67d-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ca67d-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ca67d-117">Parent Elements</span></span>  
  
|**<span data-ttu-id="ca67d-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="ca67d-118">Element</span></span>**|**<span data-ttu-id="ca67d-119">Popis</span><span class="sxs-lookup"><span data-stu-id="ca67d-119">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="ca67d-120">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="ca67d-120">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="ca67d-121">Určuje moduly používané k ověření síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="ca67d-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca67d-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ca67d-122">Remarks</span></span>  
 <span data-ttu-id="ca67d-123">`add` Element přidá ověřovací modul na konec seznamu registrovaných ověřování modulů.</span><span class="sxs-lookup"><span data-stu-id="ca67d-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="ca67d-124">Ověřovací moduly jsou volány v pořadí, ve kterém byly přidány do seznamu.</span><span class="sxs-lookup"><span data-stu-id="ca67d-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="ca67d-125">Hodnota `type` atribut by měl být platný název typu a odpovídající název sestavení, oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="ca67d-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ca67d-126">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="ca67d-126">Configuration Files</span></span>  
 <span data-ttu-id="ca67d-127">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="ca67d-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca67d-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="ca67d-128">Example</span></span>  
 <span data-ttu-id="ca67d-129">Následující příklad povolí výchozí ověřování moduly.</span><span class="sxs-lookup"><span data-stu-id="ca67d-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="ca67d-130">Měli byste nahradit hodnoty pro verzi a PublicKeyToken správné hodnoty pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="ca67d-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ca67d-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca67d-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="ca67d-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="ca67d-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
