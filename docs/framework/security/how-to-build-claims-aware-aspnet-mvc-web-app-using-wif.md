---
title: 'Postupy: Vytvoření deklaracemi rozhraní ASP.NET MVC webové aplikace pomocí WIF'
ms.date: 03/30/2017
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 146724f31e1d09f09f94d102366539dc79ddfe02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a>Postupy: Vytvoření deklaracemi rozhraní ASP.NET MVC webové aplikace pomocí WIF
## <a name="applies-to"></a>Platí pro  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® MVC  
  
## <a name="summary"></a>Souhrn  
 Tento postup obsahuje podrobné podrobné postupy pro vytvoření jednoduché deklaracemi webové aplikace ASP.NET MVC. Obsahuje také pokyny jak otestování jednoduché deklaracemi webové aplikace ASP.NET MVC pro úspěšné dokončení implementace ověřování na základě deklarace identity. Tento postup nemá podrobné pokyny pro vytvoření tokenu služby zabezpečení (STS) a předpokládá, že jste již nakonfigurovali služby tokenů zabezpečení.  
  
## <a name="contents"></a>Obsah  
  
-   Cíle  
  
-   Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché rozhraní ASP.NET MVC aplikace  
  
-   Krok 2 – konfigurace aplikace ASP.NET MVC pro ověřování založené na deklaracích  
  
-   Krok 3 – Otestování řešení  
  
-   Související položky  
  
## <a name="objectives"></a>Cíle  
  
-   Konfigurovat webovou aplikaci ASP.NET MVC pro ověřování založené na deklaracích  
  
-   Testování úspěšné deklaracemi webové aplikace ASP.NET MVC  
  
## <a name="summary-of-steps"></a>Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché rozhraní ASP.NET MVC aplikace  
  
-   Krok 2 – konfigurace aplikace ASP.NET MVC pro ověřování založené na deklaracích  
  
-   Krok 3 – Otestování řešení  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a>Krok 1 – Vytvoření jednoduché rozhraní ASP.NET MVC aplikace  
 V tomto kroku vytvoříte novou aplikaci ASP.NET MVC.  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a>Chcete-li vytvořit jednoduchou aplikaci ASP.NET MVC  
  
1.  Spuštění sady Visual Studio a klikněte na tlačítko **soubor**, **nový**a potom **projektu**.  
  
2.  V **nový projekt** okně klikněte na tlačítko **webové aplikace ASP.NET MVC 3**.  
  
3.  V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.  
  
4.  V **nový ASP.NET MVC 3 projekt** dialogovém okně, vyberte **Internetové aplikace** z dostupných šablon, zkontrolujte **zobrazovací modul** je nastaven na **Razor**a potom klikněte na **OK**.  
  
5.  Když se otevře nový projekt, klikněte pravým tlačítkem myši **TestApp** projektu v **Průzkumníku řešení** a vyberte **vlastnosti** možnost.  
  
6.  Na stránce vlastností projektu, klikněte na **webové** kartě na levé straně a ujistěte se, že **použití místního webového serveru IIS** je vybraná možnost.  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a>Krok 2 – konfigurace aplikace ASP.NET MVC pro ověřování založené na deklaracích  
 V tomto kroku budete přidávat položky konfigurace určené k *Web.config* konfigurační soubor webové aplikace ASP.NET MVC, aby pracujícím s deklaracemi.  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a>Ke konfiguraci aplikace ASP.NET MVC pro ověřování založené na deklaracích  
  
1.  Přidejte následující definice část konfigurace k *Web.config* konfigurační soubor. Tyto zásady určují konfiguračních oddílů, vyžaduje technologie Windows Identity Foundation. Přidání definice okamžitě po  **\<konfigurace >** otevírání element:  
  
    ```xml  
    <configSections>  
        <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
        <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2.  Přidat  **\<umístění >** element, který umožňuje přístup k metadatům federace aplikace:  
  
    ```xml  
    <location path="FederationMetadata">  
        <system.web>  
            <authorization>  
                <allow users="*" />  
            </authorization>  
        </system.web>  
    </location>  
    ```  
  
3.  Přidejte následující položky konfigurace v rámci  **\<system.web >** prvků tak, aby odepřel uživatelů, zakažte nativní ověřování a povolit WIF ke správě ověřování.  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4.  Přidejte následující technologie Windows Identity Foundation související položky konfigurace a ujistěte se, že vaše aplikace ASP.NET adresu URL a číslo portu shodují s hodnotami v  **\<audienceUris >** položky **sféry**  atribut  **\<wsFederation >** elementu a **odpověď** atribut  **\<wsFederation >** elementu. Také zkontrolujte, zda **vystavitele** hodnota odpovídá adresu URL vašeho tokenu služby zabezpečení (STS).  
  
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
  
5.  Přidat odkaz na <xref:System.IdentityModel> sestavení.  
  
6.  Řešení a ujistěte se, že se chyby kompilace.  
  
## <a name="step-3--test-your-solution"></a>Krok 3 – Otestování řešení  
 V tomto kroku budete testovat webové aplikace ASP.NET MVC, který je nakonfigurován pro ověřování založené na deklaracích identity. Pokud chcete provést základní test přidáte jednoduchý kód, který zobrazí deklarace identity v tokenem vydaným Security Token Service (STS).  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a>K testování aplikace ASP.NET MVC pro ověřování založené na deklaracích  
  
1.  V **Průzkumníku řešení**, rozbalte **řadiče** složky a otevřete *HomeController.cs* souboru v editoru. Přidejte následující kód, který **Index** metoda:  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2.  V **Průzkumníku řešení** rozbalte **zobrazení** a potom **Domů** složky a otevřete *Index.cshtml* souboru v editoru. Odstraňte její obsah a přidejte následující kód:  
  
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
  
3.  Spuštění řešení stisknutím **F5** klíč.  
  
4.  By se měla zobrazit stránky, které se zobrazí deklarace identity v tokenu, který byl vydán pomocí služby tokenů zabezpečení.  
  
## <a name="related-items"></a>Související položky  
  
-   [Postupy: Sestavení aplikace Webových formulářů ASP.NET pracující s deklaracemi pomocí WIF](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
