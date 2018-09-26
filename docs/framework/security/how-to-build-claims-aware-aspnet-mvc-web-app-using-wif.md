---
title: 'Postupy: Sestavení webové aplikace s deklaracemi identity ASP.NET MVC pomocí WIF'
ms.date: 03/30/2017
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
author: BrucePerlerMS
ms.openlocfilehash: 4a003acbf4e182a0493368b586a3add229d8b526
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47087668"
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a>Postupy: Sestavení webové aplikace s deklaracemi identity ASP.NET MVC pomocí WIF
## <a name="applies-to"></a>Platí pro  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® MVC  
  
## <a name="summary"></a>Souhrn  
 Tento návod obsahuje podrobně popisuje postupy pro vytvoření jednoduché webové aplikace s deklaracemi identity ASP.NET MVC. Také poskytuje pokyny k otestování jednoduché deklaracemi webové aplikace ASP.NET MVC pro úspěšnou implementaci ověřování nezaloženého na deklaracích. Tento návod neobsahuje podrobné pokyny pro vytvoření tokenu služby zabezpečení (STS) a předpokládá, že jste už nakonfigurovali služby tokenů zabezpečení.  
  
## <a name="contents"></a>Obsah  
  
-   Cíle  
  
-   Přehled kroků  
  
-   Krok 1 – Vytvoření aplikace jednoduchý ASP.NET MVC  
  
-   Krok 2 – konfigurace aplikace ASP.NET MVC pro ověřování nezaloženého na deklaracích  
  
-   Krok 3 – Otestování řešení  
  
-   Související položky  
  
## <a name="objectives"></a>Cíle  
  
-   Konfigurace webové aplikace ASP.NET MVC pro ověřování nezaloženého na deklaracích  
  
-   Test úspěšný deklaracemi webové aplikace ASP.NET MVC  
  
## <a name="summary-of-steps"></a>Přehled kroků  
  
-   Krok 1 – Vytvoření aplikace jednoduchý ASP.NET MVC  
  
-   Krok 2 – konfigurace aplikace ASP.NET MVC pro ověřování nezaloženého na deklaracích  
  
-   Krok 3 – Otestování řešení  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a>Krok 1 – Vytvoření aplikace jednoduchý ASP.NET MVC  
 V tomto kroku vytvoříte novou aplikaci ASP.NET MVC.  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a>Chcete-li vytvořit jednoduchou aplikaci ASP.NET MVC  
  
1.  Spusťte sadu Visual Studio a klikněte na tlačítko **souboru**, **nový**a potom **projektu**.  
  
2.  V **nový projekt** okna, klikněte na tlačítko **webové aplikace ASP.NET MVC 3**.  
  
3.  V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.  
  
4.  V **nového projektu ASP.NET MVC 3** dialogového okna, vyberte **internetovou aplikaci** z dostupných šablon, ověřte **zobrazovací modul** je nastavena na **Razor**a potom klikněte na tlačítko **OK**.  
  
5.  Když se nový projekt otevře, klikněte pravým tlačítkem na **TestApp** projekt **Průzkumníka řešení** a vyberte **vlastnosti** možnost.  
  
6.  Na stránce Vlastnosti projektu, klikněte na **webové** kartu na levé straně a ujistěte se, že **použití místní webový Server IIS** je vybraná možnost.  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a>Krok 2 – konfigurace aplikace ASP.NET MVC pro ověřování nezaloženého na deklaracích  
 V tomto kroku přidáte položky konfigurace *Web.config* konfiguračního souboru k němu deklaracemi webové aplikace ASP.NET MVC.  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a>Ke konfiguraci aplikace ASP.NET MVC pro ověřování nezaloženého na deklaracích  
  
1.  Přidejte následující část definice konfigurace a *Web.config* konfigurační soubor. Tyto zásady určují konfigurační oddíly funkce vyžaduje Windows Identity Foundation. Přidat definici ihned po  **\<konfigurace >** počáteční element:  
  
    ```xml  
    <configSections>  
        <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
        <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2.  Přidat  **\<umístění >** element, který umožňuje přístup k federační metadata aplikace:  
  
    ```xml  
    <location path="FederationMetadata">  
        <system.web>  
            <authorization>  
                <allow users="*" />  
            </authorization>  
        </system.web>  
    </location>  
    ```  
  
3.  Přidejte následující položky konfigurace v rámci  **\<system.web >** prvků, které mají odepřít uživatele, zakažte nativní ověřování a povolení WIF ke správě ověřování.  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4.  Přidejte následující technologie Windows Identity Foundation související položky konfigurace a ujistěte se, že adresa URL aplikace ASP.NET a číslo portu odpovídají hodnotám v  **\<audienceUris >** položka, **sféry**  atribut  **\<wsFederation >** elementu a **odpověď** atribut  **\<wsFederation >** elementu. Také zajistěte, aby **vystavitele** hodnota vejde adresu URL svého službu tokenů zabezpečení (STS).  
  
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
  
5.  Přidat odkaz <xref:System.IdentityModel> sestavení.  
  
6.  Řešení, abyste měli jistotu, že nejsou chyby kompilace.  
  
## <a name="step-3--test-your-solution"></a>Krok 3 – Otestování řešení  
 V tomto kroku budete testovat webové aplikace ASP.NET MVC nakonfigurován pro ověřování nezaloženého na deklaracích. Pokud chcete provést základní test bude Přidání jednoduchého kódu, který zobrazí deklarace identity v tokenu vydané Security Token Service (STS).  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a>Chcete-li otestovat aplikaci ASP.NET MVC pro ověřování nezaloženého na deklaracích  
  
1.  V **Průzkumníka řešení**, rozbalte **řadiče** složky a otevřete *HomeController.cs* souboru v editoru. Přidejte následující kód, který **Index** metody:  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2.  V **Průzkumníka řešení** rozbalte **zobrazení** a potom **Domů** složky a otevřete *Index.cshtml* souboru v editoru. Odstraňte její obsah a přidejte následující kód:  
  
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
  
3.  Spuštění řešení stisknutím kombinace kláves **F5** klíč.  
  
4.  Mělo by se zobrazit na stránce zobrazí deklarace identity v tokenu, který byl vydán pro vás služba tokenů zabezpečení.  
  
## <a name="related-items"></a>Související položky  
  
-   [Postupy: Sestavení aplikace Webových formulářů ASP.NET pracující s deklaracemi pomocí WIF](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
