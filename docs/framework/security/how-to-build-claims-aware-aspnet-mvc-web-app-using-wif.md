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
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a>Postupy: Sestavení webové aplikace ASP.NET MVC pracující s deklaracemi pomocí WIF
## <a name="applies-to"></a>Platí pro  
  
- Microsoft® Windows® Identity Foundation (WIF)  
  
- ASP.NET® MVC  
  
## <a name="summary"></a>Souhrn  
 V tomto postupu najdete podrobné postupy pro vytváření jednoduchých webových aplikací ASP.NET MVC, které pracují s deklaracemi. Poskytuje také pokyny k testování jednoduchých webových aplikací s ASP.NET, které pracují s deklaracemi, pro úspěšnou implementaci ověřování založeného na deklaracích identity. Tento postup nemá podrobné pokyny k vytvoření služby tokenů zabezpečení (STS) a předpokládá, že jste už nakonfigurovali STS.  
  
## <a name="contents"></a>Obsah  
  
- Cíle  
  
- Přehled kroků  
  
- Krok 1 – Vytvoření jednoduché aplikace ASP.NET MVC  
  
- Krok 2 – konfigurace aplikace ASP.NET MVC pro ověřování založené na deklaracích  
  
- Krok 3 – Otestování řešení  
  
- Související položky  
  
## <a name="objectives"></a>Cíle  
  
- Konfigurace webové aplikace ASP.NET MVC pro ověřování založené na deklaracích  
  
- Testování úspěšných webových aplikací ASP.NET MVC s podporou deklarací identity  
  
## <a name="summary-of-steps"></a>Přehled kroků  
  
- Krok 1 – Vytvoření jednoduché aplikace ASP.NET MVC  
  
- Krok 2 – konfigurace aplikace ASP.NET MVC pro ověřování založené na deklaracích  
  
- Krok 3 – Otestování řešení  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a>Krok 1 – Vytvoření jednoduché aplikace ASP.NET MVC  
 V tomto kroku vytvoříte novou aplikaci ASP.NET MVC.  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a>Vytvoření jednoduché aplikace ASP.NET MVC  
  
1. Spusťte Visual Studio a klikněte na **soubor**, **Nový**a pak na **projekt**.  
  
2. V okně **Nový projekt** klikněte na **Webová aplikace ASP.NET MVC 3**.  
  
3. Do **název**zadejte `TestApp` a stiskněte **OK**.  
  
4. V dialogovém okně **Nový projekt ASP.NET MVC 3** vyberte možnost **Internet aplikace** z dostupných šablon, ověřte, zda je **modul zobrazení** nastaven na hodnotu **Razor**, a poté klikněte na tlačítko **OK**.  
  
5. Po otevření nového projektu klikněte pravým tlačítkem myši na projekt **TestApp** v **Průzkumník řešení** a vyberte možnost **vlastnosti** .  
  
6. Na stránce Vlastnosti projektu klikněte na kartu **Web** vlevo a ujistěte se, že je vybraná možnost **použít místní webový server služby IIS** .  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a>Krok 2 – konfigurace aplikace ASP.NET MVC pro ověřování založené na deklaracích  
 V tomto kroku přidáte položky konfigurace do konfiguračního souboru *Web. config* webové aplikace ASP.NET MVC, aby se zajistilo, že bude zohledňovat deklarace identity.  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a>Konfigurace aplikace ASP.NET MVC pro ověřování založené na deklaracích  
  
1. Přidejte následující definice konfiguračního oddílu do konfiguračního souboru *Web. config* . Tyto definují konfigurační oddíly, které vyžaduje služba Windows Identity Foundation. Přidejte definice hned po  **\<>** počátečního elementu konfigurace:  
  
    ```xml  
    <configSections>  
        <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
        <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2. Přidejte > element  **Location,kterýumožňujepřístupkfederačnímmetadatůmaplikace:\<**  
  
    ```xml  
    <location path="FederationMetadata">  
        <system.web>  
            <authorization>  
                <allow users="*" />  
            </authorization>  
        </system.web>  
    </location>  
    ```  
  
3. Přidejte následující položky konfigurace v rámci  **\<prvků System. Web >** , abyste odepřeli uživatelům, zakázali nativní ověřování a povolili WIF správu ověřování.  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4. Přidejte následující položky konfigurace související s Windows Identity Foundation a ujistěte se, že se adresa URL a číslo portu vaší aplikace ASP.NET shodují s hodnotami v  **\<položce audienceUris >** Entry, atribut **Realm**  **\<wsFederation prvek >** a  **\<** atribut Reply elementu wsFederation >. Také se ujistěte, že hodnota **vystavitele** odpovídá vaší adrese URL služby tokenů zabezpečení (STS).  
  
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
  
5. Přidejte odkaz na <xref:System.IdentityModel> sestavení.  
  
6. Zkompilujte řešení, aby se zajistilo, že dojde k chybám.  
  
## <a name="step-3--test-your-solution"></a>Krok 3 – Otestování řešení  
 V tomto kroku budete testovat webovou aplikaci ASP.NET MVC nakonfigurovanou pro ověřování založené na deklaracích. K provedení základního testu přidáte jednoduchý kód, který zobrazí deklarace identity v tokenu vydaném službou tokenu zabezpečení (STS).  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a>Otestování aplikace ASP.NET MVC pro ověřování založené na deklaracích  
  
1. V **Průzkumník řešení**rozbalte složku **Controllers** a otevřete soubor *HomeController.cs* v editoru. Do metody **index** přidejte následující kód:  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2. V **Průzkumník řešení** rozbalte položku **zobrazení** a pak **domovské** složky a v editoru otevřete soubor *index. cshtml* . Odstraňte jeho obsah a přidejte následující kód:  
  
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
  
3. Spusťte řešení stisknutím klávesy **F5** .  
  
4. Měla by se zobrazit stránka, která zobrazuje deklarace identity v tokenu, který vám vystavila služba tokenů zabezpečení.  
  
## <a name="related-items"></a>Související položky  
  
- [Postupy: Sestavování aplikace webových formulářů ASP.NET pracující s deklaracemi pomocí WIF](how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
