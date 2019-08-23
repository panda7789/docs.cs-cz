---
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: 286ae88946692e6894ca3c7ee9e1348415c84ade
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943602"
---
# <a name="systemidentitymodel"></a><span data-ttu-id="afba8-102">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="afba8-102">\<system.identityModel></span></span>
<span data-ttu-id="afba8-103">Poskytuje konfiguraci pro povolení možností Windows Identity Foundation (WIF) v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="afba8-103">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
 <span data-ttu-id="afba8-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="afba8-104">\<system.identityModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afba8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afba8-105">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afba8-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="afba8-106">Attributes and Elements</span></span>  
 <span data-ttu-id="afba8-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="afba8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afba8-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="afba8-108">Attributes</span></span>  
 <span data-ttu-id="afba8-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="afba8-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="afba8-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="afba8-110">Child Elements</span></span>  
  
|<span data-ttu-id="afba8-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="afba8-111">Element</span></span>|<span data-ttu-id="afba8-112">Popis</span><span class="sxs-lookup"><span data-stu-id="afba8-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="afba8-113">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="afba8-113">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="afba8-114">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="afba8-114">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="afba8-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="afba8-115">Parent Elements</span></span>  
  
|<span data-ttu-id="afba8-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="afba8-116">Element</span></span>|<span data-ttu-id="afba8-117">Popis</span><span class="sxs-lookup"><span data-stu-id="afba8-117">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="afba8-118">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="afba8-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afba8-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="afba8-119">Remarks</span></span>  
 <span data-ttu-id="afba8-120">`<system.identityModel>` Přidejte oddíl do konfiguračního souboru a nakonfigurujte službu nebo aplikaci, aby používala Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="afba8-120">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="afba8-121">Element je reprezentován <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>třídou. `<system.identityModel>`</span><span class="sxs-lookup"><span data-stu-id="afba8-121">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afba8-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="afba8-122">Example</span></span>  
 <span data-ttu-id="afba8-123">Následující příklad ukazuje, jak přidat `<system.identityModel>` oddíl do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="afba8-123">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="afba8-124">Nejprve je nutné přidat konfigurační oddíl a deklaraci oboru názvů pod `<configSections>` prvek.</span><span class="sxs-lookup"><span data-stu-id="afba8-124">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="afba8-125">Pak můžete přidat `<system.IdentityModel>` prvek do konfiguračního souboru a zadat jednu nebo více konfigurací identity.</span><span class="sxs-lookup"><span data-stu-id="afba8-125">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="afba8-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="afba8-126">See also</span></span>

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
