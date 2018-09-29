---
title: 'Postupy: Sestavení aplikace ASP.NET pracující s deklaracemi identity pomocí ověřování pomocí formulářů'
ms.date: 03/30/2017
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
author: BrucePerlerMS
ms.openlocfilehash: 8dab5cfbcf14707699e6672017f5f80db232f01d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/29/2018
ms.locfileid: "47454931"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a>Postupy: Sestavení aplikace ASP.NET pracující s deklaracemi identity pomocí ověřování pomocí formulářů
## <a name="applies-to"></a>Platí pro  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® webových formulářů  
  
## <a name="summary"></a>Souhrn  
 Tento návod obsahuje podrobně popisuje postupy pro vytvoření jednoduché aplikace webových formulářů ASP.NET s deklaracemi identity, která používá ověřování pomocí formulářů. Také poskytuje pokyny k otestování aplikace ověřit, že jsou předkládány deklarace, když se uživatel přihlásí pomocí ověřování pomocí formulářů.  
  
## <a name="contents"></a>Obsah  
  
-   Cíle  
  
-   Přehled  
  
-   Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET  
  
-   Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity, ověřování pomocí formulářů  
  
-   Krok 3 – Otestování řešení  
  
## <a name="objectives"></a>Cíle  
  
-   Konfigurace aplikace webových formulářů ASP.NET pro deklarace identity, ověřování pomocí formulářů  
  
-   Otestovat aplikaci webových formulářů ASP.NET, abyste viděli, zda pracuje správně  
  
## <a name="overview"></a>Přehled  
 V rozhraní .NET 4.5 WIF a jeho autorizace na základě rolí byly zahrnuty jako součást rozhraní Framework. Dříve, pokud byste chtěli deklarací z uživatele s ASP.NET, jste k instalaci technologie WIF, a potom přetypování rozhraní instančnímu objektu objekty, jako `Thread.CurrentPrincipal` nebo `HttpContext.Current.User`. Nyní deklarace identity jsou obsluhovány automaticky tyto hlavní objekty.  
  
 Ověřování pomocí formulářů využívaly technologie WIF pro zahrnutí v rozhraní .NET 4.5, protože všichni uživatelé automaticky ověřované formuláře mají deklarace identity k nim má přiřazené. Můžete začít používat tyto deklarace okamžitě v aplikaci technologie ASP.NET, která používá ověřování pomocí formulářů, jak ukazuje tento návod.  
  
## <a name="summary-of-steps"></a>Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET  
  
-   Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity, ověřování pomocí formulářů  
  
-   Krok 3 – Otestování řešení  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET  
 V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Chcete-li vytvořit jednoduchou aplikaci ASP.NET  
  
1.  Spusťte sadu Visual Studio a klikněte na tlačítko **souboru**, **nový**a potom **projektu**.  
  
2.  V **nový projekt** okna, klikněte na tlačítko **aplikace webových formulářů ASP.NET**.  
  
3.  V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity, ověřování pomocí formulářů  
 V tomto kroku přidáte položku konfigurace do *Web.config* konfigurační soubor a upravit *Default.aspx* deklarací souboru chcete zobrazit informace o účtu.  
  
#### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a>Ke konfiguraci aplikace ASP.NET pro deklarace identity, ověřování pomocí formulářů  
  
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
  
     Tento krok přidá ovládací prvek GridView pro vaše *Default.aspx* načíst stránku, která naplní se deklarace identity z ověřování pomocí formulářů.  
  
2.  Uložit *Default.aspx* souboru a pak otevřete jeho použití modelu code-behind soubor s názvem *Default.aspx.cs*. Nahraďte stávající kód následujícím kódem:  
  
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
  
     Výše uvedený kód zobrazí deklarace pro ověřeného uživatele, včetně uživatelů určených ověřování pomocí formulářů.  
  
## <a name="step-3--test-your-solution"></a>Krok 3 – Otestování řešení  
 V tomto kroku otestujte aplikaci webových formulářů ASP.NET a ověřte, že jsou předkládány deklarace, když se uživatel přihlásí pomocí ověřování pomocí formulářů.  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>K testování aplikace webových formulářů ASP.NET pro deklarace identity, ověřování pomocí formulářů  
  
1.  Stisknutím klávesy **F5** sestavíte a spustíte aplikaci. By se měla zobrazit s *Default.aspx*, který má **zaregistrovat** a **přihlášení** odkazy v horní části stránky. Klikněte na tlačítko **zaregistrovat**.  
  
2.  Na **zaregistrovat** stránce, vytvořte uživatelský účet a potom klikněte na **zaregistrovat**. Váš účet se vytvoří pomocí ověřování pomocí formulářů a budete automaticky přihlášení.  
  
3.  Poté, co byli jste přesměrováni na domovskou stránku, měli byste vidět tabulku pod **Your deklarací** nadpis, který obsahuje **vystavitele**, **OriginalIssuer**, **Typ**, **hodnotu**, a **ValueType** deklarací informace o vašem účtu.
