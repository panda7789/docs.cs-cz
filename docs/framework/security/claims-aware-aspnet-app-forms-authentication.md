---
title: 'Postupy: Vytvoření aplikace ASP.NET deklaracemi pomocí ověřování pomocí formulářů'
ms.date: 03/30/2017
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 851a856d291da78265e9eac73e9e06028e24ef2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408616"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a>Postupy: Vytvoření aplikace ASP.NET deklaracemi pomocí ověřování pomocí formulářů
## <a name="applies-to"></a>Platí pro  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® webových formulářů  
  
## <a name="summary"></a>Souhrn  
 Tento postup obsahuje podrobné podrobné postupy pro vytvoření jednoduché aplikace webových formulářů ASP.NET deklaracemi identity, která používá ověřování pomocí formulářů. Také poskytuje pokyny k testování aplikace k ověření, že deklarace identity jsou uvedené Pokud se uživatel přihlásí pomocí ověřování pomocí formulářů.  
  
## <a name="contents"></a>Obsah  
  
-   Cíle  
  
-   Přehled  
  
-   Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace  
  
-   Krok 2 – konfigurace aplikaci ASP.NET Web Forms pro deklarace identity pomocí ověřování pomocí formulářů  
  
-   Krok 3 – Otestování řešení  
  
## <a name="objectives"></a>Cíle  
  
-   Konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování pomocí formulářů  
  
-   Testování aplikace webových formulářů ASP.NET, abyste viděli, zda pracuje správně  
  
## <a name="overview"></a>Přehled  
 V rozhraní .NET 4.5 WIF a její ověření na základě deklarace identity byly zahrnuty jako nedílné součásti rozhraní Framework. Dříve, pokud byste chtěli deklarací z uživatele ASP.NET, bylo nutné instalovat WIF, a pak přetypování rozhraní k objektu zabezpečení objektů, jako `Thread.CurrentPrincipal` nebo `HttpContext.Current.User`. Nyní deklarací identity zpracovává automaticky tyto hlavní objekty.  
  
 Ověřování pomocí formulářů využívaly zahrnutí WIF je v rozhraní .NET 4.5, protože všichni uživatelé ověřit Forms automaticky deklarace identity s nimi spojených. Můžete začít používat tyto deklarace okamžitě v aplikaci ASP.NET, která používá ověřování pomocí formulářů, jak ukazuje tento postup.  
  
## <a name="summary-of-steps"></a>Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace  
  
-   Krok 2 – konfigurace aplikaci ASP.NET Web Forms pro deklarace identity pomocí ověřování pomocí formulářů  
  
-   Krok 3 – Otestování řešení  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace  
 V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Chcete-li vytvořit jednoduchou aplikaci ASP.NET  
  
1.  Spuštění sady Visual Studio a klikněte na tlačítko **soubor**, **nový**a potom **projektu**.  
  
2.  V **nový projekt** okně klikněte na tlačítko **aplikaci webových formulářů ASP.NET**.  
  
3.  V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Krok 2 – konfigurace aplikaci ASP.NET Web Forms pro deklarace identity pomocí ověřování pomocí formulářů  
 V tomto kroku přidáte položku konfigurace do *Web.config* konfigurační soubor a upravit *Default.aspx* deklarací soubor zobrazíte informace o účtu.  
  
#### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a>Ke konfiguraci aplikace ASP.NET pro deklarace identity pomocí ověřování pomocí formulářů  
  
1.  V *Default.aspx* souboru, nahraďte existující kód následujícím kódem:  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
        <p>  
            This page displays the claims associated with a Forms authenticated user.          
        </p>  
        <h3>Your Claims</h3>  
        <p>  
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">  
                <AlternatingRowStyle BackColor="White" />  
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />  
            </asp:GridView>  
        </p>  
    </asp:Content>  
    ```  
  
     Tento krok přidává ovládacího prvku GridView k vaší *Default.aspx* stránky, který vyplní s deklaracemi identity načítají ověřování pomocí formulářů.  
  
2.  Uložit *Default.aspx* souboru a pak otevřete jeho kódu soubor s názvem *Default.aspx.cs*. Nahraďte stávající kód s následujícími službami:  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        public partial class _Default : Page  
        {  
            protected void Page_Load(object sender, EventArgs e)  
            {  
                ClaimsPrincipal claimsPrincipal = Page.User as ClaimsPrincipal;  
  
                if (claimsPrincipal != null)  
                {  
                    this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                    this.ClaimsGridView.DataBind();  
                }  
            }  
        }  
    }  
    ```  
  
     Ve výše uvedeném kódu se zobrazí deklarace identity o ověřeného uživatele, včetně uživatelů se identifikovanou pomocí ověřování pomocí formulářů.  
  
## <a name="step-3--test-your-solution"></a>Krok 3 – Otestování řešení  
 V tomto kroku testování vaší aplikace webových formulářů ASP.NET a ověřte, že deklarace identity jsou uvedené Pokud se uživatel přihlásí pomocí ověřování pomocí formulářů.  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>K testování aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování pomocí formulářů  
  
1.  Stiskněte klávesu **F5** sestavení a spuštění aplikace. By se měla zobrazit s *Default.aspx*, který má **zaregistrovat** a **přihlásit** odkazy v horní pravé části stránky. Klikněte na tlačítko **zaregistrovat**.  
  
2.  Na **zaregistrovat** stránky, vytvořte účet uživatele a pak klikněte na tlačítko **zaregistrovat**. Váš účet se vytvoří pomocí ověřování pomocí formulářů a budete automaticky přihlášení.  
  
3.  Po byla přesměrování na domovskou stránku, měli byste vidět tabulku pod **vaše deklarace identity** záhlaví, která zahrnuje **vystavitele**, **OriginalIssuer**, **Typ**, **hodnotu**, a **ValueType** deklarací informace o vašem účtu.
