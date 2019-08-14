---
title: 'Postupy: Sestavení aplikace ASP.NET pracující s deklaracemi s ověřováním pomocí formulářů'
ms.date: 03/30/2017
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
author: BrucePerlerMS
ms.openlocfilehash: 75db96a621d7863ef445efb24814111b34da6960
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971839"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a><span data-ttu-id="2fc9e-102">Postupy: Sestavení aplikace ASP.NET pracující s deklaracemi s ověřováním pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="2fc9e-102">How To: Build Claims-Aware ASP.NET Application Using Forms-Based Authentication</span></span>

## <a name="applies-to"></a><span data-ttu-id="2fc9e-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="2fc9e-103">Applies To</span></span>

- <span data-ttu-id="2fc9e-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="2fc9e-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>

- <span data-ttu-id="2fc9e-105">Webové formuláře ASP.NET®</span><span class="sxs-lookup"><span data-stu-id="2fc9e-105">ASP.NET® Web Forms</span></span>

## <a name="summary"></a><span data-ttu-id="2fc9e-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="2fc9e-106">Summary</span></span>

<span data-ttu-id="2fc9e-107">V tomto postupu najdete podrobné postupy pro vytváření jednoduchých webových formulářů ASP.NET pracujících s deklaracemi, které používají ověřování pomocí formulářů.</span><span class="sxs-lookup"><span data-stu-id="2fc9e-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Forms authentication.</span></span> <span data-ttu-id="2fc9e-108">Poskytuje také pokyny k otestování aplikace za účelem ověření, že se deklarace identity zobrazí, když se uživatel přihlásí pomocí ověřování pomocí formulářů.</span><span class="sxs-lookup"><span data-stu-id="2fc9e-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in with Forms authentication.</span></span>

## <a name="contents"></a><span data-ttu-id="2fc9e-109">Obsah</span><span class="sxs-lookup"><span data-stu-id="2fc9e-109">Contents</span></span>

- <span data-ttu-id="2fc9e-110">Cíle</span><span class="sxs-lookup"><span data-stu-id="2fc9e-110">Objectives</span></span>

- <span data-ttu-id="2fc9e-111">Přehled</span><span class="sxs-lookup"><span data-stu-id="2fc9e-111">Overview</span></span>

- <span data-ttu-id="2fc9e-112">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="2fc9e-112">Summary of Steps</span></span>

- <span data-ttu-id="2fc9e-113">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2fc9e-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

- <span data-ttu-id="2fc9e-114">Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="2fc9e-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>

- <span data-ttu-id="2fc9e-115">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="2fc9e-115">Step 3 – Test Your Solution</span></span>

## <a name="objectives"></a><span data-ttu-id="2fc9e-116">Cíle</span><span class="sxs-lookup"><span data-stu-id="2fc9e-116">Objectives</span></span>

- <span data-ttu-id="2fc9e-117">Konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="2fc9e-117">Configure an ASP.NET Web Forms application for claims using Forms authentication</span></span>

- <span data-ttu-id="2fc9e-118">Otestujte aplikaci webových formulářů ASP.NET, abyste viděli, jestli správně funguje.</span><span class="sxs-lookup"><span data-stu-id="2fc9e-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>

## <a name="overview"></a><span data-ttu-id="2fc9e-119">Přehled</span><span class="sxs-lookup"><span data-stu-id="2fc9e-119">Overview</span></span>

<span data-ttu-id="2fc9e-120">V rozhraní .NET 4,5 se WIF a jeho autorizace na základě deklarace identity zahrnovala jako nedílnou součást rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2fc9e-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="2fc9e-121">Pokud jste dřív potřebovali deklarace identity od uživatele ASP.NET, museli jste nainstalovat WIF a pak přetypování rozhraní na hlavní objekty, jako jsou `Thread.CurrentPrincipal` nebo `HttpContext.Current.User`.</span><span class="sxs-lookup"><span data-stu-id="2fc9e-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="2fc9e-122">Nyní jsou deklarace identity automaticky obsluhovány těmito objekty zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2fc9e-122">Now, claims are served automatically by these Principal objects.</span></span>

<span data-ttu-id="2fc9e-123">Ověřování pomocí formulářů vyvolalo zařazení do WIF v rozhraní .NET 4,5, protože všichni uživatelé ověření pomocí formulářů mají automaticky přidružené deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="2fc9e-123">Forms authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Forms automatically have claims associated with them.</span></span> <span data-ttu-id="2fc9e-124">Tyto deklarace můžete hned začít používat v aplikaci ASP.NET, která používá ověřování pomocí formulářů, jak ukazuje tento postup.</span><span class="sxs-lookup"><span data-stu-id="2fc9e-124">You can begin using these claims immediately in an ASP.NET application that uses Forms authentication, as this How-To demonstrates.</span></span>

## <a name="summary-of-steps"></a><span data-ttu-id="2fc9e-125">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="2fc9e-125">Summary of Steps</span></span>

- <span data-ttu-id="2fc9e-126">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2fc9e-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

- <span data-ttu-id="2fc9e-127">Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="2fc9e-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>

- <span data-ttu-id="2fc9e-128">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="2fc9e-128">Step 3 – Test Your Solution</span></span>

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="2fc9e-129">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2fc9e-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

<span data-ttu-id="2fc9e-130">V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2fc9e-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>

### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="2fc9e-131">Vytvoření jednoduché aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2fc9e-131">To create a simple ASP.NET application</span></span>

1. <span data-ttu-id="2fc9e-132">Spusťte Visual Studio a klikněte na **soubor**, **Nový**a pak na **projekt**.</span><span class="sxs-lookup"><span data-stu-id="2fc9e-132">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>

2. <span data-ttu-id="2fc9e-133">V okně **Nový projekt** klikněte na **ASP.NET webová Formulářová aplikace**.</span><span class="sxs-lookup"><span data-stu-id="2fc9e-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>

3. <span data-ttu-id="2fc9e-134">Do **název**zadejte `TestApp` a stiskněte **OK**.</span><span class="sxs-lookup"><span data-stu-id="2fc9e-134">In **Name**, enter `TestApp` and press **OK**.</span></span>

## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="2fc9e-135">Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="2fc9e-135">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>

<span data-ttu-id="2fc9e-136">V tomto kroku přidáte položku konfigurace do konfiguračního souboru *Web. config* a upravíte soubor *Default. aspx* pro zobrazení informací o deklaracích identity pro účet.</span><span class="sxs-lookup"><span data-stu-id="2fc9e-136">In this step you will add a configuration entry to the *Web.config* configuration file and edit the *Default.aspx* file to display claims information for an account.</span></span>

### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a><span data-ttu-id="2fc9e-137">Konfigurace aplikace ASP.NET pro deklarace identity pomocí ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="2fc9e-137">To configure ASP.NET application for claims using Forms authentication</span></span>

1. <span data-ttu-id="2fc9e-138">Ve *výchozím souboru. aspx* nahraďte existující značky následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="2fc9e-138">In the *Default.aspx* file, replace the existing markup with the following:</span></span>

    ```aspx
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>

    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">
        <p>
            This page displays the claims associated with a Forms authenticated user.
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

    <span data-ttu-id="2fc9e-139">Tento krok přidá ovládací prvek GridView na stránku *Default. aspx* , která bude naplněna deklaracemi načtenými z ověřování pomocí formulářů.</span><span class="sxs-lookup"><span data-stu-id="2fc9e-139">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Forms authentication.</span></span>

2. <span data-ttu-id="2fc9e-140">Uložte soubor *Default. aspx* a pak otevřete jeho soubor kódu na pozadí s názvem *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="2fc9e-140">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="2fc9e-141">Existující kód nahraďte následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="2fc9e-141">Replace the existing code with the following:</span></span>

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

                if (claimsPrincipal != null)
                {
                    this.ClaimsGridView.DataSource = claimsPrincipal.Claims;
                    this.ClaimsGridView.DataBind();
                }
            }
        }
    }
    ```

    <span data-ttu-id="2fc9e-142">Výše uvedený kód zobrazí deklarace identity týkající se ověřeného uživatele, včetně uživatelů identifikovaných ověřováním pomocí formulářů.</span><span class="sxs-lookup"><span data-stu-id="2fc9e-142">The above code will display claims about an authenticated user, including users identified by Forms authentication.</span></span>

## <a name="step-3--test-your-solution"></a><span data-ttu-id="2fc9e-143">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="2fc9e-143">Step 3 – Test Your Solution</span></span>

<span data-ttu-id="2fc9e-144">V tomto kroku otestujete svou aplikaci webových formulářů v ASP.NET a ověříte, že se při přihlášení uživatele k ověřování pomocí formulářů zobrazí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="2fc9e-144">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>

### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="2fc9e-145">Testování aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="2fc9e-145">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>

1. <span data-ttu-id="2fc9e-146">Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2fc9e-146">Press **F5** to build and run the application.</span></span> <span data-ttu-id="2fc9e-147">Měli byste se dodávat s *Default. aspx*, který má v pravém horním rohu stránky **Registry** a **přihlašovací** odkazy.</span><span class="sxs-lookup"><span data-stu-id="2fc9e-147">You should be presented with *Default.aspx*, which has **Register** and **Log in** links in the top right of the page.</span></span> <span data-ttu-id="2fc9e-148">Klikněte na **zaregistrovat**.</span><span class="sxs-lookup"><span data-stu-id="2fc9e-148">Click **Register**.</span></span>

2. <span data-ttu-id="2fc9e-149">Na stránce **zaregistrovat** vytvořte uživatelský účet a pak klikněte na **zaregistrovat**.</span><span class="sxs-lookup"><span data-stu-id="2fc9e-149">On the **Register** page, create a user account, and then click **Register**.</span></span> <span data-ttu-id="2fc9e-150">Váš účet se vytvoří pomocí ověřování pomocí formulářů a automaticky se přihlásíte.</span><span class="sxs-lookup"><span data-stu-id="2fc9e-150">Your account will be created using Forms authentication, and you will be automatically signed in.</span></span>

3. <span data-ttu-id="2fc9e-151">Po přesměrování na domovskou stránku byste měli vidět tabulku pod hlavičkou **deklarací identity** , která zahrnuje informace o vystaviteli, **OriginalIssuer**, **typu**, **hodnotě**a **ValueType** deklarací identity. zohledňují.</span><span class="sxs-lookup"><span data-stu-id="2fc9e-151">After you have been redirected to the home page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span>
