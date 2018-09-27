---
title: 'Postupy: Transformace příchozích deklarací identity'
ms.date: 03/30/2017
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
author: BrucePerlerMS
ms.openlocfilehash: 8673b4520d9727ae1aa78ef0bc9f435defb02598
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47235962"
---
# <a name="how-to-transform-incoming-claims"></a><span data-ttu-id="6afce-102">Postupy: Transformace příchozích deklarací identity</span><span class="sxs-lookup"><span data-stu-id="6afce-102">How To: Transform Incoming Claims</span></span>
## <a name="applies-to"></a><span data-ttu-id="6afce-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="6afce-103">Applies To</span></span>  
  
-   <span data-ttu-id="6afce-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="6afce-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="6afce-105">ASP.NET® webových formulářů</span><span class="sxs-lookup"><span data-stu-id="6afce-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="6afce-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="6afce-106">Summary</span></span>  
 <span data-ttu-id="6afce-107">Tento návod obsahuje podrobně popisuje postupy pro vytvoření jednoduché aplikace webových formulářů ASP.NET s deklaracemi identity a transformaci příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="6afce-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application and transforming incoming claims.</span></span> <span data-ttu-id="6afce-108">Také poskytuje pokyny k otestování aplikace ověřit, že jsou předkládány transformované deklarace při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="6afce-108">It also provides instructions for how to test the application to verify that transformed claims are presented when the application is run.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="6afce-109">Obsah</span><span class="sxs-lookup"><span data-stu-id="6afce-109">Contents</span></span>  
  
-   <span data-ttu-id="6afce-110">Cíle</span><span class="sxs-lookup"><span data-stu-id="6afce-110">Objectives</span></span>  
  
-   <span data-ttu-id="6afce-111">Přehled</span><span class="sxs-lookup"><span data-stu-id="6afce-111">Overview</span></span>  
  
-   <span data-ttu-id="6afce-112">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="6afce-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="6afce-113">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6afce-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="6afce-114">Krok 2 – implementace deklarací identity pomocí vlastní komponenty ClaimsAuthenticationManager transformace</span><span class="sxs-lookup"><span data-stu-id="6afce-114">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
  
-   <span data-ttu-id="6afce-115">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="6afce-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="6afce-116">Cíle</span><span class="sxs-lookup"><span data-stu-id="6afce-116">Objectives</span></span>  
  
-   <span data-ttu-id="6afce-117">Konfigurace aplikace webových formulářů ASP.NET pro ověřování nezaloženého na deklaracích</span><span class="sxs-lookup"><span data-stu-id="6afce-117">Configure an ASP.NET Web Forms application for claims-based authentication</span></span>  
  
-   <span data-ttu-id="6afce-118">Transformovat příchozí deklarace identity tak, že přidáte deklaraci identity správce rolí</span><span class="sxs-lookup"><span data-stu-id="6afce-118">Transform incoming claims by adding an Administrator role claim</span></span>  
  
-   <span data-ttu-id="6afce-119">Otestovat aplikaci webových formulářů ASP.NET, abyste viděli, zda pracuje správně</span><span class="sxs-lookup"><span data-stu-id="6afce-119">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="6afce-120">Přehled</span><span class="sxs-lookup"><span data-stu-id="6afce-120">Overview</span></span>  
 <span data-ttu-id="6afce-121">Technologie WIF zpřístupní třídu s názvem <xref:System.Security.Claims.ClaimsAuthenticationManager> , která umožňuje uživatelům změnit deklarace identity, předtím, než se zobrazí na aplikaci předávající stranu.</span><span class="sxs-lookup"><span data-stu-id="6afce-121">WIF exposes a class named <xref:System.Security.Claims.ClaimsAuthenticationManager> that enables users to modify claims before they are presented to a relying party (RP) application.</span></span> <span data-ttu-id="6afce-122"><xref:System.Security.Claims.ClaimsAuthenticationManager> Je užitečné pro oddělení oblastí zájmu mezi ověřování a základního kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="6afce-122">The <xref:System.Security.Claims.ClaimsAuthenticationManager> is useful for separation of concerns between authentication and the underlying application code.</span></span> <span data-ttu-id="6afce-123">Následující příklad ukazuje, jak přidat roli v příchozí deklarace identity <xref:System.Security.Claims.ClaimsPrincipal> , které můžou vyžadovat RP.</span><span class="sxs-lookup"><span data-stu-id="6afce-123">The example below demonstrates how to add a role to the claims in the incoming <xref:System.Security.Claims.ClaimsPrincipal> that may be required by the RP.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="6afce-124">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="6afce-124">Summary of Steps</span></span>  
  
-   <span data-ttu-id="6afce-125">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6afce-125">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="6afce-126">Krok 2 – implementace deklarací identity pomocí vlastní komponenty ClaimsAuthenticationManager transformace</span><span class="sxs-lookup"><span data-stu-id="6afce-126">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
  
-   <span data-ttu-id="6afce-127">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="6afce-127">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="6afce-128">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6afce-128">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="6afce-129">V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6afce-129">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="6afce-130">Chcete-li vytvořit jednoduchou aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6afce-130">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="6afce-131">Spusťte sadu Visual Studio jako správce v režimu se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="6afce-131">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2.  <span data-ttu-id="6afce-132">V sadě Visual Studio, klikněte na tlačítko **souboru**, klikněte na tlačítko **nový**a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="6afce-132">In Visual Studio, click **File**, click **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="6afce-133">V **nový projekt** okna, klikněte na tlačítko **aplikace webových formulářů ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="6afce-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
4.  <span data-ttu-id="6afce-134">V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.</span><span class="sxs-lookup"><span data-stu-id="6afce-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
5.  <span data-ttu-id="6afce-135">Klikněte pravým tlačítkem myši **TestApp** projektu v rámci **Průzkumníku řešení**a pak vyberte **identit a přístupu**.</span><span class="sxs-lookup"><span data-stu-id="6afce-135">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
6.  <span data-ttu-id="6afce-136">**Identit a přístupu** zobrazí se okno.</span><span class="sxs-lookup"><span data-stu-id="6afce-136">The **Identity and Access** window appears.</span></span> <span data-ttu-id="6afce-137">V části **poskytovatelé**vyberte **testování aplikace s místní službu STS pro vývoj**, pak klikněte na tlačítko **použít**.</span><span class="sxs-lookup"><span data-stu-id="6afce-137">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
7.  <span data-ttu-id="6afce-138">V *Default.aspx* souboru, nahraďte existující kód následujícím kódem a pak soubor uložte:</span><span class="sxs-lookup"><span data-stu-id="6afce-138">In the *Default.aspx* file, replace the existing markup with the following, then save the file:</span></span>  
  
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
  
8.  <span data-ttu-id="6afce-139">Otevřete soubor kódu na pozadí s názvem *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="6afce-139">Open the code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="6afce-140">Nahraďte stávající kód následujícím kódem a poté soubor uložte:</span><span class="sxs-lookup"><span data-stu-id="6afce-140">Replace the existing code with the following, then save the file:</span></span>  
  
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
  
## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="6afce-141">Krok 2 – implementace deklarací identity pomocí vlastní komponenty ClaimsAuthenticationManager transformace</span><span class="sxs-lookup"><span data-stu-id="6afce-141">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
 <span data-ttu-id="6afce-142">V tomto kroku se přepíše výchozí funkce v <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy přidat roli správce příchozí instančnímu objektu.</span><span class="sxs-lookup"><span data-stu-id="6afce-142">In this step you will override default functionality in the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to add an Administrator role to the incoming Principal.</span></span>  
  
#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="6afce-143">K implementaci transformace deklarací identity pomocí vlastní komponenty ClaimsAuthenticationManager</span><span class="sxs-lookup"><span data-stu-id="6afce-143">To implement claims transformation using a custom ClaimsAuthenticationManager</span></span>  
  
1.  <span data-ttu-id="6afce-144">V sadě Visual Studio, klikněte pravým tlačítkem myši na řešení, klikněte na tlačítko **přidat**a potom klikněte na **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="6afce-144">In Visual Studio, right-click the on the solution, click **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="6afce-145">V **přidat nový projekt** okně **knihovny tříd** z **Visual C#** šablony seznamu, zadejte `ClaimsTransformation`a potom stiskněte klávesu **OK**.</span><span class="sxs-lookup"><span data-stu-id="6afce-145">In the **Add New Project** window, select **Class Library** from the **Visual C#** templates list, enter `ClaimsTransformation`, and then press **OK**.</span></span> <span data-ttu-id="6afce-146">Vytvoří se nový projekt ve složce řešení.</span><span class="sxs-lookup"><span data-stu-id="6afce-146">The new project will be created in your solution folder.</span></span>  
  
3.  <span data-ttu-id="6afce-147">Klikněte pravým tlačítkem na **odkazy** pod **ClaimsTransformation** projektu a pak klikněte na tlačítko **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="6afce-147">Right-click on **References** under the **ClaimsTransformation** project, and then click **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="6afce-148">V **správce odkazů** okně **System.IdentityModel**a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="6afce-148">In the **Reference Manager** window, select **System.IdentityModel**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="6afce-149">Otevřít **Class1.cs**, nebo pokud neexistuje, klikněte pravým tlačítkem na **ClaimsTransformation**, klikněte na tlačítko **přidat**, pak klikněte na tlačítko **třídy...**</span><span class="sxs-lookup"><span data-stu-id="6afce-149">Open **Class1.cs**, or if it doesn’t exist, right-click **ClaimsTransformation**, click **Add**, then click **Class…**</span></span>  
  
6.  <span data-ttu-id="6afce-150">Přidejte následující direktivy using do souboru kódu:</span><span class="sxs-lookup"><span data-stu-id="6afce-150">Add the following using directives to the code file:</span></span>  
  
    ```csharp  
    using System.Security.Claims;  
    using System.Security.Principal;  
    ```  
  
7.  <span data-ttu-id="6afce-151">V souboru kódu přidejte následující třídy a metody.</span><span class="sxs-lookup"><span data-stu-id="6afce-151">Add the following class and method in the code file.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="6afce-152">Následující kód je pro demonstrační účely. Ujistěte se, že ověřte zamýšlené příslušná oprávnění v produkčním kódu.</span><span class="sxs-lookup"><span data-stu-id="6afce-152">The following code is for demonstration purposes only; make sure that you verify your intended permissions in production code.</span></span>  
  
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
  
8.  <span data-ttu-id="6afce-153">Uložte soubor a sestavení **ClaimsTransformation** projektu.</span><span class="sxs-lookup"><span data-stu-id="6afce-153">Save the file and build the **ClaimsTransformation** project.</span></span>  
  
9. <span data-ttu-id="6afce-154">Ve vaší **TestApp** projekt ASP.NET, klikněte pravým tlačítkem na odkazy a pak klikněte na tlačítko **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="6afce-154">In your **TestApp** ASP.NET project, right-click on References, and then click **Add Reference**.</span></span>  
  
10. <span data-ttu-id="6afce-155">V **správce odkazů** okně **řešení** v levé nabídce vyberte **ClaimsTransformation** mají údaj vyplněný možnosti a pak klikněte na  **OK**.</span><span class="sxs-lookup"><span data-stu-id="6afce-155">In the **Reference Manager** window, select **Solution** from the left menu, select **ClaimsTransformation** from the populated options, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="6afce-156">V kořenovém adresáři **Web.config** souboru, přejděte  **\<system.identityModel >** položka.</span><span class="sxs-lookup"><span data-stu-id="6afce-156">In the root **Web.config** file, navigate to the **\<system.identityModel>** entry.</span></span> <span data-ttu-id="6afce-157">V rámci  **\<identityConfiguration >** prvky, přidejte následující řádek a soubor uložte:</span><span class="sxs-lookup"><span data-stu-id="6afce-157">Within the **\<identityConfiguration>** elements, add the following line and save the file:</span></span>  
  
    ```xml  
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />  
    ```  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="6afce-158">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="6afce-158">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="6afce-159">V tomto kroku otestujte aplikaci webových formulářů ASP.NET a ověřte, že jsou předkládány deklarace, když se uživatel přihlásí pomocí ověřování pomocí formulářů.</span><span class="sxs-lookup"><span data-stu-id="6afce-159">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="6afce-160">K testování aplikace webových formulářů ASP.NET pro deklarace identity, ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="6afce-160">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="6afce-161">Stisknutím klávesy **F5** sestavíte a spustíte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6afce-161">Press **F5** to build and run the application.</span></span> <span data-ttu-id="6afce-162">Mělo by se zobrazit s *Default.aspx*.</span><span class="sxs-lookup"><span data-stu-id="6afce-162">You should be presented with *Default.aspx*.</span></span>  
  
2.  <span data-ttu-id="6afce-163">Na *Default.aspx* stránky, měli byste vidět tabulku pod **Your deklarací** nadpis, který obsahuje **vystavitele**, **OriginalIssuer**, **Typ**, **hodnotu**, a **ValueType** deklarací informace o vašem účtu.</span><span class="sxs-lookup"><span data-stu-id="6afce-163">On the *Default.aspx* page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span> <span data-ttu-id="6afce-164">Poslední řádek by se měla zobrazit následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="6afce-164">The last row should be presented in the following way:</span></span>  
  
    ||||||  
    |-|-|-|-|-|  
    |<span data-ttu-id="6afce-165">MÍSTNÍ AUTORITA</span><span class="sxs-lookup"><span data-stu-id="6afce-165">LOCAL AUTHORITY</span></span>|<span data-ttu-id="6afce-166">MÍSTNÍ AUTORITA</span><span class="sxs-lookup"><span data-stu-id="6afce-166">LOCAL AUTHORITY</span></span>|http://schemas.microsoft.com/ws/2008/06/identity/claims/role|<span data-ttu-id="6afce-167">Správce</span><span class="sxs-lookup"><span data-stu-id="6afce-167">Admin</span></span>|http://www.w3.org/2001/XMLSchema#string|
