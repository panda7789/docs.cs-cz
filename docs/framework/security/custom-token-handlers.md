---
title: Obslužné rutiny vlastních tokenů
ms.date: 03/30/2017
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
author: BrucePerlerMS
ms.openlocfilehash: c27abb5df7f895a9dec5f7f784f1a3ff0b31edb7
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082380"
---
# <a name="custom-token-handlers"></a>Obslužné rutiny vlastních tokenů
Toto téma popisuje obslužné rutiny tokenů v technologie WIF a jak se používají ke zpracování tokenů. Téma také popisuje, co je potřebné k vytvoření obslužné rutiny vlastních tokenů pro typy tokenů, které nejsou podporovány ve výchozím nastavení technologie WIF.  
  
## <a name="introduction-to-token-handlers-in-wif"></a>Úvod do obslužné rutiny tokenů technologie WIF  
 Technologie WIF spoléhá na obslužné rutiny tokenů zabezpečení k vytváření, čtení, zápis a ověřovat tokeny pro předávající stranu aplikace nebo služby tokenů zabezpečení (STS). Obslužné rutiny tokenů jsou body rozšiřitelnosti pro přidání obslužné rutiny vlastních tokenů do kanálu WIF nebo přizpůsobení způsobu, jakým spravuje existující token obslužné rutiny tokenů. Technologie WIF poskytuje devět předdefinovaných obslužné rutiny tokenů zabezpečení, které můžete upravit nebo zcela přepsat funkci podle potřeby změnit.  
  
## <a name="built-in-security-token-handlers-in-wif"></a>Obslužné rutiny tokenů zabezpečení integrované technologie WIF  
 Technologie WIF 4.5 obsahuje devět třídy obslužné rutiny tokenů zabezpečení, které jsou odvozeny od abstraktní základní třída <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:  
  
-   <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a>Přidání obslužné rutiny vlastních tokenů  
 Některé typy tokenů, jako je například jednoduchých webových tokenů (SWT) a webové tokeny JSON (JWT) nemají integrovanou obslužné rutiny tokenů poskytované technologie WIF. Pro tyto typy tokenů a pro ostatní uživatele, které nemají předdefinované obslužnou rutinu je třeba provést následující kroky a vytvoříte vlastní obslužná rutina tokenů.  
  
#### <a name="adding-a-custom-token-handler"></a>Přidání obslužné rutiny vlastních tokenů  
  
1.  Vytvořte novou třídu, která je odvozena z <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.  
  
2.  Přepsat následující metody a zadejte vlastní implementaci:  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3.  Přidejte odkaz na nové vlastní obslužnou rutinu tokenu v *Web.config* nebo *App.config* souborů v rámci  **\<system.identityModel >** části, která platí pro technologie WIF. Například následující kód konfigurace určuje nový token obslužná rutina s názvem **MyCustomTokenHandler** , který se nachází **CustomToken** oboru názvů.  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     Všimněte si, že pokud poskytujete vlastní token obslužné rutiny pro zpracování tokenu typ, který už má integrované obslužná rutina tokenů, budete muset přidat  **\<odebrat >** element vyřadit výchozí obslužnou rutinu a místo toho použít vlastní obslužnou rutinu. Například následující konfigurace nahradí výchozí <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> s vlastní obslužná rutina tokenů:  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <remove type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcdefg123456789">  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```
