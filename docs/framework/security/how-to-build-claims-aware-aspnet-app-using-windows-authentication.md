---
title: 'Postupy: Sestavení aplikace ASP.NET pracující s deklaracemi s ověřováním Windows'
ms.date: 03/30/2017
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
author: BrucePerlerMS
ms.openlocfilehash: 34d6c7916b3035e9896b1dd9d7c7d8b3e7b0fcfc
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041001"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a><span data-ttu-id="8c5e6-102">Postupy: Sestavení aplikace ASP.NET pracující s deklaracemi s ověřováním Windows</span><span class="sxs-lookup"><span data-stu-id="8c5e6-102">How To: Build Claims-Aware ASP.NET Application Using Windows Authentication</span></span>

## <a name="applies-to"></a><span data-ttu-id="8c5e6-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="8c5e6-103">Applies To</span></span>

- <span data-ttu-id="8c5e6-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="8c5e6-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>

- <span data-ttu-id="8c5e6-105">Webové formuláře ASP.NET®</span><span class="sxs-lookup"><span data-stu-id="8c5e6-105">ASP.NET® Web Forms</span></span>

## <a name="summary"></a><span data-ttu-id="8c5e6-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="8c5e6-106">Summary</span></span>

<span data-ttu-id="8c5e6-107">V tomto postupu najdete podrobné postupy pro vytváření jednoduchých webových formulářů ASP.NET pracujících s deklaracemi, které používají ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Windows authentication.</span></span> <span data-ttu-id="8c5e6-108">Poskytuje také pokyny k otestování aplikace za účelem ověření, že se deklarace identity zobrazí, když se uživatel přihlásí pomocí ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in using Windows authentication.</span></span>

## <a name="contents"></a><span data-ttu-id="8c5e6-109">Obsah</span><span class="sxs-lookup"><span data-stu-id="8c5e6-109">Contents</span></span>

- <span data-ttu-id="8c5e6-110">Cíle</span><span class="sxs-lookup"><span data-stu-id="8c5e6-110">Objectives</span></span>

- <span data-ttu-id="8c5e6-111">Přehled</span><span class="sxs-lookup"><span data-stu-id="8c5e6-111">Overview</span></span>

- <span data-ttu-id="8c5e6-112">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="8c5e6-112">Summary of Steps</span></span>

- <span data-ttu-id="8c5e6-113">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8c5e6-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

- <span data-ttu-id="8c5e6-114">Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="8c5e6-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>

- <span data-ttu-id="8c5e6-115">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="8c5e6-115">Step 3 – Test Your Solution</span></span>

## <a name="objectives"></a><span data-ttu-id="8c5e6-116">Cíle</span><span class="sxs-lookup"><span data-stu-id="8c5e6-116">Objectives</span></span>

- <span data-ttu-id="8c5e6-117">Konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="8c5e6-117">Configure an ASP.NET Web Forms application for claims using Windows authentication</span></span>

- <span data-ttu-id="8c5e6-118">Otestujte aplikaci webových formulářů ASP.NET, abyste viděli, jestli správně funguje.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>

## <a name="overview"></a><span data-ttu-id="8c5e6-119">Přehled</span><span class="sxs-lookup"><span data-stu-id="8c5e6-119">Overview</span></span>

<span data-ttu-id="8c5e6-120">V rozhraní .NET 4,5 se WIF a jeho autorizace na základě deklarace identity zahrnovala jako nedílnou součást rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="8c5e6-121">Pokud jste dřív potřebovali deklarace identity od uživatele ASP.NET, museli jste nainstalovat WIF a pak přetypování rozhraní na hlavní objekty, jako jsou `Thread.CurrentPrincipal` nebo `HttpContext.Current.User`.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="8c5e6-122">Nyní jsou deklarace identity automaticky obsluhovány těmito objekty zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-122">Now, claims are served automatically by these Principal objects.</span></span>

<span data-ttu-id="8c5e6-123">Ověřování systému Windows přináší WIF zařazení do .NET 4,5, protože pro všechny uživatele ověřené pověřeními systému Windows jsou automaticky přidruženy deklarace.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-123">Windows authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Windows credentials automatically have claims associated with them.</span></span> <span data-ttu-id="8c5e6-124">Tyto deklarace můžete hned začít používat v aplikaci ASP.NET, která používá ověřování systému Windows, jak ukazuje tento postup.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-124">You can begin using these claims immediately in an ASP.NET application that uses Windows authentication, as this How-To demonstrates.</span></span>

## <a name="summary-of-steps"></a><span data-ttu-id="8c5e6-125">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="8c5e6-125">Summary of Steps</span></span>

- <span data-ttu-id="8c5e6-126">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8c5e6-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

- <span data-ttu-id="8c5e6-127">Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="8c5e6-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>

- <span data-ttu-id="8c5e6-128">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="8c5e6-128">Step 3 – Test Your Solution</span></span>

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="8c5e6-129">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8c5e6-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

<span data-ttu-id="8c5e6-130">V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>

### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="8c5e6-131">Vytvoření jednoduché aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8c5e6-131">To create a simple ASP.NET application</span></span>

1. <span data-ttu-id="8c5e6-132">Spusťte Visual Studio, klikněte na **soubor**, **Nový**a pak na **projekt**.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-132">Start Visual Studio, then click **File**, **New**, and then **Project**.</span></span>

2. <span data-ttu-id="8c5e6-133">V okně **Nový projekt** klikněte na **ASP.NET webová Formulářová aplikace**.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>

3. <span data-ttu-id="8c5e6-134">Do **název**zadejte `TestApp` a stiskněte **OK**.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-134">In **Name**, enter `TestApp` and press **OK**.</span></span>

4. <span data-ttu-id="8c5e6-135">Po vytvoření projektu **TestApp** klikněte na něj v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-135">After the **TestApp** project has been created, click on it in **Solution Explorer**.</span></span> <span data-ttu-id="8c5e6-136">Vlastnosti projektu se zobrazí v podokně **vlastnosti** níže **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-136">The project’s properties will appear in the **Properties** pane below **Solution Explorer**.</span></span> <span data-ttu-id="8c5e6-137">Nastavte vlastnost **ověřování systému Windows** na **povoleno**.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-137">Set the **Windows Authentication** property to **Enabled**.</span></span>

    > [!WARNING]
    > <span data-ttu-id="8c5e6-138">Ověřování systému Windows je ve výchozím nastavení v nových aplikacích ASP.NET zakázané, takže je musíte ručně povolit.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-138">Windows authentication is disabled by default in new ASP.NET applications, so you must manually enable it.</span></span>

## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="8c5e6-139">Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="8c5e6-139">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>

<span data-ttu-id="8c5e6-140">V tomto kroku přidáte položku konfigurace do konfiguračního souboru *Web. config* a upravíte soubor *Default. aspx* pro zobrazení informací o deklaracích identity pro účet.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-140">In this step you will add a configuration entry to the *Web.config* configuration file and modify the *Default.aspx* file to display claims information for an account.</span></span>

### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a><span data-ttu-id="8c5e6-141">Konfigurace aplikace ASP.NET pro deklarace identity pomocí ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="8c5e6-141">To configure ASP.NET application for claims using Windows authentication</span></span>

1. <span data-ttu-id="8c5e6-142">V souboru *Default. aspx* projektu **TestApp** nahraďte existující značky následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="8c5e6-142">In the **TestApp** project’s *Default.aspx* file, replace the existing markup with the following:</span></span>

    ```aspx-csharp
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>

    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">
        <p>
            This page displays the claims associated with a Windows authenticated user.
        </p>
        <h3>Your Claims</h3>
        <p>
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">
                <AlternatingRowStyle BackColor="White" />
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />
            </asp:GridView>
        </p>
    </asp:Content>
    ```

    <span data-ttu-id="8c5e6-143">Tento krok přidá ovládací prvek GridView na stránku *Default. aspx* , která bude naplněna deklaracemi načtenými z ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-143">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Windows authentication.</span></span>

2. <span data-ttu-id="8c5e6-144">Uložte soubor *Default. aspx* a pak otevřete jeho soubor kódu na pozadí s názvem *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-144">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="8c5e6-145">Existující kód nahraďte následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="8c5e6-145">Replace the existing code with the following:</span></span>

    ```csharp
    using System;
    using System.Web.UI;
    using System.Security.Claims;

    namespace TestApp
    {
        public partial class _Default : Page
        {
            protected void Page_Load(object sender, EventArgs e)
            {
                ClaimsPrincipal claimsPrincipal = Page.User as ClaimsPrincipal;
                this.ClaimsGridView.DataSource = claimsPrincipal.Claims;
                this.ClaimsGridView.DataBind();
            }
        }
    }
    ```

    <span data-ttu-id="8c5e6-146">Výše uvedený kód zobrazí deklarace identity týkající se ověřeného uživatele.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-146">The above code will display claims about an authenticated user.</span></span>

3. <span data-ttu-id="8c5e6-147">Chcete-li změnit typ ověřování aplikace, upravte  **\<blok Authentication >** v oddílu  **\<System. Web >** v kořenovém souboru *Web. config* projektu tak, aby obsahoval pouze následující Položka konfigurace:</span><span class="sxs-lookup"><span data-stu-id="8c5e6-147">To change the application’s authentication type, modify the **\<authentication>** block in the **\<system.web>** section of the project’s root *Web.config* file so that it only includes the following configuration entry:</span></span>

    ```xml
    <authentication mode="Windows" />
    ```

4. <span data-ttu-id="8c5e6-148">Nakonec upravte  **\<blok autorizačního >** v  **\<oddílu System. Web >** stejného souboru *Web. config* pro vynucení ověřování:</span><span class="sxs-lookup"><span data-stu-id="8c5e6-148">Finally, modify the **\<authorization>** block in the **\<system.web>** section of the same *Web.config* file to force authentication:</span></span>

    ```xml
    <authorization>
        <deny users="?" />
    </authorization>
    ```

## <a name="step-3--test-your-solution"></a><span data-ttu-id="8c5e6-149">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="8c5e6-149">Step 3 – Test Your Solution</span></span>

<span data-ttu-id="8c5e6-150">V tomto kroku otestujete svou aplikaci webových formulářů v ASP.NET a ověříte, že se při přihlášení uživatele s ověřováním systému Windows zobrazí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-150">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Windows authentication.</span></span>

### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="8c5e6-151">Testování aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="8c5e6-151">To test your ASP.NET Web Forms application for claims using Windows authentication</span></span>

1. <span data-ttu-id="8c5e6-152">Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-152">Press **F5** to build and run the application.</span></span> <span data-ttu-id="8c5e6-153">Měla by se vám zobrazit stránka *Default. aspx*a název vašeho účtu systému Windows (včetně názvu domény) by se měl v pravém horním rohu stránky zobrazovat jako ověřený uživatel.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-153">You should be presented with *Default.aspx*, and your Windows account name (including domain name) should already appear as the authenticated user in the top right of the page.</span></span> <span data-ttu-id="8c5e6-154">Obsah stránky by měl obsahovat tabulku vyplněnou deklaracemi, které jste načetli z účtu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="8c5e6-154">The page’s content should include a table filled with claims retrieved from your Windows account.</span></span>
