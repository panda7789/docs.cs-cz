---
title: "Postupy: Transformovat příchozí deklarace identity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 1f736554cd50a5ca2bd45dfab2f41ba672601f29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-transform-incoming-claims"></a><span data-ttu-id="25ca5-102">Postupy: Transformovat příchozí deklarace identity</span><span class="sxs-lookup"><span data-stu-id="25ca5-102">How To: Transform Incoming Claims</span></span>
## <a name="applies-to"></a><span data-ttu-id="25ca5-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="25ca5-103">Applies To</span></span>  
  
-   <span data-ttu-id="25ca5-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="25ca5-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="25ca5-105">ASP.NET® webových formulářů</span><span class="sxs-lookup"><span data-stu-id="25ca5-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="25ca5-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="25ca5-106">Summary</span></span>  
 <span data-ttu-id="25ca5-107">Tento postup obsahuje podrobné podrobné postupy pro vytvoření jednoduché aplikace webových formulářů ASP.NET pracujícím s deklaracemi a transformaci příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="25ca5-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application and transforming incoming claims.</span></span> <span data-ttu-id="25ca5-108">Také poskytuje pokyny k testování aplikace k ověření, že transformované deklarace identity jsou uvedené při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="25ca5-108">It also provides instructions for how to test the application to verify that transformed claims are presented when the application is run.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="25ca5-109">Obsah</span><span class="sxs-lookup"><span data-stu-id="25ca5-109">Contents</span></span>  
  
-   <span data-ttu-id="25ca5-110">Cíle</span><span class="sxs-lookup"><span data-stu-id="25ca5-110">Objectives</span></span>  
  
-   <span data-ttu-id="25ca5-111">Přehled</span><span class="sxs-lookup"><span data-stu-id="25ca5-111">Overview</span></span>  
  
-   <span data-ttu-id="25ca5-112">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="25ca5-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="25ca5-113">Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="25ca5-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="25ca5-114">Krok 2 – implementace deklarace identity pomocí vlastní ClaimsAuthenticationManager transformace</span><span class="sxs-lookup"><span data-stu-id="25ca5-114">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
  
-   <span data-ttu-id="25ca5-115">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="25ca5-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="25ca5-116">Cíle</span><span class="sxs-lookup"><span data-stu-id="25ca5-116">Objectives</span></span>  
  
-   <span data-ttu-id="25ca5-117">Konfigurace aplikace webových formulářů ASP.NET pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="25ca5-117">Configure an ASP.NET Web Forms application for claims-based authentication</span></span>  
  
-   <span data-ttu-id="25ca5-118">Transformovat příchozí deklarace identity přidáním deklaraci identity role správce</span><span class="sxs-lookup"><span data-stu-id="25ca5-118">Transform incoming claims by adding an Administrator role claim</span></span>  
  
-   <span data-ttu-id="25ca5-119">Testování aplikace webových formulářů ASP.NET, abyste viděli, zda pracuje správně</span><span class="sxs-lookup"><span data-stu-id="25ca5-119">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="25ca5-120">Přehled</span><span class="sxs-lookup"><span data-stu-id="25ca5-120">Overview</span></span>  
 <span data-ttu-id="25ca5-121">WIF zpřístupní třídy s názvem <xref:System.Security.Claims.ClaimsAuthenticationManager> umožňující uživatelům úpravám deklarací identity, než se mají zobrazovat předávající stranu aplikaci.</span><span class="sxs-lookup"><span data-stu-id="25ca5-121">WIF exposes a class named <xref:System.Security.Claims.ClaimsAuthenticationManager> that enables users to modify claims before they are presented to a relying party (RP) application.</span></span> <span data-ttu-id="25ca5-122"><xref:System.Security.Claims.ClaimsAuthenticationManager> Je užitečné pro oddělené oblasti zájmu mezi ověřování a základního kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="25ca5-122">The <xref:System.Security.Claims.ClaimsAuthenticationManager> is useful for separation of concerns between authentication and the underlying application code.</span></span> <span data-ttu-id="25ca5-123">Následující příklad ukazuje, jak přidat roli do deklarací identity ve příchozí <xref:System.Security.Claims.ClaimsPrincipal> který může být vyžadován na základě RP.</span><span class="sxs-lookup"><span data-stu-id="25ca5-123">The example below demonstrates how to add a role to the claims in the incoming <xref:System.Security.Claims.ClaimsPrincipal> that may be required by the RP.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="25ca5-124">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="25ca5-124">Summary of Steps</span></span>  
  
-   <span data-ttu-id="25ca5-125">Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="25ca5-125">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="25ca5-126">Krok 2 – implementace deklarace identity pomocí vlastní ClaimsAuthenticationManager transformace</span><span class="sxs-lookup"><span data-stu-id="25ca5-126">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
  
-   <span data-ttu-id="25ca5-127">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="25ca5-127">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="25ca5-128">Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="25ca5-128">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="25ca5-129">V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="25ca5-129">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="25ca5-130">Chcete-li vytvořit jednoduchou aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="25ca5-130">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="25ca5-131">Spusťte sadu Visual Studio jako správce v režimu se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="25ca5-131">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2.  <span data-ttu-id="25ca5-132">V sadě Visual Studio, klikněte na tlačítko **soubor**, klikněte na tlačítko **nový**a potom klikněte na **projektu**.</span><span class="sxs-lookup"><span data-stu-id="25ca5-132">In Visual Studio, click **File**, click **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="25ca5-133">V **nový projekt** okně klikněte na tlačítko **aplikaci webových formulářů ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="25ca5-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
4.  <span data-ttu-id="25ca5-134">V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.</span><span class="sxs-lookup"><span data-stu-id="25ca5-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
5.  <span data-ttu-id="25ca5-135">Klikněte pravým tlačítkem myši **TestApp** projektu v části **Průzkumníku řešení**, pak vyberte **identit a přístupu**.</span><span class="sxs-lookup"><span data-stu-id="25ca5-135">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
6.  <span data-ttu-id="25ca5-136">**Identit a přístupu** se zobrazí v okně.</span><span class="sxs-lookup"><span data-stu-id="25ca5-136">The **Identity and Access** window appears.</span></span> <span data-ttu-id="25ca5-137">V části **zprostředkovatelé**, vyberte **testování vaší aplikace pomocí místní služby tokenů zabezpečení vývoj**, pak klikněte na tlačítko **použít**.</span><span class="sxs-lookup"><span data-stu-id="25ca5-137">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
7.  <span data-ttu-id="25ca5-138">V *Default.aspx* souboru, nahraďte existující kód následující a pak soubor uložte:</span><span class="sxs-lookup"><span data-stu-id="25ca5-138">In the *Default.aspx* file, replace the existing markup with the following, then save the file:</span></span>  
  
    ```  
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
  
8.  <span data-ttu-id="25ca5-139">Otevření souboru kódu s názvem *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="25ca5-139">Open the code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="25ca5-140">Nahraďte stávající kód následující příkaz, pak uložte soubor:</span><span class="sxs-lookup"><span data-stu-id="25ca5-140">Replace the existing code with the following, then save the file:</span></span>  
  
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
  
## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="25ca5-141">Krok 2 – implementace deklarace identity pomocí vlastní ClaimsAuthenticationManager transformace</span><span class="sxs-lookup"><span data-stu-id="25ca5-141">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
 <span data-ttu-id="25ca5-142">V tomto kroku se přepíše výchozí funkce v <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy pro přidání role správce do příchozí objekt zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="25ca5-142">In this step you will override default functionality in the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to add an Administrator role to the incoming Principal.</span></span>  
  
#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="25ca5-143">K implementaci pomocí vlastní ClaimsAuthenticationManager transformace deklarací identity</span><span class="sxs-lookup"><span data-stu-id="25ca5-143">To implement claims transformation using a custom ClaimsAuthenticationManager</span></span>  
  
1.  <span data-ttu-id="25ca5-144">V sadě Visual Studio, klikněte pravým tlačítkem myši na řešení, klikněte na tlačítko **přidat**a potom klikněte na **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="25ca5-144">In Visual Studio, right-click the on the solution, click **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="25ca5-145">V **přidat nový projekt** vyberte **knihovny tříd** z **Visual C#** šablony seznamu, zadejte `ClaimsTransformation`a potom stiskněte klávesu **OK**.</span><span class="sxs-lookup"><span data-stu-id="25ca5-145">In the **Add New Project** window, select **Class Library** from the **Visual C#** templates list, enter `ClaimsTransformation`, and then press **OK**.</span></span> <span data-ttu-id="25ca5-146">Vytvoří se nový projekt ve složce řešení.</span><span class="sxs-lookup"><span data-stu-id="25ca5-146">The new project will be created in your solution folder.</span></span>  
  
3.  <span data-ttu-id="25ca5-147">Klikněte pravým tlačítkem na **odkazy** pod **ClaimsTransformation** projektu a pak klikněte na **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="25ca5-147">Right-click on **References** under the **ClaimsTransformation** project, and then click **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="25ca5-148">V **správce odkazů** vyberte **System.IdentityModel**a potom klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="25ca5-148">In the **Reference Manager** window, select **System.IdentityModel**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="25ca5-149">Otevřete **Class1.cs**, nebo pokud neexistuje, klikněte pravým tlačítkem na **ClaimsTransformation**, klikněte na tlačítko **přidat**, pak klikněte na tlačítko **třídy...**</span><span class="sxs-lookup"><span data-stu-id="25ca5-149">Open **Class1.cs**, or if it doesn’t exist, right-click **ClaimsTransformation**, click **Add**, then click **Class…**</span></span>  
  
6.  <span data-ttu-id="25ca5-150">Přidejte následující direktivy using do souboru kódu:</span><span class="sxs-lookup"><span data-stu-id="25ca5-150">Add the following using directives to the code file:</span></span>  
  
    ```csharp  
    using System.Security.Claims;  
    using System.Security.Principal;  
    ```  
  
7.  <span data-ttu-id="25ca5-151">Přidejte následující třídy a metody do souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="25ca5-151">Add the following class and method in the code file.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="25ca5-152">Následující kód je pro demonstrační účely pouze; Ujistěte se, abyste ověřili určený oprávnění v produkčním kódu.</span><span class="sxs-lookup"><span data-stu-id="25ca5-152">The following code is for demonstration purposes only; make sure that you verify your intended permissions in production code.</span></span>  
  
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
  
8.  <span data-ttu-id="25ca5-153">Uložte tento soubor a sestavení **ClaimsTransformation** projektu.</span><span class="sxs-lookup"><span data-stu-id="25ca5-153">Save the file and build the **ClaimsTransformation** project.</span></span>  
  
9. <span data-ttu-id="25ca5-154">Ve vašem **TestApp** projekt ASP.NET, klikněte pravým tlačítkem na odkazy a pak klikněte na tlačítko **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="25ca5-154">In your **TestApp** ASP.NET project, right-click on References, and then click **Add Reference**.</span></span>  
  
10. <span data-ttu-id="25ca5-155">V **správce odkazů** vyberte **řešení** v levé nabídce vyberte **ClaimsTransformation** z vyplněná možnosti a pak klikněte na tlačítko  **OK**.</span><span class="sxs-lookup"><span data-stu-id="25ca5-155">In the **Reference Manager** window, select **Solution** from the left menu, select **ClaimsTransformation** from the populated options, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="25ca5-156">V kořenovém **Web.config** souboru, přejděte na  **\<system.identityModel >** položku.</span><span class="sxs-lookup"><span data-stu-id="25ca5-156">In the root **Web.config** file, navigate to the **\<system.identityModel>** entry.</span></span> <span data-ttu-id="25ca5-157">V rámci  **\<identityConfiguration >** elementy, přidejte následující řádek a soubor uložte:</span><span class="sxs-lookup"><span data-stu-id="25ca5-157">Within the **\<identityConfiguration>** elements, add the following line and save the file:</span></span>  
  
    ```xml  
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />  
    ```  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="25ca5-158">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="25ca5-158">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="25ca5-159">V tomto kroku testování vaší aplikace webových formulářů ASP.NET a ověřte, že deklarace identity jsou uvedené Pokud se uživatel přihlásí pomocí ověřování pomocí formulářů.</span><span class="sxs-lookup"><span data-stu-id="25ca5-159">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="25ca5-160">K testování aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="25ca5-160">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="25ca5-161">Stiskněte klávesu **F5** sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="25ca5-161">Press **F5** to build and run the application.</span></span> <span data-ttu-id="25ca5-162">By se měla zobrazit s *Default.aspx*.</span><span class="sxs-lookup"><span data-stu-id="25ca5-162">You should be presented with *Default.aspx*.</span></span>  
  
2.  <span data-ttu-id="25ca5-163">Na *Default.aspx* stránky, měli byste vidět tabulku pod **vaše deklarace identity** záhlaví, která zahrnuje **vystavitele**, **OriginalIssuer**, **Typ**, **hodnotu**, a **ValueType** deklarací informace o vašem účtu.</span><span class="sxs-lookup"><span data-stu-id="25ca5-163">On the *Default.aspx* page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span> <span data-ttu-id="25ca5-164">Poslední řádek by měla zobrazit následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="25ca5-164">The last row should be presented in the following way:</span></span>  
  
    ||||||  
    |-|-|-|-|-|  
    |<span data-ttu-id="25ca5-165">MÍSTNÍ ÚŘAD</span><span class="sxs-lookup"><span data-stu-id="25ca5-165">LOCAL AUTHORITY</span></span>|<span data-ttu-id="25ca5-166">MÍSTNÍ ÚŘAD</span><span class="sxs-lookup"><span data-stu-id="25ca5-166">LOCAL AUTHORITY</span></span>|<span data-ttu-id="25ca5-167">http://schemas.microsoft.com/ws/2008/06/identity/claims/role</span><span class="sxs-lookup"><span data-stu-id="25ca5-167">http://schemas.microsoft.com/ws/2008/06/identity/claims/role</span></span>|<span data-ttu-id="25ca5-168">Správce</span><span class="sxs-lookup"><span data-stu-id="25ca5-168">Admin</span></span>|<span data-ttu-id="25ca5-169">http://www.w3.org/2001/XMLSchema#String</span><span class="sxs-lookup"><span data-stu-id="25ca5-169">http://www.w3.org/2001/XMLSchema#string</span></span>|
