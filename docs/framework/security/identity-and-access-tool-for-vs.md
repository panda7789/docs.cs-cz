---
title: Identity and Access Tool for Visual Studio 2012
ms.date: 03/30/2017
ms.assetid: 87b8f8f2-4074-44fd-9fd6-08278e877390
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 6af769c0b5afd61015b80c3f6987c8062c596929
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481385"
---
# <a name="identity-and-access-tool-for-visual-studio-2012"></a><span data-ttu-id="bec45-102">Identity and Access Tool for Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="bec45-102">Identity and Access Tool for Visual Studio 2012</span></span>
<span data-ttu-id="bec45-103">Toto téma popisuje nový nástroj Identity and Access Tool for Visual Studio 11.</span><span class="sxs-lookup"><span data-stu-id="bec45-103">This topic describes the new Identity and Access Tool for Visual Studio 11.</span></span> <span data-ttu-id="bec45-104">Tento nástroj si můžete stáhnout z následující adresy URL: [ https://go.microsoft.com/fwlink/?LinkID=245849 ](https://go.microsoft.com/fwlink/?LinkID=245849) nebo přímo v rámci sady Visual Studio 11 tak, že "identity" ve Správci rozšíření.</span><span class="sxs-lookup"><span data-stu-id="bec45-104">You can download this tool from the following URL: [https://go.microsoft.com/fwlink/?LinkID=245849](https://go.microsoft.com/fwlink/?LinkID=245849) or directly from within Visual Studio 11 by searching for "identity" directly in the Extensions Manager.</span></span>  
  
 <span data-ttu-id="bec45-105">Nástroj Identity and Access Tool for Visual Studio 11 přináší výrazně jednodušší možnosti vývoje díky následujícím hlavním funkcím:</span><span class="sxs-lookup"><span data-stu-id="bec45-105">The Identity and Access Tool for Visual Studio 11 delivers a dramatically simplified development-time experience with the following highlights:</span></span>  
  
-   <span data-ttu-id="bec45-106">Pomocí tohoto nového nástroje můžete vyvíjet s použitím typů projektů webových aplikací a cílit při tom na službu IIS Express.</span><span class="sxs-lookup"><span data-stu-id="bec45-106">Using the new tool, you can develop using web applications project types and target IIS express.</span></span>  
  
-   <span data-ttu-id="bec45-107">Na rozdíl od obecného ověřování, které jen poskytuje ochranu, můžete pomocí nového nástroje určit svou stránku zjišťování/kontroler místní domovské sféry (nebo jiný koncový bod, který zajišťuje ověřování ve vaší aplikaci) a technologie WIF nakonfiguruje všechny neověřené žádosti tak, aby byly zasílány na toto místo namísto jejich přesměrování do služby STS.</span><span class="sxs-lookup"><span data-stu-id="bec45-107">Unlike with the blanket protection-only authentication, with the new tool, you can specify your local home realm discovery page/controller (or any other endpoint handling the authentication experience within your application) and WIF will configure all unauthenticated requests to go there, instead of redirecting them to the STS.</span></span>  
  
-   <span data-ttu-id="bec45-108">Nástroj obsahuje testovací službu tokenů zabezpečení (STS), která se po zahájení ladicí relace spustí v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="bec45-108">The tool includes a test Security Token Service (STS) which runs on your local machine when you launch a debug session.</span></span> <span data-ttu-id="bec45-109">Proto již nemusíte vytvářet vlastní projekty STS a upravovat je tak, abyste získali deklarace potřebné k testování vašich aplikací.</span><span class="sxs-lookup"><span data-stu-id="bec45-109">Therefore, you no longer need to create custom STS projects and tweak them in order to get the claims you need to test your applications.</span></span> <span data-ttu-id="bec45-110">Typy a hodnoty deklarací jsou plně přizpůsobitelné.</span><span class="sxs-lookup"><span data-stu-id="bec45-110">The claim types and values are fully customizable.</span></span>  
  
-   <span data-ttu-id="bec45-111">Můžete upravit běžná nastavení přímo prostřednictvím uživatelského rozhraní nástroje, aniž byste museli upravovat soubor web.config.</span><span class="sxs-lookup"><span data-stu-id="bec45-111">You can modify common settings directly via the tool’s UI, without the need to edit web.config.</span></span>  
  
-   <span data-ttu-id="bec45-112">Můžete vytvořit federaci se službou Active Directory Federation Services (AD FS) 2.0 (nebo jinými poskytovateli identit podporujícími protokol WS-Federation) na jedné obrazovce.</span><span class="sxs-lookup"><span data-stu-id="bec45-112">You can establish federation with Active Directory Federation Services (AD FS) 2.0 (or other WS-Federation providers) in a single screen.</span></span>  
  
-   <span data-ttu-id="bec45-113">Nástroj využívá funkce Služby řízení přístupu Microsoft Azure (ACS) prostřednictvím jednoduchého seznamu zaškrtávacích políček pro všechny poskytovatele identit, které chcete používat: Facebook, Google, Live ID, Yahoo!, jakýkoli poskytovatel OpenID a jakýkoli poskytovatel podporující protokol WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="bec45-113">The tool leverages Windows Azure Access Control Service (ACS) capabilities with a simple list of checkboxes for all the identity providers that you want to use: Facebook, Google, Live ID, Yahoo!, any OpenID provider, and any WS-Federation provider.</span></span> <span data-ttu-id="bec45-114">Vyberte poskytovatele identity, klikněte na tlačítko OK a poté stiskněte klávesu F5. Vaše aplikace i služba ACS budou automaticky nakonfigurovány a vaše testovaná aplikace bude pracovat se službou ACS.</span><span class="sxs-lookup"><span data-stu-id="bec45-114">Select your identity providers, click OK, then F5, and both your application and ACS will be automatically configured and your test application will be ACS-aware.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bec45-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="bec45-115">See Also</span></span>  
 [<span data-ttu-id="bec45-116">Funkce technologie WIF</span><span class="sxs-lookup"><span data-stu-id="bec45-116">WIF Features</span></span>](../../../docs/framework/security/wif-features.md)
