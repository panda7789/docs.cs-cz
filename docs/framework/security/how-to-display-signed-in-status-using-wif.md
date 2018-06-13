---
title: 'Postupy: Zobrazení přihlášení pomocí WIF stav'
ms.date: 03/30/2017
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 53ef5e8b3fae976bacff3be9a50c323a22aef0e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398915"
---
# <a name="how-to-display-signed-in-status-using-wif"></a><span data-ttu-id="227ca-102">Postupy: Zobrazení přihlášení pomocí WIF stav</span><span class="sxs-lookup"><span data-stu-id="227ca-102">How To: Display Signed In Status Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="227ca-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="227ca-103">Applies To</span></span>  
  
-   <span data-ttu-id="227ca-104">Microsoft® Windows® Identity Foundation (WIF) 4.5</span><span class="sxs-lookup"><span data-stu-id="227ca-104">Microsoft® Windows® Identity Foundation (WIF) 4.5</span></span>  
  
-   <span data-ttu-id="227ca-105">ASP.NET® webových formulářů</span><span class="sxs-lookup"><span data-stu-id="227ca-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="227ca-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="227ca-106">Summary</span></span>  
 <span data-ttu-id="227ca-107">Toto téma popisuje, jak zobrazit přihlašovací stav v aplikaci WIF technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="227ca-107">This topic describes how to display the sign in status in a WIF-enabled ASP.NET application.</span></span> <span data-ttu-id="227ca-108">WIF poskytuje mechanismus pro provádění vaší aplikace deklaracemi a správu ověřování a autorizace pro prostředky aplikace.</span><span class="sxs-lookup"><span data-stu-id="227ca-108">WIF provides the mechanism for making your application claims-aware, and managing authentication and authorization for application resources.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="227ca-109">Obsah</span><span class="sxs-lookup"><span data-stu-id="227ca-109">Contents</span></span>  
  
-   <span data-ttu-id="227ca-110">Přehled</span><span class="sxs-lookup"><span data-stu-id="227ca-110">Overview</span></span>  
  
-   <span data-ttu-id="227ca-111">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="227ca-111">Summary of Steps</span></span>  
  
-   <span data-ttu-id="227ca-112">Krok 1 – instalace identita a přístup k rozšíření</span><span class="sxs-lookup"><span data-stu-id="227ca-112">Step 1 – Install the Identity and Access Extension</span></span>  
  
-   <span data-ttu-id="227ca-113">Krok 2 – Vytvoření aplikace předávající strany ASP.NET</span><span class="sxs-lookup"><span data-stu-id="227ca-113">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
-   <span data-ttu-id="227ca-114">Krok 3 – povolit místní vývoj služby tokenů zabezpečení pro ověřování uživatelů</span><span class="sxs-lookup"><span data-stu-id="227ca-114">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
-   <span data-ttu-id="227ca-115">Krok 4 – upravit zobrazí přihlašovací stav aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="227ca-115">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
-   <span data-ttu-id="227ca-116">Krok 5 – Testování integrace mezi WIF a vaše aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="227ca-116">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="overview"></a><span data-ttu-id="227ca-117">Přehled</span><span class="sxs-lookup"><span data-stu-id="227ca-117">Overview</span></span>  
 <span data-ttu-id="227ca-118">Toto téma ukazuje, jak vytvořit jednoduchou aplikaci deklaracemi pomocí WIF a jak lze snadno zobrazit, zda je uživatel přihlášený nebo ne.</span><span class="sxs-lookup"><span data-stu-id="227ca-118">This topic demonstrates how to create a simple claims-aware application using WIF and how to easily display whether a user is signed in or not.</span></span> <span data-ttu-id="227ca-119">Následující postup použijte místní službu tokenů zabezpečení vývoj, která je součástí Identity a přístupu k rozšíření sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="227ca-119">The following steps use the Local Development STS that is included with the Identity and Access Visual Studio Extension.</span></span> <span data-ttu-id="227ca-120">Místní služba tokenů zabezpečení vývoj je určený pro testovací a vývojové prostředí zadat jednoduchý metodu integrace deklarace identity do aplikace.</span><span class="sxs-lookup"><span data-stu-id="227ca-120">The Local Development STS is intended for a testing and development environment to provide a simple method of integrating claims into your application.</span></span> <span data-ttu-id="227ca-121">Ho by nikdy použít v provozním prostředí, jako neprovádí skutečné ověřování a přihlašovací údaje nejsou nutné.</span><span class="sxs-lookup"><span data-stu-id="227ca-121">It should never be used in a production environment, as it does not perform real authentication and credentials are not required.</span></span> <span data-ttu-id="227ca-122">Imperativní kód v následujícím postupu je však stejný pro produkční prostředí aplikace pomocí skutečné ověřování.</span><span class="sxs-lookup"><span data-stu-id="227ca-122">However, the imperative code in the following steps is the same for a production-ready application using real authentication.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="227ca-123">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="227ca-123">Summary of Steps</span></span>  
  
-   <span data-ttu-id="227ca-124">Krok 1 – instalace identita a přístup k rozšíření</span><span class="sxs-lookup"><span data-stu-id="227ca-124">Step 1 – Install the Identity and Access Extension</span></span>  
  
-   <span data-ttu-id="227ca-125">Krok 2 – Vytvoření aplikace předávající strany ASP.NET</span><span class="sxs-lookup"><span data-stu-id="227ca-125">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
-   <span data-ttu-id="227ca-126">Krok 3 – povolit místní vývoj služby tokenů zabezpečení pro ověřování uživatelů</span><span class="sxs-lookup"><span data-stu-id="227ca-126">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
-   <span data-ttu-id="227ca-127">Krok 4 – upravit zobrazí přihlašovací stav aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="227ca-127">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
-   <span data-ttu-id="227ca-128">Krok 5 – Testování integrace mezi WIF a vaše aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="227ca-128">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="step-1--install-the-identity-and-access-extension"></a><span data-ttu-id="227ca-129">Krok 1 – instalace identita a přístup k rozšíření</span><span class="sxs-lookup"><span data-stu-id="227ca-129">Step 1 – Install the Identity and Access Extension</span></span>  
 <span data-ttu-id="227ca-130">Tento krok popisuje postup konfigurace identit a přístupu rozšíření pro sadu Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="227ca-130">This step describes how to configure the Identity and Access extension to Visual Studio 2012.</span></span> <span data-ttu-id="227ca-131">Toto rozšíření automatizuje proces konfigurace aplikace komunikovat s koncovými body služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="227ca-131">This extension automates the process of configuring your application to communicate with STS endpoints.</span></span>  
  
#### <a name="to-install-the-identity-and-access-extension"></a><span data-ttu-id="227ca-132">Chcete-li nainstalovat rozšíření identit a přístupu</span><span class="sxs-lookup"><span data-stu-id="227ca-132">To install the Identity and Access extension</span></span>  
  
1.  <span data-ttu-id="227ca-133">Spusťte sadu Visual Studio jako správce v režimu se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="227ca-133">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2.  <span data-ttu-id="227ca-134">V sadě Visual Studio, klikněte na tlačítko **nástroje** a klikněte na tlačítko **Správce rozšíření**.</span><span class="sxs-lookup"><span data-stu-id="227ca-134">In Visual Studio, click **Tools** and click **Extension Manager**.</span></span> <span data-ttu-id="227ca-135">**Správce rozšíření** se zobrazí v okně.</span><span class="sxs-lookup"><span data-stu-id="227ca-135">The **Extension Manager** window appears.</span></span>  
  
3.  <span data-ttu-id="227ca-136">V **Správce rozšíření**, klikněte na tlačítko **Online rozšíření** v levé nabídce pak vyberte **Galerie sady Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="227ca-136">In **Extension Manager**, click **Online Extensions** from the left menu, then select **Visual Studio Gallery**.</span></span>  
  
4.  <span data-ttu-id="227ca-137">V pravém horním rohu **Správce rozšíření**, vyhledejte *identit a přístupu*.</span><span class="sxs-lookup"><span data-stu-id="227ca-137">In the top right corner of **Extension Manager**, search for *Identity and Access*.</span></span>  
  
5.  <span data-ttu-id="227ca-138">**Identit a přístupu** položka se zobrazí ve výsledcích hledání.</span><span class="sxs-lookup"><span data-stu-id="227ca-138">The **Identity and Access** item will appear in the search results.</span></span> <span data-ttu-id="227ca-139">Klikněte na něj a potom klikněte na **Stáhnout**.</span><span class="sxs-lookup"><span data-stu-id="227ca-139">Click it, and then click **Download**.</span></span>  
  
6.  <span data-ttu-id="227ca-140">**Stáhněte a nainstalujte** otevře se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="227ca-140">The **Download and Install** dialog appears.</span></span> <span data-ttu-id="227ca-141">Pokud souhlasíte s licenčními podmínkami, klikněte na tlačítko **nainstalovat**.</span><span class="sxs-lookup"><span data-stu-id="227ca-141">If you agree with the license terms, click **Install**.</span></span>  
  
7.  <span data-ttu-id="227ca-142">Když **identit a přístupu** rozšíření byla dokončena instalace, restartujte Visual Studio v režimu správce.</span><span class="sxs-lookup"><span data-stu-id="227ca-142">When the **Identity and Access** extension has finished installing, restart Visual Studio in administrator mode.</span></span>  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a><span data-ttu-id="227ca-143">Krok 2 – Vytvoření aplikace předávající strany ASP.NET</span><span class="sxs-lookup"><span data-stu-id="227ca-143">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
 <span data-ttu-id="227ca-144">Tento krok popisuje postup vytvoření aplikace webových formulářů ASP.NET, která bude integrovat WIF a předávající stranou.</span><span class="sxs-lookup"><span data-stu-id="227ca-144">This step describes how to create a relying party ASP.NET Web Forms application that will integrate with WIF.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="227ca-145">Chcete-li vytvořit jednoduchou aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="227ca-145">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="227ca-146">Spuštění sady Visual Studio a klikněte na tlačítko **soubor**, **nový**a potom **projektu**.</span><span class="sxs-lookup"><span data-stu-id="227ca-146">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="227ca-147">V **nový projekt** okně klikněte na tlačítko **aplikaci webových formulářů ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="227ca-147">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="227ca-148">V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.</span><span class="sxs-lookup"><span data-stu-id="227ca-148">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a><span data-ttu-id="227ca-149">Krok 3 – povolit místní vývoj služby tokenů zabezpečení pro ověřování uživatelů</span><span class="sxs-lookup"><span data-stu-id="227ca-149">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
 <span data-ttu-id="227ca-150">Tento krok popisuje, jak povolit místní vývoj služby tokenů zabezpečení ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="227ca-150">This step describes how to enable Local Development STS in your application.</span></span> <span data-ttu-id="227ca-151">Pomocí rozšíření identit a přístupu pro sadu Visual Studio je povolena místní služby tokenů zabezpečení pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="227ca-151">Local Development STS is enabled by using the Identity and Access extension for Visual Studio.</span></span>  
  
#### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a><span data-ttu-id="227ca-152">Chcete-li povolit místní služby tokenů zabezpečení pro vývoj v aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="227ca-152">To enable Local Development STS in your ASP.NET application</span></span>  
  
1.  <span data-ttu-id="227ca-153">V sadě Visual Studio, klikněte pravým tlačítkem myši **TestApp** projektu v části **Průzkumníku řešení**, pak vyberte **identit a přístupu**.</span><span class="sxs-lookup"><span data-stu-id="227ca-153">In Visual Studio, right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
2.  <span data-ttu-id="227ca-154">**Identit a přístupu** se zobrazí v okně.</span><span class="sxs-lookup"><span data-stu-id="227ca-154">The **Identity and Access** window appears.</span></span> <span data-ttu-id="227ca-155">V části **zprostředkovatelé**, vyberte **testování vaší aplikace pomocí místní služby tokenů zabezpečení vývoj**, pak klikněte na tlačítko **použít**.</span><span class="sxs-lookup"><span data-stu-id="227ca-155">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a><span data-ttu-id="227ca-156">Krok 4 – upravit zobrazí přihlašovací stav aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="227ca-156">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
 <span data-ttu-id="227ca-157">Tento krok popisuje postup úpravy aplikace ASP.NET dynamicky uvedena informace, zda má aktuální uživatel je přihlášený.</span><span class="sxs-lookup"><span data-stu-id="227ca-157">This step describes how to modify your ASP.NET application to dynamically display whether the current user is signed in.</span></span> <span data-ttu-id="227ca-158">Jakmile poskytovatel služby tokenů zabezpečení byl nakonfigurován, WIF zpracovává příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="227ca-158">Once your STS provider has been configured, WIF handles the incoming claims.</span></span> <span data-ttu-id="227ca-159">Teď je potřeba nakonfigurovat kódu vaší aplikace zobrazíte výsledek ověřování.</span><span class="sxs-lookup"><span data-stu-id="227ca-159">Now you need to configure your application’s code to display the result of the authentication.</span></span>  
  
#### <a name="to-display-sign-in-status"></a><span data-ttu-id="227ca-160">Chcete-li zobrazit přihlašovací stav</span><span class="sxs-lookup"><span data-stu-id="227ca-160">To display sign in status</span></span>  
  
1.  <span data-ttu-id="227ca-161">V sadě Visual Studio, otevřete **Default.aspx** souboru pod **TestApp** projektu.</span><span class="sxs-lookup"><span data-stu-id="227ca-161">In Visual Studio, open the **Default.aspx** file under the **TestApp** project.</span></span>  
  
2.  <span data-ttu-id="227ca-162">Nahraďte stávající značky **Default.aspx** soubor s následující kód:</span><span class="sxs-lookup"><span data-stu-id="227ca-162">Replace the existing markup in the **Default.aspx** file with the following markup:</span></span>  
  
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
  
3.  <span data-ttu-id="227ca-163">Uložit **Default.aspx**a pak otevřete jeho kódu na pozadí soubor s názvem **Default.aspx.cs**.</span><span class="sxs-lookup"><span data-stu-id="227ca-163">Save **Default.aspx**, and then open its code behind file named **Default.aspx.cs**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="227ca-164">**Default.aspx.cs** mohou být skryty pod **Default.aspx** v Průzkumníku řešení.</span><span class="sxs-lookup"><span data-stu-id="227ca-164">**Default.aspx.cs** may be hidden beneath **Default.aspx** in Solution Explorer.</span></span> <span data-ttu-id="227ca-165">Pokud **Default.aspx.cs** nezobrazuje, rozbalte položku **Default.aspx** kliknutím na trojúhelníček vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="227ca-165">If **Default.aspx.cs** is not visible, expand **Default.aspx** by clicking on the triangle next to it.</span></span>  
  
4.  <span data-ttu-id="227ca-166">Nahraďte stávající kód v **Default.aspx.cs** následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="227ca-166">Replace the existing code in **Default.aspx.cs** with the following code:</span></span>  
  
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
  
5.  <span data-ttu-id="227ca-167">Uložit **Default.aspx.cs**a sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="227ca-167">Save **Default.aspx.cs**, and build the application.</span></span>  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a><span data-ttu-id="227ca-168">Krok 5 – Testování integrace mezi WIF a vaše aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="227ca-168">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
 <span data-ttu-id="227ca-169">Tento krok popisuje, jak můžete otestovat integrace mezi WIF a vaše aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="227ca-169">This step describes how you can test the integration between WIF and your ASP.NET application.</span></span>  
  
#### <a name="to-test-the-integration-between-wif-and-aspnet"></a><span data-ttu-id="227ca-170">K testování integrace mezi WIF a ASP.NET</span><span class="sxs-lookup"><span data-stu-id="227ca-170">To test the integration between WIF and ASP.NET</span></span>  
  
1.  <span data-ttu-id="227ca-171">V sadě Visual Studio, stiskněte klávesu **F5** spustit ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="227ca-171">In Visual Studio, press **F5** to start debugging your application.</span></span> <span data-ttu-id="227ca-172">Pokud nejsou nalezeny žádné chyby, otevře se nové okno prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="227ca-172">If no errors are found, a new browser window will open.</span></span>  
  
2.  <span data-ttu-id="227ca-173">Můžete si všimnout, že bezobslužně přesměruje žádost na službu STS prohlížeče a následně otevírá stránku Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="227ca-173">You may notice that the browser silently redirects your request to the STS, and then opens the Default.aspx page.</span></span> <span data-ttu-id="227ca-174">Pokud WIF správně nakonfigurovaný, měli byste vidět web zobrazit následující text: **"Přihlášení"**.</span><span class="sxs-lookup"><span data-stu-id="227ca-174">If WIF is properly configured, you should see the site display the following text: **"You are signed in"**.</span></span>
