---
title: Konfigurační schéma pro Windows Identity Foundation
ms.date: 03/30/2017
ms.assetid: 4d4f6d76-49a5-4bad-b345-097b2e2844e9
author: BrucePerlerMS
---
# <a name="windows-identity-foundation-configuration-schema"></a><span data-ttu-id="83f70-102">Konfigurační schéma pro Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="83f70-102">Windows Identity Foundation Configuration Schema</span></span>
<span data-ttu-id="83f70-103">Témata v této části poskytují informace o schématu konfigurace technologie Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="83f70-103">The topics in this section provide information about the Windows Identity Foundation (WIF) configuration schema.</span></span> <span data-ttu-id="83f70-104">Můžete také nakonfigurovat aplikaci pro používání technologie WIF prostřednictvím vystavit rozhraní tříd.</span><span class="sxs-lookup"><span data-stu-id="83f70-104">You can also configure an application to use WIF through classes exposed by the framework.</span></span> <span data-ttu-id="83f70-105">Tyto třídy jsou uvedené v následujících částech zpracovat odpovídající elementy ve schématu.</span><span class="sxs-lookup"><span data-stu-id="83f70-105">These classes are noted in the sections that treat relevant elements in the schema.</span></span> <span data-ttu-id="83f70-106">Zobrazí se následující základní XML označit struktura vystavené schématu konfigurace WIF.</span><span class="sxs-lookup"><span data-stu-id="83f70-106">The following shows the basic XML tag structure exposed by the WIF configuration schema.</span></span> <span data-ttu-id="83f70-107">Atributy jsou vynechány.</span><span class="sxs-lookup"><span data-stu-id="83f70-107">Attributes are omitted.</span></span> <span data-ttu-id="83f70-108">Zvýrazněný komentáře označují hlavní komponenty schématu.</span><span class="sxs-lookup"><span data-stu-id="83f70-108">Highlighted comments indicate major components of the schema.</span></span>  
  
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
  
## <a name="in-this-section"></a><span data-ttu-id="83f70-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="83f70-109">In This Section</span></span>  
 <span data-ttu-id="83f70-110">[\<system.identityModel >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) poskytuje konfigurace pro povolení technologie WIF možnosti v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="83f70-110">[\<system.identityModel>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) Provides configuration for enabling WIF options in applications.</span></span>  
  
 <span data-ttu-id="83f70-111">[\<system.identityModel.services >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) konfigurace poskytuje pro pasivní federaci pomocí technologie WIF.</span><span class="sxs-lookup"><span data-stu-id="83f70-111">[\<system.identityModel.services>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) Provides configuration for passive federation using WIF.</span></span> <span data-ttu-id="83f70-112">Konfiguruje modul federovaného ověřování (WSFAM) a ověřovací modul relace (SAM).</span><span class="sxs-lookup"><span data-stu-id="83f70-112">Configures the Session Authentication Module (SAM) and the Federated Authentication Module (WSFAM).</span></span>
