---
title: Stažení balíčku registru pro ověřování názvů vydavatelů
ms.date: 10/10/2018
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
ms.openlocfilehash: 654a513e06f528f617bc19fbc59961c5b0e16049
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121152"
---
# <a name="download-the-validating-issuer-name-registry-package"></a><span data-ttu-id="229e0-102">Stažení balíčku registru ověřování názvů vydavatelů</span><span class="sxs-lookup"><span data-stu-id="229e0-102">Download the Validating Issuer Name Registry Package</span></span>

<span data-ttu-id="229e0-103">Toto téma popisuje, jak stáhnout a použít ověřování Issuer Name Registry (VINR) ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="229e0-103">This topic discusses how to download and use the Validating Issuer Name Registry (VINR) in your project.</span></span>

<span data-ttu-id="229e0-104">Rozšíření VINR je k dispozici jako balíček NuGet, který přidá nezbytná sestavení a odkazy na projekt.</span><span class="sxs-lookup"><span data-stu-id="229e0-104">The VINR is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="229e0-105">Pokud již nemáte nainstalován nástroj NuGet, přejděte na [nuget.org](http://nuget.org) k její instalaci.</span><span class="sxs-lookup"><span data-stu-id="229e0-105">If you do not already have NuGet installed, go to [nuget.org](http://nuget.org) to install it.</span></span> <span data-ttu-id="229e0-106">Historii verzí pro rozšíření můžete zobrazit návštěvou její stránky na webu NuGet: [Microsoft ověřuje registr názvu vydavatele na NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span><span class="sxs-lookup"><span data-stu-id="229e0-106">You can see the versioning history for the extension by visiting its page on NuGet: [Microsoft Validating Issuer Name Registry on NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span></span>

## <a name="use-the-package-manager-gui"></a><span data-ttu-id="229e0-107">Pomocí GUI Správce balíčků</span><span class="sxs-lookup"><span data-stu-id="229e0-107">Use the Package Manager GUI</span></span>

1. <span data-ttu-id="229e0-108">V sadě Visual Studio, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení**a pak vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="229e0-108">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>

2. <span data-ttu-id="229e0-109">V **spravovat balíčky NuGet** okna, klikněte do vyhledávacího pole a zadejte `ValidatingIssuerNameRegistry` a stiskněte klávesu **Enter**.</span><span class="sxs-lookup"><span data-stu-id="229e0-109">In the **Manage NuGet Packages** window, click the search box and enter `ValidatingIssuerNameRegistry` and press **Enter**.</span></span>

3. <span data-ttu-id="229e0-110">V podokně výsledků klikněte **nainstalovat** tlačítko pro první výsledek.</span><span class="sxs-lookup"><span data-stu-id="229e0-110">From the results pane, click the **Install** button for the first result.</span></span>

4. <span data-ttu-id="229e0-111">Balíček se začne stahovat.</span><span class="sxs-lookup"><span data-stu-id="229e0-111">The package will begin downloading.</span></span> <span data-ttu-id="229e0-112">Před přidáním do projektu, zobrazí se dialogové okno přijetí licence.</span><span class="sxs-lookup"><span data-stu-id="229e0-112">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="229e0-113">Pokud s licenčními podmínkami souhlasíte, klikněte na tlačítko **souhlasím**.</span><span class="sxs-lookup"><span data-stu-id="229e0-113">If you agree to the license terms, click **I Accept**.</span></span>

5. <span data-ttu-id="229e0-114">Nejnovější sestavení VINR bude stažena a přidány do projektu.</span><span class="sxs-lookup"><span data-stu-id="229e0-114">The latest VINR assemblies will be downloaded and added to your project.</span></span>

## <a name="use-the-package-manager-console"></a><span data-ttu-id="229e0-115">Použití konzole Správce balíčků</span><span class="sxs-lookup"><span data-stu-id="229e0-115">Use the Package Manager Console</span></span>

1. <span data-ttu-id="229e0-116">V sadě Visual Studio, klikněte na tlačítko **nástroje** > **Správce balíčků NuGet** > **Konzola správce balíčků**.</span><span class="sxs-lookup"><span data-stu-id="229e0-116">In Visual Studio, click **Tools** > **NuGet Package Manager** > **Package Manager Console**.</span></span>

2. <span data-ttu-id="229e0-117">**Konzola správce balíčků** se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="229e0-117">The **Package Manager Console** appears.</span></span> <span data-ttu-id="229e0-118">Zadejte následující text a stiskněte klávesu **Enter**:</span><span class="sxs-lookup"><span data-stu-id="229e0-118">Enter the following text and press **Enter**:</span></span>

    ```powershell
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry
    ```

3. <span data-ttu-id="229e0-119">Nejnovější sestavení VINR bude stažena a přidány do projektu.</span><span class="sxs-lookup"><span data-stu-id="229e0-119">The latest VINR assemblies will be downloaded and added to your project.</span></span>
