---
title: 'Postupy: Sestavení aplikace Webových formulářů ASP.NET pracující s deklaracemi pomocí WIF'
ms.date: 03/30/2017
ms.assetid: efb264dd-f47b-49a9-85ee-9f45d4425765
author: BrucePerlerMS
ms.openlocfilehash: 45ad084013cbcafdf0d7c4ac3e0fd952305232c4
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851556"
---
# <a name="how-to-build-claims-aware-aspnet-web-forms-application-using-wif"></a><span data-ttu-id="eebf9-102">Postupy: Sestavení aplikace Webových formulářů ASP.NET pracující s deklaracemi pomocí WIF</span><span class="sxs-lookup"><span data-stu-id="eebf9-102">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="eebf9-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="eebf9-103">Applies To</span></span>  
  
- <span data-ttu-id="eebf9-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="eebf9-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
- <span data-ttu-id="eebf9-105">Webové formuláře ASP.NET®</span><span class="sxs-lookup"><span data-stu-id="eebf9-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="eebf9-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="eebf9-106">Summary</span></span>  
 <span data-ttu-id="eebf9-107">V tomto postupu najdete podrobné postupy pro vytváření jednoduchých webových formulářů ASP.NET pracujících s deklaracemi.</span><span class="sxs-lookup"><span data-stu-id="eebf9-107">This How-To provides detailed step-by-step procedures for creating simple claims-aware ASP.NET Web Forms application.</span></span> <span data-ttu-id="eebf9-108">Poskytuje také pokyny pro otestování jednoduchých ověřování ASP.NET webových formulářů pracujících s deklaracemi pro úspěšnou implementaci federovaného ověřování.</span><span class="sxs-lookup"><span data-stu-id="eebf9-108">It also provides instructions for how to test the simple claims-aware ASP.NET Web Forms application for successful implementation of federated authentication.</span></span> <span data-ttu-id="eebf9-109">Tento postup nemá podrobné pokyny k vytvoření služby tokenů zabezpečení (STS) a předpokládá, že jste už nakonfigurovali STS.</span><span class="sxs-lookup"><span data-stu-id="eebf9-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and assumes you have already configured an STS.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="eebf9-110">Obsah</span><span class="sxs-lookup"><span data-stu-id="eebf9-110">Contents</span></span>  
  
- <span data-ttu-id="eebf9-111">Cíle</span><span class="sxs-lookup"><span data-stu-id="eebf9-111">Objectives</span></span>  
  
- <span data-ttu-id="eebf9-112">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="eebf9-112">Summary of Steps</span></span>  
  
- <span data-ttu-id="eebf9-113">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET</span><span class="sxs-lookup"><span data-stu-id="eebf9-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
- <span data-ttu-id="eebf9-114">Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="eebf9-114">Step 2 – Configure ASP.NET Web Forms Application for Claims-Based Authentication</span></span>  
  
- <span data-ttu-id="eebf9-115">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="eebf9-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="eebf9-116">Cíle</span><span class="sxs-lookup"><span data-stu-id="eebf9-116">Objectives</span></span>  
  
- <span data-ttu-id="eebf9-117">Konfigurace aplikace webových formulářů ASP.NET pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="eebf9-117">Configure ASP.NET Web Forms application for claims-based authentication</span></span>  
  
- <span data-ttu-id="eebf9-118">Test úspěšných webových formulářů ASP.NET pracujících s deklaracemi</span><span class="sxs-lookup"><span data-stu-id="eebf9-118">Test successful claims-aware ASP.NET Web Forms application</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="eebf9-119">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="eebf9-119">Summary of Steps</span></span>  
  
- <span data-ttu-id="eebf9-120">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET</span><span class="sxs-lookup"><span data-stu-id="eebf9-120">Step 1 – Create Simple ASP.NET Web Forms Application</span></span>  
  
- <span data-ttu-id="eebf9-121">Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro federované ověřování</span><span class="sxs-lookup"><span data-stu-id="eebf9-121">Step 2 – Configure ASP.NET Web Forms Application for Federated Authentication</span></span>  
  
- <span data-ttu-id="eebf9-122">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="eebf9-122">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="eebf9-123">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET</span><span class="sxs-lookup"><span data-stu-id="eebf9-123">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="eebf9-124">V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="eebf9-124">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="eebf9-125">Vytvoření jednoduché aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="eebf9-125">To create a simple ASP.NET application</span></span>  
  
1. <span data-ttu-id="eebf9-126">Spusťte Visual Studio a klikněte na **soubor**, **Nový**a pak na **projekt**.</span><span class="sxs-lookup"><span data-stu-id="eebf9-126">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="eebf9-127">V okně **Nový projekt** klikněte na **ASP.NET webová Formulářová aplikace**.</span><span class="sxs-lookup"><span data-stu-id="eebf9-127">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3. <span data-ttu-id="eebf9-128">Do **název**zadejte `TestApp` a stiskněte **OK**.</span><span class="sxs-lookup"><span data-stu-id="eebf9-128">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-based-authentication"></a><span data-ttu-id="eebf9-129">Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="eebf9-129">Step 2 – Configure ASP.NET Web Forms Application for Claims-Based Authentication</span></span>  
 <span data-ttu-id="eebf9-130">V tomto kroku přidáte položky konfigurace do konfiguračního souboru *Web. config* vaší aplikace webových formulářů ASP.NET, aby se zajistilo, že bude zohledňovat deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="eebf9-130">In this step you will add configuration entries to the *Web.config* configuration file of your ASP.NET Web Forms application to make it claims-aware.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-based-authentication"></a><span data-ttu-id="eebf9-131">Konfigurace aplikace ASP.NET pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="eebf9-131">To configure ASP.NET application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="eebf9-132">Přidejte následující položky konfiguračního oddílu do konfiguračního souboru *Web. config* hned za  **\<konfigurační >** otevření elementu:</span><span class="sxs-lookup"><span data-stu-id="eebf9-132">Add the following configuration section entries to the *Web.config* configuration file immediately after the **\<configuration>** opening element:</span></span>  
  
    ```xml  
    <configSections>  
      <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
      <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2. <span data-ttu-id="eebf9-133">Přidejte > element  **Location,kterýumožňujepřístupkfederačnímmetadatůmaplikace:\<**</span><span class="sxs-lookup"><span data-stu-id="eebf9-133">Add a **\<location>** element that enables access to the application’s federation metadata:</span></span>  
  
    ```xml  
    <location path="FederationMetadata">  
      <system.web>  
        <authorization>  
          <allow users="*" />  
        </authorization>  
      </system.web>  
    </location>  
    ```  
  
3. <span data-ttu-id="eebf9-134">Přidejte následující položky konfigurace v rámci  **\<prvků System. Web >** , abyste odepřeli uživatelům, zakázali nativní ověřování a povolili WIF správu ověřování.</span><span class="sxs-lookup"><span data-stu-id="eebf9-134">Add the following configuration entries within the **\<system.web>** elements to deny users, disable native authentication, and enable WIF to manage authentication.</span></span>  
  
    ```xml  
    <authorization>  
      <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4. <span data-ttu-id="eebf9-135">Přidejte element System. **webserver >, který definuje moduly pro federované ověřování. \<**</span><span class="sxs-lookup"><span data-stu-id="eebf9-135">Add a **\<system.webServer>** element that defines the modules for federated authentication.</span></span> <span data-ttu-id="eebf9-136">Všimněte si, že atribut *PublicKeyToken* musí být stejný jako atribut *PublicKeyToken* pro položky  **\<configSections >** , přidané dříve:</span><span class="sxs-lookup"><span data-stu-id="eebf9-136">Note that the *PublicKeyToken* attribute must be the same as the *PublicKeyToken* attribute for the **\<configSections>** entries added earlier:</span></span>  
  
    ```xml  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5. <span data-ttu-id="eebf9-137">Přidejte následující položky konfigurace související s Windows Identity Foundation a ujistěte se, že se adresa URL a číslo portu vaší aplikace ASP.NET shodují s hodnotami v  **\<položce audienceUris >** Entry, atribut **Realm**  **\<wsFederation prvek >** a  **\<** atribut Reply elementu wsFederation >.</span><span class="sxs-lookup"><span data-stu-id="eebf9-137">Add the following Windows Identity Foundation related configuration entries and ensure that your ASP.NET application’s URL and port number match the values in the **\<audienceUris>** entry, **realm** attribute of the **\<wsFederation>** element, and the **reply** attribute of the **\<wsFederation>** element.</span></span> <span data-ttu-id="eebf9-138">Také se ujistěte, že hodnota **vystavitele** odpovídá vaší adrese URL služby tokenů zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="eebf9-138">Also ensure that the **issuer** value fits your Security Token Service (STS) URL.</span></span>  
  
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
            <cookieHandler requireSsl="true" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="true" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
6. <span data-ttu-id="eebf9-139">Přidejte odkaz na <xref:System.IdentityModel> sestavení.</span><span class="sxs-lookup"><span data-stu-id="eebf9-139">Add reference to the <xref:System.IdentityModel> assembly.</span></span>  
  
7. <span data-ttu-id="eebf9-140">Zkompilujte řešení, abyste se ujistili, že neexistují žádné chyby.</span><span class="sxs-lookup"><span data-stu-id="eebf9-140">Compile the solution to make sure there are no errors.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="eebf9-141">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="eebf9-141">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="eebf9-142">V tomto kroku otestujete svou aplikaci webových formulářů ASP.NET nakonfigurovanou pro ověřování založené na deklaracích.</span><span class="sxs-lookup"><span data-stu-id="eebf9-142">In this step you will test your ASP.NET Web Forms application configured for claims-based authentication.</span></span> <span data-ttu-id="eebf9-143">Chcete-li provést základní test, přidejte kód, který zobrazí deklarace identity v tokenu vydaném službou tokenů zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="eebf9-143">To perform a basic test, you will add code that displays claims in the token issued by the Security Token Service (STS).</span></span>  
  
#### <a name="to-test-your-aspnet-web-form-application-for-claims-based-authentication"></a><span data-ttu-id="eebf9-144">Testování aplikace webového formuláře v ASP.NET pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="eebf9-144">To test your ASP.NET Web Form application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="eebf9-145">V projektu **TestApp** otevřete soubor **Default. aspx** a nahraďte jeho stávající značky následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="eebf9-145">Open the **Default.aspx** file under the **TestApp** project and replace its existing markup with the following markup:</span></span>  
  
    ```aspx-csharp
    <%@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
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
  
2. <span data-ttu-id="eebf9-146">Uložte **Default. aspx**a pak otevřete svůj soubor kódu na pozadí s názvem **Default.aspx.cs**.</span><span class="sxs-lookup"><span data-stu-id="eebf9-146">Save **Default.aspx**, and then open its code behind file named **Default.aspx.cs**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="eebf9-147">**Default.aspx.cs** může být skrytá pod **Default. aspx** v Průzkumník řešení.</span><span class="sxs-lookup"><span data-stu-id="eebf9-147">**Default.aspx.cs** may be hidden beneath **Default.aspx** in Solution Explorer.</span></span> <span data-ttu-id="eebf9-148">Pokud není **Default.aspx.cs** viditelné, rozbalte **Default. aspx** kliknutím na trojúhelník vedle něho.</span><span class="sxs-lookup"><span data-stu-id="eebf9-148">If **Default.aspx.cs** is not visible, expand **Default.aspx** by clicking on the triangle next to it.</span></span>  
  
3. <span data-ttu-id="eebf9-149">Nahraďte existující kód v metodě **Page_Load** **Default.aspx.cs** následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="eebf9-149">Replace the existing code in the **Page_Load** method of **Default.aspx.cs** with the following code:</span></span>  
  
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
  
4. <span data-ttu-id="eebf9-150">Uložte **Default.aspx.cs**a sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="eebf9-150">Save **Default.aspx.cs**, and build the solution.</span></span>  
  
5. <span data-ttu-id="eebf9-151">Spusťte řešení stisknutím klávesy **F5** .</span><span class="sxs-lookup"><span data-stu-id="eebf9-151">Run the solution by pressing the **F5** key.</span></span>  
  
6. <span data-ttu-id="eebf9-152">Měla by se zobrazit stránka, která zobrazuje deklarace identity v tokenu, který jste vystavili pomocí služby tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="eebf9-152">You should be presented with the page that displays the claims in the token that was issued to you by the Security Token Service.</span></span>
