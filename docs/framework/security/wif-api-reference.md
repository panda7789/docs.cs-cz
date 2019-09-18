---
title: Referenční dokumentace k rozhraní API WIF
ms.date: 03/30/2017
ms.assetid: a027d902-9314-4bfd-b172-4e81847b1d68
author: BrucePerlerMS
ms.openlocfilehash: fd7f34e619626ddca63074a89ec7253fd818ab55
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045141"
---
# <a name="wif-api-reference"></a><span data-ttu-id="27d50-102">Referenční dokumentace k rozhraní API WIF</span><span class="sxs-lookup"><span data-stu-id="27d50-102">WIF API Reference</span></span>
<span data-ttu-id="27d50-103">Třídy Windows Identity Foundation (WIF) jsou rozdělené mezi následující sestavení: `mscorlib` (mscorlib. dll), `System.IdentityModel` (System. IdentityModel. dll), `System.IdentityModel.Services` (System. IdentityModel. Services. dll) a `System.ServiceModel` ( System. ServiceModel. dll).</span><span class="sxs-lookup"><span data-stu-id="27d50-103">Windows Identity Foundation (WIF) classes are split across the following assemblies: `mscorlib` (mscorlib.dll), `System.IdentityModel` (System.IdentityModel.dll), `System.IdentityModel.Services` (System.IdentityModel.Services.dll), and `System.ServiceModel` (System.ServiceModel.dll).</span></span> <span data-ttu-id="27d50-104">Toto téma obsahuje odkazy na obory názvů WIF a stručné vysvětlení tříd, které obsahují jednotlivé obory názvů.</span><span class="sxs-lookup"><span data-stu-id="27d50-104">This topic provides links to the WIF namespaces and brief explanations of the classes that each namespace contains.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="27d50-105">Následující `System.IdentityModel` obory názvů obsahují třídy, které implementují model identity založené na deklaracích <xref:System.IdentityModel.Policy?displayProperty=nameWithType>identity WCF <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, a.</span><span class="sxs-lookup"><span data-stu-id="27d50-105">The following `System.IdentityModel` namespaces contain classes that implement the WCF claims-based identity model: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, and <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>.</span></span> <span data-ttu-id="27d50-106">Počínaje .NET Framework 4,5 se model identity založený na deklaracích identity WCF nahrazuje WIF.</span><span class="sxs-lookup"><span data-stu-id="27d50-106">Starting with .NET Framework 4.5, the WCF claims-based identity model is superseded by WIF.</span></span> <span data-ttu-id="27d50-107">Při sestavování řešení založených na WIF byste neměli v těchto třech oborech názvů používat třídy.</span><span class="sxs-lookup"><span data-stu-id="27d50-107">You should not use classes in these three namespaces when building solutions based on WIF.</span></span>  
  
 <xref:System.IdentityModel?displayProperty=nameWithType>  
 <span data-ttu-id="27d50-108">Obsahuje třídy, které reprezentují transformační soubory souborů cookie, služby tokenů zabezpečení a specializované čtečky slovníku XML.</span><span class="sxs-lookup"><span data-stu-id="27d50-108">Contains classes that represent cookie transforms, security token services, and specialized XML dictionary readers.</span></span>  
  
 <xref:System.IdentityModel.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="27d50-109">Obsahuje třídy, které poskytují konfiguraci pro aplikace a služby sestavené pomocí rozhraní Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="27d50-109">Contains classes that provide configuration for applications and services built using the Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="27d50-110">Třídy v tomto oboru názvů reprezentují nastavení v rámci [ \<elementu IdentityConfiguration >](../configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="27d50-110">The classes in this namespace represent settings under the [\<identityConfiguration>](../configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span>  
  
 <xref:System.IdentityModel.Metadata?displayProperty=nameWithType>  
 <span data-ttu-id="27d50-111">Obsahuje třídy, které reprezentují elementy v dokumentu federačních metadat.</span><span class="sxs-lookup"><span data-stu-id="27d50-111">Contains classes that represent elements in a Federation Metadata document.</span></span>  
  
 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>  
 <span data-ttu-id="27d50-112">Obsahuje třídy, které reprezentují artefakty WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="27d50-112">Contains classes that represent WS-Trust artifacts.</span></span>  
  
 <xref:System.IdentityModel.Services?displayProperty=nameWithType>  
 <span data-ttu-id="27d50-113">Obsahuje třídy, které se používají v pasivních scénářích (WS-Federation).</span><span class="sxs-lookup"><span data-stu-id="27d50-113">Contains classes that are used in passive (WS-Federation) scenarios.</span></span> <span data-ttu-id="27d50-114">Obsahuje také některé třídy, které reprezentují nastavení pod [ \<> element System. IdentityModel. Services](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) .</span><span class="sxs-lookup"><span data-stu-id="27d50-114">Also contains some classes that represent settings under the [\<system.identityModel.services>](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) element.</span></span> <span data-ttu-id="27d50-115">Nastavení pod tímto prvkem konfigurují pro aplikace WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="27d50-115">Settings under this element configure WS-Federation for applications.</span></span> <span data-ttu-id="27d50-116">`System.IdentityModel.Services.Configuration` Obor názvů obsahuje většinu tříd, které se používají ke konfiguraci WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="27d50-116">The `System.IdentityModel.Services.Configuration` namespace contains most of the classes that are used to configure WS-Federation.</span></span>  
  
 <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="27d50-117">Obsahuje třídy, které poskytují konfiguraci pro aplikace WIF používající protokol WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="27d50-117">Contains classes that provide configuration for WIF applications that use the WS-Federation protocol.</span></span> <span data-ttu-id="27d50-118">Třídy v tomto oboru názvů reprezentují nastavení v rámci [ \<prvku System. IdentityModel. Services >](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) .</span><span class="sxs-lookup"><span data-stu-id="27d50-118">The classes in this namespace represent settings under the [\<system.identityModel.services>](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) element.</span></span> <span data-ttu-id="27d50-119">`System.IdentityModel.Services` Obor názvů také obsahuje některé třídy, které se používají ke konfiguraci protokolu WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="27d50-119">The `System.IdentityModel.Services` namespace also contains some classes that are used to configure WS-Federation.</span></span>  
  
 <xref:System.IdentityModel.Services.Tokens?displayProperty=nameWithType>  
 <span data-ttu-id="27d50-120">Obsahuje obslužné rutiny specializovaného tokenu zabezpečení pro scénáře webové farmy.</span><span class="sxs-lookup"><span data-stu-id="27d50-120">Contains specialized security token handlers for Web farm scenarios.</span></span>  
  
 <xref:System.IdentityModel.Tokens?displayProperty=nameWithType>  
 <span data-ttu-id="27d50-121">Obsahuje třídy, které reprezentují tokeny zabezpečení, obslužné rutiny tokenů zabezpečení a další artefakty tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="27d50-121">Contains classes that represent security tokens, security token handlers, and other security token artifacts.</span></span>  
  
 <xref:System.Security.Claims?displayProperty=nameWithType>  
 <span data-ttu-id="27d50-122">Obsahuje třídy, které reprezentují deklarace identity, identity založené na deklaracích, objekty zabezpečení založené na deklaracích a další artefakty modelu identity založené na deklaracích.</span><span class="sxs-lookup"><span data-stu-id="27d50-122">Contains classes that represent claims, claims-based identities, claims-based principals, and other claims-based identity model artifacts.</span></span>  
  
 <xref:System.ServiceModel.Security?displayProperty=nameWithType>  
 <span data-ttu-id="27d50-123">Obsahuje třídy, které představují kontrakty WCF, kanály, hostitele služeb a jiné artefakty, které se používají ve scénářích aktivních (WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="27d50-123">Contains classes that represent WCF contracts, channels, service hosts and other artifacts that are used in active (WS-Trust) scenarios.</span></span> <span data-ttu-id="27d50-124">Tento obor názvů obsahuje také třídy, které jsou specifické pro Windows Communication Foundation (WCF) a které nepoužívá WIF.</span><span class="sxs-lookup"><span data-stu-id="27d50-124">This namespace also contains classes that are specific to Windows Communication Foundation (WCF) and that are not used by WIF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27d50-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27d50-125">See also</span></span>

- [<span data-ttu-id="27d50-126">Referenční dokumentace ke konfiguraci WIF</span><span class="sxs-lookup"><span data-stu-id="27d50-126">WIF Configuration Reference</span></span>](wif-configuration-reference.md)
- [<span data-ttu-id="27d50-127">Mapování oborů názvů mezi WIF 3.5 a WIF 4.5</span><span class="sxs-lookup"><span data-stu-id="27d50-127">Namespace Mapping between WIF 3.5 and WIF 4.5</span></span>](namespace-mapping-between-wif-3-5-and-wif-4-5.md)
