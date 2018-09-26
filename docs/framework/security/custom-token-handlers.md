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
# <a name="custom-token-handlers"></a><span data-ttu-id="3b372-102">Obslužné rutiny vlastních tokenů</span><span class="sxs-lookup"><span data-stu-id="3b372-102">Custom Token Handlers</span></span>
<span data-ttu-id="3b372-103">Toto téma popisuje obslužné rutiny tokenů v technologie WIF a jak se používají ke zpracování tokenů.</span><span class="sxs-lookup"><span data-stu-id="3b372-103">This topic discusses token handlers in WIF and how they are used to process tokens.</span></span> <span data-ttu-id="3b372-104">Téma také popisuje, co je potřebné k vytvoření obslužné rutiny vlastních tokenů pro typy tokenů, které nejsou podporovány ve výchozím nastavení technologie WIF.</span><span class="sxs-lookup"><span data-stu-id="3b372-104">The topic also covers what is necessary to create custom token handlers for token types that are not supported by default in WIF.</span></span>  
  
## <a name="introduction-to-token-handlers-in-wif"></a><span data-ttu-id="3b372-105">Úvod do obslužné rutiny tokenů technologie WIF</span><span class="sxs-lookup"><span data-stu-id="3b372-105">Introduction to Token Handlers in WIF</span></span>  
 <span data-ttu-id="3b372-106">Technologie WIF spoléhá na obslužné rutiny tokenů zabezpečení k vytváření, čtení, zápis a ověřovat tokeny pro předávající stranu aplikace nebo služby tokenů zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="3b372-106">WIF relies on security token handlers to create, read, write, and validate tokens for a relying party (RP) application or a security token service (STS).</span></span> <span data-ttu-id="3b372-107">Obslužné rutiny tokenů jsou body rozšiřitelnosti pro přidání obslužné rutiny vlastních tokenů do kanálu WIF nebo přizpůsobení způsobu, jakým spravuje existující token obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="3b372-107">Token handlers are extensibility points for you to add a custom token handler in the WIF pipeline, or to customize the way that an existing token handler manages tokens.</span></span> <span data-ttu-id="3b372-108">Technologie WIF poskytuje devět předdefinovaných obslužné rutiny tokenů zabezpečení, které můžete upravit nebo zcela přepsat funkci podle potřeby změnit.</span><span class="sxs-lookup"><span data-stu-id="3b372-108">WIF provides nine built-in security token handlers that can be modified or entirely overridden to change the functionality as necessary.</span></span>  
  
## <a name="built-in-security-token-handlers-in-wif"></a><span data-ttu-id="3b372-109">Obslužné rutiny tokenů zabezpečení integrované technologie WIF</span><span class="sxs-lookup"><span data-stu-id="3b372-109">Built-In Security Token Handlers in WIF</span></span>  
 <span data-ttu-id="3b372-110">Technologie WIF 4.5 obsahuje devět třídy obslužné rutiny tokenů zabezpečení, které jsou odvozeny od abstraktní základní třída <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span><span class="sxs-lookup"><span data-stu-id="3b372-110">WIF 4.5 includes nine security token handler classes that derive from the abstract base class <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span></span>  
  
-   <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a><span data-ttu-id="3b372-111">Přidání obslužné rutiny vlastních tokenů</span><span class="sxs-lookup"><span data-stu-id="3b372-111">Adding a Custom Token Handler</span></span>  
 <span data-ttu-id="3b372-112">Některé typy tokenů, jako je například jednoduchých webových tokenů (SWT) a webové tokeny JSON (JWT) nemají integrovanou obslužné rutiny tokenů poskytované technologie WIF.</span><span class="sxs-lookup"><span data-stu-id="3b372-112">Some token types, such as Simple Web Tokens (SWT) and JSON Web Tokens (JWT) do not have built-in token handlers provided by WIF.</span></span> <span data-ttu-id="3b372-113">Pro tyto typy tokenů a pro ostatní uživatele, které nemají předdefinované obslužnou rutinu je třeba provést následující kroky a vytvoříte vlastní obslužná rutina tokenů.</span><span class="sxs-lookup"><span data-stu-id="3b372-113">For these token types and for others that do not have a built-in handler, you need to perform the following steps to create a custom token handler.</span></span>  
  
#### <a name="adding-a-custom-token-handler"></a><span data-ttu-id="3b372-114">Přidání obslužné rutiny vlastních tokenů</span><span class="sxs-lookup"><span data-stu-id="3b372-114">Adding a custom token handler</span></span>  
  
1.  <span data-ttu-id="3b372-115">Vytvořte novou třídu, která je odvozena z <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="3b372-115">Create a new class that derives from <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span></span>  
  
2.  <span data-ttu-id="3b372-116">Přepsat následující metody a zadejte vlastní implementaci:</span><span class="sxs-lookup"><span data-stu-id="3b372-116">Override the following methods and provide your own implementation:</span></span>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3.  <span data-ttu-id="3b372-117">Přidejte odkaz na nové vlastní obslužnou rutinu tokenu v *Web.config* nebo *App.config* souborů v rámci  **\<system.identityModel >** části, která platí pro technologie WIF.</span><span class="sxs-lookup"><span data-stu-id="3b372-117">Add a reference to the new custom token handler in the *Web.config* or *App.config* file, within the **\<system.identityModel>** section that applies to WIF.</span></span> <span data-ttu-id="3b372-118">Například následující kód konfigurace určuje nový token obslužná rutina s názvem **MyCustomTokenHandler** , který se nachází **CustomToken** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3b372-118">For example, the following configuration markup specifies a new token handler named **MyCustomTokenHandler** that resides in the **CustomToken** namespace.</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     <span data-ttu-id="3b372-119">Všimněte si, že pokud poskytujete vlastní token obslužné rutiny pro zpracování tokenu typ, který už má integrované obslužná rutina tokenů, budete muset přidat  **\<odebrat >** element vyřadit výchozí obslužnou rutinu a místo toho použít vlastní obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="3b372-119">Note that if you are providing your own token handler to handle a token type that already has a built-in token handler, you need to add a **\<remove>** element to drop the default handler and use your custom handler instead.</span></span> <span data-ttu-id="3b372-120">Například následující konfigurace nahradí výchozí <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> s vlastní obslužná rutina tokenů:</span><span class="sxs-lookup"><span data-stu-id="3b372-120">For example, the following configuration replaces the default <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> with the custom token handler:</span></span>  
  
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
