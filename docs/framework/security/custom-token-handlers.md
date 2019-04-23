---
title: Obslužné rutiny vlastních tokenů
ms.date: 03/30/2017
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
author: BrucePerlerMS
ms.openlocfilehash: b6b84271fc450a325270bad5f9e0355fe81a8a5c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975673"
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
  
1. Vytvořte novou třídu, která je odvozena z <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.  
  
2. Přepsat následující metody a zadejte vlastní implementaci:  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3. Přidejte odkaz na nové vlastní obslužnou rutinu tokenu v *Web.config* nebo *App.config* souborů v rámci  **\<system.identityModel >** části, která platí pro technologie WIF. Například následující kód konfigurace určuje nový token obslužná rutina s názvem **MyCustomTokenHandler** , který se nachází **CustomToken** oboru názvů.  
  
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
