---
title: 'Postupy: Sestavení aplikace ASP.NET pracující s deklaracemi s ověřováním pomocí formulářů'
ms.date: 03/30/2017
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
author: BrucePerlerMS
ms.openlocfilehash: 75db96a621d7863ef445efb24814111b34da6960
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971839"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a>Postupy: Sestavení aplikace ASP.NET pracující s deklaracemi s ověřováním pomocí formulářů

## <a name="applies-to"></a>Platí pro

- Microsoft® Windows® Identity Foundation (WIF)

- Webové formuláře ASP.NET®

## <a name="summary"></a>Souhrn

V tomto postupu najdete podrobné postupy pro vytváření jednoduchých webových formulářů ASP.NET pracujících s deklaracemi, které používají ověřování pomocí formulářů. Poskytuje také pokyny k otestování aplikace za účelem ověření, že se deklarace identity zobrazí, když se uživatel přihlásí pomocí ověřování pomocí formulářů.

## <a name="contents"></a>Obsah

- Cíle

- Přehled

- Přehled kroků

- Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET

- Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování pomocí formulářů

- Krok 3 – Otestování řešení

## <a name="objectives"></a>Cíle

- Konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování pomocí formulářů

- Otestujte aplikaci webových formulářů ASP.NET, abyste viděli, jestli správně funguje.

## <a name="overview"></a>Přehled

V rozhraní .NET 4,5 se WIF a jeho autorizace na základě deklarace identity zahrnovala jako nedílnou součást rozhraní. Pokud jste dřív potřebovali deklarace identity od uživatele ASP.NET, museli jste nainstalovat WIF a pak přetypování rozhraní na hlavní objekty, jako jsou `Thread.CurrentPrincipal` nebo `HttpContext.Current.User`. Nyní jsou deklarace identity automaticky obsluhovány těmito objekty zabezpečení.

Ověřování pomocí formulářů vyvolalo zařazení do WIF v rozhraní .NET 4,5, protože všichni uživatelé ověření pomocí formulářů mají automaticky přidružené deklarace identity. Tyto deklarace můžete hned začít používat v aplikaci ASP.NET, která používá ověřování pomocí formulářů, jak ukazuje tento postup.

## <a name="summary-of-steps"></a>Přehled kroků

- Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET

- Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování pomocí formulářů

- Krok 3 – Otestování řešení

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET

V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET.

### <a name="to-create-a-simple-aspnet-application"></a>Vytvoření jednoduché aplikace ASP.NET

1. Spusťte Visual Studio a klikněte na **soubor**, **Nový**a pak na **projekt**.

2. V okně **Nový projekt** klikněte na **ASP.NET webová Formulářová aplikace**.

3. Do **název**zadejte `TestApp` a stiskněte **OK**.

## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Krok 2 – konfigurace aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování pomocí formulářů

V tomto kroku přidáte položku konfigurace do konfiguračního souboru *Web. config* a upravíte soubor *Default. aspx* pro zobrazení informací o deklaracích identity pro účet.

### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a>Konfigurace aplikace ASP.NET pro deklarace identity pomocí ověřování pomocí formulářů

1. Ve *výchozím souboru. aspx* nahraďte existující značky následujícím kódem:

    ```aspx
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

    Tento krok přidá ovládací prvek GridView na stránku *Default. aspx* , která bude naplněna deklaracemi načtenými z ověřování pomocí formulářů.

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

                if (claimsPrincipal != null)
                {
                    this.ClaimsGridView.DataSource = claimsPrincipal.Claims;
                    this.ClaimsGridView.DataBind();
                }
            }
        }
    }
    ```

    Výše uvedený kód zobrazí deklarace identity týkající se ověřeného uživatele, včetně uživatelů identifikovaných ověřováním pomocí formulářů.

## <a name="step-3--test-your-solution"></a>Krok 3 – Otestování řešení

V tomto kroku otestujete svou aplikaci webových formulářů v ASP.NET a ověříte, že se při přihlášení uživatele k ověřování pomocí formulářů zobrazí deklarace identity.

### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Testování aplikace webových formulářů ASP.NET pro deklarace identity pomocí ověřování pomocí formulářů

1. Stisknutím klávesy **F5** Sestavte a spusťte aplikaci. Měli byste se dodávat s *Default. aspx*, který má v pravém horním rohu stránky **Registry** a **přihlašovací** odkazy. Klikněte na **zaregistrovat**.

2. Na stránce **zaregistrovat** vytvořte uživatelský účet a pak klikněte na **zaregistrovat**. Váš účet se vytvoří pomocí ověřování pomocí formulářů a automaticky se přihlásíte.

3. Po přesměrování na domovskou stránku byste měli vidět tabulku pod hlavičkou **deklarací identity** , která zahrnuje informace o vystaviteli, **OriginalIssuer**, **typu**, **hodnotě**a **ValueType** deklarací identity. zohledňují.
