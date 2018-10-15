---
title: Stažení balíčku obslužné rutiny webových tokenů JSON
ms.date: 10/10/2018
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
ms.openlocfilehash: 8f878d23afd76488de7da03f16f72cbfa43c17d7
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2018
ms.locfileid: "49316477"
---
# <a name="download-the-json-web-token-handler-package"></a><span data-ttu-id="a7bc1-102">Stažení balíčku obslužné rutiny tokenu JSON Web</span><span class="sxs-lookup"><span data-stu-id="a7bc1-102">Download the JSON Web Token Handler Package</span></span>

<span data-ttu-id="a7bc1-103">Toto téma popisuje, jak stáhnout a použít JSON Web Token Handler ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="a7bc1-103">This topic discusses how to download and use the JSON Web Token Handler in your project.</span></span>

<span data-ttu-id="a7bc1-104">Rozšíření obslužné rutiny webového tokenu JSON je k dispozici jako balíček NuGet, který přidá nezbytná sestavení a odkazy na projekt.</span><span class="sxs-lookup"><span data-stu-id="a7bc1-104">The JSON Web Token Handler extension is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="a7bc1-105">Pokud již nemáte nainstalován nástroj NuGet, přejděte na [nuget.org](https://nuget.org) k její instalaci.</span><span class="sxs-lookup"><span data-stu-id="a7bc1-105">If you do not already have NuGet installed, go to [nuget.org](https://nuget.org) to install it.</span></span> <span data-ttu-id="a7bc1-106">Historii verzí pro rozšíření můžete zobrazit návštěvou její stránky na webu NuGet: [JSON Web Token Handler na Nugetu](https://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span><span class="sxs-lookup"><span data-stu-id="a7bc1-106">You can see the versioning history for the extension by visiting its page on NuGet: [JSON Web Token Handler on NuGet](https://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span></span>

## <a name="use-the-package-manager-gui"></a><span data-ttu-id="a7bc1-107">Pomocí GUI Správce balíčků</span><span class="sxs-lookup"><span data-stu-id="a7bc1-107">Use the Package Manager GUI</span></span>

1. <span data-ttu-id="a7bc1-108">V sadě Visual Studio, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení**a pak vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="a7bc1-108">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>

2. <span data-ttu-id="a7bc1-109">V **spravovat balíčky NuGet** okna, klikněte do vyhledávacího pole a zadejte `JWT Token Handler` a stiskněte klávesu **Enter**.</span><span class="sxs-lookup"><span data-stu-id="a7bc1-109">In the **Manage NuGet Packages** window, click the search box and enter `JWT Token Handler` and press **Enter**.</span></span>

3. <span data-ttu-id="a7bc1-110">V podokně výsledků klikněte **nainstalovat** tlačítko pro první výsledek.</span><span class="sxs-lookup"><span data-stu-id="a7bc1-110">From the results pane, click the **Install** button for the first result.</span></span>

4. <span data-ttu-id="a7bc1-111">Balíček se začne stahovat.</span><span class="sxs-lookup"><span data-stu-id="a7bc1-111">The package will begin downloading.</span></span> <span data-ttu-id="a7bc1-112">Před přidáním do projektu, zobrazí se dialogové okno přijetí licence.</span><span class="sxs-lookup"><span data-stu-id="a7bc1-112">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="a7bc1-113">Pokud s licenčními podmínkami souhlasíte, klikněte na tlačítko **souhlasím**.</span><span class="sxs-lookup"><span data-stu-id="a7bc1-113">If you agree to the license terms, click **I Accept**.</span></span>

5. <span data-ttu-id="a7bc1-114">Nejnovější sestavení obslužné rutiny webového tokenu JSON bude stažena a přidány do projektu.</span><span class="sxs-lookup"><span data-stu-id="a7bc1-114">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>

## <a name="use-the-package-manager-console"></a><span data-ttu-id="a7bc1-115">Použití konzole Správce balíčků</span><span class="sxs-lookup"><span data-stu-id="a7bc1-115">Use the Package Manager Console</span></span>

1. <span data-ttu-id="a7bc1-116">V sadě Visual Studio, klikněte na tlačítko **nástroje** > **Správce balíčků NuGet** > **Konzola správce balíčků**.</span><span class="sxs-lookup"><span data-stu-id="a7bc1-116">In Visual Studio, click **Tools** > **NuGet Package Manager** > **Package Manager Console**.</span></span>

2. <span data-ttu-id="a7bc1-117">**Konzola správce balíčků** se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="a7bc1-117">The **Package Manager Console** appears.</span></span> <span data-ttu-id="a7bc1-118">Zadejte následující text a stiskněte klávesu **Enter**:</span><span class="sxs-lookup"><span data-stu-id="a7bc1-118">Enter the following text and press **Enter**:</span></span>

    ```powershell
    Install-Package System.IdentityModel.Tokens.Jwt
    ```

3. <span data-ttu-id="a7bc1-119">Nejnovější sestavení obslužné rutiny webového tokenu JSON bude stažena a přidány do projektu.</span><span class="sxs-lookup"><span data-stu-id="a7bc1-119">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>