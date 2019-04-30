---
title: Obslužné rutiny vlastních tokenů
ms.date: 03/30/2017
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
author: BrucePerlerMS
ms.openlocfilehash: b6b84271fc450a325270bad5f9e0355fe81a8a5c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792766"
---
# <a name="custom-token-handlers"></a><span data-ttu-id="62bee-102">Obslužné rutiny vlastních tokenů</span><span class="sxs-lookup"><span data-stu-id="62bee-102">Custom Token Handlers</span></span>
<span data-ttu-id="62bee-103">Toto téma popisuje obslužné rutiny tokenů v technologie WIF a jak se používají ke zpracování tokenů.</span><span class="sxs-lookup"><span data-stu-id="62bee-103">This topic discusses token handlers in WIF and how they are used to process tokens.</span></span> <span data-ttu-id="62bee-104">Téma také popisuje, co je potřebné k vytvoření obslužné rutiny vlastních tokenů pro typy tokenů, které nejsou podporovány ve výchozím nastavení technologie WIF.</span><span class="sxs-lookup"><span data-stu-id="62bee-104">The topic also covers what is necessary to create custom token handlers for token types that are not supported by default in WIF.</span></span>  
  
## <a name="introduction-to-token-handlers-in-wif"></a><span data-ttu-id="62bee-105">Úvod do obslužné rutiny tokenů technologie WIF</span><span class="sxs-lookup"><span data-stu-id="62bee-105">Introduction to Token Handlers in WIF</span></span>  
 <span data-ttu-id="62bee-106">Technologie WIF spoléhá na obslužné rutiny tokenů zabezpečení k vytváření, čtení, zápis a ověřovat tokeny pro předávající stranu aplikace nebo služby tokenů zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="62bee-106">WIF relies on security token handlers to create, read, write, and validate tokens for a relying party (RP) application or a security token service (STS).</span></span> <span data-ttu-id="62bee-107">Obslužné rutiny tokenů jsou body rozšiřitelnosti pro přidání obslužné rutiny vlastních tokenů do kanálu WIF nebo přizpůsobení způsobu, jakým spravuje existující token obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="62bee-107">Token handlers are extensibility points for you to add a custom token handler in the WIF pipeline, or to customize the way that an existing token handler manages tokens.</span></span> <span data-ttu-id="62bee-108">Technologie WIF poskytuje devět předdefinovaných obslužné rutiny tokenů zabezpečení, které můžete upravit nebo zcela přepsat funkci podle potřeby změnit.</span><span class="sxs-lookup"><span data-stu-id="62bee-108">WIF provides nine built-in security token handlers that can be modified or entirely overridden to change the functionality as necessary.</span></span>  
  
## <a name="built-in-security-token-handlers-in-wif"></a><span data-ttu-id="62bee-109">Obslužné rutiny tokenů zabezpečení integrované technologie WIF</span><span class="sxs-lookup"><span data-stu-id="62bee-109">Built-In Security Token Handlers in WIF</span></span>  
 <span data-ttu-id="62bee-110">Technologie WIF 4.5 obsahuje devět třídy obslužné rutiny tokenů zabezpečení, které jsou odvozeny od abstraktní základní třída <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span><span class="sxs-lookup"><span data-stu-id="62bee-110">WIF 4.5 includes nine security token handler classes that derive from the abstract base class <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span></span>  
  
- <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a><span data-ttu-id="62bee-111">Přidání obslužné rutiny vlastních tokenů</span><span class="sxs-lookup"><span data-stu-id="62bee-111">Adding a Custom Token Handler</span></span>  
 <span data-ttu-id="62bee-112">Některé typy tokenů, jako je například jednoduchých webových tokenů (SWT) a webové tokeny JSON (JWT) nemají integrovanou obslužné rutiny tokenů poskytované technologie WIF.</span><span class="sxs-lookup"><span data-stu-id="62bee-112">Some token types, such as Simple Web Tokens (SWT) and JSON Web Tokens (JWT) do not have built-in token handlers provided by WIF.</span></span> <span data-ttu-id="62bee-113">Pro tyto typy tokenů a pro ostatní uživatele, které nemají předdefinované obslužnou rutinu je třeba provést následující kroky a vytvoříte vlastní obslužná rutina tokenů.</span><span class="sxs-lookup"><span data-stu-id="62bee-113">For these token types and for others that do not have a built-in handler, you need to perform the following steps to create a custom token handler.</span></span>  
  
#### <a name="adding-a-custom-token-handler"></a><span data-ttu-id="62bee-114">Přidání obslužné rutiny vlastních tokenů</span><span class="sxs-lookup"><span data-stu-id="62bee-114">Adding a custom token handler</span></span>  
  
1. <span data-ttu-id="62bee-115">Vytvořte novou třídu, která je odvozena z <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="62bee-115">Create a new class that derives from <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span></span>  
  
2. <span data-ttu-id="62bee-116">Přepsat následující metody a zadejte vlastní implementaci:</span><span class="sxs-lookup"><span data-stu-id="62bee-116">Override the following methods and provide your own implementation:</span></span>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3. <span data-ttu-id="62bee-117">Přidejte odkaz na nové vlastní obslužnou rutinu tokenu v *Web.config* nebo *App.config* souborů v rámci  **\<system.identityModel >** části, která platí pro technologie WIF.</span><span class="sxs-lookup"><span data-stu-id="62bee-117">Add a reference to the new custom token handler in the *Web.config* or *App.config* file, within the **\<system.identityModel>** section that applies to WIF.</span></span> <span data-ttu-id="62bee-118">Například následující kód konfigurace určuje nový token obslužná rutina s názvem **MyCustomTokenHandler** , který se nachází **CustomToken** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="62bee-118">For example, the following configuration markup specifies a new token handler named **MyCustomTokenHandler** that resides in the **CustomToken** namespace.</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     <span data-ttu-id="62bee-119">Všimněte si, že pokud poskytujete vlastní token obslužné rutiny pro zpracování tokenu typ, který už má integrované obslužná rutina tokenů, budete muset přidat  **\<odebrat >** element vyřadit výchozí obslužnou rutinu a místo toho použít vlastní obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="62bee-119">Note that if you are providing your own token handler to handle a token type that already has a built-in token handler, you need to add a **\<remove>** element to drop the default handler and use your custom handler instead.</span></span> <span data-ttu-id="62bee-120">Například následující konfigurace nahradí výchozí <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> s vlastní obslužná rutina tokenů:</span><span class="sxs-lookup"><span data-stu-id="62bee-120">For example, the following configuration replaces the default <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> with the custom token handler:</span></span>  
  
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
