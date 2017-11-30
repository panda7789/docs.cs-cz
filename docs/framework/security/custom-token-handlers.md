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
ms.openlocfilehash: d471e860e74c9a01770c95671401bdbbc23643cb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="custom-token-handlers"></a><span data-ttu-id="078e3-102">Vlastní Token obslužné rutiny</span><span class="sxs-lookup"><span data-stu-id="078e3-102">Custom Token Handlers</span></span>
<span data-ttu-id="078e3-103">Toto téma popisuje tokenu obslužné rutiny v WIF a jak se používají ke zpracování tokeny.</span><span class="sxs-lookup"><span data-stu-id="078e3-103">This topic discusses token handlers in WIF and how they are used to process tokens.</span></span> <span data-ttu-id="078e3-104">Téma také popisuje, co je potřeba vytvořit vlastní tokenu obslužné rutiny pro typy tokenů, které nejsou podporované ve výchozím nastavení v WIF.</span><span class="sxs-lookup"><span data-stu-id="078e3-104">The topic also covers what is necessary to create custom token handlers for token types that are not supported by default in WIF.</span></span>  
  
## <a name="introduction-to-token-handlers-in-wif"></a><span data-ttu-id="078e3-105">Úvod do tokenu obslužné rutiny v WIF</span><span class="sxs-lookup"><span data-stu-id="078e3-105">Introduction to Token Handlers in WIF</span></span>  
 <span data-ttu-id="078e3-106">WIF spoléhá na token obslužné rutiny zabezpečení k vytváření, čtení, zápisu a ověření tokenů pro předávající stranu aplikace nebo služby tokenů zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="078e3-106">WIF relies on security token handlers to create, read, write, and validate tokens for a relying party (RP) application or a security token service (STS).</span></span> <span data-ttu-id="078e3-107">Token obslužné rutiny jsou body rozšiřitelnosti pro přidání vlastní obslužnou rutinu tokenu v kanálu WIF nebo přizpůsobení způsobu, jakým existující token obslužné rutiny spravuje tokeny.</span><span class="sxs-lookup"><span data-stu-id="078e3-107">Token handlers are extensibility points for you to add a custom token handler in the WIF pipeline, or to customize the way that an existing token handler manages tokens.</span></span> <span data-ttu-id="078e3-108">WIF poskytuje devět předdefinovaných zabezpečení tokenu obslužných rutin, které můžete upravit nebo zcela potlačena za účelem změnit funkce v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="078e3-108">WIF provides nine built-in security token handlers that can be modified or entirely overridden to change the functionality as necessary.</span></span>  
  
## <a name="built-in-security-token-handlers-in-wif"></a><span data-ttu-id="078e3-109">Integrované zabezpečení tokenu obslužné rutiny v WIF</span><span class="sxs-lookup"><span data-stu-id="078e3-109">Built-In Security Token Handlers in WIF</span></span>  
 <span data-ttu-id="078e3-110">WIF 4.5 zahrnuje devět třídy obslužná rutina tokenu zabezpečení, které jsou odvozeny od abstraktní základní třída <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span><span class="sxs-lookup"><span data-stu-id="078e3-110">WIF 4.5 includes nine security token handler classes that derive from the abstract base class <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span></span>  
  
-   <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a><span data-ttu-id="078e3-111">Přidání vlastní obslužnou rutinu tokenu</span><span class="sxs-lookup"><span data-stu-id="078e3-111">Adding a Custom Token Handler</span></span>  
 <span data-ttu-id="078e3-112">Některé typy tokenů, jako jsou jednoduché webové tokeny (SWT) a webové tokeny JSON (JWT) nemají integrovanou tokenu obslužné rutiny, které jsou poskytované WIF.</span><span class="sxs-lookup"><span data-stu-id="078e3-112">Some token types, such as Simple Web Tokens (SWT) and JSON Web Tokens (JWT) do not have built-in token handlers provided by WIF.</span></span> <span data-ttu-id="078e3-113">Pro tyto typy tokenů a pro ostatní, které nemají integrovanou obslužnou rutinu musíte provést následující kroky k vytvoření vlastní obslužnou rutinu tokenu.</span><span class="sxs-lookup"><span data-stu-id="078e3-113">For these token types and for others that do not have a built-in handler, you need to perform the following steps to create a custom token handler.</span></span>  
  
#### <a name="adding-a-custom-token-handler"></a><span data-ttu-id="078e3-114">Přidání vlastní obslužnou rutinu tokenu</span><span class="sxs-lookup"><span data-stu-id="078e3-114">Adding a custom token handler</span></span>  
  
1.  <span data-ttu-id="078e3-115">Vytvořte novou třídu odvozenou od <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="078e3-115">Create a new class that derives from <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span></span>  
  
2.  <span data-ttu-id="078e3-116">Přepsat tyto metody a zadejte vlastní implementace:</span><span class="sxs-lookup"><span data-stu-id="078e3-116">Override the following methods and provide your own implementation:</span></span>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3.  <span data-ttu-id="078e3-117">Přidat odkaz na nové vlastní tokenu obslužná rutina v *Web.config* nebo *App.config* v souboru  **\<system.identityModel >** část, která platí pro WIF.</span><span class="sxs-lookup"><span data-stu-id="078e3-117">Add a reference to the new custom token handler in the *Web.config* or *App.config* file, within the **\<system.identityModel>** section that applies to WIF.</span></span> <span data-ttu-id="078e3-118">Například následující kód konfigurace určuje nový token obslužná rutina s názvem **MyCustomTokenHandler** který se nachází v **CustomToken** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="078e3-118">For example, the following configuration markup specifies a new token handler named **MyCustomTokenHandler** that resides in the **CustomToken** namespace.</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     <span data-ttu-id="078e3-119">Všimněte si, že pokud zadáte vlastní tokenu obslužná rutina pro zpracování typ tokenu, který už má integrovanou obslužná rutina tokenu, je nutné přidat  **\<odebrat >** elementu, který chcete vyřadit výchozí obslužnou rutinu a místo toho použít vaší vlastní obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="078e3-119">Note that if you are providing your own token handler to handle a token type that already has a built-in token handler, you need to add a **\<remove>** element to drop the default handler and use your custom handler instead.</span></span> <span data-ttu-id="078e3-120">Například následující konfigurace nahradí výchozí <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> s vlastní tokenu obslužnou rutinou:</span><span class="sxs-lookup"><span data-stu-id="078e3-120">For example, the following configuration replaces the default <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> with the custom token handler:</span></span>  
  
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
