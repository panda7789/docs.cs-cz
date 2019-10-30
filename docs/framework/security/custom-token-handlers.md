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
# <a name="custom-token-handlers"></a><span data-ttu-id="d94ee-102">Obslužné rutiny vlastních tokenů</span><span class="sxs-lookup"><span data-stu-id="d94ee-102">Custom Token Handlers</span></span>
<span data-ttu-id="d94ee-103">Toto téma popisuje obslužné rutiny tokenů v WIF a způsob jejich použití ke zpracování tokenů.</span><span class="sxs-lookup"><span data-stu-id="d94ee-103">This topic discusses token handlers in WIF and how they are used to process tokens.</span></span> <span data-ttu-id="d94ee-104">Téma obsahuje také informace o tom, co je potřeba k vytvoření vlastních obslužných rutin tokenů pro typy tokenů, které nejsou ve výchozím nastavení ve WIF podporované.</span><span class="sxs-lookup"><span data-stu-id="d94ee-104">The topic also covers what is necessary to create custom token handlers for token types that are not supported by default in WIF.</span></span>  
  
## <a name="introduction-to-token-handlers-in-wif"></a><span data-ttu-id="d94ee-105">Úvod do obslužných rutin tokenů v WIF</span><span class="sxs-lookup"><span data-stu-id="d94ee-105">Introduction to Token Handlers in WIF</span></span>  
 <span data-ttu-id="d94ee-106">WIF spoléhá na obslužné rutiny tokenu zabezpečení k vytváření, čtení, zápisu a ověřování tokenů pro aplikaci předávající strany (RP) nebo službě tokenů zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="d94ee-106">WIF relies on security token handlers to create, read, write, and validate tokens for a relying party (RP) application or a security token service (STS).</span></span> <span data-ttu-id="d94ee-107">Obslužné rutiny tokenu jsou body rozšiřitelnosti pro přidání vlastní obslužné rutiny tokenu v kanálu WIF nebo pro přizpůsobení způsobu, jakým existující obslužná rutina tokenu spravuje tokeny.</span><span class="sxs-lookup"><span data-stu-id="d94ee-107">Token handlers are extensibility points for you to add a custom token handler in the WIF pipeline, or to customize the way that an existing token handler manages tokens.</span></span> <span data-ttu-id="d94ee-108">WIF poskytuje devět vestavěných obslužných rutin tokenů zabezpečení, které je možné upravit nebo zcela přepsat a změnit funkce podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="d94ee-108">WIF provides nine built-in security token handlers that can be modified or entirely overridden to change the functionality as necessary.</span></span>  
  
## <a name="built-in-security-token-handlers-in-wif"></a><span data-ttu-id="d94ee-109">Integrované obslužné rutiny tokenů zabezpečení v WIF</span><span class="sxs-lookup"><span data-stu-id="d94ee-109">Built-In Security Token Handlers in WIF</span></span>  
 <span data-ttu-id="d94ee-110">WIF 4,5 zahrnuje devět tříd obslužné rutiny tokenů zabezpečení, které jsou odvozeny od abstraktní základní třídy <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span><span class="sxs-lookup"><span data-stu-id="d94ee-110">WIF 4.5 includes nine security token handler classes that derive from the abstract base class <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span></span>  
  
- <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a><span data-ttu-id="d94ee-111">Přidání obslužné rutiny vlastního tokenu</span><span class="sxs-lookup"><span data-stu-id="d94ee-111">Adding a Custom Token Handler</span></span>  
 <span data-ttu-id="d94ee-112">Některé typy tokenů, jako jsou jednoduché webové tokeny (SWT) a webové tokeny JSON (JWT), nemají integrované obslužné rutiny tokenů, které poskytuje WIF.</span><span class="sxs-lookup"><span data-stu-id="d94ee-112">Some token types, such as Simple Web Tokens (SWT) and JSON Web Tokens (JWT) do not have built-in token handlers provided by WIF.</span></span> <span data-ttu-id="d94ee-113">Pro tyto typy tokenů a pro jiné, které nemají vestavěnou obslužnou rutinu, je nutné provést následující kroky a vytvořit vlastní obslužnou rutinu tokenu.</span><span class="sxs-lookup"><span data-stu-id="d94ee-113">For these token types and for others that do not have a built-in handler, you need to perform the following steps to create a custom token handler.</span></span>  
  
#### <a name="adding-a-custom-token-handler"></a><span data-ttu-id="d94ee-114">Přidání obslužné rutiny vlastního tokenu</span><span class="sxs-lookup"><span data-stu-id="d94ee-114">Adding a custom token handler</span></span>  
  
1. <span data-ttu-id="d94ee-115">Vytvořte novou třídu, která je odvozena z <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="d94ee-115">Create a new class that derives from <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span></span>  
  
2. <span data-ttu-id="d94ee-116">Přepište následující metody a poskytněte vlastní implementaci:</span><span class="sxs-lookup"><span data-stu-id="d94ee-116">Override the following methods and provide your own implementation:</span></span>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3. <span data-ttu-id="d94ee-117">Přidejte odkaz na novou obslužnou rutinu vlastního tokenu v souboru *Web. config* nebo *App. config* v části **\<System. IdentityModel >** , která se vztahuje na WIF.</span><span class="sxs-lookup"><span data-stu-id="d94ee-117">Add a reference to the new custom token handler in the *Web.config* or *App.config* file, within the **\<system.identityModel>** section that applies to WIF.</span></span> <span data-ttu-id="d94ee-118">Například následující kód konfigurace určuje novou obslužnou rutinu tokenu s názvem **MyCustomTokenHandler** , která se nachází v oboru názvů **CustomToken** .</span><span class="sxs-lookup"><span data-stu-id="d94ee-118">For example, the following configuration markup specifies a new token handler named **MyCustomTokenHandler** that resides in the **CustomToken** namespace.</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     <span data-ttu-id="d94ee-119">Všimněte si, že Pokud poskytujete vlastní obslužnou rutinu tokenu pro zpracování typu tokenu, který již má vestavěnou obslužnou rutinu tokenu, je nutné přidat **\<odebrat >** elementu pro zrušení výchozí obslužné rutiny a místo toho použít vlastní obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="d94ee-119">Note that if you are providing your own token handler to handle a token type that already has a built-in token handler, you need to add a **\<remove>** element to drop the default handler and use your custom handler instead.</span></span> <span data-ttu-id="d94ee-120">Například následující konfigurace nahrazuje výchozí <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> vlastní obslužnou rutinou tokenu:</span><span class="sxs-lookup"><span data-stu-id="d94ee-120">For example, the following configuration replaces the default <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> with the custom token handler:</span></span>  
  
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
