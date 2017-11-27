---
title: "Vytváření Můj první deklaracemi webové aplikace ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ee8ee7f-caba-4267-9343-e313fae2876d
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: aa25f163199652618e35399c6548a9864a17370a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="building-my-first-claims-aware-aspnet-web-application"></a><span data-ttu-id="8b765-102">Vytváření Můj první deklaracemi webové aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8b765-102">Building My First Claims-Aware ASP.NET Web Application</span></span>
## <a name="applies-to"></a><span data-ttu-id="8b765-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="8b765-103">Applies To</span></span>  
  
-   <span data-ttu-id="8b765-104">Windows Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="8b765-104">Windows Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="8b765-105">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8b765-105">ASP.NET</span></span>  
  
 <span data-ttu-id="8b765-106">Toto téma popisuje, jak pomocí technologie WIF vytvářet webové aplikace ASP.NET pracující s deklaracemi.</span><span class="sxs-lookup"><span data-stu-id="8b765-106">This topic outlines the scenario of building claims-aware ASP.NET web applications using WIF.</span></span> <span data-ttu-id="8b765-107">Scénář aplikací pracujících s deklaracemi má obvykle tři účastníky, kterými jsou samotná aplikace, koncový uživatel a služba tokenů zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="8b765-107">There are usually three participants in a claims-aware application scenario: the application itself, the end user, and the Security Token Service (STS).</span></span> <span data-ttu-id="8b765-108">Tento scénář zachycuje následující obrázek:</span><span class="sxs-lookup"><span data-stu-id="8b765-108">The following figure describes this scenario:</span></span>  
  
 <span data-ttu-id="8b765-109">![WIF základní webové aplikace](../../../docs/framework/security/media/wifbasicwebapp.gif "WIFBasicWebApp")</span><span class="sxs-lookup"><span data-stu-id="8b765-109">![WIF Basic Web App](../../../docs/framework/security/media/wifbasicwebapp.gif "WIFBasicWebApp")</span></span>  
  
1.  <span data-ttu-id="8b765-110">Aplikace pracující s deklaracemi zjišťují pomocí technologie WIF neověřené žádosti a směrují je na službu STS.</span><span class="sxs-lookup"><span data-stu-id="8b765-110">The claims-aware application uses WIF to identify unauthenticated requests and to redirect them to the STS.</span></span>  
  
2.  <span data-ttu-id="8b765-111">Koncový uživatel poskytne službě STS své přihlašovací údaje a po úspěšném ověření uživatele vystaví služba STS token.</span><span class="sxs-lookup"><span data-stu-id="8b765-111">The end user provides credentials to the STS and upon successful authentication the user is issued a token by the STS.</span></span>  
  
3.  <span data-ttu-id="8b765-112">Uživatel je přesměrován ze služby STS na aplikaci pracující s deklaracemi a token vystavený službou STS je přitom obsažen v žádosti.</span><span class="sxs-lookup"><span data-stu-id="8b765-112">The user is redirected from the STS to the claims-aware application with the STS-issued token in the request.</span></span>  
  
4.  <span data-ttu-id="8b765-113">Aplikace pracující s deklaracemi je nakonfigurována tak, aby službu STS a jí vystavené tokeny považovala za důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="8b765-113">The claims-aware application is configured to trust the STS and the tokens it issues.</span></span> <span data-ttu-id="8b765-114">Aplikace pracující s deklaracemi token ověří a analyzuje pomocí technologie WIF.</span><span class="sxs-lookup"><span data-stu-id="8b765-114">The claims-aware application uses WIF to validate the token and to parse it.</span></span> <span data-ttu-id="8b765-115">Vývojáři použít vhodné WIF API a typy, například **ClaimsPrincpal** pro potřeby aplikace, jako je například implementace autorizace pro ni.</span><span class="sxs-lookup"><span data-stu-id="8b765-115">Developers use the appropriate WIF API and types, for example, **ClaimsPrincpal** for the application’s needs, such as implementing authorization for it.</span></span>  
  
 <span data-ttu-id="8b765-116">Od rozhraní .NET 4.5, WIF je součástí balíčku rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8b765-116">Starting from .NET 4.5, WIF is part of the .NET Framework package.</span></span> <span data-ttu-id="8b765-117">Přímo k dispozici v rámci třídy WIF mnohem hlubší integrace založené na deklaracích identity umožní v rozhraní .NET, což usnadňuje používat deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="8b765-117">Having the WIF classes directly available in the framework allows a much deeper integration of claims-based identity in .NET, making it easier to use claims.</span></span> <span data-ttu-id="8b765-118">Technologie WIF 4.5 umožňuje začít vyvíjet webové aplikace pracující s deklaracemi bez nutnosti instalovat další samostatné součásti.</span><span class="sxs-lookup"><span data-stu-id="8b765-118">With WIF 4.5, you do not need to install any out-of-band components in order to start developing claims-aware web applications.</span></span> <span data-ttu-id="8b765-119">Třídy WIF jsou nyní rozloženy mezi několik sestavení. Mezi hlavní sestavení patří System.Security.Claims, System.IdentityModel a System.IdentityModel.Services.</span><span class="sxs-lookup"><span data-stu-id="8b765-119">WIF classes are now spread across various assemblies, the main ones being System.Security.Claims, System.IdentityModel and System.IdentityModel.Services.</span></span>  
  
 <span data-ttu-id="8b765-120">STS je služba, která vystavuje tokeny po úspěšném ověření.</span><span class="sxs-lookup"><span data-stu-id="8b765-120">STS is a service that issues tokens upon successful authentication.</span></span> <span data-ttu-id="8b765-121">Společnost Microsoft nabízí dvě služby STS, které vyhovují standardům odvětví:</span><span class="sxs-lookup"><span data-stu-id="8b765-121">Microsoft offers two industry standard STS’s:</span></span>  
  
-   <span data-ttu-id="8b765-122">[Active Directory Federation Services (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) (http://go.microsoft.com/fwlink/?LinkID=247516)</span><span class="sxs-lookup"><span data-stu-id="8b765-122">[Active Directory Federation Services (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) (http://go.microsoft.com/fwlink/?LinkID=247516)</span></span>  
  
-   <span data-ttu-id="8b765-123">[Služba řízení přístupu Azure systému Windows (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517).</span><span class="sxs-lookup"><span data-stu-id="8b765-123">[Windows Azure Access Control Service (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517).</span></span>  
  
 <span data-ttu-id="8b765-124">Služba AD FS 2.0 je součástí systému Windows Server R2 a může sloužit jako služba STS pro místní scénáře.</span><span class="sxs-lookup"><span data-stu-id="8b765-124">AD FS 2.0 is part of the Windows Server R2 and can be used as an STS for on-premise scenarios.</span></span> <span data-ttu-id="8b765-125">Služba ACS je cloudová služba, nabízená v rámci platformy Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="8b765-125">ACS is a cloud service, offered as part of the Windows Azure Platform.</span></span> <span data-ttu-id="8b765-126">Při sestavování aplikací pracujících s deklaracemi můžete pro testovací nebo vzdělávací účely použít také jinou službu STS.</span><span class="sxs-lookup"><span data-stu-id="8b765-126">For testing or educational purposes, you can also use other STS’s in order to build your claims-aware applications.</span></span> <span data-ttu-id="8b765-127">Například můžete použít místní službu tokenů zabezpečení vývoj, která je součástí [identita a přístup pro sadu Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849) tedy volně dostupných online.</span><span class="sxs-lookup"><span data-stu-id="8b765-127">For example, you can use the Local Development STS that is part of the [Identity and Access Tool for Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849) which is freely available online.</span></span>  
  
 <span data-ttu-id="8b765-128">Pokud chcete pomocí technologie WIF vytvořit svou první aplikaci ASP.NET pracující s deklaracemi, postupujte podle pokynů v jednom z následujících témat:</span><span class="sxs-lookup"><span data-stu-id="8b765-128">To build your first claims-aware ASP.NET application using WIF, follow the instructions in one of the following:</span></span>  
  
-   [<span data-ttu-id="8b765-129">Postupy: Vytvoření deklaracemi rozhraní ASP.NET MVC webové aplikace pomocí WIF</span><span class="sxs-lookup"><span data-stu-id="8b765-129">How To: Build Claims-Aware ASP.NET MVC Web Application Using WIF</span></span>](../../../docs/framework/security/how-to-build-claims-aware-aspnet-mvc-web-app-using-wif.md)  
  
-   [<span data-ttu-id="8b765-130">Postupy: Vytvoření aplikace deklaracemi rozhraní ASP.NET Web Forms pomocí WIF</span><span class="sxs-lookup"><span data-stu-id="8b765-130">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)  
  
-   [<span data-ttu-id="8b765-131">Postupy: Vytvoření aplikace ASP.NET deklaracemi pomocí ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="8b765-131">How To: Build Claims-Aware ASP.NET Application Using Forms-Based Authentication</span></span>](../../../docs/framework/security/claims-aware-aspnet-app-forms-authentication.md)  
  
## <a name="see-also"></a><span data-ttu-id="8b765-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b765-132">See Also</span></span>  
 [<span data-ttu-id="8b765-133">Začínáme s WIF</span><span class="sxs-lookup"><span data-stu-id="8b765-133">Getting Started With WIF</span></span>](../../../docs/framework/security/getting-started-with-wif.md)
