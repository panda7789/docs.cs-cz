---
title: "Vlastní Token obslužné rutiny"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 56fb7fcb162025ec05bc1171cb137d445c4dfee5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="custom-token-handlers"></a>Vlastní Token obslužné rutiny
Toto téma popisuje tokenu obslužné rutiny v WIF a jak se používají ke zpracování tokeny. Téma také popisuje, co je potřeba vytvořit vlastní tokenu obslužné rutiny pro typy tokenů, které nejsou podporované ve výchozím nastavení v WIF.  
  
## <a name="introduction-to-token-handlers-in-wif"></a>Úvod do tokenu obslužné rutiny v WIF  
 WIF spoléhá na token obslužné rutiny zabezpečení k vytváření, čtení, zápisu a ověření tokenů pro předávající stranu aplikace nebo služby tokenů zabezpečení (STS). Token obslužné rutiny jsou body rozšiřitelnosti pro přidání vlastní obslužnou rutinu tokenu v kanálu WIF nebo přizpůsobení způsobu, jakým existující token obslužné rutiny spravuje tokeny. WIF poskytuje devět předdefinovaných zabezpečení tokenu obslužných rutin, které můžete upravit nebo zcela potlačena za účelem změnit funkce v případě potřeby.  
  
## <a name="built-in-security-token-handlers-in-wif"></a>Integrované zabezpečení tokenu obslužné rutiny v WIF  
 WIF 4.5 zahrnuje devět třídy obslužná rutina tokenu zabezpečení, které jsou odvozeny od abstraktní základní třída <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:  
  
-   <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a>Přidání vlastní obslužnou rutinu tokenu  
 Některé typy tokenů, jako jsou jednoduché webové tokeny (SWT) a webové tokeny JSON (JWT) nemají integrovanou tokenu obslužné rutiny, které jsou poskytované WIF. Pro tyto typy tokenů a pro ostatní, které nemají integrovanou obslužnou rutinu musíte provést následující kroky k vytvoření vlastní obslužnou rutinu tokenu.  
  
#### <a name="adding-a-custom-token-handler"></a>Přidání vlastní obslužnou rutinu tokenu  
  
1.  Vytvořte novou třídu odvozenou od <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.  
  
2.  Přepsat tyto metody a zadejte vlastní implementace:  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3.  Přidat odkaz na nové vlastní tokenu obslužná rutina v *Web.config* nebo *App.config* v souboru  **\<system.identityModel >** část, která platí pro WIF. Například následující kód konfigurace určuje nový token obslužná rutina s názvem **MyCustomTokenHandler** který se nachází v **CustomToken** oboru názvů.  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     Všimněte si, že pokud zadáte vlastní tokenu obslužná rutina pro zpracování typ tokenu, který už má integrovanou obslužná rutina tokenu, je nutné přidat  **\<odebrat >** elementu, který chcete vyřadit výchozí obslužnou rutinu a místo toho použít vaší vlastní obslužné rutiny. Například následující konfigurace nahradí výchozí <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> s vlastní tokenu obslužnou rutinou:  
  
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
