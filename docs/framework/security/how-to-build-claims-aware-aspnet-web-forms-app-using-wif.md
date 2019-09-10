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
# <a name="how-to-build-claims-aware-aspnet-web-forms-application-using-wif"></a>Postupy: Sestavení aplikace Webových formulářů ASP.NET pracující s deklaracemi pomocí WIF
## <a name="applies-to"></a>Platí pro  
  
- Microsoft® Windows® Identity Foundation (WIF)  
  
- Webové formuláře ASP.NET®  
  
## <a name="summary"></a>Souhrn  
 V tomto postupu najdete podrobné postupy pro vytváření jednoduchých webových formulářů ASP.NET pracujících s deklaracemi. Poskytuje také pokyny pro otestování jednoduchých ověřování ASP.NET webových formulářů pracujících s deklaracemi pro úspěšnou implementaci federovaného ověřování. Tento postup nemá podrobné pokyny k vytvoření služby tokenů zabezpečení (STS) a předpokládá, že jste už nakonfigurovali STS.  
  
## <a name="contents"></a>Obsah  
  
- Cíle  
  
- Přehled kroků  
  
- Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET  
  
- Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro ověřování založené na deklaracích  
  
- Krok 3 – Otestování řešení  
  
## <a name="objectives"></a>Cíle  
  
- Konfigurace aplikace webových formulářů ASP.NET pro ověřování založené na deklaracích  
  
- Test úspěšných webových formulářů ASP.NET pracujících s deklaracemi  
  
## <a name="summary-of-steps"></a>Přehled kroků  
  
- Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET  
  
- Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro federované ověřování  
  
- Krok 3 – Otestování řešení  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET  
 V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Vytvoření jednoduché aplikace ASP.NET  
  
1. Spusťte Visual Studio a klikněte na **soubor**, **Nový**a pak na **projekt**.  
  
2. V okně **Nový projekt** klikněte na **ASP.NET webová Formulářová aplikace**.  
  
3. Do **název**zadejte `TestApp` a stiskněte **OK**.  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-based-authentication"></a>Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro ověřování založené na deklaracích  
 V tomto kroku přidáte položky konfigurace do konfiguračního souboru *Web. config* vaší aplikace webových formulářů ASP.NET, aby se zajistilo, že bude zohledňovat deklarace identity.  
  
#### <a name="to-configure-aspnet-application-for-claims-based-authentication"></a>Konfigurace aplikace ASP.NET pro ověřování založené na deklaracích  
  
1. Přidejte následující položky konfiguračního oddílu do konfiguračního souboru *Web. config* hned za  **\<konfigurační >** otevření elementu:  
  
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
  
4. Přidejte element System. **webserver >, který definuje moduly pro federované ověřování. \<** Všimněte si, že atribut *PublicKeyToken* musí být stejný jako atribut *PublicKeyToken* pro položky  **\<configSections >** , přidané dříve:  
  
    ```xml  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5. Přidejte následující položky konfigurace související s Windows Identity Foundation a ujistěte se, že se adresa URL a číslo portu vaší aplikace ASP.NET shodují s hodnotami v  **\<položce audienceUris >** Entry, atribut **Realm**  **\<wsFederation prvek >** a  **\<** atribut Reply elementu wsFederation >. Také se ujistěte, že hodnota **vystavitele** odpovídá vaší adrese URL služby tokenů zabezpečení (STS).  
  
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
  
6. Přidejte odkaz na <xref:System.IdentityModel> sestavení.  
  
7. Zkompilujte řešení, abyste se ujistili, že neexistují žádné chyby.  
  
## <a name="step-3--test-your-solution"></a>Krok 3 – Otestování řešení  
 V tomto kroku otestujete svou aplikaci webových formulářů ASP.NET nakonfigurovanou pro ověřování založené na deklaracích. Chcete-li provést základní test, přidejte kód, který zobrazí deklarace identity v tokenu vydaném službou tokenů zabezpečení (STS).  
  
#### <a name="to-test-your-aspnet-web-form-application-for-claims-based-authentication"></a>Testování aplikace webového formuláře v ASP.NET pro ověřování založené na deklaracích  
  
1. V projektu **TestApp** otevřete soubor **Default. aspx** a nahraďte jeho stávající značky následujícím kódem:  
  
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
  
2. Uložte **Default. aspx**a pak otevřete svůj soubor kódu na pozadí s názvem **Default.aspx.cs**.  
  
    > [!NOTE]
    > **Default.aspx.cs** může být skrytá pod **Default. aspx** v Průzkumník řešení. Pokud není **Default.aspx.cs** viditelné, rozbalte **Default. aspx** kliknutím na trojúhelník vedle něho.  
  
3. Nahraďte existující kód v metodě **Page_Load** **Default.aspx.cs** následujícím kódem:  
  
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
  
4. Uložte **Default.aspx.cs**a sestavte řešení.  
  
5. Spusťte řešení stisknutím klávesy **F5** .  
  
6. Měla by se zobrazit stránka, která zobrazuje deklarace identity v tokenu, který jste vystavili pomocí služby tokenu zabezpečení.
