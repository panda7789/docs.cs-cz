---
title: 'Postupy: Sestavení s deklaracemi identity aplikace webových formulářů ASP.NET pomocí WIF'
ms.date: 03/30/2017
ms.assetid: efb264dd-f47b-49a9-85ee-9f45d4425765
author: BrucePerlerMS
ms.openlocfilehash: 83b5808ced1bc6243294b23d9784ec7993e3ba4a
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47108127"
---
# <a name="how-to-build-claims-aware-aspnet-web-forms-application-using-wif"></a>Postupy: Sestavení s deklaracemi identity aplikace webových formulářů ASP.NET pomocí WIF
## <a name="applies-to"></a>Platí pro  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® webových formulářů  
  
## <a name="summary"></a>Souhrn  
 Tento návod obsahuje podrobně popisuje postupy pro vytvoření jednoduché s deklaracemi identity aplikace webových formulářů ASP.NET. Obsahuje také pokyny, jak otestovat jednoduchou aplikaci webových formulářů ASP.NET s deklaracemi identity pro úspěšnou implementaci federovaného ověřování. Tento návod neobsahuje podrobné pokyny pro vytvoření tokenu služby zabezpečení (STS) a předpokládá, že jste už nakonfigurovali služby tokenů zabezpečení.  
  
## <a name="contents"></a>Obsah  
  
-   Cíle  
  
-   Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET  
  
-   Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro ověřování nezaloženého na deklaracích  
  
-   Krok 3 – Otestování řešení  
  
## <a name="objectives"></a>Cíle  
  
-   Konfigurovat webovou aplikaci webových formulářů ASP.NET pro ověřování nezaloženého na deklaracích  
  
-   Testování úspěšné s deklaracemi identity aplikace webových formulářů ASP.NET  
  
## <a name="summary-of-steps"></a>Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET  
  
-   Krok 2 – konfigurace aplikace webových formulářů ASP.NET federovaného ověřování  
  
-   Krok 3 – Otestování řešení  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET  
 V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Chcete-li vytvořit jednoduchou aplikaci ASP.NET  
  
1.  Spusťte sadu Visual Studio a klikněte na tlačítko **souboru**, **nový**a potom **projektu**.  
  
2.  V **nový projekt** okna, klikněte na tlačítko **aplikace webových formulářů ASP.NET**.  
  
3.  V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-based-authentication"></a>Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro ověřování nezaloženého na deklaracích  
 V tomto kroku přidáte položky konfigurace *Web.config* konfiguračního souboru k němu s deklaracemi identity aplikace webových formulářů ASP.NET.  
  
#### <a name="to-configure-aspnet-application-for-claims-based-authentication"></a>Ke konfiguraci aplikace ASP.NET pro ověřování nezaloženého na deklaracích  
  
1.  Přidejte následující část položky konfigurace k *Web.config* konfigurační soubor ihned po  **\<konfigurace >** počáteční element:  
  
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
  
4.  Přidat  **\<system.webServer >** element, který definuje moduly federovaného ověřování. Všimněte si, že *PublicKeyToken* atribut musí být stejné jako *PublicKeyToken* atribut pro  **\<configSections >** položky přidané dříve:  
  
    ```xml  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5.  Přidejte následující technologie Windows Identity Foundation související položky konfigurace a ujistěte se, že adresa URL aplikace ASP.NET a číslo portu odpovídají hodnotám v  **\<audienceUris >** položka, **sféry**  atribut  **\<wsFederation >** elementu a **odpověď** atribut  **\<wsFederation >** elementu. Také zajistěte, aby **vystavitele** hodnota vejde adresu URL svého službu tokenů zabezpečení (STS).  
  
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
  
6.  Přidat odkaz <xref:System.IdentityModel> sestavení.  
  
7.  Řešení, abyste měli jistotu, že nejsou žádné chyby kompilace.  
  
## <a name="step-3--test-your-solution"></a>Krok 3 – Otestování řešení  
 V tomto kroku otestujete aplikaci webových formulářů ASP.NET nakonfigurován pro ověřování nezaloženého na deklaracích. Pokud chcete provést základní test, přidáte kód, který zobrazí deklarace identity v tokenu vydané Security Token Service (STS).  
  
#### <a name="to-test-your-aspnet-web-form-application-for-claims-based-authentication"></a>Chcete-li otestovat aplikaci technologie ASP.NET webové formuláře pro ověřování nezaloženého na deklaracích  
  
1.  Otevřít **Default.aspx** soubor **TestApp** projektu a nahraďte jeho existující kód následujícím kódem:  
  
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
  
2.  Uložit **Default.aspx**a pak otevřete soubor s názvem jeho kódu **Default.aspx.cs**.  
  
    > [!NOTE]
    >  **Default.aspx.cs** může být skrytá pod **Default.aspx** v Průzkumníku řešení. Pokud **Default.aspx.cs** není viditelný, rozbalte **Default.aspx** klepnutím na trojúhelník vedle sebe.  
  
3.  Nahraďte existující kód ve třídě **Page_Load** metoda **Default.aspx.cs** následujícím kódem:  
  
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
  
4.  Uložit **Default.aspx.cs**a sestavte řešení.  
  
5.  Spuštění řešení stisknutím kombinace kláves **F5** klíč.  
  
6.  Mělo by se zobrazit na stránce zobrazí deklarace identity v tokenu, který byl vydán pro vás služba tokenů zabezpečení.
