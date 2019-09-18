---
title: 'Postupy: Sestavení webové aplikace ASP.NET MVC pracující s deklaracemi pomocí WIF'
ms.date: 03/30/2017
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
author: BrucePerlerMS
ms.openlocfilehash: 4d245288b04d8ed3d997bc5572b40c7f8a9334e5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045452"
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a><span data-ttu-id="01135-102">Postupy: Sestavení webové aplikace ASP.NET MVC pracující s deklaracemi pomocí WIF</span><span class="sxs-lookup"><span data-stu-id="01135-102">How To: Build Claims-Aware ASP.NET MVC Web Application Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="01135-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="01135-103">Applies To</span></span>  
  
- <span data-ttu-id="01135-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="01135-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
- <span data-ttu-id="01135-105">ASP.NET® MVC</span><span class="sxs-lookup"><span data-stu-id="01135-105">ASP.NET® MVC</span></span>  
  
## <a name="summary"></a><span data-ttu-id="01135-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="01135-106">Summary</span></span>  
 <span data-ttu-id="01135-107">V tomto postupu najdete podrobné postupy pro vytváření jednoduchých webových aplikací ASP.NET MVC, které pracují s deklaracemi.</span><span class="sxs-lookup"><span data-stu-id="01135-107">This How-To provides detailed step-by-step procedures for creating simple claims-aware ASP.NET MVC web application.</span></span> <span data-ttu-id="01135-108">Poskytuje také pokyny k testování jednoduchých webových aplikací s ASP.NET, které pracují s deklaracemi, pro úspěšnou implementaci ověřování založeného na deklaracích identity.</span><span class="sxs-lookup"><span data-stu-id="01135-108">It also provides instructions how to test the simple claims-aware ASP.NET MVC web application for successful implementation of claims-based authentication.</span></span> <span data-ttu-id="01135-109">Tento postup nemá podrobné pokyny k vytvoření služby tokenů zabezpečení (STS) a předpokládá, že jste už nakonfigurovali STS.</span><span class="sxs-lookup"><span data-stu-id="01135-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and assumes you have already configured an STS.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="01135-110">Obsah</span><span class="sxs-lookup"><span data-stu-id="01135-110">Contents</span></span>  
  
- <span data-ttu-id="01135-111">Cíle</span><span class="sxs-lookup"><span data-stu-id="01135-111">Objectives</span></span>  
  
- <span data-ttu-id="01135-112">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="01135-112">Summary of Steps</span></span>  
  
- <span data-ttu-id="01135-113">Krok 1 – Vytvoření jednoduché aplikace ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="01135-113">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
- <span data-ttu-id="01135-114">Krok 2 – konfigurace aplikace ASP.NET MVC pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="01135-114">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
- <span data-ttu-id="01135-115">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="01135-115">Step 3 – Test Your Solution</span></span>  
  
- <span data-ttu-id="01135-116">Související položky</span><span class="sxs-lookup"><span data-stu-id="01135-116">Related Items</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="01135-117">Cíle</span><span class="sxs-lookup"><span data-stu-id="01135-117">Objectives</span></span>  
  
- <span data-ttu-id="01135-118">Konfigurace webové aplikace ASP.NET MVC pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="01135-118">Configure ASP.NET MVC web application for claims-based authentication</span></span>  
  
- <span data-ttu-id="01135-119">Testování úspěšných webových aplikací ASP.NET MVC s podporou deklarací identity</span><span class="sxs-lookup"><span data-stu-id="01135-119">Test successful claims-aware ASP.NET MVC web application</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="01135-120">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="01135-120">Summary of Steps</span></span>  
  
- <span data-ttu-id="01135-121">Krok 1 – Vytvoření jednoduché aplikace ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="01135-121">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
- <span data-ttu-id="01135-122">Krok 2 – konfigurace aplikace ASP.NET MVC pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="01135-122">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
- <span data-ttu-id="01135-123">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="01135-123">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a><span data-ttu-id="01135-124">Krok 1 – Vytvoření jednoduché aplikace ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="01135-124">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
 <span data-ttu-id="01135-125">V tomto kroku vytvoříte novou aplikaci ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="01135-125">In this step, you will create a new ASP.NET MVC application.</span></span>  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a><span data-ttu-id="01135-126">Vytvoření jednoduché aplikace ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="01135-126">To create simple ASP.NET MVC application</span></span>  
  
1. <span data-ttu-id="01135-127">Spusťte Visual Studio a klikněte na **soubor**, **Nový**a pak na **projekt**.</span><span class="sxs-lookup"><span data-stu-id="01135-127">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="01135-128">V okně **Nový projekt** klikněte na **Webová aplikace ASP.NET MVC 3**.</span><span class="sxs-lookup"><span data-stu-id="01135-128">In the **New Project** window, click **ASP.NET MVC 3 Web Application**.</span></span>  
  
3. <span data-ttu-id="01135-129">Do **název**zadejte `TestApp` a stiskněte **OK**.</span><span class="sxs-lookup"><span data-stu-id="01135-129">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4. <span data-ttu-id="01135-130">V dialogovém okně **Nový projekt ASP.NET MVC 3** vyberte možnost **Internet aplikace** z dostupných šablon, ověřte, zda je **modul zobrazení** nastaven na hodnotu **Razor**, a poté klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="01135-130">In the **New ASP.NET MVC 3 Project** dialog, select **Internet Application** from the available templates, ensure **View Engine** is set to **Razor**, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="01135-131">Po otevření nového projektu klikněte pravým tlačítkem myši na projekt **TestApp** v **Průzkumník řešení** a vyberte možnost **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="01135-131">When the new project opens, right-click the **TestApp** project in **Solution Explorer** and select the **Properties** option.</span></span>  
  
6. <span data-ttu-id="01135-132">Na stránce Vlastnosti projektu klikněte na kartu **Web** vlevo a ujistěte se, že je vybraná možnost **použít místní webový server služby IIS** .</span><span class="sxs-lookup"><span data-stu-id="01135-132">On the project’s properties page, click on the **Web** tab on the left and ensure that the **Use Local IIS Web Server** option is selected.</span></span>  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="01135-133">Krok 2 – konfigurace aplikace ASP.NET MVC pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="01135-133">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
 <span data-ttu-id="01135-134">V tomto kroku přidáte položky konfigurace do konfiguračního souboru *Web. config* webové aplikace ASP.NET MVC, aby se zajistilo, že bude zohledňovat deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="01135-134">In this step you will add configuration entries to the *Web.config* configuration file of your ASP.NET MVC web application to make it claims-aware.</span></span>  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="01135-135">Konfigurace aplikace ASP.NET MVC pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="01135-135">To configure ASP.NET MVC application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="01135-136">Přidejte následující definice konfiguračního oddílu do konfiguračního souboru *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="01135-136">Add the following configuration section definitions to the *Web.config* configuration file.</span></span> <span data-ttu-id="01135-137">Tyto definují konfigurační oddíly, které vyžaduje služba Windows Identity Foundation.</span><span class="sxs-lookup"><span data-stu-id="01135-137">These define configuration sections required by Windows Identity Foundation.</span></span> <span data-ttu-id="01135-138">Přidejte definice hned po  **\<>** počátečního elementu konfigurace:</span><span class="sxs-lookup"><span data-stu-id="01135-138">Add the definitions immediately after the **\<configuration>** opening element:</span></span>  
  
    ```xml  
    <configSections>  
        <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
        <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2. <span data-ttu-id="01135-139">Přidejte > element  **Location,kterýumožňujepřístupkfederačnímmetadatůmaplikace:\<**</span><span class="sxs-lookup"><span data-stu-id="01135-139">Add a **\<location>** element that enables access to the application’s federation metadata:</span></span>  
  
    ```xml  
    <location path="FederationMetadata">  
        <system.web>  
            <authorization>  
                <allow users="*" />  
            </authorization>  
        </system.web>  
    </location>  
    ```  
  
3. <span data-ttu-id="01135-140">Přidejte následující položky konfigurace v rámci  **\<prvků System. Web >** , abyste odepřeli uživatelům, zakázali nativní ověřování a povolili WIF správu ověřování.</span><span class="sxs-lookup"><span data-stu-id="01135-140">Add the following configuration entries within the **\<system.web>** elements to deny users, disable native authentication, and enable WIF to manage authentication.</span></span>  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4. <span data-ttu-id="01135-141">Přidejte následující položky konfigurace související s Windows Identity Foundation a ujistěte se, že se adresa URL a číslo portu vaší aplikace ASP.NET shodují s hodnotami v  **\<položce audienceUris >** Entry, atribut **Realm**  **\<wsFederation prvek >** a  **\<** atribut Reply elementu wsFederation >.</span><span class="sxs-lookup"><span data-stu-id="01135-141">Add the following Windows Identity Foundation related configuration entries and ensure that your ASP.NET application’s URL and port number match the values in the **\<audienceUris>** entry, **realm** attribute of the **\<wsFederation>** element, and the **reply** attribute of the **\<wsFederation>** element.</span></span> <span data-ttu-id="01135-142">Také se ujistěte, že hodnota **vystavitele** odpovídá vaší adrese URL služby tokenů zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="01135-142">Also ensure that the **issuer** value fits your Security Token Service (STS) URL.</span></span>  
  
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
  
5. <span data-ttu-id="01135-143">Přidejte odkaz na <xref:System.IdentityModel> sestavení.</span><span class="sxs-lookup"><span data-stu-id="01135-143">Add reference to the <xref:System.IdentityModel> assembly.</span></span>  
  
6. <span data-ttu-id="01135-144">Zkompilujte řešení, aby se zajistilo, že dojde k chybám.</span><span class="sxs-lookup"><span data-stu-id="01135-144">Compile the solution to make sure there are errors.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="01135-145">Krok 3 – Otestování řešení</span><span class="sxs-lookup"><span data-stu-id="01135-145">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="01135-146">V tomto kroku budete testovat webovou aplikaci ASP.NET MVC nakonfigurovanou pro ověřování založené na deklaracích.</span><span class="sxs-lookup"><span data-stu-id="01135-146">In this step you will test your ASP.NET MVC web application configured for claims-based authentication.</span></span> <span data-ttu-id="01135-147">K provedení základního testu přidáte jednoduchý kód, který zobrazí deklarace identity v tokenu vydaném službou tokenu zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="01135-147">To perform basic test you will add simple code that displays claims in the token issued by the Security Token Service (STS).</span></span>  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="01135-148">Otestování aplikace ASP.NET MVC pro ověřování založené na deklaracích</span><span class="sxs-lookup"><span data-stu-id="01135-148">To test your ASP.NET MVC application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="01135-149">V **Průzkumník řešení**rozbalte složku **Controllers** a otevřete soubor *HomeController.cs* v editoru.</span><span class="sxs-lookup"><span data-stu-id="01135-149">In the **Solution Explorer**, expand the **Controllers** folder and open *HomeController.cs* file in the editor.</span></span> <span data-ttu-id="01135-150">Do metody **index** přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="01135-150">Add the following code to the **Index** method:</span></span>  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2. <span data-ttu-id="01135-151">V **Průzkumník řešení** rozbalte položku **zobrazení** a pak **domovské** složky a v editoru otevřete soubor *index. cshtml* .</span><span class="sxs-lookup"><span data-stu-id="01135-151">In the **Solution Explorer** expand **Views** and then **Home** folders and open *Index.cshtml* file in the editor.</span></span> <span data-ttu-id="01135-152">Odstraňte jeho obsah a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="01135-152">Delete its contents and add the following markup:</span></span>  
  
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
  
3. <span data-ttu-id="01135-153">Spusťte řešení stisknutím klávesy **F5** .</span><span class="sxs-lookup"><span data-stu-id="01135-153">Run the solution by pressing the **F5** key.</span></span>  
  
4. <span data-ttu-id="01135-154">Měla by se zobrazit stránka, která zobrazuje deklarace identity v tokenu, který vám vystavila služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="01135-154">You should be presented with the page that displays the claims in the token that was issued to you by Security Token Service.</span></span>  
  
## <a name="related-items"></a><span data-ttu-id="01135-155">Související položky</span><span class="sxs-lookup"><span data-stu-id="01135-155">Related Items</span></span>  
  
- [<span data-ttu-id="01135-156">Postupy: Sestavování aplikace webových formulářů ASP.NET pracující s deklaracemi pomocí WIF</span><span class="sxs-lookup"><span data-stu-id="01135-156">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>](how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
