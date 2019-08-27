---
title: 'Postupy: Sestavení aplikace ASP.NET pracující s deklaracemi s ověřováním Windows'
ms.date: 03/30/2017
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
author: BrucePerlerMS
ms.openlocfilehash: 34d6c7916b3035e9896b1dd9d7c7d8b3e7b0fcfc
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041001"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a>Postupy: Sestavení aplikace ASP.NET pracující s deklaracemi s ověřováním Windows

## <a name="applies-to"></a>Platí pro

- Microsoft® Windows® Identity Foundation (WIF)

- Webové formuláře ASP.NET®

## <a name="summary"></a>Souhrn

V tomto postupu najdete podrobné postupy pro vytváření jednoduchých webových formulářů ASP.NET pracujících s deklaracemi, které používají ověřování systému Windows. Poskytuje také pokyny k otestování aplikace za účelem ověření, že se deklarace identity zobrazí, když se uživatel přihlásí pomocí ověřování systému Windows.

## <a name="contents"></a>Obsah

- Cíle

- Přehled

- Přehled kroků

- Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET

- Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování systému Windows

- Krok 3 – Otestování řešení

## <a name="objectives"></a>Cíle

- Konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování systému Windows

- Otestujte aplikaci webových formulářů ASP.NET, abyste viděli, jestli správně funguje.

## <a name="overview"></a>Přehled

V rozhraní .NET 4,5 se WIF a jeho autorizace na základě deklarace identity zahrnovala jako nedílnou součást rozhraní. Pokud jste dřív potřebovali deklarace identity od uživatele ASP.NET, museli jste nainstalovat WIF a pak přetypování rozhraní na hlavní objekty, jako jsou `Thread.CurrentPrincipal` nebo `HttpContext.Current.User`. Nyní jsou deklarace identity automaticky obsluhovány těmito objekty zabezpečení.

Ověřování systému Windows přináší WIF zařazení do .NET 4,5, protože pro všechny uživatele ověřené pověřeními systému Windows jsou automaticky přidruženy deklarace. Tyto deklarace můžete hned začít používat v aplikaci ASP.NET, která používá ověřování systému Windows, jak ukazuje tento postup.

## <a name="summary-of-steps"></a>Přehled kroků

- Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET

- Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování systému Windows

- Krok 3 – Otestování řešení

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET

V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET.

### <a name="to-create-a-simple-aspnet-application"></a>Vytvoření jednoduché aplikace ASP.NET

1. Spusťte Visual Studio, klikněte na **soubor**, **Nový**a pak na **projekt**.

2. V okně **Nový projekt** klikněte na **ASP.NET webová Formulářová aplikace**.

3. Do **název**zadejte `TestApp` a stiskněte **OK**.

4. Po vytvoření projektu **TestApp** klikněte na něj v **Průzkumník řešení**. Vlastnosti projektu se zobrazí v podokně **vlastnosti** níže **Průzkumník řešení**. Nastavte vlastnost **ověřování systému Windows** na **povoleno**.

    > [!WARNING]
    > Ověřování systému Windows je ve výchozím nastavení v nových aplikacích ASP.NET zakázané, takže je musíte ručně povolit.

## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování systému Windows

V tomto kroku přidáte položku konfigurace do konfiguračního souboru *Web. config* a upravíte soubor *Default. aspx* pro zobrazení informací o deklaracích identity pro účet.

### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a>Konfigurace aplikace ASP.NET pro deklarace identity pomocí ověřování systému Windows

1. V souboru *Default. aspx* projektu **TestApp** nahraďte existující značky následujícím kódem:

    ```aspx-csharp
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

    Tento krok přidá ovládací prvek GridView na stránku *Default. aspx* , která bude naplněna deklaracemi načtenými z ověřování systému Windows.

2. Uložte soubor *Default. aspx* a pak otevřete jeho soubor kódu na pozadí s názvem *Default.aspx.cs*. Existující kód nahraďte následujícím kódem:

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

    Výše uvedený kód zobrazí deklarace identity týkající se ověřeného uživatele.

3. Chcete-li změnit typ ověřování aplikace, upravte  **\<blok Authentication >** v oddílu  **\<System. Web >** v kořenovém souboru *Web. config* projektu tak, aby obsahoval pouze následující Položka konfigurace:

    ```xml
    <authentication mode="Windows" />
    ```

4. Nakonec upravte  **\<blok autorizačního >** v  **\<oddílu System. Web >** stejného souboru *Web. config* pro vynucení ověřování:

    ```xml
    <authorization>
        <deny users="?" />
    </authorization>
    ```

## <a name="step-3--test-your-solution"></a>Krok 3 – Otestování řešení

V tomto kroku otestujete svou aplikaci webových formulářů v ASP.NET a ověříte, že se při přihlášení uživatele s ověřováním systému Windows zobrazí deklarace identity.

### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>Testování aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování systému Windows

1. Stisknutím klávesy **F5** Sestavte a spusťte aplikaci. Měla by se vám zobrazit stránka *Default. aspx*a název vašeho účtu systému Windows (včetně názvu domény) by se měl v pravém horním rohu stránky zobrazovat jako ověřený uživatel. Obsah stránky by měl obsahovat tabulku vyplněnou deklaracemi, které jste načetli z účtu systému Windows.
