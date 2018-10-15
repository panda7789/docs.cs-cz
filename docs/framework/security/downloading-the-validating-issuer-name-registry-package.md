---
title: Stažení balíčku registru pro ověřování názvů vydavatelů
ms.date: 10/10/2018
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
ms.openlocfilehash: 833a0722fdd27df4e488ed7fac99444c6d9b8905
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2018
ms.locfileid: "49316182"
---
# <a name="download-the-validating-issuer-name-registry-package"></a><span data-ttu-id="27794-102">Stažení balíčku registru ověřování názvů vydavatelů</span><span class="sxs-lookup"><span data-stu-id="27794-102">Download the Validating Issuer Name Registry Package</span></span>

<span data-ttu-id="27794-103">Toto téma popisuje, jak stáhnout a použít ověřování Issuer Name Registry (VINR) ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="27794-103">This topic discusses how to download and use the Validating Issuer Name Registry (VINR) in your project.</span></span>

<span data-ttu-id="27794-104">Rozšíření VINR je k dispozici jako balíček NuGet, který přidá nezbytná sestavení a odkazy na projekt.</span><span class="sxs-lookup"><span data-stu-id="27794-104">The VINR is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="27794-105">Pokud již nemáte nainstalován nástroj NuGet, přejděte na [nuget.org](https://nuget.org) k její instalaci.</span><span class="sxs-lookup"><span data-stu-id="27794-105">If you do not already have NuGet installed, go to [nuget.org](https://nuget.org) to install it.</span></span> <span data-ttu-id="27794-106">Historii verzí pro rozšíření můžete zobrazit návštěvou její stránky na webu NuGet: [Microsoft ověřuje registr názvu vydavatele na NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span><span class="sxs-lookup"><span data-stu-id="27794-106">You can see the versioning history for the extension by visiting its page on NuGet: [Microsoft Validating Issuer Name Registry on NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span></span>

## <a name="use-the-package-manager-gui"></a><span data-ttu-id="27794-107">Pomocí GUI Správce balíčků</span><span class="sxs-lookup"><span data-stu-id="27794-107">Use the Package Manager GUI</span></span>

1. <span data-ttu-id="27794-108">V sadě Visual Studio, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení**a pak vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="27794-108">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>

2. <span data-ttu-id="27794-109">V **spravovat balíčky NuGet** okna, klikněte do vyhledávacího pole a zadejte `ValidatingIssuerNameRegistry` a stiskněte klávesu **Enter**.</span><span class="sxs-lookup"><span data-stu-id="27794-109">In the **Manage NuGet Packages** window, click the search box and enter `ValidatingIssuerNameRegistry` and press **Enter**.</span></span>

3. <span data-ttu-id="27794-110">V podokně výsledků klikněte **nainstalovat** tlačítko pro první výsledek.</span><span class="sxs-lookup"><span data-stu-id="27794-110">From the results pane, click the **Install** button for the first result.</span></span>

4. <span data-ttu-id="27794-111">Balíček se začne stahovat.</span><span class="sxs-lookup"><span data-stu-id="27794-111">The package will begin downloading.</span></span> <span data-ttu-id="27794-112">Před přidáním do projektu, zobrazí se dialogové okno přijetí licence.</span><span class="sxs-lookup"><span data-stu-id="27794-112">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="27794-113">Pokud s licenčními podmínkami souhlasíte, klikněte na tlačítko **souhlasím**.</span><span class="sxs-lookup"><span data-stu-id="27794-113">If you agree to the license terms, click **I Accept**.</span></span>

5. <span data-ttu-id="27794-114">Nejnovější sestavení VINR bude stažena a přidány do projektu.</span><span class="sxs-lookup"><span data-stu-id="27794-114">The latest VINR assemblies will be downloaded and added to your project.</span></span>

## <a name="use-the-package-manager-console"></a><span data-ttu-id="27794-115">Použití konzole Správce balíčků</span><span class="sxs-lookup"><span data-stu-id="27794-115">Use the Package Manager Console</span></span>

1. <span data-ttu-id="27794-116">V sadě Visual Studio, klikněte na tlačítko **nástroje** > **Správce balíčků NuGet** > **Konzola správce balíčků**.</span><span class="sxs-lookup"><span data-stu-id="27794-116">In Visual Studio, click **Tools** > **NuGet Package Manager** > **Package Manager Console**.</span></span>

2. <span data-ttu-id="27794-117">**Konzola správce balíčků** se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="27794-117">The **Package Manager Console** appears.</span></span> <span data-ttu-id="27794-118">Zadejte následující text a stiskněte klávesu **Enter**:</span><span class="sxs-lookup"><span data-stu-id="27794-118">Enter the following text and press **Enter**:</span></span>

    ```powershell
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry
    ```

3. <span data-ttu-id="27794-119">Nejnovější sestavení VINR bude stažena a přidány do projektu.</span><span class="sxs-lookup"><span data-stu-id="27794-119">The latest VINR assemblies will be downloaded and added to your project.</span></span>