---
title: "Postupy: Vytvoření aplikace deklaracemi rozhraní ASP.NET Web Forms pomocí WIF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efb264dd-f47b-49a9-85ee-9f45d4425765
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: d5b81e20ed1b39c7750329718729905484eb7fa1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-build-claims-aware-aspnet-web-forms-application-using-wif"></a><span data-ttu-id="99bdb-102">Postupy: Vytvoření aplikace deklaracemi rozhraní ASP.NET Web Forms pomocí WIF</span><span class="sxs-lookup"><span data-stu-id="99bdb-102">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="99bdb-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="99bdb-103">Applies To</span></span>  
  
-   <span data-ttu-id="99bdb-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="99bdb-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="99bdb-105">ASP.NET® webových formulářů</span><span class="sxs-lookup"><span data-stu-id="99bdb-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="99bdb-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="99bdb-106">Summary</span></span>  
 <span data-ttu-id="99bdb-107">Tento postup obsahuje podrobné podrobné postupy pro vytvoření jednoduché deklaracemi identity aplikace webových formulářů ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="99bdb-107">This How-To provides detailed step-by-step procedures for creating simple claims-aware ASP.NET Web Forms application.</span></span> <span data-ttu-id="99bdb-108">Poskytuje také pokyny, jak k otestování jednoduché deklaracemi identity aplikace webových formulářů ASP.NET pro úspěšné dokončení implementace federovaného ověřování.</span><span class="sxs-lookup"><span data-stu-id="99bdb-108">It also provides instructions for how to test the simple claims-aware ASP.NET Web Forms application for successful implementation of federated authentication.</span></span> <span data-ttu-id="99bdb-109">Tento postup nemá podrobné pokyny pro vytvoření tokenu služby zabezpečení (STS) a předpokládá, že jste již nakonfigurovali služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="99bdb-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and assumes you have already configured an STS.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="99bdb-110">Obsah</span><span class="sxs-lookup"><span data-stu-id="99bdb-110">Contents</span></span>  
  
-   <span data-ttu-id="99bdb-111">Cíle</span><span class="sxs-lookup"><span data-stu-id="99bdb-111">Objectives</span></span>  
  
-   <span data-ttu-id="99bdb-112">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="99bdb-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="99bdb-113">Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="99bdb-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="99bdb-114">Krok 2 – konfigurace aplikaci ASP.NET Web Forms pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="99bdb-114">Step 2 – Configure ASP.NET Web Forms Application for Claims-Based Authentication</span></span>  
  
-   <span data-ttu-id="99bdb-115">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="99bdb-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="99bdb-116">Cíle</span><span class="sxs-lookup"><span data-stu-id="99bdb-116">Objectives</span></span>  
  
-   <span data-ttu-id="99bdb-117">Konfigurace aplikace webových formulářů ASP.NET pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="99bdb-117">Configure ASP.NET Web Forms application for claims-based authentication</span></span>  
  
-   <span data-ttu-id="99bdb-118">Testování úspěšné deklaracemi identity aplikace webových formulářů ASP.NET</span><span class="sxs-lookup"><span data-stu-id="99bdb-118">Test successful claims-aware ASP.NET Web Forms application</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="99bdb-119">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="99bdb-119">Summary of Steps</span></span>  
  
-   <span data-ttu-id="99bdb-120">Krok 1 – Vytvoření jednoduché webové formuláře aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="99bdb-120">Step 1 – Create Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="99bdb-121">Krok 2 – konfigurace aplikaci ASP.NET Web Forms federovaného ověřování</span><span class="sxs-lookup"><span data-stu-id="99bdb-121">Step 2 – Configure ASP.NET Web Forms Application for Federated Authentication</span></span>  
  
-   <span data-ttu-id="99bdb-122">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="99bdb-122">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="99bdb-123">Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="99bdb-123">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="99bdb-124">V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="99bdb-124">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="99bdb-125">Chcete-li vytvořit jednoduchou aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="99bdb-125">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="99bdb-126">Spuštění sady Visual Studio a klikněte na tlačítko **soubor**, **nový**a potom **projektu**.</span><span class="sxs-lookup"><span data-stu-id="99bdb-126">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="99bdb-127">V **nový projekt** okně klikněte na tlačítko **aplikaci webových formulářů ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="99bdb-127">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="99bdb-128">V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.</span><span class="sxs-lookup"><span data-stu-id="99bdb-128">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-based-authentication"></a><span data-ttu-id="99bdb-129">Krok 2 – konfigurace aplikaci ASP.NET Web Forms pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="99bdb-129">Step 2 – Configure ASP.NET Web Forms Application for Claims-Based Authentication</span></span>  
 <span data-ttu-id="99bdb-130">V tomto kroku budete přidávat položky konfigurace určené k *Web.config* konfigurační soubor aplikace webových formulářů ASP.NET, aby pracujícím s deklaracemi.</span><span class="sxs-lookup"><span data-stu-id="99bdb-130">In this step you will add configuration entries to the *Web.config* configuration file of your ASP.NET Web Forms application to make it claims-aware.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-based-authentication"></a><span data-ttu-id="99bdb-131">Ke konfiguraci aplikace ASP.NET pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="99bdb-131">To configure ASP.NET application for claims-based authentication</span></span>  
  
1.  <span data-ttu-id="99bdb-132">Následující části položky konfigurace k přidání *Web.config* konfigurační soubor ihned po  **\<konfigurace >** otevírání element:</span><span class="sxs-lookup"><span data-stu-id="99bdb-132">Add the following configuration section entries to the *Web.config* configuration file immediately after the **\<configuration>** opening element:</span></span>  
  
    ```xml  
    <configSections>  
      <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
      <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2.  <span data-ttu-id="99bdb-133">Přidat  **\<umístění >** element, který umožňuje přístup k metadatům federace aplikace:</span><span class="sxs-lookup"><span data-stu-id="99bdb-133">Add a **\<location>** element that enables access to the application’s federation metadata:</span></span>  
  
    ```xml  
    <location path="FederationMetadata">  
      <system.web>  
        <authorization>  
          <allow users="*" />  
        </authorization>  
      </system.web>  
    </location>  
    ```  
  
3.  <span data-ttu-id="99bdb-134">Přidejte následující položky konfigurace v rámci  **\<system.web >** prvků tak, aby odepřel uživatelů, zakažte nativní ověřování a povolit WIF ke správě ověřování.</span><span class="sxs-lookup"><span data-stu-id="99bdb-134">Add the following configuration entries within the **\<system.web>** elements to deny users, disable native authentication, and enable WIF to manage authentication.</span></span>  
  
    ```xml  
    <authorization>  
      <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4.  <span data-ttu-id="99bdb-135">Přidat  **\<system.webServer >** element, který definuje moduly federovaného ověřování.</span><span class="sxs-lookup"><span data-stu-id="99bdb-135">Add a **\<system.webServer>** element that defines the modules for federated authentication.</span></span> <span data-ttu-id="99bdb-136">Všimněte si, že *PublicKeyToken* atribut musí být stejná jako *PublicKeyToken* atribut pro  **\<configSections >** položky přidali dříve:</span><span class="sxs-lookup"><span data-stu-id="99bdb-136">Note that the *PublicKeyToken* attribute must be the same as the *PublicKeyToken* attribute for the **\<configSections>** entries added earlier:</span></span>  
  
    ```xml  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5.  <span data-ttu-id="99bdb-137">Přidejte následující technologie Windows Identity Foundation související položky konfigurace a ujistěte se, že vaše aplikace ASP.NET adresu URL a číslo portu shodují s hodnotami v  **\<audienceUris >** položky **sféry**  atribut  **\<wsFederation >** elementu a **odpověď** atribut  **\<wsFederation >**elementu.</span><span class="sxs-lookup"><span data-stu-id="99bdb-137">Add the following Windows Identity Foundation related configuration entries and ensure that your ASP.NET application’s URL and port number match the values in the **\<audienceUris>** entry, **realm** attribute of the **\<wsFederation>** element, and the **reply** attribute of the **\<wsFederation>** element.</span></span> <span data-ttu-id="99bdb-138">Také zkontrolujte, zda **vystavitele** hodnota odpovídá adresu URL vašeho tokenu služby zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="99bdb-138">Also ensure that the **issuer** value fits your Security Token Service (STS) URL.</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <audienceUris>  
                <add value="http://localhost:28503/" />  
            </audienceUris>  
            <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
                <trustedIssuers>  
                    <add thumbprint="1234567890ABCDEFGHIJKLMNOPQRSTUVWXYZ1234" name="YourSTSName" />  
                </trustedIssuers>   
            </issuerNameRegistry>  
            <certificateValidation certificateValidationMode="None" />  
        </identityConfiguration>  
    </system.identityModel>  
    <system.identityModel.services>  
        <federationConfiguration>  
            <cookieHandler requireSsl="false" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="false" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
6.  <span data-ttu-id="99bdb-139">Přidat odkaz na <xref:System.IdentityModel> sestavení.</span><span class="sxs-lookup"><span data-stu-id="99bdb-139">Add reference to the <xref:System.IdentityModel> assembly.</span></span>  
  
7.  <span data-ttu-id="99bdb-140">Řešení a ujistěte se, že nejsou žádné chyby kompilace.</span><span class="sxs-lookup"><span data-stu-id="99bdb-140">Compile the solution to make sure there are no errors.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="99bdb-141">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="99bdb-141">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="99bdb-142">V tomto kroku budete testovat aplikace webových formulářů ASP.NET nakonfigurovaná pro ověřování založené na deklaracích identity.</span><span class="sxs-lookup"><span data-stu-id="99bdb-142">In this step you will test your ASP.NET Web Forms application configured for claims-based authentication.</span></span> <span data-ttu-id="99bdb-143">Pokud chcete provést základní test, přidáte kód, který zobrazí deklarace identity v tokenem vydaným Security Token Service (STS).</span><span class="sxs-lookup"><span data-stu-id="99bdb-143">To perform a basic test, you will add code that displays claims in the token issued by the Security Token Service (STS).</span></span>  
  
#### <a name="to-test-your-aspnet-web-form-application-for-claims-based-authentication"></a><span data-ttu-id="99bdb-144">K testování aplikace ASP.NET webového formuláře pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="99bdb-144">To test your ASP.NET Web Form application for claims-based authentication</span></span>  
  
1.  <span data-ttu-id="99bdb-145">Otevřete **Default.aspx** souboru pod **TestApp** projektu a nahraďte jeho existující značky následující kód:</span><span class="sxs-lookup"><span data-stu-id="99bdb-145">Open the **Default.aspx** file under the **TestApp** project and replace its existing markup with the following markup:</span></span>  
  
    ```  
    %@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head id="Head1" runat="server">  
        <title></title>  
    </head>  
    <body>  
        <h1><asp:label ID="signedIn" runat="server" /></h1>  
        <asp:label ID="claimType" runat="server" />  
        <asp:label ID="claimValue" runat="server" />  
        <asp:label ID="claimValueType" runat="server" />  
        <asp:label ID="claimSubjectName" runat="server" />  
        <asp:label ID="claimIssuer" runat="server" />  
    </body>  
    </html>  
    ```  
  
2.  <span data-ttu-id="99bdb-146">Uložit **Default.aspx**a pak otevřete jeho kódu na pozadí soubor s názvem **Default.aspx.cs**.</span><span class="sxs-lookup"><span data-stu-id="99bdb-146">Save **Default.aspx**, and then open its code behind file named **Default.aspx.cs**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="99bdb-147">**Default.aspx.cs** mohou být skryty pod **Default.aspx** v Průzkumníku řešení.</span><span class="sxs-lookup"><span data-stu-id="99bdb-147">**Default.aspx.cs** may be hidden beneath **Default.aspx** in Solution Explorer.</span></span> <span data-ttu-id="99bdb-148">Pokud **Default.aspx.cs** nezobrazuje, rozbalte položku **Default.aspx** kliknutím na trojúhelníček vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="99bdb-148">If **Default.aspx.cs** is not visible, expand **Default.aspx** by clicking on the triangle next to it.</span></span>  
  
3.  <span data-ttu-id="99bdb-149">Nahraďte stávající kód v **Page_Load** metodu **Default.aspx.cs** následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="99bdb-149">Replace the existing code in the **Page_Load** method of **Default.aspx.cs** with the following code:</span></span>  
  
    ```csharp  
    using System;  
    using System.IdentityModel;  
    using System.Security.Claims;  
    using System.Threading;  
    using System.Web.UI;  
  
    namespace TestApp  
    {  
        public partial class _Default : System.Web.UI.Page  
        {  
            protected void Page_Load(object sender, EventArgs e)  
            {  
                ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
                if (claimsPrincipal != null)  
                {  
                    signedIn.Text = "You are signed in.";  
  
                    foreach (Claim claim in claimsPrincipal.Claims)  
                    {  
                        claimType.Text = claim.Type;  
                        claimValue.Text = claim.Value;  
                        claimValueType.Text = claim.ValueType;  
                        claimSubjectName.Text = claim.Subject.Name;  
                        claimIssuer.Text = claim.Issuer;  
                    }  
                }  
                else  
                {  
                    signedIn.Text = "You are not signed in.";  
                }  
            }  
        }  
    }  
    ```  
  
4.  <span data-ttu-id="99bdb-150">Uložit **Default.aspx.cs**a sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="99bdb-150">Save **Default.aspx.cs**, and build the solution.</span></span>  
  
5.  <span data-ttu-id="99bdb-151">Spuštění řešení stisknutím **F5** klíč.</span><span class="sxs-lookup"><span data-stu-id="99bdb-151">Run the solution by pressing the **F5** key.</span></span>  
  
6.  <span data-ttu-id="99bdb-152">By se měla zobrazit stránky, které se zobrazí deklarace identity v tokenu, který byl vydán pomocí služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="99bdb-152">You should be presented with the page that displays the claims in the token that was issued to you by the Security Token Service.</span></span>
