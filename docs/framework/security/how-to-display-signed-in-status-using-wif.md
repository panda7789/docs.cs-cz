---
title: "Postupy: Zobrazení přihlášení pomocí WIF stav"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 494e67b39187a2a38f29f994e17051430d90f708
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-display-signed-in-status-using-wif"></a>Postupy: Zobrazení přihlášení pomocí WIF stav
## <a name="applies-to"></a>Platí pro  
  
-   Microsoft® Windows® Identity Foundation (WIF) 4.5  
  
-   ASP.NET® webových formulářů  
  
## <a name="summary"></a>Souhrn  
 Toto téma popisuje, jak zobrazit přihlašovací stav v aplikaci WIF technologie ASP.NET. WIF poskytuje mechanismus pro provádění vaší aplikace deklaracemi a správu ověřování a autorizace pro prostředky aplikace.  
  
## <a name="contents"></a>Obsah  
  
-   Přehled  
  
-   Přehled kroků  
  
-   Krok 1 – instalace identita a přístup k rozšíření  
  
-   Krok 2 – Vytvoření aplikace předávající strany ASP.NET  
  
-   Krok 3 – povolit místní vývoj služby tokenů zabezpečení pro ověřování uživatelů  
  
-   Krok 4 – upravit zobrazí přihlašovací stav aplikace ASP.NET  
  
-   Krok 5 – Testování integrace mezi WIF a vaše aplikace ASP.NET  
  
## <a name="overview"></a>Přehled  
 Toto téma ukazuje, jak vytvořit jednoduchou aplikaci deklaracemi pomocí WIF a jak lze snadno zobrazit, zda je uživatel přihlášený nebo ne. Následující postup použijte místní službu tokenů zabezpečení vývoj, která je součástí Identity a přístupu k rozšíření sady Visual Studio. Místní služba tokenů zabezpečení vývoj je určený pro testovací a vývojové prostředí zadat jednoduchý metodu integrace deklarace identity do aplikace. Ho by nikdy použít v provozním prostředí, jako neprovádí skutečné ověřování a přihlašovací údaje nejsou nutné. Imperativní kód v následujícím postupu je však stejný pro produkční prostředí aplikace pomocí skutečné ověřování.  
  
## <a name="summary-of-steps"></a>Přehled kroků  
  
-   Krok 1 – instalace identita a přístup k rozšíření  
  
-   Krok 2 – Vytvoření aplikace předávající strany ASP.NET  
  
-   Krok 3 – povolit místní vývoj služby tokenů zabezpečení pro ověřování uživatelů  
  
-   Krok 4 – upravit zobrazí přihlašovací stav aplikace ASP.NET  
  
-   Krok 5 – Testování integrace mezi WIF a vaše aplikace ASP.NET  
  
## <a name="step-1--install-the-identity-and-access-extension"></a>Krok 1 – instalace identita a přístup k rozšíření  
 Tento krok popisuje postup konfigurace identit a přístupu rozšíření pro sadu Visual Studio 2012. Toto rozšíření automatizuje proces konfigurace aplikace komunikovat s koncovými body služby tokenů zabezpečení.  
  
#### <a name="to-install-the-identity-and-access-extension"></a>Chcete-li nainstalovat rozšíření identit a přístupu  
  
1.  Spusťte sadu Visual Studio jako správce v režimu se zvýšenými oprávněními.  
  
2.  V sadě Visual Studio, klikněte na tlačítko **nástroje** a klikněte na tlačítko **Správce rozšíření**. **Správce rozšíření** se zobrazí v okně.  
  
3.  V **Správce rozšíření**, klikněte na tlačítko **Online rozšíření** v levé nabídce pak vyberte **Galerie sady Visual Studio**.  
  
4.  V pravém horním rohu **Správce rozšíření**, vyhledejte *identit a přístupu*.  
  
5.  **Identit a přístupu** položka se zobrazí ve výsledcích hledání. Klikněte na něj a potom klikněte na **Stáhnout**.  
  
6.  **Stáhněte a nainstalujte** otevře se dialogové okno. Pokud souhlasíte s licenčními podmínkami, klikněte na tlačítko **nainstalovat**.  
  
7.  Když **identit a přístupu** rozšíření byla dokončena instalace, restartujte Visual Studio v režimu správce.  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a>Krok 2 – Vytvoření aplikace předávající strany ASP.NET  
 Tento krok popisuje postup vytvoření aplikace webových formulářů ASP.NET, která bude integrovat WIF a předávající stranou.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Chcete-li vytvořit jednoduchou aplikaci ASP.NET  
  
1.  Spuštění sady Visual Studio a klikněte na tlačítko **soubor**, **nový**a potom **projektu**.  
  
2.  V **nový projekt** okně klikněte na tlačítko **aplikaci webových formulářů ASP.NET**.  
  
3.  V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a>Krok 3 – povolit místní vývoj služby tokenů zabezpečení pro ověřování uživatelů  
 Tento krok popisuje, jak povolit místní vývoj služby tokenů zabezpečení ve vaší aplikaci. Pomocí rozšíření identit a přístupu pro sadu Visual Studio je povolena místní služby tokenů zabezpečení pro vývoj.  
  
#### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a>Chcete-li povolit místní služby tokenů zabezpečení pro vývoj v aplikaci ASP.NET  
  
1.  V sadě Visual Studio, klikněte pravým tlačítkem myši **TestApp** projektu v části **Průzkumníku řešení**, pak vyberte **identit a přístupu**.  
  
2.  **Identit a přístupu** se zobrazí v okně. V části **zprostředkovatelé**, vyberte **testování vaší aplikace pomocí místní služby tokenů zabezpečení vývoj**, pak klikněte na tlačítko **použít**.  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a>Krok 4 – upravit zobrazí přihlašovací stav aplikace ASP.NET  
 Tento krok popisuje postup úpravy aplikace ASP.NET dynamicky uvedena informace, zda má aktuální uživatel je přihlášený. Jakmile poskytovatel služby tokenů zabezpečení byl nakonfigurován, WIF zpracovává příchozí deklarace identity. Teď je potřeba nakonfigurovat kódu vaší aplikace zobrazíte výsledek ověřování.  
  
#### <a name="to-display-sign-in-status"></a>Chcete-li zobrazit přihlašovací stav  
  
1.  V sadě Visual Studio, otevřete **Default.aspx** souboru pod **TestApp** projektu.  
  
2.  Nahraďte stávající značky **Default.aspx** soubor s následující kód:  
  
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
  
3.  Uložit **Default.aspx**a pak otevřete jeho kódu na pozadí soubor s názvem **Default.aspx.cs**.  
  
    > [!NOTE]
    >  **Default.aspx.cs** mohou být skryty pod **Default.aspx** v Průzkumníku řešení. Pokud **Default.aspx.cs** nezobrazuje, rozbalte položku **Default.aspx** kliknutím na trojúhelníček vedle sebe.  
  
4.  Nahraďte stávající kód v **Default.aspx.cs** následujícím kódem:  
  
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
  
5.  Uložit **Default.aspx.cs**a sestavení aplikace.  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a>Krok 5 – Testování integrace mezi WIF a vaše aplikace ASP.NET  
 Tento krok popisuje, jak můžete otestovat integrace mezi WIF a vaše aplikace ASP.NET.  
  
#### <a name="to-test-the-integration-between-wif-and-aspnet"></a>K testování integrace mezi WIF a ASP.NET  
  
1.  V sadě Visual Studio, stiskněte klávesu **F5** spustit ladění aplikace. Pokud nejsou nalezeny žádné chyby, otevře se nové okno prohlížeče.  
  
2.  Můžete si všimnout, že bezobslužně přesměruje žádost na službu STS prohlížeče a následně otevírá stránku Default.aspx. Pokud WIF správně nakonfigurovaný, měli byste vidět web zobrazit následující text: **"Přihlášení"**.
