---
title: '&lt;system.identityModel&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 356dd1531f093282a1a8463b7d697400f8b45862
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltsystemidentitymodelgt"></a><span data-ttu-id="dde8c-102">&lt;system.identityModel&gt;</span><span class="sxs-lookup"><span data-stu-id="dde8c-102">&lt;system.identityModel&gt;</span></span>
<span data-ttu-id="dde8c-103">Poskytuje konfigurace pro povolení možnosti Windows Identity Foundation (WIF) v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="dde8c-103">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
 <span data-ttu-id="dde8c-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="dde8c-104">\<system.identityModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dde8c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dde8c-105">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dde8c-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dde8c-106">Attributes and Elements</span></span>  
 <span data-ttu-id="dde8c-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dde8c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dde8c-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="dde8c-108">Attributes</span></span>  
 <span data-ttu-id="dde8c-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="dde8c-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dde8c-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dde8c-110">Child Elements</span></span>  
  
|<span data-ttu-id="dde8c-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="dde8c-111">Element</span></span>|<span data-ttu-id="dde8c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="dde8c-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dde8c-113">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="dde8c-113">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="dde8c-114">Určuje nastavení identity úrovně služeb.</span><span class="sxs-lookup"><span data-stu-id="dde8c-114">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dde8c-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dde8c-115">Parent Elements</span></span>  
  
|<span data-ttu-id="dde8c-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="dde8c-116">Element</span></span>|<span data-ttu-id="dde8c-117">Popis</span><span class="sxs-lookup"><span data-stu-id="dde8c-117">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="dde8c-118">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dde8c-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dde8c-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dde8c-119">Remarks</span></span>  
 <span data-ttu-id="dde8c-120">Přidat `<system.identityModel>` oddíl konfiguračního souboru pro konfiguraci služby nebo aplikace pro používání Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="dde8c-120">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="dde8c-121">`<system.identityModel>` Element je reprezentována <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> třídy.</span><span class="sxs-lookup"><span data-stu-id="dde8c-121">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dde8c-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="dde8c-122">Example</span></span>  
 <span data-ttu-id="dde8c-123">Následující příklad ukazuje, jak přidat `<system.identityModel>` oddíl konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="dde8c-123">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="dde8c-124">Je nutné nejdříve přidat deklaraci konfigurace části a oboru názvů, v části `<configSections>` elementu.</span><span class="sxs-lookup"><span data-stu-id="dde8c-124">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="dde8c-125">Potom můžete přidat `<system.IdentityModel>` element konfigurační soubor k určení minimálně jedna konfigurace identity.</span><span class="sxs-lookup"><span data-stu-id="dde8c-125">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dde8c-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="dde8c-126">See Also</span></span>  
 <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
