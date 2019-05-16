---
title: Stažení balíčku obslužné rutiny webových tokenů JSON
ms.date: 10/10/2018
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
ms.openlocfilehash: a8685a71d46778d932595965f32c0041b176bd83
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633529"
---
# <a name="download-the-json-web-token-handler-package"></a><span data-ttu-id="35f79-102">Stažení balíčku obslužné rutiny tokenu JSON Web</span><span class="sxs-lookup"><span data-stu-id="35f79-102">Download the JSON Web Token Handler Package</span></span>

<span data-ttu-id="35f79-103">Toto téma popisuje, jak stáhnout a použít JSON Web Token Handler ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="35f79-103">This topic discusses how to download and use the JSON Web Token Handler in your project.</span></span>

<span data-ttu-id="35f79-104">Rozšíření obslužné rutiny webového tokenu JSON je k dispozici jako balíček NuGet, který přidá nezbytná sestavení a odkazy na projekt.</span><span class="sxs-lookup"><span data-stu-id="35f79-104">The JSON Web Token Handler extension is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="35f79-105">Pokud již nemáte nainstalován nástroj NuGet, přejděte na [nuget.org](https://nuget.org) k její instalaci.</span><span class="sxs-lookup"><span data-stu-id="35f79-105">If you do not already have NuGet installed, go to [nuget.org](https://nuget.org) to install it.</span></span> <span data-ttu-id="35f79-106">Historii verzí pro rozšíření můžete zobrazit návštěvou její stránky na webu NuGet: [JSON Web Token Handler na Nugetu](https://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span><span class="sxs-lookup"><span data-stu-id="35f79-106">You can see the versioning history for the extension by visiting its page on NuGet: [JSON Web Token Handler on NuGet](https://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span></span>

## <a name="use-the-package-manager-gui"></a><span data-ttu-id="35f79-107">Pomocí GUI Správce balíčků</span><span class="sxs-lookup"><span data-stu-id="35f79-107">Use the Package Manager GUI</span></span>

1. <span data-ttu-id="35f79-108">V sadě Visual Studio, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení**a pak vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="35f79-108">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>

2. <span data-ttu-id="35f79-109">V **spravovat balíčky NuGet** okna, klikněte do vyhledávacího pole a zadejte `JWT Token Handler` a stiskněte klávesu **Enter**.</span><span class="sxs-lookup"><span data-stu-id="35f79-109">In the **Manage NuGet Packages** window, click the search box and enter `JWT Token Handler` and press **Enter**.</span></span>

3. <span data-ttu-id="35f79-110">V podokně výsledků klikněte **nainstalovat** tlačítko pro první výsledek.</span><span class="sxs-lookup"><span data-stu-id="35f79-110">From the results pane, click the **Install** button for the first result.</span></span>

4. <span data-ttu-id="35f79-111">Balíček se začne stahovat.</span><span class="sxs-lookup"><span data-stu-id="35f79-111">The package will begin downloading.</span></span> <span data-ttu-id="35f79-112">Před přidáním do projektu, zobrazí se dialogové okno přijetí licence.</span><span class="sxs-lookup"><span data-stu-id="35f79-112">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="35f79-113">Pokud s licenčními podmínkami souhlasíte, klikněte na tlačítko **souhlasím**.</span><span class="sxs-lookup"><span data-stu-id="35f79-113">If you agree to the license terms, click **I Accept**.</span></span>

5. <span data-ttu-id="35f79-114">Nejnovější sestavení obslužné rutiny webového tokenu JSON bude stažena a přidány do projektu.</span><span class="sxs-lookup"><span data-stu-id="35f79-114">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>

## <a name="use-the-package-manager-console"></a><span data-ttu-id="35f79-115">Použití konzole Správce balíčků</span><span class="sxs-lookup"><span data-stu-id="35f79-115">Use the Package Manager Console</span></span>

1. <span data-ttu-id="35f79-116">V sadě Visual Studio, klikněte na tlačítko **nástroje** > **Správce balíčků NuGet** > **Konzola správce balíčků**.</span><span class="sxs-lookup"><span data-stu-id="35f79-116">In Visual Studio, click **Tools** > **NuGet Package Manager** > **Package Manager Console**.</span></span>

2. <span data-ttu-id="35f79-117">**Konzola správce balíčků** se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="35f79-117">The **Package Manager Console** appears.</span></span> <span data-ttu-id="35f79-118">Zadejte následující text a stiskněte klávesu **Enter**:</span><span class="sxs-lookup"><span data-stu-id="35f79-118">Enter the following text and press **Enter**:</span></span>

    ```powershell
    Install-Package System.IdentityModel.Tokens.Jwt
    ```

3. <span data-ttu-id="35f79-119">Nejnovější sestavení obslužné rutiny webového tokenu JSON bude stažena a přidány do projektu.</span><span class="sxs-lookup"><span data-stu-id="35f79-119">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>
