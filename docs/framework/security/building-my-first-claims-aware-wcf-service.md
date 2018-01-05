---
title: "Vytváření Můj první službu WCF používající deklarace identity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0e6d091-9a97-4888-8f2c-cbcee42d90ee
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: af39c3c5788db95eaee248ca8454534022cab659
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="building-my-first-claims-aware-wcf-service"></a><span data-ttu-id="572d0-102">Vytváření Můj první službu WCF používající deklarace identity</span><span class="sxs-lookup"><span data-stu-id="572d0-102">Building My First Claims-Aware WCF Service</span></span>
## <a name="applies-to"></a><span data-ttu-id="572d0-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="572d0-103">Applies To</span></span>  
  
-   <span data-ttu-id="572d0-104">Windows Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="572d0-104">Windows Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="572d0-105">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="572d0-105">Windows Communication Foundation (WCF)</span></span>  
  
## <a name="overview"></a><span data-ttu-id="572d0-106">Přehled</span><span class="sxs-lookup"><span data-stu-id="572d0-106">Overview</span></span>  
 <span data-ttu-id="572d0-107">Toto téma popisuje, jak pomocí technologie WIF vytvářet webové služby WCF pracující s deklaracemi.</span><span class="sxs-lookup"><span data-stu-id="572d0-107">This topic outlines the scenario of building claims-aware WCF services using WIF.</span></span> <span data-ttu-id="572d0-108">Scénář webových služeb pracujících s deklaracemi má obvykle tři účastníky, kterými jsou samotná webová služba, koncový uživatel a služba tokenů zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="572d0-108">There are usually three participants in a claims-aware web service scenario: the web service itself, the end user, and the Security Token Service (STS).</span></span> <span data-ttu-id="572d0-109">Tento scénář zachycuje následující obrázek:</span><span class="sxs-lookup"><span data-stu-id="572d0-109">The following figure describes this scenario:</span></span>  
  
 <span data-ttu-id="572d0-110">![WIF Basic deklarace identity služby využívající WCF](../../../docs/framework/security/media/wifbasicclaimsawarewcfservice.gif "WIFBasicClaimsAwareWCFService")</span><span class="sxs-lookup"><span data-stu-id="572d0-110">![WIF Basic Claims Aware WCF Service](../../../docs/framework/security/media/wifbasicclaimsawarewcfservice.gif "WIFBasicClaimsAwareWCFService")</span></span>  
  
1.  <span data-ttu-id="572d0-111">Klient služby WCF (někdy označovaný jako agent) odesílá pověření službě STS pomocí technologie WIF a po úspěšném ověření vystaví služba STS agentovi token.</span><span class="sxs-lookup"><span data-stu-id="572d0-111">The WCF service client (sometimes called agent) uses WIF to send credentials to the STS and upon successful authentication, the agent is issued a token by the STS.</span></span>  
  
2.  <span data-ttu-id="572d0-112">Tento token vystavený službou STS odešle agent službě WCF.</span><span class="sxs-lookup"><span data-stu-id="572d0-112">The agent sends this STS-issued token to the WCF service.</span></span>  
  
3.  <span data-ttu-id="572d0-113">Služba WCF pracující s deklaracemi je nakonfigurována tak, aby službu STS a jí vystavené tokeny považovala za důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="572d0-113">The claims-aware WCF service is configured to trust the STS and the tokens it issues.</span></span> <span data-ttu-id="572d0-114">Služba WCF pracující s deklaracemi token ověří a analyzuje pomocí technologie WIF.</span><span class="sxs-lookup"><span data-stu-id="572d0-114">The claims-aware WCF service uses WIF to validate the token and to parse it.</span></span> <span data-ttu-id="572d0-115">Vývojáři použít vhodné WIF API a typy, například **ClaimsPrincipal** pro potřeby aplikace, jako je například implementace autorizace pro ni.</span><span class="sxs-lookup"><span data-stu-id="572d0-115">Developers use the appropriate WIF API and types, for example, **ClaimsPrincipal** for the application’s needs, such as implementing authorization for it.</span></span>  
  
 <span data-ttu-id="572d0-116">Od rozhraní .NET 4.5, WIF je součástí balíčku rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="572d0-116">Starting from .NET 4.5, WIF is part of the .NET Framework package.</span></span> <span data-ttu-id="572d0-117">Přímo k dispozici v rámci třídy WIF mnohem hlubší integrace založené na deklaracích identity umožní v rozhraní .NET, což usnadňuje používat deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="572d0-117">Having the WIF classes directly available in the framework allows a much deeper integration of claims-based identity in .NET, making it easier to use claims.</span></span> <span data-ttu-id="572d0-118">Technologie WIF 4.5 umožňuje začít vyvíjet webové aplikace pracující s deklaracemi bez nutnosti instalovat další samostatné součásti.</span><span class="sxs-lookup"><span data-stu-id="572d0-118">With WIF 4.5, you do not need to install any out-of-band components in order to start developing claims-aware web applications.</span></span> <span data-ttu-id="572d0-119">Třídy WIF jsou nyní rozloženy mezi několik sestavení. Mezi hlavní sestavení patří System.Security.Claims, System.IdentityModel a System.IdentityModel.Services.</span><span class="sxs-lookup"><span data-stu-id="572d0-119">WIF classes are now spread across various assemblies, the main ones being System.Security.Claims, System.IdentityModel and System.IdentityModel.Services.</span></span>  
  
 <span data-ttu-id="572d0-120">STS je služba, která vystavuje tokeny po úspěšném ověření.</span><span class="sxs-lookup"><span data-stu-id="572d0-120">STS is a service that issues tokens upon successful authentication.</span></span> <span data-ttu-id="572d0-121">Společnost Microsoft nabízí dvě služby STS, které vyhovují standardům odvětví:</span><span class="sxs-lookup"><span data-stu-id="572d0-121">Microsoft offers two industry standard STS’s:</span></span>  
  
-   <span data-ttu-id="572d0-122">[Active Directory Federation Services (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) (http://go.microsoft.com/fwlink/?LinkID=247516)</span><span class="sxs-lookup"><span data-stu-id="572d0-122">[Active Directory Federation Services (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) (http://go.microsoft.com/fwlink/?LinkID=247516)</span></span>  
  
-   <span data-ttu-id="572d0-123">[Služba řízení přístupu Azure systému Windows (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517).</span><span class="sxs-lookup"><span data-stu-id="572d0-123">[Windows Azure Access Control Service (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517).</span></span>  
  
 <span data-ttu-id="572d0-124">Služba AD FS 2.0 je součástí systému Windows Server R2 a může sloužit jako služba STS pro místní scénáře.</span><span class="sxs-lookup"><span data-stu-id="572d0-124">AD FS 2.0 is part of the Windows Server R2 and can be used as an STS for on-premise scenarios.</span></span> <span data-ttu-id="572d0-125">Azure Active Directory řízení přístupu (také označované jako služby Řízení přístupu nebo služby ACS) je Cloudová služba, které nabízí v rámci Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="572d0-125">Azure Active Directory Access Control (also known as Access Control Service or ACS) is a cloud service, offered as part of Microsoft Azure.</span></span> <span data-ttu-id="572d0-126">Při sestavování aplikací pracujících s deklaracemi můžete pro testovací nebo vzdělávací účely použít také jinou službu STS.</span><span class="sxs-lookup"><span data-stu-id="572d0-126">For testing or educational purposes, you can also use other STS’s in order to build your claims-aware applications.</span></span> <span data-ttu-id="572d0-127">Například můžete použít místní službu tokenů zabezpečení vývoj, která je součástí [identita a přístup pro sadu Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849) tedy volně dostupných online.</span><span class="sxs-lookup"><span data-stu-id="572d0-127">For example, you can use the Local Development STS that is part of the [Identity and Access Tool for Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849) which is freely available online.</span></span>  
  
 <span data-ttu-id="572d0-128">Vytvoření vaší první deklaracemi identity služby WCF pomocí WIF, najdete v části [postupy: sestavení deklaracemi WCF služby pomocí WIF](http://msdn.microsoft.com/en-us/431e6415-62ed-4a9f-af03-f14d2b4dfe6d).</span><span class="sxs-lookup"><span data-stu-id="572d0-128">To build your first claims-aware WCF service using WIF, see [How To: Build Claims-Aware WCF Service Using WIF](http://msdn.microsoft.com/en-us/431e6415-62ed-4a9f-af03-f14d2b4dfe6d).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="572d0-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="572d0-129">See Also</span></span>  
 [<span data-ttu-id="572d0-130">Začínáme s WIF</span><span class="sxs-lookup"><span data-stu-id="572d0-130">Getting Started With WIF</span></span>](../../../docs/framework/security/getting-started-with-wif.md)
