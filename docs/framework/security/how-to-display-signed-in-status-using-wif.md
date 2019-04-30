---
title: 'Postupy: Zobrazení stavu přihlášení pomocí WIF'
ms.date: 03/30/2017
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
author: BrucePerlerMS
ms.openlocfilehash: b07a8930255786686fb1e587b2a29bbc708eff63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940501"
---
# <a name="how-to-display-signed-in-status-using-wif"></a><span data-ttu-id="5b6a1-102">Postupy: Zobrazení stavu přihlášení pomocí WIF</span><span class="sxs-lookup"><span data-stu-id="5b6a1-102">How To: Display Signed In Status Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="5b6a1-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="5b6a1-103">Applies To</span></span>  
  
- <span data-ttu-id="5b6a1-104">Microsoft Windows® Identity Foundation (WIF) 4.5</span><span class="sxs-lookup"><span data-stu-id="5b6a1-104">Microsoft® Windows® Identity Foundation (WIF) 4.5</span></span>  
  
- <span data-ttu-id="5b6a1-105">ASP.NET® webových formulářů</span><span class="sxs-lookup"><span data-stu-id="5b6a1-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="5b6a1-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="5b6a1-106">Summary</span></span>  
 <span data-ttu-id="5b6a1-107">Toto téma popisuje, jak zobrazit znaménko ve stavu v aplikaci technologie ASP.NET s podporou technologie WIF.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-107">This topic describes how to display the sign in status in a WIF-enabled ASP.NET application.</span></span> <span data-ttu-id="5b6a1-108">Technologie WIF poskytuje mechanismus pro provádění vaší aplikace s deklaracemi identity a správu ověřování a autorizace pro prostředky aplikace.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-108">WIF provides the mechanism for making your application claims-aware, and managing authentication and authorization for application resources.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="5b6a1-109">Obsah</span><span class="sxs-lookup"><span data-stu-id="5b6a1-109">Contents</span></span>  
  
- <span data-ttu-id="5b6a1-110">Přehled</span><span class="sxs-lookup"><span data-stu-id="5b6a1-110">Overview</span></span>  
  
- <span data-ttu-id="5b6a1-111">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="5b6a1-111">Summary of Steps</span></span>  
  
- <span data-ttu-id="5b6a1-112">Krok 1 – instalace identita a přístup k rozšíření</span><span class="sxs-lookup"><span data-stu-id="5b6a1-112">Step 1 – Install the Identity and Access Extension</span></span>  
  
- <span data-ttu-id="5b6a1-113">Krok 2 – Vytvoření aplikace předávající strany ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5b6a1-113">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
- <span data-ttu-id="5b6a1-114">Krok 3 – povolit místní služby STS pro vývoj k ověřování uživatelů</span><span class="sxs-lookup"><span data-stu-id="5b6a1-114">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
- <span data-ttu-id="5b6a1-115">Krok 4 – upravit svou aplikaci technologie ASP.NET pro zobrazení přihlašovací ve stavu</span><span class="sxs-lookup"><span data-stu-id="5b6a1-115">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
- <span data-ttu-id="5b6a1-116">Krok 5 – otestovat integraci technologie WIF a vaše aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5b6a1-116">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="overview"></a><span data-ttu-id="5b6a1-117">Přehled</span><span class="sxs-lookup"><span data-stu-id="5b6a1-117">Overview</span></span>  
 <span data-ttu-id="5b6a1-118">Toto téma ukazuje, jak vytvořit jednoduchou aplikaci deklaracemi pomocí technologie WIF a jak lze snadno zobrazit, zda je uživatel přihlášený, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-118">This topic demonstrates how to create a simple claims-aware application using WIF and how to easily display whether a user is signed in or not.</span></span> <span data-ttu-id="5b6a1-119">V následujících krocích se používá místní službu STS, která je součástí Identity a přístupu k rozšíření sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-119">The following steps use the Local Development STS that is included with the Identity and Access Visual Studio Extension.</span></span> <span data-ttu-id="5b6a1-120">Místní službu STS je určená pro vývoj a testování prostředí nabízejí jednoduchý způsob začlenění deklarací do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-120">The Local Development STS is intended for a testing and development environment to provide a simple method of integrating claims into your application.</span></span> <span data-ttu-id="5b6a1-121">To byste nikdy neměli používat v produkčním prostředí, jak neprovádí skutečné ověřování a přihlašovací údaje se nevyžadují.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-121">It should never be used in a production environment, as it does not perform real authentication and credentials are not required.</span></span> <span data-ttu-id="5b6a1-122">Imperativního kódu v následujícím postupu je však stejný pro aplikace připravené pro produkční prostředí pomocí skutečné ověřování.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-122">However, the imperative code in the following steps is the same for a production-ready application using real authentication.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="5b6a1-123">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="5b6a1-123">Summary of Steps</span></span>  
  
- <span data-ttu-id="5b6a1-124">Krok 1 – instalace identita a přístup k rozšíření</span><span class="sxs-lookup"><span data-stu-id="5b6a1-124">Step 1 – Install the Identity and Access Extension</span></span>  
  
- <span data-ttu-id="5b6a1-125">Krok 2 – Vytvoření aplikace předávající strany ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5b6a1-125">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
- <span data-ttu-id="5b6a1-126">Krok 3 – povolit místní služby STS pro vývoj k ověřování uživatelů</span><span class="sxs-lookup"><span data-stu-id="5b6a1-126">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
- <span data-ttu-id="5b6a1-127">Krok 4 – upravit svou aplikaci technologie ASP.NET pro zobrazení přihlašovací ve stavu</span><span class="sxs-lookup"><span data-stu-id="5b6a1-127">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
- <span data-ttu-id="5b6a1-128">Krok 5 – otestovat integraci technologie WIF a vaše aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5b6a1-128">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="step-1--install-the-identity-and-access-extension"></a><span data-ttu-id="5b6a1-129">Krok 1 – instalace identita a přístup k rozšíření</span><span class="sxs-lookup"><span data-stu-id="5b6a1-129">Step 1 – Install the Identity and Access Extension</span></span>  
 <span data-ttu-id="5b6a1-130">Tento krok popisuje postup konfigurace identit a přístupu rozšíření pro Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-130">This step describes how to configure the Identity and Access extension to Visual Studio 2012.</span></span> <span data-ttu-id="5b6a1-131">Toto rozšíření automatizuje proces konfigurace vaší aplikace ke komunikaci s koncovými body služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-131">This extension automates the process of configuring your application to communicate with STS endpoints.</span></span>  
  
#### <a name="to-install-the-identity-and-access-extension"></a><span data-ttu-id="5b6a1-132">Chcete-li nainstalovat rozšíření identit a přístupu</span><span class="sxs-lookup"><span data-stu-id="5b6a1-132">To install the Identity and Access extension</span></span>  
  
1. <span data-ttu-id="5b6a1-133">Spusťte sadu Visual Studio jako správce v režimu se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-133">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2. <span data-ttu-id="5b6a1-134">V sadě Visual Studio, klikněte na tlačítko **nástroje** a klikněte na tlačítko **Správce rozšíření**.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-134">In Visual Studio, click **Tools** and click **Extension Manager**.</span></span> <span data-ttu-id="5b6a1-135">**Správce rozšíření** zobrazí se okno.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-135">The **Extension Manager** window appears.</span></span>  
  
3. <span data-ttu-id="5b6a1-136">V **Správce rozšíření**, klikněte na tlačítko **Online rozšíření** v levé nabídce vyberte **Galerie sady Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-136">In **Extension Manager**, click **Online Extensions** from the left menu, then select **Visual Studio Gallery**.</span></span>  
  
4. <span data-ttu-id="5b6a1-137">V pravém horním rohu **Správce rozšíření**, vyhledejte *identit a přístupu*.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-137">In the top right corner of **Extension Manager**, search for *Identity and Access*.</span></span>  
  
5. <span data-ttu-id="5b6a1-138">**Identit a přístupu** položky se zobrazí ve výsledcích hledání.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-138">The **Identity and Access** item will appear in the search results.</span></span> <span data-ttu-id="5b6a1-139">Klikněte na něj a potom klikněte na tlačítko **Stáhnout**.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-139">Click it, and then click **Download**.</span></span>  
  
6. <span data-ttu-id="5b6a1-140">**Stáhnout a nainstalovat** se zobrazí dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-140">The **Download and Install** dialog appears.</span></span> <span data-ttu-id="5b6a1-141">Pokud s licenčními podmínkami souhlasíte, klikněte na tlačítko **nainstalovat**.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-141">If you agree with the license terms, click **Install**.</span></span>  
  
7. <span data-ttu-id="5b6a1-142">Když **identit a přístupu** rozšíření dokončil instalaci, restartujte Visual Studio v režimu správce.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-142">When the **Identity and Access** extension has finished installing, restart Visual Studio in administrator mode.</span></span>  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a><span data-ttu-id="5b6a1-143">Krok 2 – Vytvoření aplikace předávající strany ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5b6a1-143">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
 <span data-ttu-id="5b6a1-144">Tento krok popisuje, jak vytvořit webovou aplikaci webových formulářů ASP.NET, které se integrují s WIF předávající stranu.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-144">This step describes how to create a relying party ASP.NET Web Forms application that will integrate with WIF.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="5b6a1-145">Chcete-li vytvořit jednoduchou aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5b6a1-145">To create a simple ASP.NET application</span></span>  
  
1. <span data-ttu-id="5b6a1-146">Spusťte sadu Visual Studio a klikněte na tlačítko **souboru**, **nový**a potom **projektu**.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-146">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="5b6a1-147">V **nový projekt** okna, klikněte na tlačítko **aplikace webových formulářů ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-147">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3. <span data-ttu-id="5b6a1-148">V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-148">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a><span data-ttu-id="5b6a1-149">Krok 3 – povolit místní služby STS pro vývoj k ověřování uživatelů</span><span class="sxs-lookup"><span data-stu-id="5b6a1-149">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
 <span data-ttu-id="5b6a1-150">Tento krok popisuje, jak povolit místní službu STS pro vývoj ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-150">This step describes how to enable Local Development STS in your application.</span></span> <span data-ttu-id="5b6a1-151">Místní službu STS je povolit pomocí rozšíření identit a přístupu pro sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-151">Local Development STS is enabled by using the Identity and Access extension for Visual Studio.</span></span>  
  
#### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a><span data-ttu-id="5b6a1-152">Povolit místní službu STS pro vývoj aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5b6a1-152">To enable Local Development STS in your ASP.NET application</span></span>  
  
1. <span data-ttu-id="5b6a1-153">V sadě Visual Studio, klikněte pravým tlačítkem myši **TestApp** projektu v části **Průzkumníku řešení**a pak vyberte **identit a přístupu**.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-153">In Visual Studio, right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
2. <span data-ttu-id="5b6a1-154">**Identit a přístupu** zobrazí se okno.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-154">The **Identity and Access** window appears.</span></span> <span data-ttu-id="5b6a1-155">V části **poskytovatelé**vyberte **testování aplikace s místní službu STS pro vývoj**, pak klikněte na tlačítko **použít**.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-155">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a><span data-ttu-id="5b6a1-156">Krok 4 – upravit svou aplikaci technologie ASP.NET pro zobrazení přihlašovací ve stavu</span><span class="sxs-lookup"><span data-stu-id="5b6a1-156">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
 <span data-ttu-id="5b6a1-157">Tento krok popisuje, jak upravit svou aplikaci ASP.NET dynamicky uvedena informace, zda aktuální uživatel je přihlášený.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-157">This step describes how to modify your ASP.NET application to dynamically display whether the current user is signed in.</span></span> <span data-ttu-id="5b6a1-158">Jakmile poskytovatel služby tokenů zabezpečení nakonfigurovaný, technologie WIF zpracovává příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-158">Once your STS provider has been configured, WIF handles the incoming claims.</span></span> <span data-ttu-id="5b6a1-159">Teď musíte nakonfigurovat kódu vaší aplikace k zobrazení výsledku ověřování.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-159">Now you need to configure your application’s code to display the result of the authentication.</span></span>  
  
#### <a name="to-display-sign-in-status"></a><span data-ttu-id="5b6a1-160">Chcete-li zobrazit přihlašování ve stavu</span><span class="sxs-lookup"><span data-stu-id="5b6a1-160">To display sign in status</span></span>  
  
1. <span data-ttu-id="5b6a1-161">V sadě Visual Studio, otevřete **Default.aspx** soubor **TestApp** projektu.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-161">In Visual Studio, open the **Default.aspx** file under the **TestApp** project.</span></span>  
  
2. <span data-ttu-id="5b6a1-162">Nahraďte stávající značky **Default.aspx** souboru následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="5b6a1-162">Replace the existing markup in the **Default.aspx** file with the following markup:</span></span>  
  
    ```  
    <%@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head runat="server">  
        <title>Logged In Status</title>  
    </head>  
    <body>  
        <asp:label ID="myLabel" runat="server" />  
    </body>  
    </html>  
    ```  
  
3. <span data-ttu-id="5b6a1-163">Uložit **Default.aspx**a pak otevřete soubor s názvem jeho kódu **Default.aspx.cs**.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-163">Save **Default.aspx**, and then open its code behind file named **Default.aspx.cs**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5b6a1-164">**Default.aspx.cs** může být skrytá pod **Default.aspx** v Průzkumníku řešení.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-164">**Default.aspx.cs** may be hidden beneath **Default.aspx** in Solution Explorer.</span></span> <span data-ttu-id="5b6a1-165">Pokud **Default.aspx.cs** není viditelný, rozbalte **Default.aspx** klepnutím na trojúhelník vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-165">If **Default.aspx.cs** is not visible, expand **Default.aspx** by clicking on the triangle next to it.</span></span>  
  
4. <span data-ttu-id="5b6a1-166">Nahraďte existující kód ve třídě **Default.aspx.cs** následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="5b6a1-166">Replace the existing code in **Default.aspx.cs** with the following code:</span></span>  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        protected void Page_Load(object sender, EventArgs e)  
        {  
            ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
            if (claimsPrincipal != null)  
            {  
                myLabel.Text = "You are signed in.";  
            }  
            else  
            {  
                myLabel.Text = "You are not signed in.";  
            }  
        }  
    }  
    ```  
  
5. <span data-ttu-id="5b6a1-167">Uložit **Default.aspx.cs**a sestavte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-167">Save **Default.aspx.cs**, and build the application.</span></span>  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a><span data-ttu-id="5b6a1-168">Krok 5 – otestovat integraci technologie WIF a vaše aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5b6a1-168">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
 <span data-ttu-id="5b6a1-169">Tento krok popisuje, jak otestovat integraci technologie WIF a vaše aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-169">This step describes how you can test the integration between WIF and your ASP.NET application.</span></span>  
  
#### <a name="to-test-the-integration-between-wif-and-aspnet"></a><span data-ttu-id="5b6a1-170">Chcete-li otestovat integraci technologie WIF a ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5b6a1-170">To test the integration between WIF and ASP.NET</span></span>  
  
1. <span data-ttu-id="5b6a1-171">V sadě Visual Studio, stiskněte klávesu **F5** pro spuštění ladění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-171">In Visual Studio, press **F5** to start debugging your application.</span></span> <span data-ttu-id="5b6a1-172">Pokud se nenajdou žádné chyby, otevře se nové okno prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-172">If no errors are found, a new browser window will open.</span></span>  
  
2. <span data-ttu-id="5b6a1-173">Můžete si všimnout, že v prohlížeči tiše přesměruje požadavek na službu STS a pak otevře stránku Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-173">You may notice that the browser silently redirects your request to the STS, and then opens the Default.aspx page.</span></span> <span data-ttu-id="5b6a1-174">Pokud technologie WIF je správně nakonfigurovaná, měli byste vidět web zobrazit následující text: **"Přihlášení"**.</span><span class="sxs-lookup"><span data-stu-id="5b6a1-174">If WIF is properly configured, you should see the site display the following text: **"You are signed in"**.</span></span>
