---
title: 'Postupy: Transformace příchozích deklarací identit'
ms.date: 03/30/2017
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
author: BrucePerlerMS
ms.openlocfilehash: ce99b97007bf7608856345d6da87cd9e422d2266
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041481"
---
# <a name="how-to-transform-incoming-claims"></a>Postupy: Transformace příchozích deklarací identit

## <a name="applies-to"></a>Platí pro

- Microsoft® Windows® Identity Foundation (WIF)

- Webové formuláře ASP.NET®

## <a name="summary"></a>Souhrn

Tento postup poskytuje podrobné postupy pro vytváření jednoduchých webových formulářů ASP.NET pracujících s deklaracemi a transformují příchozí deklarace identity. Poskytuje také pokyny k otestování aplikace za účelem ověření, zda jsou transformované deklarace uváděny při spuštění aplikace.

## <a name="contents"></a>Obsah

- Cíle

- Přehled

- Přehled kroků

- Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET

- Krok 2 – implementace transformace deklarací pomocí vlastního komponenty ClaimsAuthenticationManager

- Krok 3 – Otestování řešení

## <a name="objectives"></a>Cíle

- Konfigurace aplikace webových formulářů ASP.NET pro ověřování založené na deklaracích

- Transformace příchozích deklarací přidáním deklarace identity role správce

- Otestujte aplikaci webových formulářů ASP.NET, abyste viděli, jestli správně funguje.

## <a name="overview"></a>Přehled

WIF zpřístupňuje třídu s <xref:System.Security.Claims.ClaimsAuthenticationManager> názvem, která umožňuje uživatelům změnit deklarace identity předtím, než se předloží aplikaci předávající strany (RP). <xref:System.Security.Claims.ClaimsAuthenticationManager> Je vhodný pro oddělení obav mezi ověřováním a podkladovým kódem aplikace. Následující příklad ukazuje, jak přidat roli k deklaracím v příchozím <xref:System.Security.Claims.ClaimsPrincipal> , které mohou být požadovány pro RP.

## <a name="summary-of-steps"></a>Přehled kroků

- Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET

- Krok 2 – implementace transformace deklarací pomocí vlastního komponenty ClaimsAuthenticationManager

- Krok 3 – Otestování řešení

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET

V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET.

#### <a name="to-create-a-simple-aspnet-application"></a>Vytvoření jednoduché aplikace ASP.NET

1. Spusťte sadu Visual Studio jako správce v režimu se zvýšenými oprávněními.

2. V aplikaci Visual Studio klikněte na možnost **soubor**, klikněte na možnost **Nový**a poté klikněte na možnost **projekt**.

3. V okně **Nový projekt** klikněte na **ASP.NET webová Formulářová aplikace**.

4. Do **název**zadejte `TestApp` a stiskněte **OK**.

5. V části **Průzkumník řešení**klikněte pravým tlačítkem na projekt **TestApp** a pak vyberte **Identita a přístup**.

6. Zobrazí se okno **Identita a přístup** . Včásti poskytovatelé vyberte **test aplikace pomocí místní služby tokenů pro vývoj**a pak klikněte na **použít**.

7. Ve *výchozím souboru. aspx* nahraďte existující značky následujícím kódem a pak soubor uložte:

    ```aspx-csharp
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

8. Otevřete soubor kódu na pozadí s názvem *Default.aspx.cs*. Nahraďte existující kód následujícím kódem a poté soubor uložte:

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

## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>Krok 2 – implementace transformace deklarací pomocí vlastního komponenty ClaimsAuthenticationManager

V tomto kroku potlačíte výchozí funkce ve <xref:System.Security.Claims.ClaimsAuthenticationManager> třídě, aby se do objektu pro příchozího zabezpečení přidala role správce.

#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>Implementace transformace deklarací pomocí vlastního komponenty ClaimsAuthenticationManager

1. V aplikaci Visual Studio klikněte pravým tlačítkem myši na řešení, klikněte na tlačítko **Přidat**a poté klikněte na možnost **Nový projekt**.

2. V okně **Přidat nový projekt** vyberte v seznamu šablony **vizuálů C#**  položku `ClaimsTransformation` **Knihovna tříd** , zadejte a potom stiskněte **OK**. Vytvoří se nový projekt ve složce řešení.

3. Klikněte pravým tlačítkem na **odkazy** v rámci projektu **ClaimsTransformation** a pak klikněte na **Přidat odkaz**.

4. V okně **Správce odkazů** vyberte **System. IdentityModel**a pak klikněte na **OK**.

5. Otevřete **Class1.cs**, nebo pokud neexistuje, klikněte pravým tlačítkem myši na **ClaimsTransformation**, klikněte na **Přidat**a pak na **Třída...**

6. Do souboru kódu přidejte následující direktivy using:

    ```csharp
    using System.Security.Claims;
    using System.Security.Principal;
    ```

7. Do souboru kódu přidejte následující třídu a metodu.

    > [!WARNING]
    > Následující kód je určen pouze pro demonstrační účely; Ujistěte se, že jste ověřili zamýšlená oprávnění v produkčním kódu.

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

8. Uložte soubor a sestavte projekt **ClaimsTransformation** .

9. V projektu **TestApp** ASP.NET klikněte pravým tlačítkem na odkazy a pak klikněte na **Přidat odkaz**.

10. V okně **Správce odkazů** vyberte v nabídce vlevo možnost **řešení** , z naplněných možností vyberte **ClaimsTransformation** a pak klikněte na **OK**.

11. V kořenovém souboru **Web. config** přejděte na  **\<položku System. IdentityModel >** . Do IdentityConfiguration  **>prvkypřidejtenásledujícířádekauložtesoubor:\<**

    ```xml
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />
    ```

## <a name="step-3--test-your-solution"></a>Krok 3 – Otestování řešení

V tomto kroku otestujete svou aplikaci webových formulářů v ASP.NET a ověříte, že se při přihlášení uživatele k ověřování pomocí formulářů zobrazí deklarace identity.

#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Testování aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování pomocí formulářů

1. Stisknutím klávesy **F5** Sestavte a spusťte aplikaci. Měla by se vám prezentovat *Default. aspx*.

2. Na stránce *Default. aspx* by se měla zobrazit tabulka pod hlavičkou **deklarací identity** , která obsahuje informace ovystaviteli, **OriginalIssuer**, **typu**, **hodnotě**a **ValueType** deklarací identity vašeho účtu. Poslední řádek by měl být prezentován následujícím způsobem:

    ||||||
    |-|-|-|-|-|
    |MÍSTNÍ AUTORITA|MÍSTNÍ AUTORITA|`http://schemas.microsoft.com/ws/2008/06/identity/claims/role`|Správce|<https://www.w3.org/2001/XMLSchema#string>|
