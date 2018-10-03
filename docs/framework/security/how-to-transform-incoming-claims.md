---
title: 'Postupy: Transformace příchozích deklarací identity'
ms.date: 03/30/2017
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
author: BrucePerlerMS
ms.openlocfilehash: 8673b4520d9727ae1aa78ef0bc9f435defb02598
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48032332"
---
# <a name="how-to-transform-incoming-claims"></a>Postupy: Transformace příchozích deklarací identity
## <a name="applies-to"></a>Platí pro  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® webových formulářů  
  
## <a name="summary"></a>Souhrn  
 Tento návod obsahuje podrobně popisuje postupy pro vytvoření jednoduché aplikace webových formulářů ASP.NET s deklaracemi identity a transformaci příchozí deklarace identity. Také poskytuje pokyny k otestování aplikace ověřit, že jsou předkládány transformované deklarace při spuštění aplikace.  
  
## <a name="contents"></a>Obsah  
  
-   Cíle  
  
-   Přehled  
  
-   Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET  
  
-   Krok 2 – implementace deklarací identity pomocí vlastní komponenty ClaimsAuthenticationManager transformace  
  
-   Krok 3 – Otestování řešení  
  
## <a name="objectives"></a>Cíle  
  
-   Konfigurace aplikace webových formulářů ASP.NET pro ověřování nezaloženého na deklaracích  
  
-   Transformovat příchozí deklarace identity tak, že přidáte deklaraci identity správce rolí  
  
-   Otestovat aplikaci webových formulářů ASP.NET, abyste viděli, zda pracuje správně  
  
## <a name="overview"></a>Přehled  
 Technologie WIF zpřístupní třídu s názvem <xref:System.Security.Claims.ClaimsAuthenticationManager> , která umožňuje uživatelům změnit deklarace identity, předtím, než se zobrazí na aplikaci předávající stranu. <xref:System.Security.Claims.ClaimsAuthenticationManager> Je užitečné pro oddělení oblastí zájmu mezi ověřování a základního kódu aplikace. Následující příklad ukazuje, jak přidat roli v příchozí deklarace identity <xref:System.Security.Claims.ClaimsPrincipal> , které můžou vyžadovat RP.  
  
## <a name="summary-of-steps"></a>Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET  
  
-   Krok 2 – implementace deklarací identity pomocí vlastní komponenty ClaimsAuthenticationManager transformace  
  
-   Krok 3 – Otestování řešení  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET  
 V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Chcete-li vytvořit jednoduchou aplikaci ASP.NET  
  
1.  Spusťte sadu Visual Studio jako správce v režimu se zvýšenými oprávněními.  
  
2.  V sadě Visual Studio, klikněte na tlačítko **souboru**, klikněte na tlačítko **nový**a potom klikněte na tlačítko **projektu**.  
  
3.  V **nový projekt** okna, klikněte na tlačítko **aplikace webových formulářů ASP.NET**.  
  
4.  V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.  
  
5.  Klikněte pravým tlačítkem myši **TestApp** projektu v rámci **Průzkumníku řešení**a pak vyberte **identit a přístupu**.  
  
6.  **Identit a přístupu** zobrazí se okno. V části **poskytovatelé**vyberte **testování aplikace s místní službu STS pro vývoj**, pak klikněte na tlačítko **použít**.  
  
7.  V *Default.aspx* souboru, nahraďte existující kód následujícím kódem a pak soubor uložte:  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"  
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
          <h3>Your Claims</h3>  
        <p>  
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">  
                <AlternatingRowStyle BackColor="White" />  
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />  
            </asp:GridView>  
        </p>  
    </asp:Content>  
    ```  
  
8.  Otevřete soubor kódu na pozadí s názvem *Default.aspx.cs*. Nahraďte stávající kód následujícím kódem a poté soubor uložte:  
  
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
  
## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>Krok 2 – implementace deklarací identity pomocí vlastní komponenty ClaimsAuthenticationManager transformace  
 V tomto kroku se přepíše výchozí funkce v <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy přidat roli správce příchozí instančnímu objektu.  
  
#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>K implementaci transformace deklarací identity pomocí vlastní komponenty ClaimsAuthenticationManager  
  
1.  V sadě Visual Studio, klikněte pravým tlačítkem myši na řešení, klikněte na tlačítko **přidat**a potom klikněte na **nový projekt**.  
  
2.  V **přidat nový projekt** okně **knihovny tříd** z **Visual C#** šablony seznamu, zadejte `ClaimsTransformation`a potom stiskněte klávesu **OK**. Vytvoří se nový projekt ve složce řešení.  
  
3.  Klikněte pravým tlačítkem na **odkazy** pod **ClaimsTransformation** projektu a pak klikněte na tlačítko **přidat odkaz**.  
  
4.  V **správce odkazů** okně **System.IdentityModel**a potom klikněte na tlačítko **OK**.  
  
5.  Otevřít **Class1.cs**, nebo pokud neexistuje, klikněte pravým tlačítkem na **ClaimsTransformation**, klikněte na tlačítko **přidat**, pak klikněte na tlačítko **třídy...**  
  
6.  Přidejte následující direktivy using do souboru kódu:  
  
    ```csharp  
    using System.Security.Claims;  
    using System.Security.Principal;  
    ```  
  
7.  V souboru kódu přidejte následující třídy a metody.  
  
    > [!WARNING]
    >  Následující kód je pro demonstrační účely. Ujistěte se, že ověřte zamýšlené příslušná oprávnění v produkčním kódu.  
  
    ```csharp  
    public class ClaimsTransformationModule : ClaimsAuthenticationManager  
    {  
        public override ClaimsPrincipal Authenticate(string resourceName, ClaimsPrincipal incomingPrincipal)  
        {  
            if (incomingPrincipal != null && incomingPrincipal.Identity.IsAuthenticated == true)  
            {  
               ((ClaimsIdentity)incomingPrincipal.Identity).AddClaim(new Claim(ClaimTypes.Role, "Admin"));  
            }  
  
            return incomingPrincipal;  
        }  
    }  
    ```  
  
8.  Uložte soubor a sestavení **ClaimsTransformation** projektu.  
  
9. Ve vaší **TestApp** projekt ASP.NET, klikněte pravým tlačítkem na odkazy a pak klikněte na tlačítko **přidat odkaz**.  
  
10. V **správce odkazů** okně **řešení** v levé nabídce vyberte **ClaimsTransformation** mají údaj vyplněný možnosti a pak klikněte na  **OK**.  
  
11. V kořenovém adresáři **Web.config** souboru, přejděte  **\<system.identityModel >** položka. V rámci  **\<identityConfiguration >** prvky, přidejte následující řádek a soubor uložte:  
  
    ```xml  
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />  
    ```  
  
## <a name="step-3--test-your-solution"></a>Krok 3 – Otestování řešení  
 V tomto kroku otestujte aplikaci webových formulářů ASP.NET a ověřte, že jsou předkládány deklarace, když se uživatel přihlásí pomocí ověřování pomocí formulářů.  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>K testování aplikace webových formulářů ASP.NET pro deklarace identity, ověřování pomocí formulářů  
  
1.  Stisknutím klávesy **F5** sestavíte a spustíte aplikaci. Mělo by se zobrazit s *Default.aspx*.  
  
2.  Na *Default.aspx* stránky, měli byste vidět tabulku pod **Your deklarací** nadpis, který obsahuje **vystavitele**, **OriginalIssuer**, **Typ**, **hodnotu**, a **ValueType** deklarací informace o vašem účtu. Poslední řádek by se měla zobrazit následujícím způsobem:  
  
    ||||||  
    |-|-|-|-|-|  
    |MÍSTNÍ AUTORITA|MÍSTNÍ AUTORITA|http://schemas.microsoft.com/ws/2008/06/identity/claims/role|Správce|http://www.w3.org/2001/XMLSchema#string|
