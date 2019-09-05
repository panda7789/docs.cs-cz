---
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: a54f5ce86aee1a5e831c0b10aa1471d4a82f40a5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251796"
---
# <a name="systemidentitymodel"></a><span data-ttu-id="f63c3-102">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="f63c3-102">\<system.identityModel></span></span>
<span data-ttu-id="f63c3-103">Poskytuje konfiguraci pro povolení možností Windows Identity Foundation (WIF) v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="f63c3-103">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
<span data-ttu-id="f63c3-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f63c3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f63c3-105">&nbsp;&nbsp; **\<System. identityModel >**</span><span class="sxs-lookup"><span data-stu-id="f63c3-105">&nbsp;&nbsp;**\<system.identityModel>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f63c3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f63c3-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f63c3-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f63c3-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f63c3-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f63c3-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f63c3-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="f63c3-109">Attributes</span></span>  
 <span data-ttu-id="f63c3-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="f63c3-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f63c3-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f63c3-111">Child Elements</span></span>  
  
|<span data-ttu-id="f63c3-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="f63c3-112">Element</span></span>|<span data-ttu-id="f63c3-113">Popis</span><span class="sxs-lookup"><span data-stu-id="f63c3-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f63c3-114">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="f63c3-114">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="f63c3-115">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="f63c3-115">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f63c3-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f63c3-116">Parent Elements</span></span>  
  
|<span data-ttu-id="f63c3-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="f63c3-117">Element</span></span>|<span data-ttu-id="f63c3-118">Popis</span><span class="sxs-lookup"><span data-stu-id="f63c3-118">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="f63c3-119">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f63c3-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f63c3-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f63c3-120">Remarks</span></span>  
 <span data-ttu-id="f63c3-121">`<system.identityModel>` Přidejte oddíl do konfiguračního souboru a nakonfigurujte službu nebo aplikaci, aby používala Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="f63c3-121">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="f63c3-122">Element je reprezentován <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>třídou. `<system.identityModel>`</span><span class="sxs-lookup"><span data-stu-id="f63c3-122">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f63c3-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="f63c3-123">Example</span></span>  
 <span data-ttu-id="f63c3-124">Následující příklad ukazuje, jak přidat `<system.identityModel>` oddíl do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="f63c3-124">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="f63c3-125">Nejprve je nutné přidat konfigurační oddíl a deklaraci oboru názvů pod `<configSections>` prvek.</span><span class="sxs-lookup"><span data-stu-id="f63c3-125">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="f63c3-126">Pak můžete přidat `<system.IdentityModel>` prvek do konfiguračního souboru a zadat jednu nebo více konfigurací identity.</span><span class="sxs-lookup"><span data-stu-id="f63c3-126">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
    <!--WIF 4.5 sections -->  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
  </configSections>  
  
  ...  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost/WebApplication1/" />  
      </audienceUris>  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089">  
        <trustedIssuers>  
          <add thumbprint="313D3B … 9106A9EC" name="SelfSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
      <certificateValidation certificateValidationMode="None"/>  
    </identityConfiguration>  
  </system.identityModel>  
  
  ...  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f63c3-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f63c3-127">See also</span></span>

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
