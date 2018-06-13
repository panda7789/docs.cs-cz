---
title: Stažení balíčku obslužné rutiny webových tokenů JSON
ms.date: 03/30/2017
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
ms.openlocfilehash: 5a4846a5ec92324105f41b320d0d77f8749c28f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404674"
---
# <a name="downloading-the-json-web-token-handler-package"></a><span data-ttu-id="bc57c-102">Stažení balíčku obslužné rutiny webových tokenů JSON</span><span class="sxs-lookup"><span data-stu-id="bc57c-102">Downloading the JSON Web Token Handler Package</span></span>
<span data-ttu-id="bc57c-103">Toto téma popisuje, jak stáhnout a použít JSON obslužná rutina webových tokenů ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="bc57c-103">This topic discusses how to download and use the JSON Web Token Handler in your project.</span></span>  
  
## <a name="downloading-the-json-web-token-handler"></a><span data-ttu-id="bc57c-104">Stažení obslužné rutiny webových tokenů JSON</span><span class="sxs-lookup"><span data-stu-id="bc57c-104">Downloading the JSON Web Token Handler</span></span>  
 <span data-ttu-id="bc57c-105">Obslužná rutina webových tokenů JSON rozšíření není k dispozici jako balíčku NuGet, který přidá nezbytné sestavení a odkazy na projekt.</span><span class="sxs-lookup"><span data-stu-id="bc57c-105">The JSON Web Token Handler extension is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="bc57c-106">Pokud již nemáte NuGet nainstalovaná, přejděte na [nuget.org](http://nuget.org) k její instalaci.</span><span class="sxs-lookup"><span data-stu-id="bc57c-106">If you do not already have NuGet installed, go to [nuget.org](http://nuget.org) to install it.</span></span> <span data-ttu-id="bc57c-107">Zobrazí historii Správa verzí pro rozšíření navštivte stránku s jeho na NuGet: [JSON obslužná rutina webových tokenů na NuGet](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span><span class="sxs-lookup"><span data-stu-id="bc57c-107">You can see the versioning history for the extension by visiting its page on NuGet: [JSON Web Token Handler on NuGet](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span></span>  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-gui"></a><span data-ttu-id="bc57c-108">Stahování obslužná rutina tokenu JSON Web pomocí grafického uživatelského rozhraní Správce balíčků</span><span class="sxs-lookup"><span data-stu-id="bc57c-108">Downloading the JSON Web Token Handler by using the Package Manager GUI</span></span>  
  
1.  <span data-ttu-id="bc57c-109">V sadě Visual Studio, klikněte pravým tlačítkem na projekt v **Průzkumníku řešení**a potom vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="bc57c-109">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>  
  
2.  <span data-ttu-id="bc57c-110">V **spravovat balíčky NuGet** okně klikněte na vyhledávací pole a zadejte `JWT Token Handler` a stiskněte klávesu **Enter**.</span><span class="sxs-lookup"><span data-stu-id="bc57c-110">In the **Manage NuGet Packages** window, click the search box and enter `JWT Token Handler` and press **Enter**.</span></span>  
  
3.  <span data-ttu-id="bc57c-111">V podokně výsledků klikněte na **nainstalovat** tlačítko pro první výsledek.</span><span class="sxs-lookup"><span data-stu-id="bc57c-111">From the results pane, click the **Install** button for the first result.</span></span>  
  
4.  <span data-ttu-id="bc57c-112">Balíček zahájíte stahování.</span><span class="sxs-lookup"><span data-stu-id="bc57c-112">The package will begin downloading.</span></span> <span data-ttu-id="bc57c-113">Před přidáním do projektu, zobrazí se dialogové okno přijetí licence.</span><span class="sxs-lookup"><span data-stu-id="bc57c-113">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="bc57c-114">Pokud souhlasíte s licenčními podmínkami, klikněte na tlačítko **souhlasím**.</span><span class="sxs-lookup"><span data-stu-id="bc57c-114">If you agree to the license terms, click **I Accept**.</span></span>  
  
5.  <span data-ttu-id="bc57c-115">Nejnovější sestavení obslužná rutina webových tokenů JSON, bude možné stáhnout a přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="bc57c-115">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-console"></a><span data-ttu-id="bc57c-116">Stahování obslužná rutina tokenu JSON Web pomocí konzoly Správce balíčků</span><span class="sxs-lookup"><span data-stu-id="bc57c-116">Downloading the JSON Web Token Handler by using the Package Manager Console</span></span>  
  
1.  <span data-ttu-id="bc57c-117">V sadě Visual Studio, klikněte na tlačítko **nástroje**, **Správce balíčků knihoven**a potom **Konzola správce balíčků**.</span><span class="sxs-lookup"><span data-stu-id="bc57c-117">In Visual Studio, click **Tools**, **Library Package Manager**, and then **Package Manager Console**.</span></span>  
  
2.  <span data-ttu-id="bc57c-118">**Konzola správce balíčků** se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="bc57c-118">The **Package Manager Console** appears.</span></span> <span data-ttu-id="bc57c-119">Zadejte následující text a stiskněte klávesu **Enter**:</span><span class="sxs-lookup"><span data-stu-id="bc57c-119">Enter the following text and press **Enter**:</span></span>  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.Jwt  
    ```  
  
3.  <span data-ttu-id="bc57c-120">Nejnovější sestavení obslužná rutina webových tokenů JSON, bude možné stáhnout a přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="bc57c-120">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>
