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
# <a name="how-to-build-claims-aware-aspnet-web-forms-application-using-wif"></a>Postupy: Vytvoření aplikace deklaracemi rozhraní ASP.NET Web Forms pomocí WIF
## <a name="applies-to"></a>Platí pro  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® webových formulářů  
  
## <a name="summary"></a>Souhrn  
 Tento postup obsahuje podrobné podrobné postupy pro vytvoření jednoduché deklaracemi identity aplikace webových formulářů ASP.NET. Poskytuje také pokyny, jak k otestování jednoduché deklaracemi identity aplikace webových formulářů ASP.NET pro úspěšné dokončení implementace federovaného ověřování. Tento postup nemá podrobné pokyny pro vytvoření tokenu služby zabezpečení (STS) a předpokládá, že jste již nakonfigurovali služby tokenů zabezpečení.  
  
## <a name="contents"></a>Obsah  
  
-   Cíle  
  
-   Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace  
  
-   Krok 2 – konfigurace aplikaci ASP.NET Web Forms pro ověřování založené na deklaracích  
  
-   Krok 3 – Otestování řešení  
  
## <a name="objectives"></a>Cíle  
  
-   Konfigurace aplikace webových formulářů ASP.NET pro ověřování založené na deklaracích  
  
-   Testování úspěšné deklaracemi identity aplikace webových formulářů ASP.NET  
  
## <a name="summary-of-steps"></a>Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché webové formuláře aplikace ASP.NET  
  
-   Krok 2 – konfigurace aplikaci ASP.NET Web Forms federovaného ověřování  
  
-   Krok 3 – Otestování řešení  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace  
 V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Chcete-li vytvořit jednoduchou aplikaci ASP.NET  
  
1.  Spuštění sady Visual Studio a klikněte na tlačítko **soubor**, **nový**a potom **projektu**.  
  
2.  V **nový projekt** okně klikněte na tlačítko **aplikaci webových formulářů ASP.NET**.  
  
3.  V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-based-authentication"></a>Krok 2 – konfigurace aplikaci ASP.NET Web Forms pro ověřování založené na deklaracích  
 V tomto kroku budete přidávat položky konfigurace určené k *Web.config* konfigurační soubor aplikace webových formulářů ASP.NET, aby pracujícím s deklaracemi.  
  
#### <a name="to-configure-aspnet-application-for-claims-based-authentication"></a>Ke konfiguraci aplikace ASP.NET pro ověřování založené na deklaracích  
  
1.  Následující části položky konfigurace k přidání *Web.config* konfigurační soubor ihned po  **\<konfigurace >** otevírání element:  
  
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
  
4.  Přidat  **\<system.webServer >** element, který definuje moduly federovaného ověřování. Všimněte si, že *PublicKeyToken* atribut musí být stejná jako *PublicKeyToken* atribut pro  **\<configSections >** položky přidali dříve:  
  
    ```xml  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5.  Přidejte následující technologie Windows Identity Foundation související položky konfigurace a ujistěte se, že vaše aplikace ASP.NET adresu URL a číslo portu shodují s hodnotami v  **\<audienceUris >** položky **sféry**  atribut  **\<wsFederation >** elementu a **odpověď** atribut  **\<wsFederation >**elementu. Také zkontrolujte, zda **vystavitele** hodnota odpovídá adresu URL vašeho tokenu služby zabezpečení (STS).  
  
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
  
6.  Přidat odkaz na <xref:System.IdentityModel> sestavení.  
  
7.  Řešení a ujistěte se, že nejsou žádné chyby kompilace.  
  
## <a name="step-3--test-your-solution"></a>Krok 3 – Otestování řešení  
 V tomto kroku budete testovat aplikace webových formulářů ASP.NET nakonfigurovaná pro ověřování založené na deklaracích identity. Pokud chcete provést základní test, přidáte kód, který zobrazí deklarace identity v tokenem vydaným Security Token Service (STS).  
  
#### <a name="to-test-your-aspnet-web-form-application-for-claims-based-authentication"></a>K testování aplikace ASP.NET webového formuláře pro ověřování založené na deklaracích  
  
1.  Otevřete **Default.aspx** souboru pod **TestApp** projektu a nahraďte jeho existující značky následující kód:  
  
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
  
2.  Uložit **Default.aspx**a pak otevřete jeho kódu na pozadí soubor s názvem **Default.aspx.cs**.  
  
    > [!NOTE]
    >  **Default.aspx.cs** mohou být skryty pod **Default.aspx** v Průzkumníku řešení. Pokud **Default.aspx.cs** nezobrazuje, rozbalte položku **Default.aspx** kliknutím na trojúhelníček vedle sebe.  
  
3.  Nahraďte stávající kód v **Page_Load** metodu **Default.aspx.cs** následujícím kódem:  
  
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
  
5.  Spuštění řešení stisknutím **F5** klíč.  
  
6.  By se měla zobrazit stránky, které se zobrazí deklarace identity v tokenu, který byl vydán pomocí služby tokenů zabezpečení.
