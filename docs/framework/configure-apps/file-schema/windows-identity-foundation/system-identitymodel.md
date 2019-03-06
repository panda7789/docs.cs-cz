---
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: fd17c0318480f5e157c8c9114116735b82bbfcef
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351291"
---
# <a name="systemidentitymodel"></a><span data-ttu-id="a17a4-102">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="a17a4-102">\<system.identityModel></span></span>
<span data-ttu-id="a17a4-103">Poskytuje konfiguraci pro povolení technologie Windows Identity Foundation (WIF) možnosti v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="a17a4-103">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
 <span data-ttu-id="a17a4-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="a17a4-104">\<system.identityModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a17a4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a17a4-105">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a17a4-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a17a4-106">Attributes and Elements</span></span>  
 <span data-ttu-id="a17a4-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a17a4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a17a4-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="a17a4-108">Attributes</span></span>  
 <span data-ttu-id="a17a4-109">Žádná</span><span class="sxs-lookup"><span data-stu-id="a17a4-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a17a4-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a17a4-110">Child Elements</span></span>  
  
|<span data-ttu-id="a17a4-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="a17a4-111">Element</span></span>|<span data-ttu-id="a17a4-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a17a4-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a17a4-113">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="a17a4-113">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="a17a4-114">Určuje nastavení identit na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="a17a4-114">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a17a4-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a17a4-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a17a4-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="a17a4-116">Element</span></span>|<span data-ttu-id="a17a4-117">Popis</span><span class="sxs-lookup"><span data-stu-id="a17a4-117">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="a17a4-118">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a17a4-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a17a4-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a17a4-119">Remarks</span></span>  
 <span data-ttu-id="a17a4-120">Přidat `<system.identityModel>` části do konfiguračního souboru pro konfiguraci služby nebo aplikace pro používání technologie Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="a17a4-120">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="a17a4-121">`<system.identityModel>` Prvek je reprezentován <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> třídy.</span><span class="sxs-lookup"><span data-stu-id="a17a4-121">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a17a4-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="a17a4-122">Example</span></span>  
 <span data-ttu-id="a17a4-123">Následující příklad ukazuje, jak přidat `<system.identityModel>` části ke konfiguračnímu souboru.</span><span class="sxs-lookup"><span data-stu-id="a17a4-123">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="a17a4-124">Konfigurace části a obor názvů deklarace podle musíte nejprve přidat `<configSections>` elementu.</span><span class="sxs-lookup"><span data-stu-id="a17a4-124">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="a17a4-125">Potom můžete přidat `<system.IdentityModel>` element zadat jednu nebo několik konfigurací identit konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="a17a4-125">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a17a4-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a17a4-126">See also</span></span>
- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
