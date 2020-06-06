---
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: a54f5ce86aee1a5e831c0b10aa1471d4a82f40a5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251796"
---
# \<system.identityModel>
<span data-ttu-id="d8552-102">Poskytuje konfiguraci pro povolení možností Windows Identity Foundation (WIF) v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="d8552-102">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel>**  
  
## <a name="syntax"></a><span data-ttu-id="d8552-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8552-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8552-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d8552-104">Attributes and Elements</span></span>  
 <span data-ttu-id="d8552-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d8552-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8552-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="d8552-106">Attributes</span></span>  
 <span data-ttu-id="d8552-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="d8552-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d8552-108">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d8552-108">Child Elements</span></span>  
  
|<span data-ttu-id="d8552-109">Prvek</span><span class="sxs-lookup"><span data-stu-id="d8552-109">Element</span></span>|<span data-ttu-id="d8552-110">Description</span><span class="sxs-lookup"><span data-stu-id="d8552-110">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="d8552-111">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="d8552-111">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d8552-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d8552-112">Parent Elements</span></span>  
  
|<span data-ttu-id="d8552-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="d8552-113">Element</span></span>|<span data-ttu-id="d8552-114">Description</span><span class="sxs-lookup"><span data-stu-id="d8552-114">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="d8552-115">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d8552-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8552-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d8552-116">Remarks</span></span>  
 <span data-ttu-id="d8552-117">Přidejte `<system.identityModel>` oddíl do konfiguračního souboru a nakonfigurujte službu nebo aplikaci, aby používala Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="d8552-117">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="d8552-118">`<system.identityModel>`Element je reprezentován <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> třídou.</span><span class="sxs-lookup"><span data-stu-id="d8552-118">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8552-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="d8552-119">Example</span></span>  
 <span data-ttu-id="d8552-120">Následující příklad ukazuje, jak přidat `<system.identityModel>` oddíl do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="d8552-120">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="d8552-121">Nejprve je nutné přidat konfigurační oddíl a deklaraci oboru názvů pod `<configSections>` prvek.</span><span class="sxs-lookup"><span data-stu-id="d8552-121">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="d8552-122">Pak můžete přidat `<system.IdentityModel>` prvek do konfiguračního souboru a zadat jednu nebo více konfigurací identity.</span><span class="sxs-lookup"><span data-stu-id="d8552-122">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d8552-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8552-123">See also</span></span>

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
