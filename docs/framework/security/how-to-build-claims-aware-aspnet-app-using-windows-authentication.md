---
title: 'Postupy: Sestavení aplikace ASP.NET pracující s deklaracemi identity pomocí ověřování Windows'
ms.date: 03/30/2017
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
author: BrucePerlerMS
ms.openlocfilehash: 2c7877c452c729b30029cad1a8e17600f3dc9661
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47112423"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a><span data-ttu-id="79381-102">Postupy: Sestavení aplikace ASP.NET pracující s deklaracemi identity pomocí ověřování Windows</span><span class="sxs-lookup"><span data-stu-id="79381-102">How To: Build Claims-Aware ASP.NET Application Using Windows Authentication</span></span>
## <a name="applies-to"></a><span data-ttu-id="79381-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="79381-103">Applies To</span></span>  
  
-   <span data-ttu-id="79381-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="79381-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="79381-105">ASP.NET® webových formulářů</span><span class="sxs-lookup"><span data-stu-id="79381-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="79381-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="79381-106">Summary</span></span>  
 <span data-ttu-id="79381-107">Tento návod obsahuje podrobně popisuje postupy pro vytvoření jednoduché aplikace webových formulářů ASP.NET s deklaracemi identity, která používá ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="79381-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Windows authentication.</span></span> <span data-ttu-id="79381-108">Také poskytuje pokyny k otestování aplikace ověřit, že jsou předkládány deklarace, když se uživatel přihlásí pomocí ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="79381-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in using Windows authentication.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="79381-109">Obsah</span><span class="sxs-lookup"><span data-stu-id="79381-109">Contents</span></span>  
  
-   <span data-ttu-id="79381-110">Cíle</span><span class="sxs-lookup"><span data-stu-id="79381-110">Objectives</span></span>  
  
-   <span data-ttu-id="79381-111">Přehled</span><span class="sxs-lookup"><span data-stu-id="79381-111">Overview</span></span>  
  
-   <span data-ttu-id="79381-112">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="79381-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="79381-113">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET</span><span class="sxs-lookup"><span data-stu-id="79381-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="79381-114">Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování Windows</span><span class="sxs-lookup"><span data-stu-id="79381-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
  
-   <span data-ttu-id="79381-115">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="79381-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="79381-116">Cíle</span><span class="sxs-lookup"><span data-stu-id="79381-116">Objectives</span></span>  
  
-   <span data-ttu-id="79381-117">Konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování Windows</span><span class="sxs-lookup"><span data-stu-id="79381-117">Configure an ASP.NET Web Forms application for claims using Windows authentication</span></span>  
  
-   <span data-ttu-id="79381-118">Otestovat aplikaci webových formulářů ASP.NET, abyste viděli, zda pracuje správně</span><span class="sxs-lookup"><span data-stu-id="79381-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="79381-119">Přehled</span><span class="sxs-lookup"><span data-stu-id="79381-119">Overview</span></span>  
 <span data-ttu-id="79381-120">V rozhraní .NET 4.5 WIF a jeho autorizace na základě rolí byly zahrnuty jako součást rozhraní Framework.</span><span class="sxs-lookup"><span data-stu-id="79381-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="79381-121">Dříve, pokud byste chtěli deklarací z uživatele s ASP.NET, jste k instalaci technologie WIF, a potom přetypování rozhraní instančnímu objektu objekty, jako `Thread.CurrentPrincipal` nebo `HttpContext.Current.User`.</span><span class="sxs-lookup"><span data-stu-id="79381-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="79381-122">Nyní deklarace identity jsou obsluhovány automaticky tyto hlavní objekty.</span><span class="sxs-lookup"><span data-stu-id="79381-122">Now, claims are served automatically by these Principal objects.</span></span>  
  
 <span data-ttu-id="79381-123">Ověřování Windows využívaly technologie WIF pro zahrnutí v rozhraní .NET 4.5, protože mají všichni uživatelé automaticky ověřit přihlašovací údaje Windows k nim má přiřazené deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="79381-123">Windows authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Windows credentials automatically have claims associated with them.</span></span> <span data-ttu-id="79381-124">Můžete začít používat tyto deklarace okamžitě v aplikaci technologie ASP.NET, která používá ověřování Windows, jak ukazuje tento návod.</span><span class="sxs-lookup"><span data-stu-id="79381-124">You can begin using these claims immediately in an ASP.NET application that uses Windows authentication, as this How-To demonstrates.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="79381-125">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="79381-125">Summary of Steps</span></span>  
  
-   <span data-ttu-id="79381-126">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET</span><span class="sxs-lookup"><span data-stu-id="79381-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="79381-127">Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování Windows</span><span class="sxs-lookup"><span data-stu-id="79381-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
  
-   <span data-ttu-id="79381-128">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="79381-128">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="79381-129">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET</span><span class="sxs-lookup"><span data-stu-id="79381-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="79381-130">V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="79381-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="79381-131">Chcete-li vytvořit jednoduchou aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="79381-131">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="79381-132">Spusťte sadu Visual Studio a pak klikněte na **souboru**, **nový**a potom **projektu**.</span><span class="sxs-lookup"><span data-stu-id="79381-132">Start Visual Studio, then click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="79381-133">V **nový projekt** okna, klikněte na tlačítko **aplikace webových formulářů ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="79381-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="79381-134">V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.</span><span class="sxs-lookup"><span data-stu-id="79381-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4.  <span data-ttu-id="79381-135">Po **TestApp** projekt je vytvořený, klikněte na něj v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="79381-135">After the **TestApp** project has been created, click on it in **Solution Explorer**.</span></span> <span data-ttu-id="79381-136">Vlastnosti projektu se zobrazí v **vlastnosti** podokno, níže **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="79381-136">The project’s properties will appear in the **Properties** pane below **Solution Explorer**.</span></span> <span data-ttu-id="79381-137">Nastavte **ověřování Windows** vlastnost **povoleno**.</span><span class="sxs-lookup"><span data-stu-id="79381-137">Set the **Windows Authentication** property to **Enabled**.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="79381-138">Ve výchozím nastavení nové aplikace ASP.NET je zakázáno ověřování Windows, takže je nutné ručně povolit.</span><span class="sxs-lookup"><span data-stu-id="79381-138">Windows authentication is disabled by default in new ASP.NET applications, so you must manually enable it.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="79381-139">Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování Windows</span><span class="sxs-lookup"><span data-stu-id="79381-139">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
 <span data-ttu-id="79381-140">V tomto kroku přidáte položku konfigurace pro *Web.config* konfigurační soubor a upravit *Default.aspx* deklarací souboru chcete zobrazit informace o účtu.</span><span class="sxs-lookup"><span data-stu-id="79381-140">In this step you will add a configuration entry to the *Web.config* configuration file and modify the *Default.aspx* file to display claims information for an account.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a><span data-ttu-id="79381-141">Ke konfiguraci aplikace ASP.NET pro deklarace identity pomocí ověřování Windows</span><span class="sxs-lookup"><span data-stu-id="79381-141">To configure ASP.NET application for claims using Windows authentication</span></span>  
  
1.  <span data-ttu-id="79381-142">V **TestApp** projektu *Default.aspx* souboru, nahraďte existující kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="79381-142">In the **TestApp** project’s *Default.aspx* file, replace the existing markup with the following:</span></span>  
  
    ```  
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
  
     <span data-ttu-id="79381-143">Tento krok přidá ovládací prvek GridView pro vaše *Default.aspx* načíst stránku, která naplní se deklarace identity z ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="79381-143">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Windows authentication.</span></span>  
  
2.  <span data-ttu-id="79381-144">Uložit *Default.aspx* souboru a pak otevřete jeho použití modelu code-behind soubor s názvem *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="79381-144">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="79381-145">Nahraďte stávající kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="79381-145">Replace the existing code with the following:</span></span>  
  
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
  
     <span data-ttu-id="79381-146">Výše uvedený kód zobrazí deklarace pro ověřeného uživatele.</span><span class="sxs-lookup"><span data-stu-id="79381-146">The above code will display claims about an authenticated user.</span></span>  
  
3.  <span data-ttu-id="79381-147">Chcete-li změnit typ ověřování vaší aplikace, změnit  **\<ověřování >** blokovat  **\<system.web >** části kořen projektu  *Soubor Web.config* souboru tak, že obsahují pouze následující položku konfigurace:</span><span class="sxs-lookup"><span data-stu-id="79381-147">To change the application’s authentication type, modify the **\<authentication>** block in the **\<system.web>** section of the project’s root *Web.config* file so that it only includes the following configuration entry:</span></span>  
  
    ```xml  
    <authentication mode="Windows" />  
    ```  
  
4.  <span data-ttu-id="79381-148">Nakonec upravte  **\<autorizace >** blokovat  **\<system.web >** části stejného *Web.config* souboru k vynucení ověřování:</span><span class="sxs-lookup"><span data-stu-id="79381-148">Finally, modify the **\<authorization>** block in the **\<system.web>** section of the same *Web.config* file to force authentication:</span></span>  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    ```  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="79381-149">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="79381-149">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="79381-150">V tomto kroku otestujte aplikaci webových formulářů ASP.NET a ověřte, že jsou předkládány deklarace, když se uživatel přihlásí pomocí ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="79381-150">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Windows authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="79381-151">K testování aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování Windows</span><span class="sxs-lookup"><span data-stu-id="79381-151">To test your ASP.NET Web Forms application for claims using Windows authentication</span></span>  
  
1.  <span data-ttu-id="79381-152">Stisknutím klávesy **F5** sestavíte a spustíte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="79381-152">Press **F5** to build and run the application.</span></span> <span data-ttu-id="79381-153">Mělo by se zobrazit s *Default.aspx*, a název účtu Windows (včetně názvu domény) už mají zobrazit jako ověřený uživatel v horní části stránky.</span><span class="sxs-lookup"><span data-stu-id="79381-153">You should be presented with *Default.aspx*, and your Windows account name (including domain name) should already appear as the authenticated user in the top right of the page.</span></span> <span data-ttu-id="79381-154">Na stránce obsahu by měl obsahovat tabulku se deklarace identity načíst z vašeho účtu Windows.</span><span class="sxs-lookup"><span data-stu-id="79381-154">The page’s content should include a table filled with claims retrieved from your Windows account.</span></span>
