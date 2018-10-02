---
title: 'Postupy: Sestavení webové aplikace s deklaracemi identity ASP.NET MVC pomocí WIF'
ms.date: 03/30/2017
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
author: BrucePerlerMS
ms.openlocfilehash: 4a003acbf4e182a0493368b586a3add229d8b526
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48035997"
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a><span data-ttu-id="03895-102">Postupy: Sestavení webové aplikace s deklaracemi identity ASP.NET MVC pomocí WIF</span><span class="sxs-lookup"><span data-stu-id="03895-102">How To: Build Claims-Aware ASP.NET MVC Web Application Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="03895-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="03895-103">Applies To</span></span>  
  
-   <span data-ttu-id="03895-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="03895-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="03895-105">ASP.NET® MVC</span><span class="sxs-lookup"><span data-stu-id="03895-105">ASP.NET® MVC</span></span>  
  
## <a name="summary"></a><span data-ttu-id="03895-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="03895-106">Summary</span></span>  
 <span data-ttu-id="03895-107">Tento návod obsahuje podrobně popisuje postupy pro vytvoření jednoduché webové aplikace s deklaracemi identity ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="03895-107">This How-To provides detailed step-by-step procedures for creating simple claims-aware ASP.NET MVC web application.</span></span> <span data-ttu-id="03895-108">Také poskytuje pokyny k otestování jednoduché deklaracemi webové aplikace ASP.NET MVC pro úspěšnou implementaci ověřování nezaloženého na deklaracích.</span><span class="sxs-lookup"><span data-stu-id="03895-108">It also provides instructions how to test the simple claims-aware ASP.NET MVC web application for successful implementation of claims-based authentication.</span></span> <span data-ttu-id="03895-109">Tento návod neobsahuje podrobné pokyny pro vytvoření tokenu služby zabezpečení (STS) a předpokládá, že jste už nakonfigurovali služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="03895-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and assumes you have already configured an STS.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="03895-110">Obsah</span><span class="sxs-lookup"><span data-stu-id="03895-110">Contents</span></span>  
  
-   <span data-ttu-id="03895-111">Cíle</span><span class="sxs-lookup"><span data-stu-id="03895-111">Objectives</span></span>  
  
-   <span data-ttu-id="03895-112">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="03895-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="03895-113">Krok 1 – Vytvoření aplikace jednoduchý ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="03895-113">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
-   <span data-ttu-id="03895-114">Krok 2 – konfigurace aplikace ASP.NET MVC pro ověřování nezaloženého na deklaracích</span><span class="sxs-lookup"><span data-stu-id="03895-114">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
-   <span data-ttu-id="03895-115">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="03895-115">Step 3 – Test Your Solution</span></span>  
  
-   <span data-ttu-id="03895-116">Související položky</span><span class="sxs-lookup"><span data-stu-id="03895-116">Related Items</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="03895-117">Cíle</span><span class="sxs-lookup"><span data-stu-id="03895-117">Objectives</span></span>  
  
-   <span data-ttu-id="03895-118">Konfigurace webové aplikace ASP.NET MVC pro ověřování nezaloženého na deklaracích</span><span class="sxs-lookup"><span data-stu-id="03895-118">Configure ASP.NET MVC web application for claims-based authentication</span></span>  
  
-   <span data-ttu-id="03895-119">Test úspěšný deklaracemi webové aplikace ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="03895-119">Test successful claims-aware ASP.NET MVC web application</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="03895-120">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="03895-120">Summary of Steps</span></span>  
  
-   <span data-ttu-id="03895-121">Krok 1 – Vytvoření aplikace jednoduchý ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="03895-121">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
-   <span data-ttu-id="03895-122">Krok 2 – konfigurace aplikace ASP.NET MVC pro ověřování nezaloženého na deklaracích</span><span class="sxs-lookup"><span data-stu-id="03895-122">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
-   <span data-ttu-id="03895-123">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="03895-123">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a><span data-ttu-id="03895-124">Krok 1 – Vytvoření aplikace jednoduchý ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="03895-124">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
 <span data-ttu-id="03895-125">V tomto kroku vytvoříte novou aplikaci ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="03895-125">In this step, you will create a new ASP.NET MVC application.</span></span>  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a><span data-ttu-id="03895-126">Chcete-li vytvořit jednoduchou aplikaci ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="03895-126">To create simple ASP.NET MVC application</span></span>  
  
1.  <span data-ttu-id="03895-127">Spusťte sadu Visual Studio a klikněte na tlačítko **souboru**, **nový**a potom **projektu**.</span><span class="sxs-lookup"><span data-stu-id="03895-127">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="03895-128">V **nový projekt** okna, klikněte na tlačítko **webové aplikace ASP.NET MVC 3**.</span><span class="sxs-lookup"><span data-stu-id="03895-128">In the **New Project** window, click **ASP.NET MVC 3 Web Application**.</span></span>  
  
3.  <span data-ttu-id="03895-129">V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.</span><span class="sxs-lookup"><span data-stu-id="03895-129">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4.  <span data-ttu-id="03895-130">V **nového projektu ASP.NET MVC 3** dialogového okna, vyberte **internetovou aplikaci** z dostupných šablon, ověřte **zobrazovací modul** je nastavena na **Razor**a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="03895-130">In the **New ASP.NET MVC 3 Project** dialog, select **Internet Application** from the available templates, ensure **View Engine** is set to **Razor**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="03895-131">Když se nový projekt otevře, klikněte pravým tlačítkem na **TestApp** projekt **Průzkumníka řešení** a vyberte **vlastnosti** možnost.</span><span class="sxs-lookup"><span data-stu-id="03895-131">When the new project opens, right-click the **TestApp** project in **Solution Explorer** and select the **Properties** option.</span></span>  
  
6.  <span data-ttu-id="03895-132">Na stránce Vlastnosti projektu, klikněte na **webové** kartu na levé straně a ujistěte se, že **použití místní webový Server IIS** je vybraná možnost.</span><span class="sxs-lookup"><span data-stu-id="03895-132">On the project’s properties page, click on the **Web** tab on the left and ensure that the **Use Local IIS Web Server** option is selected.</span></span>  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="03895-133">Krok 2 – konfigurace aplikace ASP.NET MVC pro ověřování nezaloženého na deklaracích</span><span class="sxs-lookup"><span data-stu-id="03895-133">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
 <span data-ttu-id="03895-134">V tomto kroku přidáte položky konfigurace *Web.config* konfiguračního souboru k němu deklaracemi webové aplikace ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="03895-134">In this step you will add configuration entries to the *Web.config* configuration file of your ASP.NET MVC web application to make it claims-aware.</span></span>  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="03895-135">Ke konfiguraci aplikace ASP.NET MVC pro ověřování nezaloženého na deklaracích</span><span class="sxs-lookup"><span data-stu-id="03895-135">To configure ASP.NET MVC application for claims-based authentication</span></span>  
  
1.  <span data-ttu-id="03895-136">Přidejte následující část definice konfigurace a *Web.config* konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="03895-136">Add the following configuration section definitions to the *Web.config* configuration file.</span></span> <span data-ttu-id="03895-137">Tyto zásady určují konfigurační oddíly funkce vyžaduje Windows Identity Foundation.</span><span class="sxs-lookup"><span data-stu-id="03895-137">These define configuration sections required by Windows Identity Foundation.</span></span> <span data-ttu-id="03895-138">Přidat definici ihned po  **\<konfigurace >** počáteční element:</span><span class="sxs-lookup"><span data-stu-id="03895-138">Add the definitions immediately after the **\<configuration>** opening element:</span></span>  
  
    ```xml  
    <configSections>  
        <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
        <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2.  <span data-ttu-id="03895-139">Přidat  **\<umístění >** element, který umožňuje přístup k federační metadata aplikace:</span><span class="sxs-lookup"><span data-stu-id="03895-139">Add a **\<location>** element that enables access to the application’s federation metadata:</span></span>  
  
    ```xml  
    <location path="FederationMetadata">  
        <system.web>  
            <authorization>  
                <allow users="*" />  
            </authorization>  
        </system.web>  
    </location>  
    ```  
  
3.  <span data-ttu-id="03895-140">Přidejte následující položky konfigurace v rámci  **\<system.web >** prvků, které mají odepřít uživatele, zakažte nativní ověřování a povolení WIF ke správě ověřování.</span><span class="sxs-lookup"><span data-stu-id="03895-140">Add the following configuration entries within the **\<system.web>** elements to deny users, disable native authentication, and enable WIF to manage authentication.</span></span>  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4.  <span data-ttu-id="03895-141">Přidejte následující technologie Windows Identity Foundation související položky konfigurace a ujistěte se, že adresa URL aplikace ASP.NET a číslo portu odpovídají hodnotám v  **\<audienceUris >** položka, **sféry**  atribut  **\<wsFederation >** elementu a **odpověď** atribut  **\<wsFederation >** elementu.</span><span class="sxs-lookup"><span data-stu-id="03895-141">Add the following Windows Identity Foundation related configuration entries and ensure that your ASP.NET application’s URL and port number match the values in the **\<audienceUris>** entry, **realm** attribute of the **\<wsFederation>** element, and the **reply** attribute of the **\<wsFederation>** element.</span></span> <span data-ttu-id="03895-142">Také zajistěte, aby **vystavitele** hodnota vejde adresu URL svého službu tokenů zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="03895-142">Also ensure that the **issuer** value fits your Security Token Service (STS) URL.</span></span>  
  
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
  
5.  <span data-ttu-id="03895-143">Přidat odkaz <xref:System.IdentityModel> sestavení.</span><span class="sxs-lookup"><span data-stu-id="03895-143">Add reference to the <xref:System.IdentityModel> assembly.</span></span>  
  
6.  <span data-ttu-id="03895-144">Řešení, abyste měli jistotu, že nejsou chyby kompilace.</span><span class="sxs-lookup"><span data-stu-id="03895-144">Compile the solution to make sure there are errors.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="03895-145">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="03895-145">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="03895-146">V tomto kroku budete testovat webové aplikace ASP.NET MVC nakonfigurován pro ověřování nezaloženého na deklaracích.</span><span class="sxs-lookup"><span data-stu-id="03895-146">In this step you will test your ASP.NET MVC web application configured for claims-based authentication.</span></span> <span data-ttu-id="03895-147">Pokud chcete provést základní test bude Přidání jednoduchého kódu, který zobrazí deklarace identity v tokenu vydané Security Token Service (STS).</span><span class="sxs-lookup"><span data-stu-id="03895-147">To perform basic test you will add simple code that displays claims in the token issued by the Security Token Service (STS).</span></span>  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="03895-148">Chcete-li otestovat aplikaci ASP.NET MVC pro ověřování nezaloženého na deklaracích</span><span class="sxs-lookup"><span data-stu-id="03895-148">To test your ASP.NET MVC application for claims-based authentication</span></span>  
  
1.  <span data-ttu-id="03895-149">V **Průzkumníka řešení**, rozbalte **řadiče** složky a otevřete *HomeController.cs* souboru v editoru.</span><span class="sxs-lookup"><span data-stu-id="03895-149">In the **Solution Explorer**, expand the **Controllers** folder and open *HomeController.cs* file in the editor.</span></span> <span data-ttu-id="03895-150">Přidejte následující kód, který **Index** metody:</span><span class="sxs-lookup"><span data-stu-id="03895-150">Add the following code to the **Index** method:</span></span>  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2.  <span data-ttu-id="03895-151">V **Průzkumníka řešení** rozbalte **zobrazení** a potom **Domů** složky a otevřete *Index.cshtml* souboru v editoru.</span><span class="sxs-lookup"><span data-stu-id="03895-151">In the **Solution Explorer** expand **Views** and then **Home** folders and open *Index.cshtml* file in the editor.</span></span> <span data-ttu-id="03895-152">Odstraňte její obsah a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="03895-152">Delete its contents and add the following markup:</span></span>  
  
    ```html  
    @{  
        ViewBag.Title = "Home Page";  
    }  
  
    <h2>Welcome: @ViewBag.ClaimsIdentity.Name</h2>  
    <h3>Values from Identity</h3>  
    <table>  
        <tr>  
            <th>  
                IsAuthenticated   
            </th>  
            <td>  
                @ViewBag.ClaimsIdentity.IsAuthenticated   
            </td>  
        </tr>  
        <tr>  
            <th>  
                Name   
            </th>          
            <td>  
                @ViewBag.ClaimsIdentity.Name  
            </td>          
        </tr>  
    </table>  
    <h3>Claims from ClaimsIdentity</h3>  
    <table>  
        <tr>  
            <th>  
                Claim Type  
            </th>  
            <th>  
                Claim Value  
            </th>  
            <th>  
                Value Type  
            </th>  
            <th>  
                Subject Name  
            </th>          
            <th>  
                Issuer Name  
            </th>          
        </tr>  
            @foreach (System.Security.Claims.Claim claim in ViewBag.ClaimsIdentity.Claims ) {  
        <tr>  
            <td>  
                @claim.Type  
            </td>  
            <td>  
                @claim.Value  
            </td>  
            <td>  
                @claim.ValueType  
            </td>  
            <td>  
                @claim.Subject.Name  
            </td>  
            <td>  
                @claim.Issuer  
            </td>  
        </tr>  
    }  
    </table>  
    ```  
  
3.  <span data-ttu-id="03895-153">Spuštění řešení stisknutím kombinace kláves **F5** klíč.</span><span class="sxs-lookup"><span data-stu-id="03895-153">Run the solution by pressing the **F5** key.</span></span>  
  
4.  <span data-ttu-id="03895-154">Mělo by se zobrazit na stránce zobrazí deklarace identity v tokenu, který byl vydán pro vás služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="03895-154">You should be presented with the page that displays the claims in the token that was issued to you by Security Token Service.</span></span>  
  
## <a name="related-items"></a><span data-ttu-id="03895-155">Související položky</span><span class="sxs-lookup"><span data-stu-id="03895-155">Related Items</span></span>  
  
-   [<span data-ttu-id="03895-156">Postupy: Sestavení aplikace Webových formulářů ASP.NET pracující s deklaracemi pomocí WIF</span><span class="sxs-lookup"><span data-stu-id="03895-156">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
