---
title: "Postupy: Vytvoření aplikace ASP.NET deklaracemi pomocí ověřování systému Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 1f623cceec04e45d168269379e1af6bdeb573af0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a>Postupy: Vytvoření aplikace ASP.NET deklaracemi pomocí ověřování systému Windows
## <a name="applies-to"></a>Platí pro  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® webových formulářů  
  
## <a name="summary"></a>Souhrn  
 Tento postup obsahuje podrobné podrobné postupy pro vytvoření jednoduché aplikace webových formulářů ASP.NET deklaracemi identity, která používá ověřování systému Windows. Také poskytuje pokyny k testování aplikace pro kontrolu, aby byly poskytovány deklarace identity, když se uživatel přihlásí pomocí ověřování systému Windows.  
  
## <a name="contents"></a>Obsah  
  
-   Cíle  
  
-   Přehled  
  
-   Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace  
  
-   Krok 2 – konfigurace aplikaci ASP.NET Web Forms pro deklarace identity pomocí ověřování systému Windows  
  
-   Krok 3 – Otestování řešení  
  
## <a name="objectives"></a>Cíle  
  
-   Konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování systému Windows  
  
-   Testování aplikace webových formulářů ASP.NET, abyste viděli, zda pracuje správně  
  
## <a name="overview"></a>Přehled  
 V rozhraní .NET 4.5 WIF a její ověření na základě deklarace identity byly zahrnuty jako nedílné součásti rozhraní Framework. Dříve, pokud byste chtěli deklarací z uživatele ASP.NET, bylo nutné instalovat WIF, a pak přetypování rozhraní k objektu zabezpečení objektů, jako `Thread.CurrentPrincipal` nebo `HttpContext.Current.User`. Nyní deklarací identity zpracovává automaticky tyto hlavní objekty.  
  
 Ověřování systému Windows využívaly zahrnutí WIF je v rozhraní .NET 4.5, protože všichni uživatelé ověřit pověření systému Windows automaticky deklarace identity s nimi spojených. Můžete začít používat tyto deklarace okamžitě v aplikaci ASP.NET, která používá ověřování systému Windows, jak ukazuje tento postup.  
  
## <a name="summary-of-steps"></a>Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace  
  
-   Krok 2 – konfigurace aplikaci ASP.NET Web Forms pro deklarace identity pomocí ověřování systému Windows  
  
-   Krok 3 – Otestování řešení  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace  
 V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Chcete-li vytvořit jednoduchou aplikaci ASP.NET  
  
1.  Spuštění sady Visual Studio a pak klikněte na **soubor**, **nový**a potom **projektu**.  
  
2.  V **nový projekt** okně klikněte na tlačítko **aplikaci webových formulářů ASP.NET**.  
  
3.  V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.  
  
4.  Po **TestApp** vytvoření projektu, klikněte na jeho **Průzkumníku řešení**. Vlastnosti projektu se zobrazí v **vlastnosti** podokně níže **Průzkumníku řešení**. Nastavte **ověřování systému Windows** vlastnost **povoleno**.  
  
    > [!WARNING]
    >  Ověřování systému Windows je zakázáno ve výchozím nastavení v nové aplikace ASP.NET, takže je nutné ručně povolit.  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>Krok 2 – konfigurace aplikaci ASP.NET Web Forms pro deklarace identity pomocí ověřování systému Windows  
 V tomto kroku přidáte položku konfigurace do *Web.config* konfigurace soubor a upravte *Default.aspx* deklarací soubor zobrazíte informace o účtu.  
  
#### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a>Ke konfiguraci aplikace ASP.NET pro deklarace identity pomocí ověřování systému Windows  
  
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
  
     Tento krok přidává ovládacího prvku GridView k vaší *Default.aspx* stránky, který vyplní s deklaracemi identity načítají ověřování systému Windows.  
  
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
                this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                this.ClaimsGridView.DataBind();  
            }  
        }  
    }  
    ```  
  
     Ve výše uvedeném kódu se zobrazí deklarace identity o ověřeného uživatele.  
  
3.  Chcete-li změnit typ ověřování aplikace, změnit  **\<ověřování >** blokovat  **\<system.web >** části projektu kořenových  *Soubor Web.config* souboru tak, aby zahrnovala pouze následující položku konfigurace:  
  
    ```xml  
    <authentication mode="Windows" />  
    ```  
  
4.  Nakonec upravte  **\<autorizace >** blokovat  **\<system.web >** části stejné *Web.config* souboru k vynucení ověřování:  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    ```  
  
## <a name="step-3--test-your-solution"></a>Krok 3 – Otestování řešení  
 V tomto kroku testování vaší aplikace webových formulářů ASP.NET a ověřte, že deklarace identity uvádíme, pokud se uživatel přihlásí pomocí ověřování systému Windows.  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>K testování aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování systému Windows  
  
1.  Stiskněte klávesu **F5** sestavení a spuštění aplikace. By se měla zobrazit s *Default.aspx*, a název účtu systému Windows (včetně názvu domény) mají již zobrazit jako ověřený uživatel v horní pravé části stránky. Stránky obsahu by měly obsahovat tabulku vyplněnou deklarace identity načíst z vašeho účtu systému Windows.
