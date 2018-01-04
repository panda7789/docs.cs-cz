---
title: "Postupy: Vytvoření deklaracemi rozhraní ASP.NET MVC webové aplikace pomocí WIF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 39364f06cec35b1a5417540dfa29b0cac24fbdb6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a><span data-ttu-id="d6f17-102">Postupy: Vytvoření deklaracemi rozhraní ASP.NET MVC webové aplikace pomocí WIF</span><span class="sxs-lookup"><span data-stu-id="d6f17-102">How To: Build Claims-Aware ASP.NET MVC Web Application Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="d6f17-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="d6f17-103">Applies To</span></span>  
  
-   <span data-ttu-id="d6f17-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="d6f17-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="d6f17-105">ASP.NET® MVC</span><span class="sxs-lookup"><span data-stu-id="d6f17-105">ASP.NET® MVC</span></span>  
  
## <a name="summary"></a><span data-ttu-id="d6f17-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="d6f17-106">Summary</span></span>  
 <span data-ttu-id="d6f17-107">Tento postup obsahuje podrobné podrobné postupy pro vytvoření jednoduché deklaracemi webové aplikace ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="d6f17-107">This How-To provides detailed step-by-step procedures for creating simple claims-aware ASP.NET MVC web application.</span></span> <span data-ttu-id="d6f17-108">Obsahuje také pokyny jak otestování jednoduché deklaracemi webové aplikace ASP.NET MVC pro úspěšné dokončení implementace ověřování na základě deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="d6f17-108">It also provides instructions how to test the simple claims-aware ASP.NET MVC web application for successful implementation of claims-based authentication.</span></span> <span data-ttu-id="d6f17-109">Tento postup nemá podrobné pokyny pro vytvoření tokenu služby zabezpečení (STS) a předpokládá, že jste již nakonfigurovali služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d6f17-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and assumes you have already configured an STS.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="d6f17-110">Obsah</span><span class="sxs-lookup"><span data-stu-id="d6f17-110">Contents</span></span>  
  
-   <span data-ttu-id="d6f17-111">Cíle</span><span class="sxs-lookup"><span data-stu-id="d6f17-111">Objectives</span></span>  
  
-   <span data-ttu-id="d6f17-112">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="d6f17-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="d6f17-113">Krok 1 – Vytvoření jednoduché rozhraní ASP.NET MVC aplikace</span><span class="sxs-lookup"><span data-stu-id="d6f17-113">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
-   <span data-ttu-id="d6f17-114">Krok 2 – konfigurace aplikace ASP.NET MVC pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="d6f17-114">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
-   <span data-ttu-id="d6f17-115">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="d6f17-115">Step 3 – Test Your Solution</span></span>  
  
-   <span data-ttu-id="d6f17-116">Související položky</span><span class="sxs-lookup"><span data-stu-id="d6f17-116">Related Items</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="d6f17-117">Cíle</span><span class="sxs-lookup"><span data-stu-id="d6f17-117">Objectives</span></span>  
  
-   <span data-ttu-id="d6f17-118">Konfigurovat webovou aplikaci ASP.NET MVC pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="d6f17-118">Configure ASP.NET MVC web application for claims-based authentication</span></span>  
  
-   <span data-ttu-id="d6f17-119">Testování úspěšné deklaracemi webové aplikace ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="d6f17-119">Test successful claims-aware ASP.NET MVC web application</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="d6f17-120">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="d6f17-120">Summary of Steps</span></span>  
  
-   <span data-ttu-id="d6f17-121">Krok 1 – Vytvoření jednoduché rozhraní ASP.NET MVC aplikace</span><span class="sxs-lookup"><span data-stu-id="d6f17-121">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
-   <span data-ttu-id="d6f17-122">Krok 2 – konfigurace aplikace ASP.NET MVC pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="d6f17-122">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
-   <span data-ttu-id="d6f17-123">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="d6f17-123">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a><span data-ttu-id="d6f17-124">Krok 1 – Vytvoření jednoduché rozhraní ASP.NET MVC aplikace</span><span class="sxs-lookup"><span data-stu-id="d6f17-124">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
 <span data-ttu-id="d6f17-125">V tomto kroku vytvoříte novou aplikaci ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="d6f17-125">In this step, you will create a new ASP.NET MVC application.</span></span>  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a><span data-ttu-id="d6f17-126">Chcete-li vytvořit jednoduchou aplikaci ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="d6f17-126">To create simple ASP.NET MVC application</span></span>  
  
1.  <span data-ttu-id="d6f17-127">Spuštění sady Visual Studio a klikněte na tlačítko **soubor**, **nový**a potom **projektu**.</span><span class="sxs-lookup"><span data-stu-id="d6f17-127">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="d6f17-128">V **nový projekt** okně klikněte na tlačítko **webové aplikace ASP.NET MVC 3**.</span><span class="sxs-lookup"><span data-stu-id="d6f17-128">In the **New Project** window, click **ASP.NET MVC 3 Web Application**.</span></span>  
  
3.  <span data-ttu-id="d6f17-129">V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.</span><span class="sxs-lookup"><span data-stu-id="d6f17-129">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4.  <span data-ttu-id="d6f17-130">V **nový ASP.NET MVC 3 projekt** dialogovém okně, vyberte **Internetové aplikace** z dostupných šablon, zkontrolujte **zobrazovací modul** je nastaven na **Razor**a potom klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="d6f17-130">In the **New ASP.NET MVC 3 Project** dialog, select **Internet Application** from the available templates, ensure **View Engine** is set to **Razor**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="d6f17-131">Když se otevře nový projekt, klikněte pravým tlačítkem myši **TestApp** projektu v **Průzkumníku řešení** a vyberte **vlastnosti** možnost.</span><span class="sxs-lookup"><span data-stu-id="d6f17-131">When the new project opens, right-click the **TestApp** project in **Solution Explorer** and select the **Properties** option.</span></span>  
  
6.  <span data-ttu-id="d6f17-132">Na stránce vlastností projektu, klikněte na **webové** kartě na levé straně a ujistěte se, že **použití místního webového serveru IIS** je vybraná možnost.</span><span class="sxs-lookup"><span data-stu-id="d6f17-132">On the project’s properties page, click on the **Web** tab on the left and ensure that the **Use Local IIS Web Server** option is selected.</span></span>  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="d6f17-133">Krok 2 – konfigurace aplikace ASP.NET MVC pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="d6f17-133">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
 <span data-ttu-id="d6f17-134">V tomto kroku budete přidávat položky konfigurace určené k *Web.config* konfigurační soubor webové aplikace ASP.NET MVC, aby pracujícím s deklaracemi.</span><span class="sxs-lookup"><span data-stu-id="d6f17-134">In this step you will add configuration entries to the *Web.config* configuration file of your ASP.NET MVC web application to make it claims-aware.</span></span>  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="d6f17-135">Ke konfiguraci aplikace ASP.NET MVC pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="d6f17-135">To configure ASP.NET MVC application for claims-based authentication</span></span>  
  
1.  <span data-ttu-id="d6f17-136">Přidejte následující definice část konfigurace k *Web.config* konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="d6f17-136">Add the following configuration section definitions to the *Web.config* configuration file.</span></span> <span data-ttu-id="d6f17-137">Tyto zásady určují konfiguračních oddílů, vyžaduje technologie Windows Identity Foundation.</span><span class="sxs-lookup"><span data-stu-id="d6f17-137">These define configuration sections required by Windows Identity Foundation.</span></span> <span data-ttu-id="d6f17-138">Přidání definice okamžitě po  **\<konfigurace >** otevírání element:</span><span class="sxs-lookup"><span data-stu-id="d6f17-138">Add the definitions immediately after the **\<configuration>** opening element:</span></span>  
  
    ```xml  
    <configSections>  
        <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
        <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2.  <span data-ttu-id="d6f17-139">Přidat  **\<umístění >** element, který umožňuje přístup k metadatům federace aplikace:</span><span class="sxs-lookup"><span data-stu-id="d6f17-139">Add a **\<location>** element that enables access to the application’s federation metadata:</span></span>  
  
    ```xml  
    <location path="FederationMetadata">  
        <system.web>  
            <authorization>  
                <allow users="*" />  
            </authorization>  
        </system.web>  
    </location>  
    ```  
  
3.  <span data-ttu-id="d6f17-140">Přidejte následující položky konfigurace v rámci  **\<system.web >** prvků tak, aby odepřel uživatelů, zakažte nativní ověřování a povolit WIF ke správě ověřování.</span><span class="sxs-lookup"><span data-stu-id="d6f17-140">Add the following configuration entries within the **\<system.web>** elements to deny users, disable native authentication, and enable WIF to manage authentication.</span></span>  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4.  <span data-ttu-id="d6f17-141">Přidejte následující technologie Windows Identity Foundation související položky konfigurace a ujistěte se, že vaše aplikace ASP.NET adresu URL a číslo portu shodují s hodnotami v  **\<audienceUris >** položky **sféry**  atribut  **\<wsFederation >** elementu a **odpověď** atribut  **\<wsFederation >**elementu.</span><span class="sxs-lookup"><span data-stu-id="d6f17-141">Add the following Windows Identity Foundation related configuration entries and ensure that your ASP.NET application’s URL and port number match the values in the **\<audienceUris>** entry, **realm** attribute of the **\<wsFederation>** element, and the **reply** attribute of the **\<wsFederation>** element.</span></span> <span data-ttu-id="d6f17-142">Také zkontrolujte, zda **vystavitele** hodnota odpovídá adresu URL vašeho tokenu služby zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="d6f17-142">Also ensure that the **issuer** value fits your Security Token Service (STS) URL.</span></span>  
  
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
  
5.  <span data-ttu-id="d6f17-143">Přidat odkaz na <xref:System.IdentityModel> sestavení.</span><span class="sxs-lookup"><span data-stu-id="d6f17-143">Add reference to the <xref:System.IdentityModel> assembly.</span></span>  
  
6.  <span data-ttu-id="d6f17-144">Řešení a ujistěte se, že se chyby kompilace.</span><span class="sxs-lookup"><span data-stu-id="d6f17-144">Compile the solution to make sure there are errors.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="d6f17-145">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="d6f17-145">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="d6f17-146">V tomto kroku budete testovat webové aplikace ASP.NET MVC, který je nakonfigurován pro ověřování založené na deklaracích identity.</span><span class="sxs-lookup"><span data-stu-id="d6f17-146">In this step you will test your ASP.NET MVC web application configured for claims-based authentication.</span></span> <span data-ttu-id="d6f17-147">Pokud chcete provést základní test přidáte jednoduchý kód, který zobrazí deklarace identity v tokenem vydaným Security Token Service (STS).</span><span class="sxs-lookup"><span data-stu-id="d6f17-147">To perform basic test you will add simple code that displays claims in the token issued by the Security Token Service (STS).</span></span>  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="d6f17-148">K testování aplikace ASP.NET MVC pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="d6f17-148">To test your ASP.NET MVC application for claims-based authentication</span></span>  
  
1.  <span data-ttu-id="d6f17-149">V **Průzkumníku řešení**, rozbalte **řadiče** složky a otevřete *HomeController.cs* souboru v editoru.</span><span class="sxs-lookup"><span data-stu-id="d6f17-149">In the **Solution Explorer**, expand the **Controllers** folder and open *HomeController.cs* file in the editor.</span></span> <span data-ttu-id="d6f17-150">Přidejte následující kód, který **Index** metoda:</span><span class="sxs-lookup"><span data-stu-id="d6f17-150">Add the following code to the **Index** method:</span></span>  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2.  <span data-ttu-id="d6f17-151">V **Průzkumníku řešení** rozbalte **zobrazení** a potom **Domů** složky a otevřete *Index.cshtml* souboru v editoru.</span><span class="sxs-lookup"><span data-stu-id="d6f17-151">In the **Solution Explorer** expand **Views** and then **Home** folders and open *Index.cshtml* file in the editor.</span></span> <span data-ttu-id="d6f17-152">Odstraňte její obsah a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="d6f17-152">Delete its contents and add the following markup:</span></span>  
  
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
  
3.  <span data-ttu-id="d6f17-153">Spuštění řešení stisknutím **F5** klíč.</span><span class="sxs-lookup"><span data-stu-id="d6f17-153">Run the solution by pressing the **F5** key.</span></span>  
  
4.  <span data-ttu-id="d6f17-154">By se měla zobrazit stránky, které se zobrazí deklarace identity v tokenu, který byl vydán pomocí služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d6f17-154">You should be presented with the page that displays the claims in the token that was issued to you by Security Token Service.</span></span>  
  
## <a name="related-items"></a><span data-ttu-id="d6f17-155">Související položky</span><span class="sxs-lookup"><span data-stu-id="d6f17-155">Related Items</span></span>  
  
-   [<span data-ttu-id="d6f17-156">Postupy: Sestavení aplikace Webových formulářů ASP.NET pracující s deklaracemi pomocí WIF</span><span class="sxs-lookup"><span data-stu-id="d6f17-156">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
