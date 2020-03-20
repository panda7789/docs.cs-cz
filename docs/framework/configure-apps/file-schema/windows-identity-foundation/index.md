---
title: Konfigurační schéma pro Windows Identity Foundation
ms.date: 03/30/2017
ms.assetid: 4d4f6d76-49a5-4bad-b345-097b2e2844e9
author: BrucePerlerMS
ms.openlocfilehash: 14d596ae77019932d169e1a84732fb8522bfc46c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152720"
---
# <a name="windows-identity-foundation-configuration-schema"></a><span data-ttu-id="29310-102">Konfigurační schéma pro Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="29310-102">Windows Identity Foundation Configuration Schema</span></span>

<span data-ttu-id="29310-103">Témata v této části obsahují informace o schématu konfigurace Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="29310-103">The topics in this section provide information about the Windows Identity Foundation (WIF) configuration schema.</span></span> <span data-ttu-id="29310-104">Můžete také nakonfigurovat aplikaci pro použití WIF prostřednictvím tříd vystavených rozhraní.</span><span class="sxs-lookup"><span data-stu-id="29310-104">You can also configure an application to use WIF through classes exposed by the framework.</span></span> <span data-ttu-id="29310-105">Tyto třídy jsou uvedeny v částech, které zacházejí s příslušnými prvky ve schématu.</span><span class="sxs-lookup"><span data-stu-id="29310-105">These classes are noted in the sections that treat relevant elements in the schema.</span></span> <span data-ttu-id="29310-106">Následující text ukazuje základní strukturu značek XML vystavenou schématu konfigurace Rozhraní WIF.</span><span class="sxs-lookup"><span data-stu-id="29310-106">The following shows the basic XML tag structure exposed by the WIF configuration schema.</span></span> <span data-ttu-id="29310-107">Atributy jsou vynechány.</span><span class="sxs-lookup"><span data-stu-id="29310-107">Attributes are omitted.</span></span> <span data-ttu-id="29310-108">Zvýrazněné komentáře označují hlavní součásti schématu.</span><span class="sxs-lookup"><span data-stu-id="29310-108">Highlighted comments indicate major components of the schema.</span></span>  
  
```xml  
<configuration>  
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
</configuration>  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="29310-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="29310-109">In This Section</span></span>  

<span data-ttu-id="29310-110">[ \<system.identityModel>](system-identitymodel.md) Poskytuje konfiguraci pro povolení možností WIF v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="29310-110">[\<system.identityModel>](system-identitymodel.md) Provides configuration for enabling WIF options in applications.</span></span>  
  
<span data-ttu-id="29310-111">[ \<system.identityModel.services>](system-identitymodel-services.md) Poskytuje konfiguraci pro pasivní federaci pomocí WIF.</span><span class="sxs-lookup"><span data-stu-id="29310-111">[\<system.identityModel.services>](system-identitymodel-services.md) Provides configuration for passive federation using WIF.</span></span> <span data-ttu-id="29310-112">Konfiguruje modul ověřování relací (SAM) a federovaný ověřovací modul (WSFAM).</span><span class="sxs-lookup"><span data-stu-id="29310-112">Configures the Session Authentication Module (SAM) and the Federated Authentication Module (WSFAM).</span></span>
