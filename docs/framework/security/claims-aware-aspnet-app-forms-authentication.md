---
title: "Postupy: Vytvoření aplikace ASP.NET deklaracemi pomocí ověřování pomocí formulářů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f4977a40d440ca45a3130fb1b06e0b286a2ab2f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a><span data-ttu-id="e74d5-102">Postupy: Vytvoření aplikace ASP.NET deklaracemi pomocí ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="e74d5-102">How To: Build Claims-Aware ASP.NET Application Using Forms-Based Authentication</span></span>
## <a name="applies-to"></a><span data-ttu-id="e74d5-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="e74d5-103">Applies To</span></span>  
  
-   <span data-ttu-id="e74d5-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="e74d5-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="e74d5-105">ASP.NET® webových formulářů</span><span class="sxs-lookup"><span data-stu-id="e74d5-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="e74d5-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="e74d5-106">Summary</span></span>  
 <span data-ttu-id="e74d5-107">Tento postup obsahuje podrobné podrobné postupy pro vytvoření jednoduché aplikace webových formulářů ASP.NET deklaracemi identity, která používá ověřování pomocí formulářů.</span><span class="sxs-lookup"><span data-stu-id="e74d5-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Forms authentication.</span></span> <span data-ttu-id="e74d5-108">Také poskytuje pokyny k testování aplikace k ověření, že deklarace identity jsou uvedené Pokud se uživatel přihlásí pomocí ověřování pomocí formulářů.</span><span class="sxs-lookup"><span data-stu-id="e74d5-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="e74d5-109">Obsah</span><span class="sxs-lookup"><span data-stu-id="e74d5-109">Contents</span></span>  
  
-   <span data-ttu-id="e74d5-110">Cíle</span><span class="sxs-lookup"><span data-stu-id="e74d5-110">Objectives</span></span>  
  
-   <span data-ttu-id="e74d5-111">Přehled</span><span class="sxs-lookup"><span data-stu-id="e74d5-111">Overview</span></span>  
  
-   <span data-ttu-id="e74d5-112">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="e74d5-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="e74d5-113">Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="e74d5-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="e74d5-114">Krok 2 – konfigurace aplikaci ASP.NET Web Forms pro deklarace identity pomocí ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="e74d5-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
  
-   <span data-ttu-id="e74d5-115">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="e74d5-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="e74d5-116">Cíle</span><span class="sxs-lookup"><span data-stu-id="e74d5-116">Objectives</span></span>  
  
-   <span data-ttu-id="e74d5-117">Konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="e74d5-117">Configure an ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
-   <span data-ttu-id="e74d5-118">Testování aplikace webových formulářů ASP.NET, abyste viděli, zda pracuje správně</span><span class="sxs-lookup"><span data-stu-id="e74d5-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="e74d5-119">Přehled</span><span class="sxs-lookup"><span data-stu-id="e74d5-119">Overview</span></span>  
 <span data-ttu-id="e74d5-120">V rozhraní .NET 4.5 WIF a její ověření na základě deklarace identity byly zahrnuty jako nedílné součásti rozhraní Framework.</span><span class="sxs-lookup"><span data-stu-id="e74d5-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="e74d5-121">Dříve, pokud byste chtěli deklarací z uživatele ASP.NET, bylo nutné instalovat WIF, a pak přetypování rozhraní k objektu zabezpečení objektů, jako `Thread.CurrentPrincipal` nebo `HttpContext.Current.User`.</span><span class="sxs-lookup"><span data-stu-id="e74d5-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="e74d5-122">Nyní deklarací identity zpracovává automaticky tyto hlavní objekty.</span><span class="sxs-lookup"><span data-stu-id="e74d5-122">Now, claims are served automatically by these Principal objects.</span></span>  
  
 <span data-ttu-id="e74d5-123">Ověřování pomocí formulářů využívaly zahrnutí WIF je v rozhraní .NET 4.5, protože všichni uživatelé ověřit Forms automaticky deklarace identity s nimi spojených.</span><span class="sxs-lookup"><span data-stu-id="e74d5-123">Forms authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Forms automatically have claims associated with them.</span></span> <span data-ttu-id="e74d5-124">Můžete začít používat tyto deklarace okamžitě v aplikaci ASP.NET, která používá ověřování pomocí formulářů, jak ukazuje tento postup.</span><span class="sxs-lookup"><span data-stu-id="e74d5-124">You can begin using these claims immediately in an ASP.NET application that uses Forms authentication, as this How-To demonstrates.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="e74d5-125">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="e74d5-125">Summary of Steps</span></span>  
  
-   <span data-ttu-id="e74d5-126">Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="e74d5-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="e74d5-127">Krok 2 – konfigurace aplikaci ASP.NET Web Forms pro deklarace identity pomocí ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="e74d5-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
  
-   <span data-ttu-id="e74d5-128">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="e74d5-128">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="e74d5-129">Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="e74d5-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="e74d5-130">V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e74d5-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="e74d5-131">Chcete-li vytvořit jednoduchou aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e74d5-131">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="e74d5-132">Spuštění sady Visual Studio a klikněte na tlačítko **soubor**, **nový**a potom **projektu**.</span><span class="sxs-lookup"><span data-stu-id="e74d5-132">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="e74d5-133">V **nový projekt** okně klikněte na tlačítko **aplikaci webových formulářů ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="e74d5-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="e74d5-134">V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.</span><span class="sxs-lookup"><span data-stu-id="e74d5-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="e74d5-135">Krok 2 – konfigurace aplikaci ASP.NET Web Forms pro deklarace identity pomocí ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="e74d5-135">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
 <span data-ttu-id="e74d5-136">V tomto kroku přidáte položku konfigurace do *Web.config* konfigurační soubor a upravit *Default.aspx* deklarací soubor zobrazíte informace o účtu.</span><span class="sxs-lookup"><span data-stu-id="e74d5-136">In this step you will add a configuration entry to the *Web.config* configuration file and edit the *Default.aspx* file to display claims information for an account.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a><span data-ttu-id="e74d5-137">Ke konfiguraci aplikace ASP.NET pro deklarace identity pomocí ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="e74d5-137">To configure ASP.NET application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="e74d5-138">V *Default.aspx* souboru, nahraďte existující kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="e74d5-138">In the *Default.aspx* file, replace the existing markup with the following:</span></span>  
  
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
  
     <span data-ttu-id="e74d5-139">Tento krok přidává ovládacího prvku GridView k vaší *Default.aspx* stránky, který vyplní s deklaracemi identity načítají ověřování pomocí formulářů.</span><span class="sxs-lookup"><span data-stu-id="e74d5-139">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Forms authentication.</span></span>  
  
2.  <span data-ttu-id="e74d5-140">Uložit *Default.aspx* souboru a pak otevřete jeho kódu soubor s názvem *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="e74d5-140">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="e74d5-141">Nahraďte stávající kód s následujícími službami:</span><span class="sxs-lookup"><span data-stu-id="e74d5-141">Replace the existing code with the following:</span></span>  
  
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
  
     <span data-ttu-id="e74d5-142">Ve výše uvedeném kódu se zobrazí deklarace identity o ověřeného uživatele, včetně uživatelů se identifikovanou pomocí ověřování pomocí formulářů.</span><span class="sxs-lookup"><span data-stu-id="e74d5-142">The above code will display claims about an authenticated user, including users identified by Forms authentication.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="e74d5-143">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="e74d5-143">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="e74d5-144">V tomto kroku testování vaší aplikace webových formulářů ASP.NET a ověřte, že deklarace identity jsou uvedené Pokud se uživatel přihlásí pomocí ověřování pomocí formulářů.</span><span class="sxs-lookup"><span data-stu-id="e74d5-144">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="e74d5-145">K testování aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování pomocí formulářů</span><span class="sxs-lookup"><span data-stu-id="e74d5-145">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="e74d5-146">Stiskněte klávesu **F5** sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="e74d5-146">Press **F5** to build and run the application.</span></span> <span data-ttu-id="e74d5-147">By se měla zobrazit s *Default.aspx*, který má **zaregistrovat** a **přihlásit** odkazy v horní pravé části stránky.</span><span class="sxs-lookup"><span data-stu-id="e74d5-147">You should be presented with *Default.aspx*, which has **Register** and **Log in** links in the top right of the page.</span></span> <span data-ttu-id="e74d5-148">Klikněte na tlačítko **zaregistrovat**.</span><span class="sxs-lookup"><span data-stu-id="e74d5-148">Click **Register**.</span></span>  
  
2.  <span data-ttu-id="e74d5-149">Na **zaregistrovat** stránky, vytvořte účet uživatele a pak klikněte na tlačítko **zaregistrovat**.</span><span class="sxs-lookup"><span data-stu-id="e74d5-149">On the **Register** page, create a user account, and then click **Register**.</span></span> <span data-ttu-id="e74d5-150">Váš účet se vytvoří pomocí ověřování pomocí formulářů a budete automaticky přihlášení.</span><span class="sxs-lookup"><span data-stu-id="e74d5-150">Your account will be created using Forms authentication, and you will be automatically signed in.</span></span>  
  
3.  <span data-ttu-id="e74d5-151">Po byla přesměrování na domovskou stránku, měli byste vidět tabulku pod **vaše deklarace identity** záhlaví, která zahrnuje **vystavitele**, **OriginalIssuer**, **Typ**, **hodnotu**, a **ValueType** deklarací informace o vašem účtu.</span><span class="sxs-lookup"><span data-stu-id="e74d5-151">After you have been redirected to the home page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span>
