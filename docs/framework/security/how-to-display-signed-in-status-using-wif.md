---
title: 'Postupy: Zobrazení stavu přihlášení pomocí WIF'
ms.date: 03/30/2017
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
author: BrucePerlerMS
ms.openlocfilehash: d2500c6ded485fca76715425b9a52258e07be08d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851568"
---
# <a name="how-to-display-signed-in-status-using-wif"></a>Postupy: Zobrazení stavu přihlášení pomocí WIF
## <a name="applies-to"></a>Platí pro  
  
- Microsoft® Windows® Identity Foundation (WIF) 4,5  
  
- Webové formuláře ASP.NET®  
  
## <a name="summary"></a>Souhrn  
 Toto téma popisuje, jak zobrazit stav přihlášení v aplikaci ASP.NET s podporou WIF. WIF poskytuje mechanismus pro poskytování deklarací identity vaší aplikace a správu ověřování a autorizace prostředků aplikace.  
  
## <a name="contents"></a>Obsah  
  
- Přehled  
  
- Přehled kroků  
  
- Krok 1 – instalace rozšíření identity and Access Extension  
  
- Krok 2 – Vytvoření aplikace ASP.NET předávající strany  
  
- Krok 3 – povolení služby STS pro místní vývoj pro ověřování uživatelů  
  
- Krok 4 – Úprava aplikace v ASP.NET pro zobrazení stavu přihlášení  
  
- Krok 5 – testování integrace mezi WIF a aplikací ASP.NET  
  
## <a name="overview"></a>Přehled  
 Toto téma ukazuje, jak vytvořit jednoduchou aplikaci pracující s deklaracemi identity pomocí WIF a jak snadno zobrazit, jestli je uživatel přihlášený nebo ne. V následujících krocích se používá místní vývoj STS, který je součástí identity a přístupu k rozšíření sady Visual Studio. Místní služba STS pro vývoj je určená pro testovací a vývojové prostředí, které poskytuje jednoduchou metodu integrace deklarací identity do vaší aplikace. Nikdy by neměl být použit v produkčním prostředí, protože neprovádí reálné ověřování a přihlašovací údaje nejsou požadovány. Nicméně imperativní kód v následujících krocích je stejný pro aplikaci připravenou pro produkční prostředí pomocí reálného ověřování.  
  
## <a name="summary-of-steps"></a>Přehled kroků  
  
- Krok 1 – instalace rozšíření identity and Access Extension  
  
- Krok 2 – Vytvoření aplikace ASP.NET předávající strany  
  
- Krok 3 – povolení služby STS pro místní vývoj pro ověřování uživatelů  
  
- Krok 4 – Úprava aplikace v ASP.NET pro zobrazení stavu přihlášení  
  
- Krok 5 – testování integrace mezi WIF a aplikací ASP.NET  
  
## <a name="step-1--install-the-identity-and-access-extension"></a>Krok 1 – instalace rozšíření identity and Access Extension  
 Tento krok popisuje, jak nakonfigurovat rozšíření identita a přístup k aplikaci Visual Studio 2012. Toto rozšíření automatizuje proces konfigurace vaší aplikace pro komunikaci s koncovými body služby STS.  
  
### <a name="to-install-the-identity-and-access-extension"></a>Instalace rozšíření identity and Access Extension  
  
1. Spusťte sadu Visual Studio jako správce v režimu se zvýšenými oprávněními.  
  
2. V aplikaci Visual Studio klikněte na **nástroje** a pak na **Správce rozšíření**. Zobrazí se okno **Správce rozšíření** .  
  
3. Ve **Správci rozšíření**klikněte v levé nabídce na **rozšíření online** a pak vyberte **Galerie sady Visual Studio**.  
  
4. V pravém horním rohu **Správce rozšíření**vyhledejte *identitu a přístup*.  
  
5. Položka **Identita a přístup** se zobrazí ve výsledcích hledání. Klikněte na něj a pak klikněte na **Stáhnout**.  
  
6. Zobrazí se dialogové okno **Stáhnout a nainstalovat** . Pokud souhlasíte s licenčními podmínkami, klikněte na **nainstalovat**.  
  
7. Až se instalace rozšíření **identity a přístupu** dokončí, restartujte Visual Studio v režimu správce.  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a>Krok 2 – Vytvoření aplikace ASP.NET předávající strany  
 Tento krok popisuje, jak vytvořit aplikaci webových formulářů ASP.NET předávající strany, která se bude integrovat s WIF.  
  
### <a name="to-create-a-simple-aspnet-application"></a>Vytvoření jednoduché aplikace ASP.NET  
  
1. Spusťte Visual Studio a klikněte na **soubor**, **Nový**a pak na **projekt**.  
  
2. V okně **Nový projekt** klikněte na **ASP.NET webová Formulářová aplikace**.  
  
3. Do **název**zadejte `TestApp` a stiskněte **OK**.  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a>Krok 3 – povolení služby STS pro místní vývoj pro ověřování uživatelů  
 Tento krok popisuje, jak ve vaší aplikaci povolit místní vývoj STS. Místní vývoj STS je povolený pomocí rozšíření identity a přístupu pro Visual Studio.  
  
### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a>Povolení místního vývojového tokenu STS v aplikaci ASP.NET  
  
1. V aplikaci Visual Studio klikněte pravým tlačítkem myši na projekt **TestApp** v části **Průzkumník řešení**a pak vyberte možnost **Identita a přístup**.  
  
2. Zobrazí se okno **Identita a přístup** . V části **poskytovatelé**vyberte **test aplikace pomocí místní služby tokenů pro vývoj**a pak klikněte na **použít**.  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a>Krok 4 – Úprava aplikace v ASP.NET pro zobrazení stavu přihlášení  
 Tento krok popisuje, jak upravit aplikaci v ASP.NET tak, aby dynamicky zobrazovala informace o tom, jestli je aktuální uživatel přihlášený. Po nakonfigurování zprostředkovatele STS WIF zpracuje příchozí deklarace identity. Teď je potřeba nakonfigurovat kód vaší aplikace, aby zobrazoval výsledek ověřování.  
  
### <a name="to-display-sign-in-status"></a>Zobrazení stavu přihlášení  
  
1. V aplikaci Visual Studio otevřete soubor **Default. aspx** v projektu **TestApp** .  
  
2. Nahraďte existující kód ve **výchozím souboru. aspx** následujícím kódem:  
  
    ```aspx-csharp  
    <%@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head runat="server">  
        <title>Logged In Status</title>  
    </head>  
    <body>  
        <asp:label ID="myLabel" runat="server" />  
    </body>  
    </html>  
    ```  
  
3. Uložte **Default. aspx**a pak otevřete svůj soubor kódu na pozadí s názvem **Default.aspx.cs**.  
  
    > [!NOTE]
    > **Default.aspx.cs** může být skrytá pod **Default. aspx** v Průzkumník řešení. Pokud není **Default.aspx.cs** viditelné, rozbalte **Default. aspx** kliknutím na trojúhelník vedle něho.  
  
4. Existující kód nahraďte v **Default.aspx.cs** následujícím kódem:  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        protected void Page_Load(object sender, EventArgs e)  
        {  
            ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
            if (claimsPrincipal != null)  
            {  
                myLabel.Text = "You are signed in.";  
            }  
            else  
            {  
                myLabel.Text = "You are not signed in.";  
            }  
        }  
    }  
    ```  
  
5. Uložte **Default.aspx.cs**a sestavte aplikaci.  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a>Krok 5 – testování integrace mezi WIF a aplikací ASP.NET  
 Tento krok popisuje, jak můžete testovat integraci mezi WIF a aplikací ASP.NET.  
  
### <a name="to-test-the-integration-between-wif-and-aspnet"></a>Otestování integrace mezi WIF a ASP.NET  
  
1. V aplikaci Visual Studio stiskněte klávesu **F5** a spusťte ladění aplikace. Pokud se nenaleznou žádné chyby, otevře se nové okno prohlížeče.  
  
2. Můžete si všimnout, že prohlížeč tiše přesměruje vaši žádost na službu STS a pak otevře stránku Default. aspx. Pokud je WIF správně nakonfigurovaný, měli byste vidět, že se v lokalitě zobrazuje následující text: **Přihlásili jste se**.
