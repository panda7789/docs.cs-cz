---
title: "Konfigurační schéma pro Windows Identity Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d4f6d76-49a5-4bad-b345-097b2e2844e9
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 2000ae86f38ff2fd06dbe7424cbfdd74781c6c3c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="windows-identity-foundation-configuration-schema"></a><span data-ttu-id="a8b5b-102">Konfigurační schéma pro Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="a8b5b-102">Windows Identity Foundation Configuration Schema</span></span>
<span data-ttu-id="a8b5b-103">Témata v této části poskytují informace o schématu konfigurace Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="a8b5b-103">The topics in this section provide information about the Windows Identity Foundation (WIF) configuration schema.</span></span> <span data-ttu-id="a8b5b-104">Můžete také nakonfigurovat aplikaci technologii WIF používají prostřednictvím třídy vystavené rozhraní framework.</span><span class="sxs-lookup"><span data-stu-id="a8b5b-104">You can also configure an application to use WIF through classes exposed by the framework,.</span></span> <span data-ttu-id="a8b5b-105">Tyto třídy jsou uvedené v následujících částech považovat relevantní elementy ve schématu.</span><span class="sxs-lookup"><span data-stu-id="a8b5b-105">These classes are noted in the sections that treat relevant elements in the schema.</span></span> <span data-ttu-id="a8b5b-106">Následují základní XML označit struktura vystavené WIF schématu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a8b5b-106">The following shows the basic XML tag structure exposed by the WIF configuration schema.</span></span> <span data-ttu-id="a8b5b-107">Atributy byly vynechány.</span><span class="sxs-lookup"><span data-stu-id="a8b5b-107">Attributes are omitted.</span></span> <span data-ttu-id="a8b5b-108">Zvýrazněná komentáře znamenat hlavní součásti schématu.</span><span class="sxs-lookup"><span data-stu-id="a8b5b-108">Highlighted comments indicate major components of the schema.</span></span>  
  
```xml  
<system.identityModel>  
    <!-- Service Configuration -->  
    <identityConfiguration>  
        <caches>  
            <sessionSecurityTokenCache />  
            <tokenReplayCache />  
        </caches>  
  
        <certificateValidation>  
            <certificateValidator />   
        </certificateValidation>  
  
        <claimsAuthenticationManager />  
  
        <claimsAuthorizationManager>  
            <optionalConfigurationElement>  
        </claimsAuthorizationManager>  
  
        <claimTypeRequired>  
            <claimType />   
        </claimTypeRequired>  
  
        <tokenReplayDetection />  
  
        <!-- Security Token Handler Collection Configuration -->  
        <securityTokenHandlers>  
            <add>  
                <!-- Can take an optional configuration element which can be one of  
                     the following or a custom element -->  
                <samlSecurityTokenHandlerRequirement>  
                    <nameClaimType>  
                    <roleClaimType>   
                </samlSecurityTokenHandlerRequirement>  
  
                <sessionSecurityTokenHandlerRequirement />  
                <x509SecurityTokenHandlerRequirement />  
                <userNameSecurityTokenHandlerRequirement />  
            </add>  
            <clear />  
            <remove />  
            <securityTokenHandlerConfiguration>  
                <audienceUris>  
                    <add>  
                    <clear>  
                    <remove>  
                </audienceUris>  
  
                <caches>  
                    <sessionSecurityTokenCache />  
                    <tokenReplayCache />  
                </caches>  
  
                <certificateValidation>  
                    <certificateValidator>   
                </certificateValidation>  
  
                <issuerNameRegistry>  
                    <!-- Can take an optional configuration element which can be   
                         the <trustedIssuers> element to configure a configuration-based  
                         issuer name registry or can be a custom element -->  
                    <trustedIssuers>  
                        <add>  
                        <clear>  
                        <remove>  
                    </trustedIssuers>  
                </issuerNameRegistry>  
  
                <issuerTokenResolver />  
                <serviceTokenResolver />  
                <tokenReplayDetection />  
            </securityTokenHandlerConfiguration>  
        </securityTokenHandlers>  
    </identityConfiguration>  
</system.identityModel>  
  
<system.identityModel.services>  
    <!-- Federation Authentication Configuration -->  
    <federatedAuthentication>  
        <cookieHandler>  
            <chunkedCookieHandler />  
            <customCookieHandler />  
        </cookieHandler>  
  
        <serviceCertificate>  
            <certificateReference>  
        </serviceCertificate>  
  
        <wsFederation />  
    </federatedAuthentication>  
</system.identityModel.services>  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="a8b5b-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a8b5b-109">In This Section</span></span>  
 <span data-ttu-id="a8b5b-110">[\<system.identityModel >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) možnosti konfigurace poskytuje pro povolení WIF v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="a8b5b-110">[\<system.identityModel>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) Provides configuration for enabling WIF options in applications.</span></span>  
  
 <span data-ttu-id="a8b5b-111">[\<system.identityModel.services >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) konfigurace poskytuje pro pasivní federace pomocí WIF.</span><span class="sxs-lookup"><span data-stu-id="a8b5b-111">[\<system.identityModel.services>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) Provides configuration for passive federation using WIF.</span></span> <span data-ttu-id="a8b5b-112">Nakonfiguruje modul relace ověřování (SAM) a modul federovaného ověřování (WSFAM).</span><span class="sxs-lookup"><span data-stu-id="a8b5b-112">Configures the Session Authentication Module (SAM) and the Federated Authentication Module (WSFAM).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a8b5b-113">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="a8b5b-113">Related Sections</span></span>  
 <span data-ttu-id="a8b5b-114">[Správa a konfigurace, správa,](http://msdn.microsoft.com/en-us/1e03c389-de2c-4096-aaff-86b087e1bea0) popisuje, jak konfigurovat a spravovat WIF aplikací a služeb.</span><span class="sxs-lookup"><span data-stu-id="a8b5b-114">[Configuration, Administration, And Management](http://msdn.microsoft.com/en-us/1e03c389-de2c-4096-aaff-86b087e1bea0) Describes how to configure and manage WIF applications and services.</span></span>
