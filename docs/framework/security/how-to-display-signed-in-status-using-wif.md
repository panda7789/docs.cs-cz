---
title: 'Postupy: Zobrazení stavu přihlášení pomocí WIF'
ms.date: 03/30/2017
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
author: BrucePerlerMS
ms.openlocfilehash: e44dc80260e46b81ac723ada32085390a18a153a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945702"
---
# <a name="how-to-display-signed-in-status-using-wif"></a><span data-ttu-id="20062-102">Postupy: Zobrazení stavu přihlášení pomocí WIF</span><span class="sxs-lookup"><span data-stu-id="20062-102">How To: Display Signed In Status Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="20062-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="20062-103">Applies To</span></span>  
  
- <span data-ttu-id="20062-104">Microsoft® Windows® Identity Foundation (WIF) 4,5</span><span class="sxs-lookup"><span data-stu-id="20062-104">Microsoft® Windows® Identity Foundation (WIF) 4.5</span></span>  
  
- <span data-ttu-id="20062-105">Webové formuláře ASP.NET®</span><span class="sxs-lookup"><span data-stu-id="20062-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="20062-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="20062-106">Summary</span></span>  
 <span data-ttu-id="20062-107">Toto téma popisuje, jak zobrazit stav přihlášení v aplikaci ASP.NET s podporou WIF.</span><span class="sxs-lookup"><span data-stu-id="20062-107">This topic describes how to display the sign in status in a WIF-enabled ASP.NET application.</span></span> <span data-ttu-id="20062-108">WIF poskytuje mechanismus pro poskytování deklarací identity vaší aplikace a správu ověřování a autorizace prostředků aplikace.</span><span class="sxs-lookup"><span data-stu-id="20062-108">WIF provides the mechanism for making your application claims-aware, and managing authentication and authorization for application resources.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="20062-109">Obsah</span><span class="sxs-lookup"><span data-stu-id="20062-109">Contents</span></span>  
  
- <span data-ttu-id="20062-110">Přehled</span><span class="sxs-lookup"><span data-stu-id="20062-110">Overview</span></span>  
  
- <span data-ttu-id="20062-111">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="20062-111">Summary of Steps</span></span>  
  
- <span data-ttu-id="20062-112">Krok 1 – instalace rozšíření identity and Access Extension</span><span class="sxs-lookup"><span data-stu-id="20062-112">Step 1 – Install the Identity and Access Extension</span></span>  
  
- <span data-ttu-id="20062-113">Krok 2 – Vytvoření aplikace ASP.NET předávající strany</span><span class="sxs-lookup"><span data-stu-id="20062-113">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
- <span data-ttu-id="20062-114">Krok 3 – povolení služby STS pro místní vývoj pro ověřování uživatelů</span><span class="sxs-lookup"><span data-stu-id="20062-114">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
- <span data-ttu-id="20062-115">Krok 4 – Úprava aplikace v ASP.NET pro zobrazení stavu přihlášení</span><span class="sxs-lookup"><span data-stu-id="20062-115">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
- <span data-ttu-id="20062-116">Krok 5 – testování integrace mezi WIF a aplikací ASP.NET</span><span class="sxs-lookup"><span data-stu-id="20062-116">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="overview"></a><span data-ttu-id="20062-117">Přehled</span><span class="sxs-lookup"><span data-stu-id="20062-117">Overview</span></span>  
 <span data-ttu-id="20062-118">Toto téma ukazuje, jak vytvořit jednoduchou aplikaci pracující s deklaracemi identity pomocí WIF a jak snadno zobrazit, jestli je uživatel přihlášený nebo ne.</span><span class="sxs-lookup"><span data-stu-id="20062-118">This topic demonstrates how to create a simple claims-aware application using WIF and how to easily display whether a user is signed in or not.</span></span> <span data-ttu-id="20062-119">V následujících krocích se používá místní vývoj STS, který je součástí identity a přístupu k rozšíření sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="20062-119">The following steps use the Local Development STS that is included with the Identity and Access Visual Studio Extension.</span></span> <span data-ttu-id="20062-120">Místní služba STS pro vývoj je určená pro testovací a vývojové prostředí, které poskytuje jednoduchou metodu integrace deklarací identity do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="20062-120">The Local Development STS is intended for a testing and development environment to provide a simple method of integrating claims into your application.</span></span> <span data-ttu-id="20062-121">Nikdy by neměl být použit v produkčním prostředí, protože neprovádí reálné ověřování a přihlašovací údaje nejsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="20062-121">It should never be used in a production environment, as it does not perform real authentication and credentials are not required.</span></span> <span data-ttu-id="20062-122">Nicméně imperativní kód v následujících krocích je stejný pro aplikaci připravenou pro produkční prostředí pomocí reálného ověřování.</span><span class="sxs-lookup"><span data-stu-id="20062-122">However, the imperative code in the following steps is the same for a production-ready application using real authentication.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="20062-123">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="20062-123">Summary of Steps</span></span>  
  
- <span data-ttu-id="20062-124">Krok 1 – instalace rozšíření identity and Access Extension</span><span class="sxs-lookup"><span data-stu-id="20062-124">Step 1 – Install the Identity and Access Extension</span></span>  
  
- <span data-ttu-id="20062-125">Krok 2 – Vytvoření aplikace ASP.NET předávající strany</span><span class="sxs-lookup"><span data-stu-id="20062-125">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
- <span data-ttu-id="20062-126">Krok 3 – povolení služby STS pro místní vývoj pro ověřování uživatelů</span><span class="sxs-lookup"><span data-stu-id="20062-126">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
- <span data-ttu-id="20062-127">Krok 4 – Úprava aplikace v ASP.NET pro zobrazení stavu přihlášení</span><span class="sxs-lookup"><span data-stu-id="20062-127">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
- <span data-ttu-id="20062-128">Krok 5 – testování integrace mezi WIF a aplikací ASP.NET</span><span class="sxs-lookup"><span data-stu-id="20062-128">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="step-1--install-the-identity-and-access-extension"></a><span data-ttu-id="20062-129">Krok 1 – instalace rozšíření identity and Access Extension</span><span class="sxs-lookup"><span data-stu-id="20062-129">Step 1 – Install the Identity and Access Extension</span></span>  
 <span data-ttu-id="20062-130">Tento krok popisuje, jak nakonfigurovat rozšíření identita a přístup k aplikaci Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="20062-130">This step describes how to configure the Identity and Access extension to Visual Studio 2012.</span></span> <span data-ttu-id="20062-131">Toto rozšíření automatizuje proces konfigurace vaší aplikace pro komunikaci s koncovými body služby STS.</span><span class="sxs-lookup"><span data-stu-id="20062-131">This extension automates the process of configuring your application to communicate with STS endpoints.</span></span>  
  
### <a name="to-install-the-identity-and-access-extension"></a><span data-ttu-id="20062-132">Instalace rozšíření identity and Access Extension</span><span class="sxs-lookup"><span data-stu-id="20062-132">To install the Identity and Access extension</span></span>  
  
1. <span data-ttu-id="20062-133">Spusťte sadu Visual Studio jako správce v režimu se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="20062-133">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2. <span data-ttu-id="20062-134">V aplikaci Visual Studio klikněte na **nástroje** a pak na **Správce rozšíření**.</span><span class="sxs-lookup"><span data-stu-id="20062-134">In Visual Studio, click **Tools** and click **Extension Manager**.</span></span> <span data-ttu-id="20062-135">Zobrazí se okno **Správce rozšíření** .</span><span class="sxs-lookup"><span data-stu-id="20062-135">The **Extension Manager** window appears.</span></span>  
  
3. <span data-ttu-id="20062-136">Ve **Správci rozšíření**klikněte v levé nabídce na **rozšíření online** a pak vyberte **Galerie sady Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="20062-136">In **Extension Manager**, click **Online Extensions** from the left menu, then select **Visual Studio Gallery**.</span></span>  
  
4. <span data-ttu-id="20062-137">V pravém horním rohu **Správce rozšíření**vyhledejte *identitu a přístup*.</span><span class="sxs-lookup"><span data-stu-id="20062-137">In the top right corner of **Extension Manager**, search for *Identity and Access*.</span></span>  
  
5. <span data-ttu-id="20062-138">Položka **Identita a přístup** se zobrazí ve výsledcích hledání.</span><span class="sxs-lookup"><span data-stu-id="20062-138">The **Identity and Access** item will appear in the search results.</span></span> <span data-ttu-id="20062-139">Klikněte na něj a pak klikněte na **Stáhnout**.</span><span class="sxs-lookup"><span data-stu-id="20062-139">Click it, and then click **Download**.</span></span>  
  
6. <span data-ttu-id="20062-140">Zobrazí se dialogové okno **Stáhnout a nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="20062-140">The **Download and Install** dialog appears.</span></span> <span data-ttu-id="20062-141">Pokud souhlasíte s licenčními podmínkami, klikněte na **nainstalovat**.</span><span class="sxs-lookup"><span data-stu-id="20062-141">If you agree with the license terms, click **Install**.</span></span>  
  
7. <span data-ttu-id="20062-142">Až se instalace rozšíření **identity a přístupu** dokončí, restartujte Visual Studio v režimu správce.</span><span class="sxs-lookup"><span data-stu-id="20062-142">When the **Identity and Access** extension has finished installing, restart Visual Studio in administrator mode.</span></span>  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a><span data-ttu-id="20062-143">Krok 2 – Vytvoření aplikace ASP.NET předávající strany</span><span class="sxs-lookup"><span data-stu-id="20062-143">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
 <span data-ttu-id="20062-144">Tento krok popisuje, jak vytvořit aplikaci webových formulářů ASP.NET předávající strany, která se bude integrovat s WIF.</span><span class="sxs-lookup"><span data-stu-id="20062-144">This step describes how to create a relying party ASP.NET Web Forms application that will integrate with WIF.</span></span>  
  
### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="20062-145">Vytvoření jednoduché aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="20062-145">To create a simple ASP.NET application</span></span>  
  
1. <span data-ttu-id="20062-146">Spusťte Visual Studio a klikněte na **soubor**, **Nový**a pak na **projekt**.</span><span class="sxs-lookup"><span data-stu-id="20062-146">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="20062-147">V okně **Nový projekt** klikněte na **ASP.NET webová Formulářová aplikace**.</span><span class="sxs-lookup"><span data-stu-id="20062-147">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3. <span data-ttu-id="20062-148">Do **název**zadejte `TestApp` a stiskněte **OK**.</span><span class="sxs-lookup"><span data-stu-id="20062-148">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a><span data-ttu-id="20062-149">Krok 3 – povolení služby STS pro místní vývoj pro ověřování uživatelů</span><span class="sxs-lookup"><span data-stu-id="20062-149">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
 <span data-ttu-id="20062-150">Tento krok popisuje, jak ve vaší aplikaci povolit místní vývoj STS.</span><span class="sxs-lookup"><span data-stu-id="20062-150">This step describes how to enable Local Development STS in your application.</span></span> <span data-ttu-id="20062-151">Místní vývoj STS je povolený pomocí rozšíření identity a přístupu pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="20062-151">Local Development STS is enabled by using the Identity and Access extension for Visual Studio.</span></span>  
  
### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a><span data-ttu-id="20062-152">Povolení místního vývojového tokenu STS v aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="20062-152">To enable Local Development STS in your ASP.NET application</span></span>  
  
1. <span data-ttu-id="20062-153">V aplikaci Visual Studio klikněte pravým tlačítkem myši na projekt **TestApp** v části **Průzkumník řešení**a pak vyberte možnost **Identita a přístup**.</span><span class="sxs-lookup"><span data-stu-id="20062-153">In Visual Studio, right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
2. <span data-ttu-id="20062-154">Zobrazí se okno **Identita a přístup** .</span><span class="sxs-lookup"><span data-stu-id="20062-154">The **Identity and Access** window appears.</span></span> <span data-ttu-id="20062-155">Včásti poskytovatelé vyberte **test aplikace pomocí místní služby tokenů pro vývoj**a pak klikněte na **použít**.</span><span class="sxs-lookup"><span data-stu-id="20062-155">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a><span data-ttu-id="20062-156">Krok 4 – Úprava aplikace v ASP.NET pro zobrazení stavu přihlášení</span><span class="sxs-lookup"><span data-stu-id="20062-156">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
 <span data-ttu-id="20062-157">Tento krok popisuje, jak upravit aplikaci v ASP.NET tak, aby dynamicky zobrazovala informace o tom, jestli je aktuální uživatel přihlášený.</span><span class="sxs-lookup"><span data-stu-id="20062-157">This step describes how to modify your ASP.NET application to dynamically display whether the current user is signed in.</span></span> <span data-ttu-id="20062-158">Po nakonfigurování zprostředkovatele STS WIF zpracuje příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="20062-158">Once your STS provider has been configured, WIF handles the incoming claims.</span></span> <span data-ttu-id="20062-159">Teď je potřeba nakonfigurovat kód vaší aplikace, aby zobrazoval výsledek ověřování.</span><span class="sxs-lookup"><span data-stu-id="20062-159">Now you need to configure your application’s code to display the result of the authentication.</span></span>  
  
### <a name="to-display-sign-in-status"></a><span data-ttu-id="20062-160">Zobrazení stavu přihlášení</span><span class="sxs-lookup"><span data-stu-id="20062-160">To display sign in status</span></span>  
  
1. <span data-ttu-id="20062-161">V aplikaci Visual Studio otevřete soubor **Default. aspx** v projektu **TestApp** .</span><span class="sxs-lookup"><span data-stu-id="20062-161">In Visual Studio, open the **Default.aspx** file under the **TestApp** project.</span></span>  
  
2. <span data-ttu-id="20062-162">Nahraďte existující kód ve **výchozím souboru. aspx** následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="20062-162">Replace the existing markup in the **Default.aspx** file with the following markup:</span></span>  
  
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
  
3. <span data-ttu-id="20062-163">Uložte **Default. aspx**a pak otevřete svůj soubor kódu na pozadí s názvem **Default.aspx.cs**.</span><span class="sxs-lookup"><span data-stu-id="20062-163">Save **Default.aspx**, and then open its code behind file named **Default.aspx.cs**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="20062-164">**Default.aspx.cs** může být skrytá pod **Default. aspx** v Průzkumník řešení.</span><span class="sxs-lookup"><span data-stu-id="20062-164">**Default.aspx.cs** may be hidden beneath **Default.aspx** in Solution Explorer.</span></span> <span data-ttu-id="20062-165">Pokud není **Default.aspx.cs** viditelné, rozbalte **Default. aspx** kliknutím na trojúhelník vedle něho.</span><span class="sxs-lookup"><span data-stu-id="20062-165">If **Default.aspx.cs** is not visible, expand **Default.aspx** by clicking on the triangle next to it.</span></span>  
  
4. <span data-ttu-id="20062-166">Existující kód nahraďte v **Default.aspx.cs** následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="20062-166">Replace the existing code in **Default.aspx.cs** with the following code:</span></span>  
  
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
  
5. <span data-ttu-id="20062-167">Uložte **Default.aspx.cs**a sestavte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="20062-167">Save **Default.aspx.cs**, and build the application.</span></span>  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a><span data-ttu-id="20062-168">Krok 5 – testování integrace mezi WIF a aplikací ASP.NET</span><span class="sxs-lookup"><span data-stu-id="20062-168">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
 <span data-ttu-id="20062-169">Tento krok popisuje, jak můžete testovat integraci mezi WIF a aplikací ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="20062-169">This step describes how you can test the integration between WIF and your ASP.NET application.</span></span>  
  
### <a name="to-test-the-integration-between-wif-and-aspnet"></a><span data-ttu-id="20062-170">Otestování integrace mezi WIF a ASP.NET</span><span class="sxs-lookup"><span data-stu-id="20062-170">To test the integration between WIF and ASP.NET</span></span>  
  
1. <span data-ttu-id="20062-171">V aplikaci Visual Studio stiskněte klávesu **F5** a spusťte ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="20062-171">In Visual Studio, press **F5** to start debugging your application.</span></span> <span data-ttu-id="20062-172">Pokud se nenaleznou žádné chyby, otevře se nové okno prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="20062-172">If no errors are found, a new browser window will open.</span></span>  
  
2. <span data-ttu-id="20062-173">Můžete si všimnout, že prohlížeč tiše přesměruje vaši žádost na službu STS a pak otevře stránku Default. aspx.</span><span class="sxs-lookup"><span data-stu-id="20062-173">You may notice that the browser silently redirects your request to the STS, and then opens the Default.aspx page.</span></span> <span data-ttu-id="20062-174">Pokud je WIF správně nakonfigurovaný, měli byste vidět, že se v lokalitě zobrazuje následující text: **Přihlásili jste se**.</span><span class="sxs-lookup"><span data-stu-id="20062-174">If WIF is properly configured, you should see the site display the following text: **"You are signed in"**.</span></span>
