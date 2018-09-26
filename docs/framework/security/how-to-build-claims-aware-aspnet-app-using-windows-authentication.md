---
title: 'Postupy: Sestavení aplikace ASP.NET pracující s deklaracemi identity pomocí ověřování Windows'
ms.date: 03/30/2017
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
author: BrucePerlerMS
ms.openlocfilehash: 2c7877c452c729b30029cad1a8e17600f3dc9661
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47112423"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a>Postupy: Sestavení aplikace ASP.NET pracující s deklaracemi identity pomocí ověřování Windows
## <a name="applies-to"></a>Platí pro  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® webových formulářů  
  
## <a name="summary"></a>Souhrn  
 Tento návod obsahuje podrobně popisuje postupy pro vytvoření jednoduché aplikace webových formulářů ASP.NET s deklaracemi identity, která používá ověřování Windows. Také poskytuje pokyny k otestování aplikace ověřit, že jsou předkládány deklarace, když se uživatel přihlásí pomocí ověřování Windows.  
  
## <a name="contents"></a>Obsah  
  
-   Cíle  
  
-   Přehled  
  
-   Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET  
  
-   Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování Windows  
  
-   Krok 3 – Otestování řešení  
  
## <a name="objectives"></a>Cíle  
  
-   Konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování Windows  
  
-   Otestovat aplikaci webových formulářů ASP.NET, abyste viděli, zda pracuje správně  
  
## <a name="overview"></a>Přehled  
 V rozhraní .NET 4.5 WIF a jeho autorizace na základě rolí byly zahrnuty jako součást rozhraní Framework. Dříve, pokud byste chtěli deklarací z uživatele s ASP.NET, jste k instalaci technologie WIF, a potom přetypování rozhraní instančnímu objektu objekty, jako `Thread.CurrentPrincipal` nebo `HttpContext.Current.User`. Nyní deklarace identity jsou obsluhovány automaticky tyto hlavní objekty.  
  
 Ověřování Windows využívaly technologie WIF pro zahrnutí v rozhraní .NET 4.5, protože mají všichni uživatelé automaticky ověřit přihlašovací údaje Windows k nim má přiřazené deklarací identity. Můžete začít používat tyto deklarace okamžitě v aplikaci technologie ASP.NET, která používá ověřování Windows, jak ukazuje tento návod.  
  
## <a name="summary-of-steps"></a>Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET  
  
-   Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování Windows  
  
-   Krok 3 – Otestování řešení  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET  
 V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Chcete-li vytvořit jednoduchou aplikaci ASP.NET  
  
1.  Spusťte sadu Visual Studio a pak klikněte na **souboru**, **nový**a potom **projektu**.  
  
2.  V **nový projekt** okna, klikněte na tlačítko **aplikace webových formulářů ASP.NET**.  
  
3.  V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.  
  
4.  Po **TestApp** projekt je vytvořený, klikněte na něj v **Průzkumníka řešení**. Vlastnosti projektu se zobrazí v **vlastnosti** podokno, níže **Průzkumníka řešení**. Nastavte **ověřování Windows** vlastnost **povoleno**.  
  
    > [!WARNING]
    >  Ve výchozím nastavení nové aplikace ASP.NET je zakázáno ověřování Windows, takže je nutné ručně povolit.  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování Windows  
 V tomto kroku přidáte položku konfigurace pro *Web.config* konfigurační soubor a upravit *Default.aspx* deklarací souboru chcete zobrazit informace o účtu.  
  
#### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a>Ke konfiguraci aplikace ASP.NET pro deklarace identity pomocí ověřování Windows  
  
1.  V **TestApp** projektu *Default.aspx* souboru, nahraďte existující kód následujícím kódem:  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"  
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
        <p>  
            This page displays the claims associated with a Windows authenticated user.          
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
  
     Tento krok přidá ovládací prvek GridView pro vaše *Default.aspx* načíst stránku, která naplní se deklarace identity z ověřování Windows.  
  
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
                this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                this.ClaimsGridView.DataBind();  
            }  
        }  
    }  
    ```  
  
     Výše uvedený kód zobrazí deklarace pro ověřeného uživatele.  
  
3.  Chcete-li změnit typ ověřování vaší aplikace, změnit  **\<ověřování >** blokovat  **\<system.web >** části kořen projektu  *Soubor Web.config* souboru tak, že obsahují pouze následující položku konfigurace:  
  
    ```xml  
    <authentication mode="Windows" />  
    ```  
  
4.  Nakonec upravte  **\<autorizace >** blokovat  **\<system.web >** části stejného *Web.config* souboru k vynucení ověřování:  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    ```  
  
## <a name="step-3--test-your-solution"></a>Krok 3 – Otestování řešení  
 V tomto kroku otestujte aplikaci webových formulářů ASP.NET a ověřte, že jsou předkládány deklarace, když se uživatel přihlásí pomocí ověřování Windows.  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>K testování aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování Windows  
  
1.  Stisknutím klávesy **F5** sestavíte a spustíte aplikaci. Mělo by se zobrazit s *Default.aspx*, a název účtu Windows (včetně názvu domény) už mají zobrazit jako ověřený uživatel v horní části stránky. Na stránce obsahu by měl obsahovat tabulku se deklarace identity načíst z vašeho účtu Windows.
