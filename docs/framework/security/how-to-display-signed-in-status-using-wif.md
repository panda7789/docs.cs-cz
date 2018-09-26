---
title: 'Postupy: Zobrazení stavu přihlášení pomocí WIF'
ms.date: 03/30/2017
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
author: BrucePerlerMS
ms.openlocfilehash: 7d3d23dc1f2e081c0a7c53fbdfaef749c9729fd4
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47207082"
---
# <a name="how-to-display-signed-in-status-using-wif"></a>Postupy: Zobrazení stavu přihlášení pomocí WIF
## <a name="applies-to"></a>Platí pro  
  
-   Microsoft Windows® Identity Foundation (WIF) 4.5  
  
-   ASP.NET® webových formulářů  
  
## <a name="summary"></a>Souhrn  
 Toto téma popisuje, jak zobrazit znaménko ve stavu v aplikaci technologie ASP.NET s podporou technologie WIF. Technologie WIF poskytuje mechanismus pro provádění vaší aplikace s deklaracemi identity a správu ověřování a autorizace pro prostředky aplikace.  
  
## <a name="contents"></a>Obsah  
  
-   Přehled  
  
-   Přehled kroků  
  
-   Krok 1 – instalace identita a přístup k rozšíření  
  
-   Krok 2 – Vytvoření aplikace předávající strany ASP.NET  
  
-   Krok 3 – povolit místní služby STS pro vývoj k ověřování uživatelů  
  
-   Krok 4 – upravit svou aplikaci technologie ASP.NET pro zobrazení přihlašovací ve stavu  
  
-   Krok 5 – otestovat integraci technologie WIF a vaše aplikace ASP.NET  
  
## <a name="overview"></a>Přehled  
 Toto téma ukazuje, jak vytvořit jednoduchou aplikaci deklaracemi pomocí technologie WIF a jak lze snadno zobrazit, zda je uživatel přihlášený, nebo ne. V následujících krocích se používá místní službu STS, která je součástí Identity a přístupu k rozšíření sady Visual Studio. Místní službu STS je určená pro vývoj a testování prostředí nabízejí jednoduchý způsob začlenění deklarací do vaší aplikace. To byste nikdy neměli používat v produkčním prostředí, jak neprovádí skutečné ověřování a přihlašovací údaje se nevyžadují. Imperativního kódu v následujícím postupu je však stejný pro aplikace připravené pro produkční prostředí pomocí skutečné ověřování.  
  
## <a name="summary-of-steps"></a>Přehled kroků  
  
-   Krok 1 – instalace identita a přístup k rozšíření  
  
-   Krok 2 – Vytvoření aplikace předávající strany ASP.NET  
  
-   Krok 3 – povolit místní služby STS pro vývoj k ověřování uživatelů  
  
-   Krok 4 – upravit svou aplikaci technologie ASP.NET pro zobrazení přihlašovací ve stavu  
  
-   Krok 5 – otestovat integraci technologie WIF a vaše aplikace ASP.NET  
  
## <a name="step-1--install-the-identity-and-access-extension"></a>Krok 1 – instalace identita a přístup k rozšíření  
 Tento krok popisuje postup konfigurace identit a přístupu rozšíření pro Visual Studio 2012. Toto rozšíření automatizuje proces konfigurace vaší aplikace ke komunikaci s koncovými body služby tokenů zabezpečení.  
  
#### <a name="to-install-the-identity-and-access-extension"></a>Chcete-li nainstalovat rozšíření identit a přístupu  
  
1.  Spusťte sadu Visual Studio jako správce v režimu se zvýšenými oprávněními.  
  
2.  V sadě Visual Studio, klikněte na tlačítko **nástroje** a klikněte na tlačítko **Správce rozšíření**. **Správce rozšíření** zobrazí se okno.  
  
3.  V **Správce rozšíření**, klikněte na tlačítko **Online rozšíření** v levé nabídce vyberte **Galerie sady Visual Studio**.  
  
4.  V pravém horním rohu **Správce rozšíření**, vyhledejte *identit a přístupu*.  
  
5.  **Identit a přístupu** položky se zobrazí ve výsledcích hledání. Klikněte na něj a potom klikněte na tlačítko **Stáhnout**.  
  
6.  **Stáhnout a nainstalovat** se zobrazí dialogové okno. Pokud s licenčními podmínkami souhlasíte, klikněte na tlačítko **nainstalovat**.  
  
7.  Když **identit a přístupu** rozšíření dokončil instalaci, restartujte Visual Studio v režimu správce.  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a>Krok 2 – Vytvoření aplikace předávající strany ASP.NET  
 Tento krok popisuje, jak vytvořit webovou aplikaci webových formulářů ASP.NET, které se integrují s WIF předávající stranu.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Chcete-li vytvořit jednoduchou aplikaci ASP.NET  
  
1.  Spusťte sadu Visual Studio a klikněte na tlačítko **souboru**, **nový**a potom **projektu**.  
  
2.  V **nový projekt** okna, klikněte na tlačítko **aplikace webových formulářů ASP.NET**.  
  
3.  V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a>Krok 3 – povolit místní služby STS pro vývoj k ověřování uživatelů  
 Tento krok popisuje, jak povolit místní službu STS pro vývoj ve vaší aplikaci. Místní službu STS je povolit pomocí rozšíření identit a přístupu pro sadu Visual Studio.  
  
#### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a>Povolit místní službu STS pro vývoj aplikace ASP.NET  
  
1.  V sadě Visual Studio, klikněte pravým tlačítkem myši **TestApp** projektu v části **Průzkumníku řešení**a pak vyberte **identit a přístupu**.  
  
2.  **Identit a přístupu** zobrazí se okno. V části **poskytovatelé**vyberte **testování aplikace s místní službu STS pro vývoj**, pak klikněte na tlačítko **použít**.  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a>Krok 4 – upravit svou aplikaci technologie ASP.NET pro zobrazení přihlašovací ve stavu  
 Tento krok popisuje, jak upravit svou aplikaci ASP.NET dynamicky uvedena informace, zda aktuální uživatel je přihlášený. Jakmile poskytovatel služby tokenů zabezpečení nakonfigurovaný, technologie WIF zpracovává příchozí deklarace identity. Teď musíte nakonfigurovat kódu vaší aplikace k zobrazení výsledku ověřování.  
  
#### <a name="to-display-sign-in-status"></a>Chcete-li zobrazit přihlašování ve stavu  
  
1.  V sadě Visual Studio, otevřete **Default.aspx** soubor **TestApp** projektu.  
  
2.  Nahraďte stávající značky **Default.aspx** souboru následujícím kódem:  
  
    ```  
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
  
3.  Uložit **Default.aspx**a pak otevřete soubor s názvem jeho kódu **Default.aspx.cs**.  
  
    > [!NOTE]
    >  **Default.aspx.cs** může být skrytá pod **Default.aspx** v Průzkumníku řešení. Pokud **Default.aspx.cs** není viditelný, rozbalte **Default.aspx** klepnutím na trojúhelník vedle sebe.  
  
4.  Nahraďte existující kód ve třídě **Default.aspx.cs** následujícím kódem:  
  
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
  
5.  Uložit **Default.aspx.cs**a sestavte aplikaci.  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a>Krok 5 – otestovat integraci technologie WIF a vaše aplikace ASP.NET  
 Tento krok popisuje, jak otestovat integraci technologie WIF a vaše aplikace ASP.NET.  
  
#### <a name="to-test-the-integration-between-wif-and-aspnet"></a>Chcete-li otestovat integraci technologie WIF a ASP.NET  
  
1.  V sadě Visual Studio, stiskněte klávesu **F5** pro spuštění ladění vaší aplikace. Pokud se nenajdou žádné chyby, otevře se nové okno prohlížeče.  
  
2.  Můžete si všimnout, že v prohlížeči tiše přesměruje požadavek na službu STS a pak otevře stránku Default.aspx. Pokud technologie WIF je správně nakonfigurovaná, měli byste vidět web zobrazit následující text: **"Přihlášení"**.
