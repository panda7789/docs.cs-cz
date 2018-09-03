---
title: 'Postupy: Povolení zjišťování opakování tokenů'
ms.date: 03/30/2017
ms.assetid: 5a9f5771-f5f6-4100-8501-406aa20d731a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: dd5adf39c37fce92d4caf1d85e2a6a12e9e6b59b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486513"
---
# <a name="how-to-enable-token-replay-detection"></a>Postupy: Povolení zjišťování opakování tokenů
## <a name="applies-to"></a>Platí pro  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® webových formulářů  
  
## <a name="summary"></a>Souhrn  
 Tento návod obsahuje podrobně popisuje postupy pro povolení rozpoznání opětovného přehrání tokenu v aplikaci ASP.NET, která pomocí technologie WIF. Také poskytuje pokyny k otestování aplikace ověřit, zda je povoleno rozpoznání opětovného přehrání tokenu. Tento návod neobsahuje podrobné pokyny pro vytvoření služby tokenů zabezpečení (STS) a namísto toho používá službu STS určenou pro vývoj, která je součástí instalace nástroje Identity and Access Tool. Služba STS pro vývoj neprovádí skutečné ověřování a je určena pouze pro testovací účely. Abyste mohli dokončit postupy v tomto návodu, je třeba nainstalovat nástroj Identity and Access Tool. Můžete ho stáhnout z následujícího umístění: [Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)  
  
## <a name="contents"></a>Obsah  
  
-   Cíle  
  
-   Přehled  
  
-   Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché technologie ASP.NET webové formuláře aplikace a povolení zjišťování opakování  
  
-   Krok 2 – otestování řešení  
  
## <a name="objectives"></a>Cíle  
  
-   Vytvořit jednoduchou aplikaci ASP.NET, která používá technologie WIF a služba STS pro vývoj od Identity and Access Tool  
  
-   Povolení rozpoznání opětovného přehrání tokenu a ověření, že je funkční  
  
## <a name="overview"></a>Přehled  
 Opakování útoku nastane, pokud klient pokus o ověření k předávající straně s tokenem služby tokenů zabezpečení, které už klient použil. Aby se zabránilo útoku, obsahuje technologie WIF mezipaměti zjišťování opakování předchozích tokenů služby tokenů zabezpečení. Pokud povolená, rozpoznání opětovného přehrání ověří token příchozího požadavku a ověří, zda token, který byl dříve používali. Pokud token, který se už používá, žádost byla odmítnuta a <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> je vyvolána výjimka.  
  
 Následující kroky ukazují, změny konfigurace, které jsou nutné k povolení zjišťování opakování.  
  
## <a name="summary-of-steps"></a>Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché technologie ASP.NET webové formuláře aplikace a povolení zjišťování opakování  
  
-   Krok 2 – otestování řešení  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-replay-detection"></a>Krok 1 – Vytvoření jednoduché technologie ASP.NET webové formuláře aplikace a povolení zjišťování opakování  
 V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET a upravit *Web.config* souboru k povolení zjišťování opakování.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Chcete-li vytvořit jednoduchou aplikaci ASP.NET  
  
1.  Spusťte sadu Visual Studio a klikněte na tlačítko **souboru**, **nový**a potom **projektu**.  
  
2.  V **nový projekt** okna, klikněte na tlačítko **aplikace webových formulářů ASP.NET**.  
  
3.  V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.  
  
4.  Klikněte pravým tlačítkem myši **TestApp** projektu v rámci **Průzkumníku řešení**a pak vyberte **identit a přístupu**.  
  
5.  **Identit a přístupu** zobrazí se okno. V části **poskytovatelé**vyberte **testování aplikace s místní službu STS pro vývoj**, pak klikněte na tlačítko **použít**.  
  
6.  Přidejte následující  **\<tokenReplayDetection >** elementu *Web.config* bezprostředně následující konfigurační soubor  **\<system.identityModel >** a  **\<identityConfiguration >** prvky, jako jsou zobrazeny:  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <tokenReplayDetection enabled="true"/>  
    ```  
  
## <a name="step-2--test-your-solution"></a>Krok 2 – otestování řešení  
 V tomto kroku otestujete aplikaci technologie ASP.NET s podporou technologie WIF ověřit, že byl povolen rozpoznání opětovného přehrání.  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-replay-detection"></a>Chcete-li otestovat aplikaci technologie ASP.NET s podporou technologie WIF pro rozpoznání opětovného přehrání  
  
1.  Spuštění řešení stisknutím kombinace kláves **F5** klíč. Měli byste se výchozí domovskou stránku ASP.NET a automaticky ověřuje se uživatelské jméno *Terry*, což je výchozí uživatel, který je vrácen služba STS pro vývoj.  
  
2.  Stiskněte v prohlížeči **zpět** tlačítko. By se měla zobrazit pomocí **chyba serveru v aplikaci '/'** stránky s popisem následující: *ID1062: byl zjištěn opakování pro: Token: "System.IdentityModel.Tokens.samlsecuritytoken tak"* , za nímž následuje *AssertionId* a *vystavitele*.  
  
     Tato chybová stránka se zobrazuje, protože výjimku typu <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> byla vyvolána, když byla zjištěna opětovného přehrání tokenu. K této chybě dochází, protože se pokoušíte znovu poslat počáteční požadavek POST převedou token, který byl poprvé. **Zpět** tlačítko nezpůsobí toto chování o následných požadavcích na server.
