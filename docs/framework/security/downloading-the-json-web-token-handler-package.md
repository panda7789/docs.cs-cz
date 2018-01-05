---
title: "Stažení balíčku obslužné rutiny webových tokenů JSON"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5982830404d8d8780bf41153741928b68dc5c7d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="downloading-the-json-web-token-handler-package"></a><span data-ttu-id="480fd-102">Stažení balíčku obslužné rutiny webových tokenů JSON</span><span class="sxs-lookup"><span data-stu-id="480fd-102">Downloading the JSON Web Token Handler Package</span></span>
<span data-ttu-id="480fd-103">Toto téma popisuje, jak stáhnout a použít JSON obslužná rutina webových tokenů ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="480fd-103">This topic discusses how to download and use the JSON Web Token Handler in your project.</span></span>  
  
## <a name="downloading-the-json-web-token-handler"></a><span data-ttu-id="480fd-104">Stažení obslužné rutiny webových tokenů JSON</span><span class="sxs-lookup"><span data-stu-id="480fd-104">Downloading the JSON Web Token Handler</span></span>  
 <span data-ttu-id="480fd-105">Obslužná rutina webových tokenů JSON rozšíření není k dispozici jako balíčku NuGet, který přidá nezbytné sestavení a odkazy na projekt.</span><span class="sxs-lookup"><span data-stu-id="480fd-105">The JSON Web Token Handler extension is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="480fd-106">Pokud již nemáte NuGet nainstalovaná, přejděte na [nuget.org](http://nuget.org) k její instalaci.</span><span class="sxs-lookup"><span data-stu-id="480fd-106">If you do not already have NuGet installed, go to [nuget.org](http://nuget.org) to install it.</span></span> <span data-ttu-id="480fd-107">Zobrazí historii Správa verzí pro rozšíření navštivte stránku s jeho na NuGet: [JSON obslužná rutina webových tokenů na NuGet](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span><span class="sxs-lookup"><span data-stu-id="480fd-107">You can see the versioning history for the extension by visiting its page on NuGet: [JSON Web Token Handler on NuGet](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span></span>  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-gui"></a><span data-ttu-id="480fd-108">Stahování obslužná rutina tokenu JSON Web pomocí grafického uživatelského rozhraní Správce balíčků</span><span class="sxs-lookup"><span data-stu-id="480fd-108">Downloading the JSON Web Token Handler by using the Package Manager GUI</span></span>  
  
1.  <span data-ttu-id="480fd-109">V sadě Visual Studio, klikněte pravým tlačítkem na projekt v **Průzkumníku řešení**a potom vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="480fd-109">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>  
  
2.  <span data-ttu-id="480fd-110">V **spravovat balíčky NuGet** okně klikněte na vyhledávací pole a zadejte `JWT Token Handler` a stiskněte klávesu **Enter**.</span><span class="sxs-lookup"><span data-stu-id="480fd-110">In the **Manage NuGet Packages** window, click the search box and enter `JWT Token Handler` and press **Enter**.</span></span>  
  
3.  <span data-ttu-id="480fd-111">V podokně výsledků klikněte na **nainstalovat** tlačítko pro první výsledek.</span><span class="sxs-lookup"><span data-stu-id="480fd-111">From the results pane, click the **Install** button for the first result.</span></span>  
  
4.  <span data-ttu-id="480fd-112">Balíček zahájíte stahování.</span><span class="sxs-lookup"><span data-stu-id="480fd-112">The package will begin downloading.</span></span> <span data-ttu-id="480fd-113">Před přidáním do projektu, zobrazí se dialogové okno přijetí licence.</span><span class="sxs-lookup"><span data-stu-id="480fd-113">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="480fd-114">Pokud souhlasíte s licenčními podmínkami, klikněte na tlačítko **souhlasím**.</span><span class="sxs-lookup"><span data-stu-id="480fd-114">If you agree to the license terms, click **I Accept**.</span></span>  
  
5.  <span data-ttu-id="480fd-115">Nejnovější sestavení obslužná rutina webových tokenů JSON, bude možné stáhnout a přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="480fd-115">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-console"></a><span data-ttu-id="480fd-116">Stahování obslužná rutina tokenu JSON Web pomocí konzoly Správce balíčků</span><span class="sxs-lookup"><span data-stu-id="480fd-116">Downloading the JSON Web Token Handler by using the Package Manager Console</span></span>  
  
1.  <span data-ttu-id="480fd-117">V sadě Visual Studio, klikněte na tlačítko **nástroje**, **Správce balíčků knihoven**a potom **Konzola správce balíčků**.</span><span class="sxs-lookup"><span data-stu-id="480fd-117">In Visual Studio, click **Tools**, **Library Package Manager**, and then **Package Manager Console**.</span></span>  
  
2.  <span data-ttu-id="480fd-118">**Konzola správce balíčků** se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="480fd-118">The **Package Manager Console** appears.</span></span> <span data-ttu-id="480fd-119">Zadejte následující text a stiskněte klávesu **Enter**:</span><span class="sxs-lookup"><span data-stu-id="480fd-119">Enter the following text and press **Enter**:</span></span>  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.Jwt  
    ```  
  
3.  <span data-ttu-id="480fd-120">Nejnovější sestavení obslužná rutina webových tokenů JSON, bude možné stáhnout a přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="480fd-120">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>
