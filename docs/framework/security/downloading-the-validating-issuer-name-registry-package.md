---
title: "Stažení balíčku registru pro ověřování názvů vydavatelů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bf6869de939ed7eda7cd3de868e712126f71751
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="downloading-the-validating-issuer-name-registry-package"></a><span data-ttu-id="747f9-102">Stažení balíčku registru pro ověřování názvů vydavatelů</span><span class="sxs-lookup"><span data-stu-id="747f9-102">Downloading the Validating Issuer Name Registry Package</span></span>
<span data-ttu-id="747f9-103">Toto téma popisuje, jak stáhnout a použít registru název vystavitele (VINR) ověřování ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="747f9-103">This topic discusses how to download and use the Validating Issuer Name Registry (VINR) in your project.</span></span>  
  
## <a name="downloading-the-validating-issuer-name-registry"></a><span data-ttu-id="747f9-104">Stahování ověřování registru název vystavitele</span><span class="sxs-lookup"><span data-stu-id="747f9-104">Downloading the Validating Issuer Name Registry</span></span>  
 <span data-ttu-id="747f9-105">VINR je k dispozici jako balíčku NuGet, který přidá nezbytné sestavení a odkazy na projekt.</span><span class="sxs-lookup"><span data-stu-id="747f9-105">The VINR is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="747f9-106">Pokud již nemáte NuGet nainstalovaná, přejděte na [nuget.org](http://nuget.org) k její instalaci.</span><span class="sxs-lookup"><span data-stu-id="747f9-106">If you do not already have NuGet installed, go to [nuget.org](http://nuget.org) to install it.</span></span> <span data-ttu-id="747f9-107">Zobrazí historii Správa verzí pro rozšíření navštivte stránku s jeho na NuGet: [Microsoft ověřování vystavitele název registru na NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span><span class="sxs-lookup"><span data-stu-id="747f9-107">You can see the versioning history for the extension by visiting its page on NuGet: [Microsoft Validating Issuer Name Registry on NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span></span>  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-gui"></a><span data-ttu-id="747f9-108">Stahování registru název vystavitele ověřování pomocí grafického uživatelského rozhraní Správce balíčků</span><span class="sxs-lookup"><span data-stu-id="747f9-108">Downloading the Validating Issuer Name Registry by using the Package Manager GUI</span></span>  
  
1.  <span data-ttu-id="747f9-109">V sadě Visual Studio, klikněte pravým tlačítkem na projekt v **Průzkumníku řešení**a potom vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="747f9-109">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>  
  
2.  <span data-ttu-id="747f9-110">V **spravovat balíčky NuGet** okně klikněte na vyhledávací pole a zadejte `ValidatingIssuerNameRegistry` a stiskněte klávesu **Enter**.</span><span class="sxs-lookup"><span data-stu-id="747f9-110">In the **Manage NuGet Packages** window, click the search box and enter `ValidatingIssuerNameRegistry` and press **Enter**.</span></span>  
  
3.  <span data-ttu-id="747f9-111">V podokně výsledků klikněte na **nainstalovat** tlačítko pro první výsledek.</span><span class="sxs-lookup"><span data-stu-id="747f9-111">From the results pane, click the **Install** button for the first result.</span></span>  
  
4.  <span data-ttu-id="747f9-112">Balíček zahájíte stahování.</span><span class="sxs-lookup"><span data-stu-id="747f9-112">The package will begin downloading.</span></span> <span data-ttu-id="747f9-113">Před přidáním do projektu, zobrazí se dialogové okno přijetí licence.</span><span class="sxs-lookup"><span data-stu-id="747f9-113">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="747f9-114">Pokud souhlasíte s licenčními podmínkami, klikněte na tlačítko **souhlasím**.</span><span class="sxs-lookup"><span data-stu-id="747f9-114">If you agree to the license terms, click **I Accept**.</span></span>  
  
5.  <span data-ttu-id="747f9-115">Nejnovější sestavení VINR bude možné stáhnout a přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="747f9-115">The latest VINR assemblies will be downloaded and added to your project.</span></span>  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-console"></a><span data-ttu-id="747f9-116">Stahování registru název vystavitele ověřování pomocí konzoly Správce balíčků</span><span class="sxs-lookup"><span data-stu-id="747f9-116">Downloading the Validating Issuer Name Registry by using the Package Manager Console</span></span>  
  
1.  <span data-ttu-id="747f9-117">V sadě Visual Studio, klikněte na tlačítko **nástroje**, **Správce balíčků knihoven**a potom **Konzola správce balíčků**.</span><span class="sxs-lookup"><span data-stu-id="747f9-117">In Visual Studio, click **Tools**, **Library Package Manager**, and then **Package Manager Console**.</span></span>  
  
2.  <span data-ttu-id="747f9-118">**Konzola správce balíčků** se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="747f9-118">The **Package Manager Console** appears.</span></span> <span data-ttu-id="747f9-119">Zadejte následující text a stiskněte klávesu **Enter**:</span><span class="sxs-lookup"><span data-stu-id="747f9-119">Enter the following text and press **Enter**:</span></span>  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry  
    ```  
  
3.  <span data-ttu-id="747f9-120">Nejnovější sestavení VINR bude možné stáhnout a přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="747f9-120">The latest VINR assemblies will be downloaded and added to your project.</span></span>
