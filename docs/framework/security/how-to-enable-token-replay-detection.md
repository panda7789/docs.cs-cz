---
title: 'Postupy: Povolení rozpoznání opětovného přehrání tokenu'
ms.date: 03/30/2017
ms.assetid: 5a9f5771-f5f6-4100-8501-406aa20d731a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b9c187998b4af41e1a56ed9a64625da7e4f95d5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408057"
---
# <a name="how-to-enable-token-replay-detection"></a>Postupy: Povolení rozpoznání opětovného přehrání tokenu
## <a name="applies-to"></a>Platí pro  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® webových formulářů  
  
## <a name="summary"></a>Souhrn  
 Tento postup obsahuje podrobné podrobné postupy pro povolení rozpoznání opětovného přehrání tokenu v aplikaci ASP.NET, která používá technologii WIF. Poskytuje také pokyny, jak otestovat aplikace a ověřte, zda je povoleno rozpoznání opětovného přehrání tokenu. Tento návod neobsahuje podrobné pokyny pro vytvoření služby tokenů zabezpečení (STS) a namísto toho používá službu STS určenou pro vývoj, která je součástí instalace nástroje Identity and Access Tool. Služba STS pro vývoj neprovádí skutečné ověřování a je určena pouze pro testovací účely. Abyste mohli dokončit postupy v tomto návodu, je třeba nainstalovat nástroj Identity and Access Tool. Ho můžete stáhnout z následujícího umístění: [identita a přístup](http://go.microsoft.com/fwlink/?LinkID=245849)  
  
## <a name="contents"></a>Obsah  
  
-   Cíle  
  
-   Přehled  
  
-   Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace a povolte rozpoznání opětovného přehrání  
  
-   Krok 2 – testování řešení  
  
## <a name="objectives"></a>Cíle  
  
-   Vytvořit jednoduchou aplikaci ASP.NET, která používá WIF a vývoj služby tokenů zabezpečení z Identity a přístup  
  
-   Povolení rozpoznání opětovného přehrání tokenu a ověření, že funguje  
  
## <a name="overview"></a>Přehled  
 Opakování útoku nastane, když se klient pokouší ověření předávající strany k tokenu služby tokenů zabezpečení, který klient se již používá. Aby se zabránilo tento útok, obsahuje WIF mezipaměť zjištění opětovného přehrání dřív použité tokeny služby tokenů zabezpečení. Když je povolené, rozpoznání opětovného přehrání tokenu příchozího požadavku zkontroluje a ověřuje, zda je token dřív používal. Pokud token je již používán, žádost byla odmítnuta a <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> je vyvolána výjimka.  
  
 Následující kroky ukazují změny konfigurace vyžaduje, aby se povolilo rozpoznání opětovného přehrání.  
  
## <a name="summary-of-steps"></a>Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace a povolte rozpoznání opětovného přehrání  
  
-   Krok 2 – testování řešení  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-replay-detection"></a>Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace a povolte rozpoznání opětovného přehrání  
 V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET a upravit *Web.config* souboru, aby se povolilo rozpoznání opětovného přehrání.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Chcete-li vytvořit jednoduchou aplikaci ASP.NET  
  
1.  Spuštění sady Visual Studio a klikněte na tlačítko **soubor**, **nový**a potom **projektu**.  
  
2.  V **nový projekt** okně klikněte na tlačítko **aplikaci webových formulářů ASP.NET**.  
  
3.  V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.  
  
4.  Klikněte pravým tlačítkem myši **TestApp** projektu v části **Průzkumníku řešení**, pak vyberte **identit a přístupu**.  
  
5.  **Identit a přístupu** se zobrazí v okně. V části **zprostředkovatelé**, vyberte **testování vaší aplikace pomocí místní služby tokenů zabezpečení vývoj**, pak klikněte na tlačítko **použít**.  
  
6.  Přidejte následující  **\<tokenReplayDetection >** elementu, který chcete *Web.config* okamžitě následující konfigurační soubor  **\<system.identityModel >** a  **\<identityConfiguration >** elementy, zobrazí:  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <tokenReplayDetection enabled="true"/>  
    ```  
  
## <a name="step-2--test-your-solution"></a>Krok 2 – testování řešení  
 V tomto kroku budete testovat aplikace ASP.NET WIF povoleno ověření, že je povoleno rozpoznání opětovného přehrání.  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-replay-detection"></a>K testování aplikace WIF technologie ASP.NET pro rozpoznání opětovného přehrání  
  
1.  Spuštění řešení stisknutím **F5** klíč. Můžete by měl mít výchozí domovskou stránku ASP.NET a automaticky k ověření pomocí uživatelského jména *Terry*, což je výchozí uživatel, který je vrácena službou tokenů zabezpečení vývoj.  
  
2.  V prohlížeči stiskněte **zpět** tlačítko. By se měla zobrazit s **chyba serveru v aplikaci '/'** stránky s popisem následující: *ID1062: opětovného přehrání zjištěna: tokenu: 'System.IdentityModel.Tokens.SamlSecurityToken'* , za nímž následuje *AssertionId* a *vystavitele*.  
  
     Tato chybová stránka se zobrazuje, protože k výjimce typu <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> se vyvolá, když byla zjištěna opětovného přehrání tokenu. K této chybě dojde, protože se pokoušíte znovu odešle počáteční požadavek POST při token byl nejdříve. **Zpět** tlačítko nezpůsobí toto chování na následné požadavky na server.
