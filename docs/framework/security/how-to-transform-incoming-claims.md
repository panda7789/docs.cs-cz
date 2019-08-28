---
title: 'Postupy: Transformace příchozích deklarací identit'
ms.date: 03/30/2017
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
author: BrucePerlerMS
ms.openlocfilehash: ce99b97007bf7608856345d6da87cd9e422d2266
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041481"
---
# <a name="how-to-transform-incoming-claims"></a><span data-ttu-id="e93ea-102">Postupy: Transformace příchozích deklarací identit</span><span class="sxs-lookup"><span data-stu-id="e93ea-102">How To: Transform Incoming Claims</span></span>

## <a name="applies-to"></a><span data-ttu-id="e93ea-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="e93ea-103">Applies To</span></span>

- <span data-ttu-id="e93ea-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="e93ea-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>

- <span data-ttu-id="e93ea-105">Webové formuláře ASP.NET®</span><span class="sxs-lookup"><span data-stu-id="e93ea-105">ASP.NET® Web Forms</span></span>

## <a name="summary"></a><span data-ttu-id="e93ea-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="e93ea-106">Summary</span></span>

<span data-ttu-id="e93ea-107">Tento postup poskytuje podrobné postupy pro vytváření jednoduchých webových formulářů ASP.NET pracujících s deklaracemi a transformují příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="e93ea-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application and transforming incoming claims.</span></span> <span data-ttu-id="e93ea-108">Poskytuje také pokyny k otestování aplikace za účelem ověření, zda jsou transformované deklarace uváděny při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="e93ea-108">It also provides instructions for how to test the application to verify that transformed claims are presented when the application is run.</span></span>

## <a name="contents"></a><span data-ttu-id="e93ea-109">Obsah</span><span class="sxs-lookup"><span data-stu-id="e93ea-109">Contents</span></span>

- <span data-ttu-id="e93ea-110">Cíle</span><span class="sxs-lookup"><span data-stu-id="e93ea-110">Objectives</span></span>

- <span data-ttu-id="e93ea-111">Přehled</span><span class="sxs-lookup"><span data-stu-id="e93ea-111">Overview</span></span>

- <span data-ttu-id="e93ea-112">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="e93ea-112">Summary of Steps</span></span>

- <span data-ttu-id="e93ea-113">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e93ea-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

- <span data-ttu-id="e93ea-114">Krok 2 – implementace transformace deklarací pomocí vlastního komponenty ClaimsAuthenticationManager</span><span class="sxs-lookup"><span data-stu-id="e93ea-114">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>

- <span data-ttu-id="e93ea-115">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="e93ea-115">Step 3 – Test Your Solution</span></span>

## <a name="objectives"></a><span data-ttu-id="e93ea-116">Cíle</span><span class="sxs-lookup"><span data-stu-id="e93ea-116">Objectives</span></span>

- <span data-ttu-id="e93ea-117">Konfigurace aplikace webových formulářů ASP.NET pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="e93ea-117">Configure an ASP.NET Web Forms application for claims-based authentication</span></span>

- <span data-ttu-id="e93ea-118">Transformace příchozích deklarací přidáním deklarace identity role správce</span><span class="sxs-lookup"><span data-stu-id="e93ea-118">Transform incoming claims by adding an Administrator role claim</span></span>

- <span data-ttu-id="e93ea-119">Otestujte aplikaci webových formulářů ASP.NET, abyste viděli, jestli správně funguje.</span><span class="sxs-lookup"><span data-stu-id="e93ea-119">Test the ASP.NET Web Forms application to see if it is working properly</span></span>

## <a name="overview"></a><span data-ttu-id="e93ea-120">Přehled</span><span class="sxs-lookup"><span data-stu-id="e93ea-120">Overview</span></span>

<span data-ttu-id="e93ea-121">WIF zpřístupňuje třídu s <xref:System.Security.Claims.ClaimsAuthenticationManager> názvem, která umožňuje uživatelům změnit deklarace identity předtím, než se předloží aplikaci předávající strany (RP).</span><span class="sxs-lookup"><span data-stu-id="e93ea-121">WIF exposes a class named <xref:System.Security.Claims.ClaimsAuthenticationManager> that enables users to modify claims before they are presented to a relying party (RP) application.</span></span> <span data-ttu-id="e93ea-122"><xref:System.Security.Claims.ClaimsAuthenticationManager> Je vhodný pro oddělení obav mezi ověřováním a podkladovým kódem aplikace.</span><span class="sxs-lookup"><span data-stu-id="e93ea-122">The <xref:System.Security.Claims.ClaimsAuthenticationManager> is useful for separation of concerns between authentication and the underlying application code.</span></span> <span data-ttu-id="e93ea-123">Následující příklad ukazuje, jak přidat roli k deklaracím v příchozím <xref:System.Security.Claims.ClaimsPrincipal> , které mohou být požadovány pro RP.</span><span class="sxs-lookup"><span data-stu-id="e93ea-123">The example below demonstrates how to add a role to the claims in the incoming <xref:System.Security.Claims.ClaimsPrincipal> that may be required by the RP.</span></span>

## <a name="summary-of-steps"></a><span data-ttu-id="e93ea-124">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="e93ea-124">Summary of Steps</span></span>

- <span data-ttu-id="e93ea-125">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e93ea-125">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

- <span data-ttu-id="e93ea-126">Krok 2 – implementace transformace deklarací pomocí vlastního komponenty ClaimsAuthenticationManager</span><span class="sxs-lookup"><span data-stu-id="e93ea-126">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>

- <span data-ttu-id="e93ea-127">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="e93ea-127">Step 3 – Test Your Solution</span></span>

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="e93ea-128">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e93ea-128">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

<span data-ttu-id="e93ea-129">V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e93ea-129">In this step, you will create a new ASP.NET Web Forms application.</span></span>

#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="e93ea-130">Vytvoření jednoduché aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e93ea-130">To create a simple ASP.NET application</span></span>

1. <span data-ttu-id="e93ea-131">Spusťte sadu Visual Studio jako správce v režimu se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="e93ea-131">Start Visual Studio in elevated mode as administrator.</span></span>

2. <span data-ttu-id="e93ea-132">V aplikaci Visual Studio klikněte na možnost **soubor**, klikněte na možnost **Nový**a poté klikněte na možnost **projekt**.</span><span class="sxs-lookup"><span data-stu-id="e93ea-132">In Visual Studio, click **File**, click **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="e93ea-133">V okně **Nový projekt** klikněte na **ASP.NET webová Formulářová aplikace**.</span><span class="sxs-lookup"><span data-stu-id="e93ea-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>

4. <span data-ttu-id="e93ea-134">Do **název**zadejte `TestApp` a stiskněte **OK**.</span><span class="sxs-lookup"><span data-stu-id="e93ea-134">In **Name**, enter `TestApp` and press **OK**.</span></span>

5. <span data-ttu-id="e93ea-135">V části **Průzkumník řešení**klikněte pravým tlačítkem na projekt **TestApp** a pak vyberte **Identita a přístup**.</span><span class="sxs-lookup"><span data-stu-id="e93ea-135">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>

6. <span data-ttu-id="e93ea-136">Zobrazí se okno **Identita a přístup** .</span><span class="sxs-lookup"><span data-stu-id="e93ea-136">The **Identity and Access** window appears.</span></span> <span data-ttu-id="e93ea-137">Včásti poskytovatelé vyberte **test aplikace pomocí místní služby tokenů pro vývoj**a pak klikněte na **použít**.</span><span class="sxs-lookup"><span data-stu-id="e93ea-137">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>

7. <span data-ttu-id="e93ea-138">Ve *výchozím souboru. aspx* nahraďte existující značky následujícím kódem a pak soubor uložte:</span><span class="sxs-lookup"><span data-stu-id="e93ea-138">In the *Default.aspx* file, replace the existing markup with the following, then save the file:</span></span>

    ```aspx-csharp
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>

    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">
          <h3>Your Claims</h3>
        <p>
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">
                <AlternatingRowStyle BackColor="White" />
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />
            </asp:GridView>
        </p>
    </asp:Content>
    ```

8. <span data-ttu-id="e93ea-139">Otevřete soubor kódu na pozadí s názvem *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="e93ea-139">Open the code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="e93ea-140">Nahraďte existující kód následujícím kódem a poté soubor uložte:</span><span class="sxs-lookup"><span data-stu-id="e93ea-140">Replace the existing code with the following, then save the file:</span></span>

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

## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="e93ea-141">Krok 2 – implementace transformace deklarací pomocí vlastního komponenty ClaimsAuthenticationManager</span><span class="sxs-lookup"><span data-stu-id="e93ea-141">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>

<span data-ttu-id="e93ea-142">V tomto kroku potlačíte výchozí funkce ve <xref:System.Security.Claims.ClaimsAuthenticationManager> třídě, aby se do objektu pro příchozího zabezpečení přidala role správce.</span><span class="sxs-lookup"><span data-stu-id="e93ea-142">In this step you will override default functionality in the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to add an Administrator role to the incoming Principal.</span></span>

#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="e93ea-143">Implementace transformace deklarací pomocí vlastního komponenty ClaimsAuthenticationManager</span><span class="sxs-lookup"><span data-stu-id="e93ea-143">To implement claims transformation using a custom ClaimsAuthenticationManager</span></span>

1. <span data-ttu-id="e93ea-144">V aplikaci Visual Studio klikněte pravým tlačítkem myši na řešení, klikněte na tlačítko **Přidat**a poté klikněte na možnost **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="e93ea-144">In Visual Studio, right-click the on the solution, click **Add**, and then click **New Project**.</span></span>

2. <span data-ttu-id="e93ea-145">V okně **Přidat nový projekt** vyberte v seznamu šablony **vizuálů C#**  položku `ClaimsTransformation` **Knihovna tříd** , zadejte a potom stiskněte **OK**.</span><span class="sxs-lookup"><span data-stu-id="e93ea-145">In the **Add New Project** window, select **Class Library** from the **Visual C#** templates list, enter `ClaimsTransformation`, and then press **OK**.</span></span> <span data-ttu-id="e93ea-146">Vytvoří se nový projekt ve složce řešení.</span><span class="sxs-lookup"><span data-stu-id="e93ea-146">The new project will be created in your solution folder.</span></span>

3. <span data-ttu-id="e93ea-147">Klikněte pravým tlačítkem na **odkazy** v rámci projektu **ClaimsTransformation** a pak klikněte na **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="e93ea-147">Right-click on **References** under the **ClaimsTransformation** project, and then click **Add Reference**.</span></span>

4. <span data-ttu-id="e93ea-148">V okně **Správce odkazů** vyberte **System. IdentityModel**a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="e93ea-148">In the **Reference Manager** window, select **System.IdentityModel**, and then click **OK**.</span></span>

5. <span data-ttu-id="e93ea-149">Otevřete **Class1.cs**, nebo pokud neexistuje, klikněte pravým tlačítkem myši na **ClaimsTransformation**, klikněte na **Přidat**a pak na **Třída...**</span><span class="sxs-lookup"><span data-stu-id="e93ea-149">Open **Class1.cs**, or if it doesn’t exist, right-click **ClaimsTransformation**, click **Add**, then click **Class…**</span></span>

6. <span data-ttu-id="e93ea-150">Do souboru kódu přidejte následující direktivy using:</span><span class="sxs-lookup"><span data-stu-id="e93ea-150">Add the following using directives to the code file:</span></span>

    ```csharp
    using System.Security.Claims;
    using System.Security.Principal;
    ```

7. <span data-ttu-id="e93ea-151">Do souboru kódu přidejte následující třídu a metodu.</span><span class="sxs-lookup"><span data-stu-id="e93ea-151">Add the following class and method in the code file.</span></span>

    > [!WARNING]
    > <span data-ttu-id="e93ea-152">Následující kód je určen pouze pro demonstrační účely; Ujistěte se, že jste ověřili zamýšlená oprávnění v produkčním kódu.</span><span class="sxs-lookup"><span data-stu-id="e93ea-152">The following code is for demonstration purposes only; make sure that you verify your intended permissions in production code.</span></span>

    ```csharp
    public class ClaimsTransformationModule : ClaimsAuthenticationManager
    {
        public override ClaimsPrincipal Authenticate(string resourceName, ClaimsPrincipal incomingPrincipal)
        {
            if (incomingPrincipal != null && incomingPrincipal.Identity.IsAuthenticated == true)
            {
               ((ClaimsIdentity)incomingPrincipal.Identity).AddClaim(new Claim(ClaimTypes.Role, "Admin"));
            }

            return incomingPrincipal;
        }
    }
    ```

8. <span data-ttu-id="e93ea-153">Uložte soubor a sestavte projekt **ClaimsTransformation** .</span><span class="sxs-lookup"><span data-stu-id="e93ea-153">Save the file and build the **ClaimsTransformation** project.</span></span>

9. <span data-ttu-id="e93ea-154">V projektu **TestApp** ASP.NET klikněte pravým tlačítkem na odkazy a pak klikněte na **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="e93ea-154">In your **TestApp** ASP.NET project, right-click on References, and then click **Add Reference**.</span></span>

10. <span data-ttu-id="e93ea-155">V okně **Správce odkazů** vyberte v nabídce vlevo možnost **řešení** , z naplněných možností vyberte **ClaimsTransformation** a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="e93ea-155">In the **Reference Manager** window, select **Solution** from the left menu, select **ClaimsTransformation** from the populated options, and then click **OK**.</span></span>

11. <span data-ttu-id="e93ea-156">V kořenovém souboru **Web. config** přejděte na  **\<položku System. IdentityModel >** .</span><span class="sxs-lookup"><span data-stu-id="e93ea-156">In the root **Web.config** file, navigate to the **\<system.identityModel>** entry.</span></span> <span data-ttu-id="e93ea-157">Do IdentityConfiguration  **>prvkypřidejtenásledujícířádekauložtesoubor:\<**</span><span class="sxs-lookup"><span data-stu-id="e93ea-157">Within the **\<identityConfiguration>** elements, add the following line and save the file:</span></span>

    ```xml
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />
    ```

## <a name="step-3--test-your-solution"></a><span data-ttu-id="e93ea-158">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="e93ea-158">Step 3 – Test Your Solution</span></span>

<span data-ttu-id="e93ea-159">V tomto kroku otestujete svou aplikaci webových formulářů v ASP.NET a ověříte, že se při přihlášení uživatele k ověřování pomocí formulářů zobrazí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="e93ea-159">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>

#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="e93ea-160">Testování aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="e93ea-160">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>

1. <span data-ttu-id="e93ea-161">Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e93ea-161">Press **F5** to build and run the application.</span></span> <span data-ttu-id="e93ea-162">Měla by se vám prezentovat *Default. aspx*.</span><span class="sxs-lookup"><span data-stu-id="e93ea-162">You should be presented with *Default.aspx*.</span></span>

2. <span data-ttu-id="e93ea-163">Na stránce *Default. aspx* by se měla zobrazit tabulka pod hlavičkou **deklarací identity** , která obsahuje informace ovystaviteli, **OriginalIssuer**, **typu**, **hodnotě**a **ValueType** deklarací identity vašeho účtu.</span><span class="sxs-lookup"><span data-stu-id="e93ea-163">On the *Default.aspx* page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span> <span data-ttu-id="e93ea-164">Poslední řádek by měl být prezentován následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e93ea-164">The last row should be presented in the following way:</span></span>

    ||||||
    |-|-|-|-|-|
    |<span data-ttu-id="e93ea-165">MÍSTNÍ AUTORITA</span><span class="sxs-lookup"><span data-stu-id="e93ea-165">LOCAL AUTHORITY</span></span>|<span data-ttu-id="e93ea-166">MÍSTNÍ AUTORITA</span><span class="sxs-lookup"><span data-stu-id="e93ea-166">LOCAL AUTHORITY</span></span>|`http://schemas.microsoft.com/ws/2008/06/identity/claims/role`|<span data-ttu-id="e93ea-167">Správce</span><span class="sxs-lookup"><span data-stu-id="e93ea-167">Admin</span></span>|<https://www.w3.org/2001/XMLSchema#string>|
