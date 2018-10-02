---
title: 'Postupy: Sestavení aplikace ASP.NET pracující s deklaracemi identity pomocí ověřování pomocí formulářů'
ms.date: 03/30/2017
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
author: BrucePerlerMS
ms.openlocfilehash: 8dab5cfbcf14707699e6672017f5f80db232f01d
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48025529"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a><span data-ttu-id="6b611-102">Postupy: Sestavení aplikace ASP.NET pracující s deklaracemi identity pomocí ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="6b611-102">How To: Build Claims-Aware ASP.NET Application Using Forms-Based Authentication</span></span>
## <a name="applies-to"></a><span data-ttu-id="6b611-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="6b611-103">Applies To</span></span>  
  
-   <span data-ttu-id="6b611-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="6b611-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="6b611-105">ASP.NET® webových formulářů</span><span class="sxs-lookup"><span data-stu-id="6b611-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="6b611-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="6b611-106">Summary</span></span>  
 <span data-ttu-id="6b611-107">Tento návod obsahuje podrobně popisuje postupy pro vytvoření jednoduché aplikace webových formulářů ASP.NET s deklaracemi identity, která používá ověřování pomocí formulářů.</span><span class="sxs-lookup"><span data-stu-id="6b611-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Forms authentication.</span></span> <span data-ttu-id="6b611-108">Také poskytuje pokyny k otestování aplikace ověřit, že jsou předkládány deklarace, když se uživatel přihlásí pomocí ověřování pomocí formulářů.</span><span class="sxs-lookup"><span data-stu-id="6b611-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="6b611-109">Obsah</span><span class="sxs-lookup"><span data-stu-id="6b611-109">Contents</span></span>  
  
-   <span data-ttu-id="6b611-110">Cíle</span><span class="sxs-lookup"><span data-stu-id="6b611-110">Objectives</span></span>  
  
-   <span data-ttu-id="6b611-111">Přehled</span><span class="sxs-lookup"><span data-stu-id="6b611-111">Overview</span></span>  
  
-   <span data-ttu-id="6b611-112">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="6b611-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="6b611-113">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6b611-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="6b611-114">Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity, ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="6b611-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
  
-   <span data-ttu-id="6b611-115">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="6b611-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="6b611-116">Cíle</span><span class="sxs-lookup"><span data-stu-id="6b611-116">Objectives</span></span>  
  
-   <span data-ttu-id="6b611-117">Konfigurace aplikace webových formulářů ASP.NET pro deklarace identity, ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="6b611-117">Configure an ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
-   <span data-ttu-id="6b611-118">Otestovat aplikaci webových formulářů ASP.NET, abyste viděli, zda pracuje správně</span><span class="sxs-lookup"><span data-stu-id="6b611-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="6b611-119">Přehled</span><span class="sxs-lookup"><span data-stu-id="6b611-119">Overview</span></span>  
 <span data-ttu-id="6b611-120">V rozhraní .NET 4.5 WIF a jeho autorizace na základě rolí byly zahrnuty jako součást rozhraní Framework.</span><span class="sxs-lookup"><span data-stu-id="6b611-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="6b611-121">Dříve, pokud byste chtěli deklarací z uživatele s ASP.NET, jste k instalaci technologie WIF, a potom přetypování rozhraní instančnímu objektu objekty, jako `Thread.CurrentPrincipal` nebo `HttpContext.Current.User`.</span><span class="sxs-lookup"><span data-stu-id="6b611-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="6b611-122">Nyní deklarace identity jsou obsluhovány automaticky tyto hlavní objekty.</span><span class="sxs-lookup"><span data-stu-id="6b611-122">Now, claims are served automatically by these Principal objects.</span></span>  
  
 <span data-ttu-id="6b611-123">Ověřování pomocí formulářů využívaly technologie WIF pro zahrnutí v rozhraní .NET 4.5, protože všichni uživatelé automaticky ověřované formuláře mají deklarace identity k nim má přiřazené.</span><span class="sxs-lookup"><span data-stu-id="6b611-123">Forms authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Forms automatically have claims associated with them.</span></span> <span data-ttu-id="6b611-124">Můžete začít používat tyto deklarace okamžitě v aplikaci technologie ASP.NET, která používá ověřování pomocí formulářů, jak ukazuje tento návod.</span><span class="sxs-lookup"><span data-stu-id="6b611-124">You can begin using these claims immediately in an ASP.NET application that uses Forms authentication, as this How-To demonstrates.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="6b611-125">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="6b611-125">Summary of Steps</span></span>  
  
-   <span data-ttu-id="6b611-126">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6b611-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="6b611-127">Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity, ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="6b611-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
  
-   <span data-ttu-id="6b611-128">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="6b611-128">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="6b611-129">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6b611-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="6b611-130">V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6b611-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="6b611-131">Chcete-li vytvořit jednoduchou aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6b611-131">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="6b611-132">Spusťte sadu Visual Studio a klikněte na tlačítko **souboru**, **nový**a potom **projektu**.</span><span class="sxs-lookup"><span data-stu-id="6b611-132">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="6b611-133">V **nový projekt** okna, klikněte na tlačítko **aplikace webových formulářů ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="6b611-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="6b611-134">V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.</span><span class="sxs-lookup"><span data-stu-id="6b611-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="6b611-135">Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity, ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="6b611-135">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
 <span data-ttu-id="6b611-136">V tomto kroku přidáte položku konfigurace do *Web.config* konfigurační soubor a upravit *Default.aspx* deklarací souboru chcete zobrazit informace o účtu.</span><span class="sxs-lookup"><span data-stu-id="6b611-136">In this step you will add a configuration entry to the *Web.config* configuration file and edit the *Default.aspx* file to display claims information for an account.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a><span data-ttu-id="6b611-137">Ke konfiguraci aplikace ASP.NET pro deklarace identity, ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="6b611-137">To configure ASP.NET application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="6b611-138">V *Default.aspx* souboru, nahraďte existující kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="6b611-138">In the *Default.aspx* file, replace the existing markup with the following:</span></span>  
  
    ```  
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
  
     <span data-ttu-id="6b611-139">Tento krok přidá ovládací prvek GridView pro vaše *Default.aspx* načíst stránku, která naplní se deklarace identity z ověřování pomocí formulářů.</span><span class="sxs-lookup"><span data-stu-id="6b611-139">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Forms authentication.</span></span>  
  
2.  <span data-ttu-id="6b611-140">Uložit *Default.aspx* souboru a pak otevřete jeho použití modelu code-behind soubor s názvem *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="6b611-140">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="6b611-141">Nahraďte stávající kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="6b611-141">Replace the existing code with the following:</span></span>  
  
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
  
     <span data-ttu-id="6b611-142">Výše uvedený kód zobrazí deklarace pro ověřeného uživatele, včetně uživatelů určených ověřování pomocí formulářů.</span><span class="sxs-lookup"><span data-stu-id="6b611-142">The above code will display claims about an authenticated user, including users identified by Forms authentication.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="6b611-143">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="6b611-143">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="6b611-144">V tomto kroku otestujte aplikaci webových formulářů ASP.NET a ověřte, že jsou předkládány deklarace, když se uživatel přihlásí pomocí ověřování pomocí formulářů.</span><span class="sxs-lookup"><span data-stu-id="6b611-144">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="6b611-145">K testování aplikace webových formulářů ASP.NET pro deklarace identity, ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="6b611-145">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="6b611-146">Stisknutím klávesy **F5** sestavíte a spustíte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6b611-146">Press **F5** to build and run the application.</span></span> <span data-ttu-id="6b611-147">By se měla zobrazit s *Default.aspx*, který má **zaregistrovat** a **přihlášení** odkazy v horní části stránky.</span><span class="sxs-lookup"><span data-stu-id="6b611-147">You should be presented with *Default.aspx*, which has **Register** and **Log in** links in the top right of the page.</span></span> <span data-ttu-id="6b611-148">Klikněte na tlačítko **zaregistrovat**.</span><span class="sxs-lookup"><span data-stu-id="6b611-148">Click **Register**.</span></span>  
  
2.  <span data-ttu-id="6b611-149">Na **zaregistrovat** stránce, vytvořte uživatelský účet a potom klikněte na **zaregistrovat**.</span><span class="sxs-lookup"><span data-stu-id="6b611-149">On the **Register** page, create a user account, and then click **Register**.</span></span> <span data-ttu-id="6b611-150">Váš účet se vytvoří pomocí ověřování pomocí formulářů a budete automaticky přihlášení.</span><span class="sxs-lookup"><span data-stu-id="6b611-150">Your account will be created using Forms authentication, and you will be automatically signed in.</span></span>  
  
3.  <span data-ttu-id="6b611-151">Poté, co byli jste přesměrováni na domovskou stránku, měli byste vidět tabulku pod **Your deklarací** nadpis, který obsahuje **vystavitele**, **OriginalIssuer**, **Typ**, **hodnotu**, a **ValueType** deklarací informace o vašem účtu.</span><span class="sxs-lookup"><span data-stu-id="6b611-151">After you have been redirected to the home page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span>
