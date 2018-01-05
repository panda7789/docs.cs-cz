---
title: "Postupy: Vytvoření aplikace ASP.NET deklaracemi pomocí ověřování systému Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 1f623cceec04e45d168269379e1af6bdeb573af0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a><span data-ttu-id="346a7-102">Postupy: Vytvoření aplikace ASP.NET deklaracemi pomocí ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="346a7-102">How To: Build Claims-Aware ASP.NET Application Using Windows Authentication</span></span>
## <a name="applies-to"></a><span data-ttu-id="346a7-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="346a7-103">Applies To</span></span>  
  
-   <span data-ttu-id="346a7-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="346a7-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="346a7-105">ASP.NET® webových formulářů</span><span class="sxs-lookup"><span data-stu-id="346a7-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="346a7-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="346a7-106">Summary</span></span>  
 <span data-ttu-id="346a7-107">Tento postup obsahuje podrobné podrobné postupy pro vytvoření jednoduché aplikace webových formulářů ASP.NET deklaracemi identity, která používá ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="346a7-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Windows authentication.</span></span> <span data-ttu-id="346a7-108">Také poskytuje pokyny k testování aplikace pro kontrolu, aby byly poskytovány deklarace identity, když se uživatel přihlásí pomocí ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="346a7-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in using Windows authentication.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="346a7-109">Obsah</span><span class="sxs-lookup"><span data-stu-id="346a7-109">Contents</span></span>  
  
-   <span data-ttu-id="346a7-110">Cíle</span><span class="sxs-lookup"><span data-stu-id="346a7-110">Objectives</span></span>  
  
-   <span data-ttu-id="346a7-111">Přehled</span><span class="sxs-lookup"><span data-stu-id="346a7-111">Overview</span></span>  
  
-   <span data-ttu-id="346a7-112">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="346a7-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="346a7-113">Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="346a7-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="346a7-114">Krok 2 – konfigurace aplikaci ASP.NET Web Forms pro deklarace identity pomocí ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="346a7-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
  
-   <span data-ttu-id="346a7-115">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="346a7-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="346a7-116">Cíle</span><span class="sxs-lookup"><span data-stu-id="346a7-116">Objectives</span></span>  
  
-   <span data-ttu-id="346a7-117">Konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="346a7-117">Configure an ASP.NET Web Forms application for claims using Windows authentication</span></span>  
  
-   <span data-ttu-id="346a7-118">Testování aplikace webových formulářů ASP.NET, abyste viděli, zda pracuje správně</span><span class="sxs-lookup"><span data-stu-id="346a7-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="346a7-119">Přehled</span><span class="sxs-lookup"><span data-stu-id="346a7-119">Overview</span></span>  
 <span data-ttu-id="346a7-120">V rozhraní .NET 4.5 WIF a její ověření na základě deklarace identity byly zahrnuty jako nedílné součásti rozhraní Framework.</span><span class="sxs-lookup"><span data-stu-id="346a7-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="346a7-121">Dříve, pokud byste chtěli deklarací z uživatele ASP.NET, bylo nutné instalovat WIF, a pak přetypování rozhraní k objektu zabezpečení objektů, jako `Thread.CurrentPrincipal` nebo `HttpContext.Current.User`.</span><span class="sxs-lookup"><span data-stu-id="346a7-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="346a7-122">Nyní deklarací identity zpracovává automaticky tyto hlavní objekty.</span><span class="sxs-lookup"><span data-stu-id="346a7-122">Now, claims are served automatically by these Principal objects.</span></span>  
  
 <span data-ttu-id="346a7-123">Ověřování systému Windows využívaly zahrnutí WIF je v rozhraní .NET 4.5, protože všichni uživatelé ověřit pověření systému Windows automaticky deklarace identity s nimi spojených.</span><span class="sxs-lookup"><span data-stu-id="346a7-123">Windows authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Windows credentials automatically have claims associated with them.</span></span> <span data-ttu-id="346a7-124">Můžete začít používat tyto deklarace okamžitě v aplikaci ASP.NET, která používá ověřování systému Windows, jak ukazuje tento postup.</span><span class="sxs-lookup"><span data-stu-id="346a7-124">You can begin using these claims immediately in an ASP.NET application that uses Windows authentication, as this How-To demonstrates.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="346a7-125">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="346a7-125">Summary of Steps</span></span>  
  
-   <span data-ttu-id="346a7-126">Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="346a7-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="346a7-127">Krok 2 – konfigurace aplikaci ASP.NET Web Forms pro deklarace identity pomocí ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="346a7-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
  
-   <span data-ttu-id="346a7-128">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="346a7-128">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="346a7-129">Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="346a7-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="346a7-130">V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="346a7-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="346a7-131">Chcete-li vytvořit jednoduchou aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="346a7-131">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="346a7-132">Spuštění sady Visual Studio a pak klikněte na **soubor**, **nový**a potom **projektu**.</span><span class="sxs-lookup"><span data-stu-id="346a7-132">Start Visual Studio, then click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="346a7-133">V **nový projekt** okně klikněte na tlačítko **aplikaci webových formulářů ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="346a7-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="346a7-134">V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.</span><span class="sxs-lookup"><span data-stu-id="346a7-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4.  <span data-ttu-id="346a7-135">Po **TestApp** vytvoření projektu, klikněte na jeho **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="346a7-135">After the **TestApp** project has been created, click on it in **Solution Explorer**.</span></span> <span data-ttu-id="346a7-136">Vlastnosti projektu se zobrazí v **vlastnosti** podokně níže **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="346a7-136">The project’s properties will appear in the **Properties** pane below **Solution Explorer**.</span></span> <span data-ttu-id="346a7-137">Nastavte **ověřování systému Windows** vlastnost **povoleno**.</span><span class="sxs-lookup"><span data-stu-id="346a7-137">Set the **Windows Authentication** property to **Enabled**.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="346a7-138">Ověřování systému Windows je zakázáno ve výchozím nastavení v nové aplikace ASP.NET, takže je nutné ručně povolit.</span><span class="sxs-lookup"><span data-stu-id="346a7-138">Windows authentication is disabled by default in new ASP.NET applications, so you must manually enable it.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="346a7-139">Krok 2 – konfigurace aplikaci ASP.NET Web Forms pro deklarace identity pomocí ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="346a7-139">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
 <span data-ttu-id="346a7-140">V tomto kroku přidáte položku konfigurace do *Web.config* konfigurace soubor a upravte *Default.aspx* deklarací soubor zobrazíte informace o účtu.</span><span class="sxs-lookup"><span data-stu-id="346a7-140">In this step you will add a configuration entry to the *Web.config* configuration file and modify the *Default.aspx* file to display claims information for an account.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a><span data-ttu-id="346a7-141">Ke konfiguraci aplikace ASP.NET pro deklarace identity pomocí ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="346a7-141">To configure ASP.NET application for claims using Windows authentication</span></span>  
  
1.  <span data-ttu-id="346a7-142">V **TestApp** projektu *Default.aspx* souboru, nahraďte existující kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="346a7-142">In the **TestApp** project’s *Default.aspx* file, replace the existing markup with the following:</span></span>  
  
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
  
     <span data-ttu-id="346a7-143">Tento krok přidává ovládacího prvku GridView k vaší *Default.aspx* stránky, který vyplní s deklaracemi identity načítají ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="346a7-143">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Windows authentication.</span></span>  
  
2.  <span data-ttu-id="346a7-144">Uložit *Default.aspx* souboru a pak otevřete jeho kódu soubor s názvem *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="346a7-144">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="346a7-145">Nahraďte stávající kód s následujícími službami:</span><span class="sxs-lookup"><span data-stu-id="346a7-145">Replace the existing code with the following:</span></span>  
  
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
  
     <span data-ttu-id="346a7-146">Ve výše uvedeném kódu se zobrazí deklarace identity o ověřeného uživatele.</span><span class="sxs-lookup"><span data-stu-id="346a7-146">The above code will display claims about an authenticated user.</span></span>  
  
3.  <span data-ttu-id="346a7-147">Chcete-li změnit typ ověřování aplikace, změnit  **\<ověřování >** blokovat  **\<system.web >** části projektu kořenových  *Soubor Web.config* souboru tak, aby zahrnovala pouze následující položku konfigurace:</span><span class="sxs-lookup"><span data-stu-id="346a7-147">To change the application’s authentication type, modify the **\<authentication>** block in the **\<system.web>** section of the project’s root *Web.config* file so that it only includes the following configuration entry:</span></span>  
  
    ```xml  
    <authentication mode="Windows" />  
    ```  
  
4.  <span data-ttu-id="346a7-148">Nakonec upravte  **\<autorizace >** blokovat  **\<system.web >** části stejné *Web.config* souboru k vynucení ověřování:</span><span class="sxs-lookup"><span data-stu-id="346a7-148">Finally, modify the **\<authorization>** block in the **\<system.web>** section of the same *Web.config* file to force authentication:</span></span>  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    ```  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="346a7-149">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="346a7-149">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="346a7-150">V tomto kroku testování vaší aplikace webových formulářů ASP.NET a ověřte, že deklarace identity uvádíme, pokud se uživatel přihlásí pomocí ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="346a7-150">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Windows authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="346a7-151">K testování aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="346a7-151">To test your ASP.NET Web Forms application for claims using Windows authentication</span></span>  
  
1.  <span data-ttu-id="346a7-152">Stiskněte klávesu **F5** sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="346a7-152">Press **F5** to build and run the application.</span></span> <span data-ttu-id="346a7-153">By se měla zobrazit s *Default.aspx*, a název účtu systému Windows (včetně názvu domény) mají již zobrazit jako ověřený uživatel v horní pravé části stránky.</span><span class="sxs-lookup"><span data-stu-id="346a7-153">You should be presented with *Default.aspx*, and your Windows account name (including domain name) should already appear as the authenticated user in the top right of the page.</span></span> <span data-ttu-id="346a7-154">Stránky obsahu by měly obsahovat tabulku vyplněnou deklarace identity načíst z vašeho účtu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="346a7-154">The page’s content should include a table filled with claims retrieved from your Windows account.</span></span>
