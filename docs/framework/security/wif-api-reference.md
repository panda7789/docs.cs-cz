---
title: "Referenční dokumentace rozhraní API WIF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a027d902-9314-4bfd-b172-4e81847b1d68
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: d7ae7ef82d12c024441d01ef420bc9366e3c589d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="wif-api-reference"></a><span data-ttu-id="998fd-102">Referenční dokumentace rozhraní API WIF</span><span class="sxs-lookup"><span data-stu-id="998fd-102">WIF API Reference</span></span>
<span data-ttu-id="998fd-103">Třídy Windows Identity Foundation (WIF) jsou rozdělit do následujících sestavení: `mscorlib` (mscorlib.dll), `System.IdentityModel` (System.IdentityModel.dll), `System.IdentityModel.Services` (System.IdentityModel.Services.dll), a `System.ServiceModel` () System.ServiceModel.dll).</span><span class="sxs-lookup"><span data-stu-id="998fd-103">Windows Identity Foundation (WIF) classes are split across the following assemblies: `mscorlib` (mscorlib.dll), `System.IdentityModel` (System.IdentityModel.dll), `System.IdentityModel.Services` (System.IdentityModel.Services.dll), and `System.ServiceModel` (System.ServiceModel.dll).</span></span> <span data-ttu-id="998fd-104">Toto téma obsahuje odkazy na obory názvů WIF a stručné vysvětlení tříd, které obsahuje každý obor názvů.</span><span class="sxs-lookup"><span data-stu-id="998fd-104">This topic provides links to the WIF namespaces and brief explanations of the classes that each namespace contains.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="998fd-105">Následující `System.IdentityModel` obory názvů obsahuje třídy, které implementují modelu WCF na základě deklarace identity: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, a <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="998fd-105">The following `System.IdentityModel` namespaces contain classes that implement the WCF claims-based identity model: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, and <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>.</span></span> <span data-ttu-id="998fd-106">Od verze rozhraní .NET Framework 4.5, je WIF nahrazen modelu WCF na základě deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="998fd-106">Starting with .NET Framework 4.5, the WCF claims-based identity model is superseded by WIF.</span></span> <span data-ttu-id="998fd-107">Při sestavování řešení založená na verzi WIF byste neměli používat třídy v tyto tři obory názvů.</span><span class="sxs-lookup"><span data-stu-id="998fd-107">You should not use classes in these three namespaces when building solutions based on WIF.</span></span>  
  
 <xref:System.IdentityModel?displayProperty=nameWithType>  
 <span data-ttu-id="998fd-108">Obsahuje třídy, které představují transformace souborů cookie, služby tokenů zabezpečení a specializované slovník čtečky XML.</span><span class="sxs-lookup"><span data-stu-id="998fd-108">Contains classes that represent cookie transforms, security token services, and specialized XML dictionary readers.</span></span>  
  
 <xref:System.IdentityModel.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="998fd-109">Obsahuje třídy, které poskytují konfiguraci pro aplikace a služby vytvořená s využitím Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="998fd-109">Contains classes that provide configuration for applications and services built using the Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="998fd-110">Nastavení v části představují třídy v tomto oboru názvů [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span><span class="sxs-lookup"><span data-stu-id="998fd-110">The classes in this namespace represent settings under the [\<identityConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span>  
  
 <xref:System.IdentityModel.Metadata?displayProperty=nameWithType>  
 <span data-ttu-id="998fd-111">Obsahuje třídy, které představují prvky v dokument federačních metadat.</span><span class="sxs-lookup"><span data-stu-id="998fd-111">Contains classes that represent elements in a Federation Metadata document.</span></span>  
  
 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>  
 <span data-ttu-id="998fd-112">Obsahuje třídy, které představují WS-Trust artefakty.</span><span class="sxs-lookup"><span data-stu-id="998fd-112">Contains classes that represent WS-Trust artifacts.</span></span>  
  
 <xref:System.IdentityModel.Services?displayProperty=nameWithType>  
 <span data-ttu-id="998fd-113">Obsahuje třídy, které se používají ve scénářích pasivní (WS-Federation).</span><span class="sxs-lookup"><span data-stu-id="998fd-113">Contains classes that are used in passive (WS-Federation) scenarios.</span></span> <span data-ttu-id="998fd-114">Také obsahuje některé třídy, které představují nastavení v části [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) element.</span><span class="sxs-lookup"><span data-stu-id="998fd-114">Also contains some classes that represent settings under the [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) element.</span></span> <span data-ttu-id="998fd-115">Nastavení v části Tento element konfigurace služby WS-Federation pro aplikace.</span><span class="sxs-lookup"><span data-stu-id="998fd-115">Settings under this element configure WS-Federation for applications.</span></span> <span data-ttu-id="998fd-116">`System.IdentityModel.Services.Configuration` Obor názvů obsahuje třídy, které se používají ke konfiguraci služby WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="998fd-116">The `System.IdentityModel.Services.Configuration` namespace contains most of the classes that are used to configure WS-Federation.</span></span>  
  
 <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="998fd-117">Obsahuje třídy, které poskytují konfiguraci pro WIF aplikace, které používají protokol WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="998fd-117">Contains classes that provide configuration for WIF applications that use the WS-Federation protocol.</span></span> <span data-ttu-id="998fd-118">Nastavení v části představují třídy v tomto oboru názvů [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) element.</span><span class="sxs-lookup"><span data-stu-id="998fd-118">The classes in this namespace represent settings under the [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) element.</span></span> <span data-ttu-id="998fd-119">`System.IdentityModel.Services` Obor názvů obsahuje také některé třídy, které se používají ke konfiguraci služby WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="998fd-119">The `System.IdentityModel.Services` namespace also contains some classes that are used to configure WS-Federation.</span></span>  
  
 <xref:System.IdentityModel.Services.Tokens?displayProperty=nameWithType>  
 <span data-ttu-id="998fd-120">Obsahuje tokenů obslužné rutiny specializované zabezpečení pro webové farmy scénáře.</span><span class="sxs-lookup"><span data-stu-id="998fd-120">Contains specialized security token handlers for Web farm scenarios.</span></span>  
  
 <xref:System.IdentityModel.Tokens?displayProperty=nameWithType>  
 <span data-ttu-id="998fd-121">Obsahuje třídy, které představují tokeny zabezpečení, obslužné rutiny tokenu zabezpečení a artefaktů tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="998fd-121">Contains classes that represent security tokens, security token handlers, and other security token artifacts.</span></span>  
  
 <xref:System.Security.Claims?displayProperty=nameWithType>  
 <span data-ttu-id="998fd-122">Obsahuje třídy, které představují deklarace identity, na základě deklarace identity, na základě deklarace objektů a artefaktů modelu na základě deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="998fd-122">Contains classes that represent claims, claims-based identities, claims-based principals, and other claims-based identity model artifacts.</span></span>  
  
 <xref:System.ServiceModel.Security?displayProperty=nameWithType>  
 <span data-ttu-id="998fd-123">Obsahuje třídy, které představují WCF kontrakty, kanály, hostitelé služeb a jiných artefaktů, které se používají ve scénářích active (WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="998fd-123">Contains classes that represent WCF contracts, channels, service hosts and other artifacts that are used in active (WS-Trust) scenarios.</span></span> <span data-ttu-id="998fd-124">Tento obor názvů také obsahuje třídy, které jsou specifické pro Windows Communication Foundation (WCF) a které nejsou používána WIF.</span><span class="sxs-lookup"><span data-stu-id="998fd-124">This namespace also contains classes that are specific to Windows Communication Foundation (WCF) and that are not used by WIF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="998fd-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="998fd-125">See Also</span></span>  
 [<span data-ttu-id="998fd-126">Referenci na konfigurační WIF</span><span class="sxs-lookup"><span data-stu-id="998fd-126">WIF Configuration Reference</span></span>](../../../docs/framework/security/wif-configuration-reference.md)  
 [<span data-ttu-id="998fd-127">Namespace mapování mezi WIF 3.5 a WIF 4.5</span><span class="sxs-lookup"><span data-stu-id="998fd-127">Namespace Mapping between WIF 3.5 and WIF 4.5</span></span>](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)
