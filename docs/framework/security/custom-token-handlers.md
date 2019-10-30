---
title: Obslužné rutiny vlastních tokenů
ms.date: 03/30/2017
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
author: BrucePerlerMS
ms.openlocfilehash: ccf794b4c229bbc9b40ae7ec2fd649825122cecf
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040561"
---
# <a name="custom-token-handlers"></a>Obslužné rutiny vlastních tokenů
Toto téma popisuje obslužné rutiny tokenů v WIF a způsob jejich použití ke zpracování tokenů. Téma obsahuje také informace o tom, co je potřeba k vytvoření vlastních obslužných rutin tokenů pro typy tokenů, které nejsou ve výchozím nastavení ve WIF podporované.  
  
## <a name="introduction-to-token-handlers-in-wif"></a>Úvod do obslužných rutin tokenů v WIF  
 WIF spoléhá na obslužné rutiny tokenu zabezpečení k vytváření, čtení, zápisu a ověřování tokenů pro aplikaci předávající strany (RP) nebo službě tokenů zabezpečení (STS). Obslužné rutiny tokenu jsou body rozšiřitelnosti pro přidání vlastní obslužné rutiny tokenu v kanálu WIF nebo pro přizpůsobení způsobu, jakým existující obslužná rutina tokenu spravuje tokeny. WIF poskytuje devět vestavěných obslužných rutin tokenů zabezpečení, které je možné upravit nebo zcela přepsat a změnit funkce podle potřeby.  
  
## <a name="built-in-security-token-handlers-in-wif"></a>Integrované obslužné rutiny tokenů zabezpečení v WIF  
 WIF 4,5 zahrnuje devět tříd obslužné rutiny tokenů zabezpečení, které jsou odvozeny od abstraktní základní třídy <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:  
  
- <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a>Přidání obslužné rutiny vlastního tokenu  
 Některé typy tokenů, jako jsou jednoduché webové tokeny (SWT) a webové tokeny JSON (JWT), nemají integrované obslužné rutiny tokenů, které poskytuje WIF. Pro tyto typy tokenů a pro jiné, které nemají vestavěnou obslužnou rutinu, je nutné provést následující kroky a vytvořit vlastní obslužnou rutinu tokenu.  
  
#### <a name="adding-a-custom-token-handler"></a>Přidání obslužné rutiny vlastního tokenu  
  
1. Vytvořte novou třídu, která je odvozena z <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.  
  
2. Přepište následující metody a poskytněte vlastní implementaci:  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3. Přidejte odkaz na novou obslužnou rutinu vlastního tokenu v souboru *Web. config* nebo *App. config* v části **\<System. IdentityModel >** , která se vztahuje na WIF. Například následující kód konfigurace určuje novou obslužnou rutinu tokenu s názvem **MyCustomTokenHandler** , která se nachází v oboru názvů **CustomToken** .  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     Všimněte si, že Pokud poskytujete vlastní obslužnou rutinu tokenu pro zpracování typu tokenu, který již má vestavěnou obslužnou rutinu tokenu, je nutné přidat **\<odebrat >** elementu pro zrušení výchozí obslužné rutiny a místo toho použít vlastní obslužnou rutinu. Například následující konfigurace nahrazuje výchozí <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> vlastní obslužnou rutinou tokenu:  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <remove type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcdefg123456789" />  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```
