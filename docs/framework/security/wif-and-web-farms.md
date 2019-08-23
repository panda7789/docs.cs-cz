---
title: WIF a webové farmy
ms.date: 03/30/2017
ms.assetid: fc3cd7fa-2b45-4614-a44f-8fa9b9d15284
author: BrucePerlerMS
ms.openlocfilehash: e6806971bd2260785d66bfdb54a3e2938043c746
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967192"
---
# <a name="wif-and-web-farms"></a><span data-ttu-id="521c7-102">WIF a webové farmy</span><span class="sxs-lookup"><span data-stu-id="521c7-102">WIF and Web Farms</span></span>
<span data-ttu-id="521c7-103">Použijete-li technologii Windows Identity Foundation (WIF) k zabezpečení prostředků aplikace předávající strany (RP), která je nasazena ve webové farmě, je nutné provést konkrétní kroky, abyste zajistili, že WIF může zpracovávat tokeny z instancí aplikace RP spuštěné v různých počítače ve farmě.</span><span class="sxs-lookup"><span data-stu-id="521c7-103">When you use Windows Identity Foundation (WIF) to secure the resources of a relying party (RP) application that is deployed in a web farm, you must take specific steps to ensure that WIF can process tokens from instances of the RP application running on different computers in the farm.</span></span> <span data-ttu-id="521c7-104">Toto zpracování zahrnuje ověřování signatury tokenů relace, šifrování a dešifrování tokenů relací, ukládání tokenů relací do mezipaměti a zjišťování přehraných tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="521c7-104">This processing includes validating session token signatures, encrypting and decrypting session tokens, caching session tokens, and detecting replayed security tokens.</span></span>  
  
 <span data-ttu-id="521c7-105">V typickém případě, když se WIF používá k zabezpečení prostředků aplikace RP – to, jestli je RP spuštěný v jednom počítači nebo ve webové farmě – relace se naváže s klientem na základě tokenu zabezpečení, který se získal ze služby tokenu zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="521c7-105">In the typical case, when WIF is used to secure resources of an RP application – whether the RP is running on a single computer or in a web farm -- a session is established with the client based on the security token that was obtained from the security token service (STS).</span></span> <span data-ttu-id="521c7-106">K tomu je potřeba zabránit vynucení ověřování klienta na STS pro každý prostředek aplikace, který je zabezpečený pomocí WIF.</span><span class="sxs-lookup"><span data-stu-id="521c7-106">This is to avoid forcing the client to have to authenticate at the STS for every application resource that is secured using WIF.</span></span> <span data-ttu-id="521c7-107">Další informace o tom, jak WIF zpracovává relace, najdete v tématu [Správa relací WIF](../../../docs/framework/security/wif-session-management.md).</span><span class="sxs-lookup"><span data-stu-id="521c7-107">For more information about how WIF handles sessions, see [WIF Session Management](../../../docs/framework/security/wif-session-management.md).</span></span>  
  
 <span data-ttu-id="521c7-108">Při použití výchozího nastavení provede WIF následující:</span><span class="sxs-lookup"><span data-stu-id="521c7-108">When default settings are used, WIF does the following:</span></span>  
  
- <span data-ttu-id="521c7-109">Používá instanci <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> třídy pro čtení a zápis tokenu relace (instance <xref:System.IdentityModel.Tokens.SessionSecurityToken> třídy), který přináší deklarace identity a další informace o tokenu zabezpečení, který se použil pro ověřování, a také informace o relaci. využít.</span><span class="sxs-lookup"><span data-stu-id="521c7-109">It uses an instance of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class to read and write a session token (an instance of the <xref:System.IdentityModel.Tokens.SessionSecurityToken> class) that carries the claims and other information about the security token that was used for authentication as well as information about the session itself.</span></span> <span data-ttu-id="521c7-110">Token relace je zabalený a uložený v souboru cookie relace.</span><span class="sxs-lookup"><span data-stu-id="521c7-110">The session token is packaged and stored in a session cookie.</span></span> <span data-ttu-id="521c7-111">Ve výchozím nastavení <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> <xref:System.IdentityModel.ProtectedDataCookieTransform> používá k ochraně tokenu relace třídu, která používá rozhraní data Protection API (DPAPI).</span><span class="sxs-lookup"><span data-stu-id="521c7-111">By default, <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> uses the <xref:System.IdentityModel.ProtectedDataCookieTransform> class, which uses the Data Protection API (DPAPI), to protect the session token.</span></span> <span data-ttu-id="521c7-112">Rozhraní DPAPI zajišťuje ochranu pomocí přihlašovacích údajů uživatele nebo počítače a ukládá klíčová data v profilu uživatele.</span><span class="sxs-lookup"><span data-stu-id="521c7-112">The DPAPI provides protection by using the user or machine credentials and stores the key data in the user profile.</span></span>  
  
- <span data-ttu-id="521c7-113">Používá výchozí implementaci <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> třídy v paměti pro ukládání a zpracování tokenu relace.</span><span class="sxs-lookup"><span data-stu-id="521c7-113">It uses a default, in-memory implementation of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class to store and process the session token.</span></span>  
  
 <span data-ttu-id="521c7-114">Tato výchozí nastavení fungují ve scénářích, ve kterých je aplikace RP nasazena v jednom počítači. Při nasazení ve webové farmě je však možné každý požadavek HTTP odeslat a zpracovat jinou instancí aplikace RP běžící v jiném počítači.</span><span class="sxs-lookup"><span data-stu-id="521c7-114">These default settings work in scenarios in which the RP application is deployed on a single computer; however, when deployed in a web farm, each HTTP request may be sent to and processed by a different instance of the RP application running on a different computer.</span></span> <span data-ttu-id="521c7-115">V tomto scénáři nebudou výchozí nastavení WIF popsaná výše fungovat, protože ochrana tokenů a ukládání tokenů do mezipaměti je závislé na konkrétním počítači.</span><span class="sxs-lookup"><span data-stu-id="521c7-115">In this scenario, the default WIF settings described above will not work because both token protection and token caching are dependent on a specific computer.</span></span>  
  
 <span data-ttu-id="521c7-116">Chcete-li nasadit aplikaci RP ve webové farmě, je nutné zajistit, aby zpracování tokenů relace (a také předaných tokenů) nefungovalo na aplikaci spuštěné v určitém počítači.</span><span class="sxs-lookup"><span data-stu-id="521c7-116">To deploy an RP application in a web farm, you must ensure that the processing of session tokens (as well as of replayed tokens) is not dependent on the application running on a specific computer.</span></span> <span data-ttu-id="521c7-117">Jedním ze způsobů, jak to provést, je implementovat aplikaci RP, aby používala funkce poskytované prvkem ASP.NET `<machineKey>` Configuration a poskytovala distribuované ukládání do mezipaměti pro zpracování tokenů relací a přehrání tokenů.</span><span class="sxs-lookup"><span data-stu-id="521c7-117">One way to do this is to implement your RP application so that it uses the functionality provided by the ASP.NET `<machineKey>` configuration element and provides distributed caching for processing session tokens and replayed tokens.</span></span> <span data-ttu-id="521c7-118">`<machineKey>` Element umožňuje určit klíče potřebné k ověřování, šifrování a dešifrování tokenů v konfiguračním souboru, což umožňuje zadat stejné klíče v různých počítačích ve webové farmě.</span><span class="sxs-lookup"><span data-stu-id="521c7-118">The `<machineKey>` element allows you to specify the keys needed to validate, encrypt, and decrypt tokens in a configuration file, which enables you to specify the same keys on different computers in the web farm.</span></span> <span data-ttu-id="521c7-119">WIF poskytuje specializované obslužné rutiny <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>tokenů relace, které chrání tokeny pomocí klíčů určených `<machineKey>` v elementu.</span><span class="sxs-lookup"><span data-stu-id="521c7-119">WIF provides a specialized session token handler, the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>, that protects tokens by using the keys specified in the `<machineKey>` element.</span></span> <span data-ttu-id="521c7-120">Při implementaci této strategie můžete postupovat podle těchto pokynů:</span><span class="sxs-lookup"><span data-stu-id="521c7-120">To implement this strategy, you can follow these guidelines:</span></span>  
  
- <span data-ttu-id="521c7-121">Použijte element ASP.NET `<machineKey>` v konfiguraci k explicitnímu zadání podpisových a šifrovacích klíčů, které lze použít v počítačích ve farmě.</span><span class="sxs-lookup"><span data-stu-id="521c7-121">Use the ASP.NET `<machineKey>` element in configuration to explicitly specify signing and encryption keys that can be used across computers in the farm.</span></span> <span data-ttu-id="521c7-122">Následující kód XML ukazuje specifikaci `<machineKey>` prvku `<system.web>` pod prvkem v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="521c7-122">The following XML shows the specification of the `<machineKey>` element under the `<system.web>` element in a configuration file.</span></span>  
  
    ```xml  
    <machineKey compatibilityMode="Framework45" decryptionKey="CC510D … 8925E6" validationKey="BEAC8 … 6A4B1DE" />  
    ```  
  
- <span data-ttu-id="521c7-123">Nakonfigurujte aplikaci tak, aby používala <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> ji přidáním do kolekce obslužných rutin tokenu.</span><span class="sxs-lookup"><span data-stu-id="521c7-123">Configure the application to use the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> by adding it to the token handler collection.</span></span> <span data-ttu-id="521c7-124">Je nutné nejprve odebrat <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (nebo jakékoli obslužné rutiny odvozené <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> z třídy) z kolekce obslužných rutin tokenu, pokud je taková obslužná rutina přítomna.</span><span class="sxs-lookup"><span data-stu-id="521c7-124">You must first remove the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (or any handler derived from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class) from the token handler collection if such a handler is present.</span></span> <span data-ttu-id="521c7-125">Používá třídu, která chrání data souborů cookie relace pomocí `<machineKey>` kryptografického materiálu zadaného v elementu. <xref:System.IdentityModel.Services.MachineKeyTransform> <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler></span><span class="sxs-lookup"><span data-stu-id="521c7-125">The <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> uses the <xref:System.IdentityModel.Services.MachineKeyTransform> class, which protects the session cookie data by using the cryptographic material specified in the `<machineKey>` element.</span></span> <span data-ttu-id="521c7-126">Následující kód XML ukazuje, jak přidat <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> do kolekce obslužných rutin tokenu.</span><span class="sxs-lookup"><span data-stu-id="521c7-126">The following XML shows how to add the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> to a token handler collection.</span></span>  
  
    ```xml  
    <securityTokenHandlers>  
      <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
      <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </securityTokenHandlers>  
    ```  
  
- <span data-ttu-id="521c7-127">Je nutné <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> odvozovat z a implementovat distribuované ukládání do mezipaměti, tj. mezipaměť, která je přístupná ze všech počítačů ve farmě, na které se může spustit RP.</span><span class="sxs-lookup"><span data-stu-id="521c7-127">Derive from <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> and implement distributed caching, that is, a cache that is accessible from all computers in the farm on which the RP might run.</span></span> <span data-ttu-id="521c7-128">Nakonfigurujte RP tak, aby používal distribuovanou mezipaměť, zadáním [ \<prvku sessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="521c7-128">Configure the RP to use your distributed cache by specifying the [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element in the configuration file.</span></span> <span data-ttu-id="521c7-129">Můžete přepsat <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> metodu v odvozené třídě pro implementaci podřízených elementů `<sessionSecurityTokenCache>` elementu, pokud jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="521c7-129">You can override the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> method in your derived class to implement child elements of the `<sessionSecurityTokenCache>` element if they are required.</span></span>  
  
    ```xml  
    <caches>  
      <sessionSecurityTokenCache type="MyCacheLibrary.MySharedSessionSecurityTokenCache, MyCacheLibrary">  
        <!--optional child configuration elements, if implemented by the derived class -->  
      </sessionSecurityTokenCache>  
    </caches>  
    ```  
  
     <span data-ttu-id="521c7-130">Jedním ze způsobů, jak implementovat distribuované ukládání do mezipaměti, je poskytnout front-endu WCF pro vlastní mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="521c7-130">One way to implement distributed caching is to provide a WCF front end for your custom cache.</span></span> <span data-ttu-id="521c7-131">Další informace o implementaci služby ukládání do mezipaměti WCF najdete v tématu [Služba pro ukládání do mezipaměti WCF](#BKMK_TheWCFCachingService).</span><span class="sxs-lookup"><span data-stu-id="521c7-131">For more information about implementing a WCF caching service, see [The WCF Caching Service](#BKMK_TheWCFCachingService).</span></span> <span data-ttu-id="521c7-132">Další informace o implementaci klienta WCF, který může aplikace RP použít k volání služby ukládání do mezipaměti, najdete v tématu [klient mezipaměti WCF](#BKMK_TheWCFClient).</span><span class="sxs-lookup"><span data-stu-id="521c7-132">For more information about implementing a WCF client that the RP application can use to call the caching service, see [The WCF Caching Client](#BKMK_TheWCFClient).</span></span>  
  
- <span data-ttu-id="521c7-133">Pokud vaše aplikace zjistí přesměrované tokeny, musíte dodržovat podobnou strategii distribuovaného ukládání do mezipaměti pro mezipaměť tokenu, která <xref:System.IdentityModel.Tokens.TokenReplayCache> se odvozuje z a odkazuje na službu ukládání do mezipaměti tokenů [ \<v tokenReplayCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element konfigurace.</span><span class="sxs-lookup"><span data-stu-id="521c7-133">If your application detects replayed tokens you must follow a similar distributed caching strategy for the token replay cache by deriving from <xref:System.IdentityModel.Tokens.TokenReplayCache> and pointing to your token replay caching service in the [\<tokenReplayCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) configuration element.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="521c7-134">Všechny příklady XML a kód v tomto tématu jsou pořízeny z ukázky [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) .</span><span class="sxs-lookup"><span data-stu-id="521c7-134">All of the example XML and code in this topic is taken from the [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="521c7-135">Příklady v tomto tématu jsou k dispozici tak, jak jsou, a nejsou určeny pro použití v produkčním kódu beze změny.</span><span class="sxs-lookup"><span data-stu-id="521c7-135">The examples in this topic are provided as-is and are not intended to be used in production code without modification.</span></span>  
  
<a name="BKMK_TheWCFCachingService"></a>   
## <a name="the-wcf-caching-service"></a><span data-ttu-id="521c7-136">Služba pro ukládání do mezipaměti WCF</span><span class="sxs-lookup"><span data-stu-id="521c7-136">The WCF Caching Service</span></span>  
 <span data-ttu-id="521c7-137">Následující rozhraní definuje kontrakt mezi službou pro ukládání do mezipaměti WCF a klientem WCF používaným aplikací předávající strany ke komunikaci s ním.</span><span class="sxs-lookup"><span data-stu-id="521c7-137">The following interface defines the contract between the WCF caching service and the WCF client used by the relying party application to communicate with it.</span></span> <span data-ttu-id="521c7-138">V podstatě zveřejňuje metody <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> třídy jako operace služby.</span><span class="sxs-lookup"><span data-stu-id="521c7-138">It essentially exposes the methods of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class as service operations.</span></span>  
  
```  
[ServiceContract()]  
public interface ISessionSecurityTokenCacheService  
{  
    [OperationContract]  
    void AddOrUpdate(string endpointId, string contextId, string keyGeneration, SessionSecurityToken value, DateTime expiryTime);  
  
    [OperationContract]  
    IEnumerable<SessionSecurityToken> GetAll(string endpointId, string contextId);  
  
    [OperationContract]  
    SessionSecurityToken Get(string endpointId, string contextId, string keyGeneration);  
  
    [OperationContract(Name = "RemoveAll")]  
    void RemoveAll(string endpointId, string contextId);  
  
    [OperationContract(Name = "RemoveAllByEndpointId")]  
    void RemoveAll(string endpointId);  
  
    [OperationContract]  
    void Remove(string endpointId, string contextId, string keyGeneration);  
}  
```  
  
 <span data-ttu-id="521c7-139">Následující kód ukazuje implementaci služby pro ukládání do mezipaměti WCF.</span><span class="sxs-lookup"><span data-stu-id="521c7-139">The following code shows the implementation of the WCF caching service.</span></span> <span data-ttu-id="521c7-140">V tomto příkladu se používá výchozí mezipaměť tokenu relace v paměti, kterou implementuje WIF.</span><span class="sxs-lookup"><span data-stu-id="521c7-140">In this example, the default, in-memory session token cache implemented by WIF is used.</span></span> <span data-ttu-id="521c7-141">Alternativně můžete implementovat trvalou mezipaměť zálohovanou databází.</span><span class="sxs-lookup"><span data-stu-id="521c7-141">Alternatively, you could implement a durable cache backed by a database.</span></span> <span data-ttu-id="521c7-142">`ISessionSecurityTokenCacheService`Definuje rozhraní zobrazené výše.</span><span class="sxs-lookup"><span data-stu-id="521c7-142">`ISessionSecurityTokenCacheService` defines the interface shown above.</span></span> <span data-ttu-id="521c7-143">V tomto příkladu nejsou zobrazeny všechny metody vyžadované k implementaci rozhraní pro zkrácení.</span><span class="sxs-lookup"><span data-stu-id="521c7-143">In this example, not all of the methods required to implement the interface are shown for brevity.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.IdentityModel.Configuration;  
using System.IdentityModel.Tokens;  
using System.ServiceModel;  
using System.Xml;  
  
namespace WcfSessionSecurityTokenCacheService  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    public class SessionSecurityTokenCacheService : ISessionSecurityTokenCacheService  
    {  
        SessionSecurityTokenCache internalCache;  
  
        // sets the internal cache used by the service to the default WIF in-memory cache.  
        public SessionSecurityTokenCacheService()  
        {  
            internalCache = new IdentityModelCaches().SessionSecurityTokenCache;  
        }  
  
        ...  
  
        public SessionSecurityToken Get(string endpointId, string contextId, string keyGeneration)  
        {  
            // Delegates to the default, in-memory MruSessionSecurityTokenCache used by WIF  
            SessionSecurityToken token = internalCache.Get(new SessionSecurityTokenCacheKey(endpointId, GetContextId(contextId), GetKeyGeneration(keyGeneration)));  
            return token;  
        }  
  
        ...  
  
        private static UniqueId GetContextId(string contextIdString)  
        {  
            return contextIdString == null ? null : new UniqueId(contextIdString);  
        }  
  
        private static UniqueId GetKeyGeneration(string keyGenerationString)  
        {  
            return keyGenerationString == null ? null : new UniqueId(keyGenerationString);  
        }  
    }  
}  
```  
  
<a name="BKMK_TheWCFClient"></a>   
## <a name="the-wcf-caching-client"></a><span data-ttu-id="521c7-144">Klient mezipaměti WCF</span><span class="sxs-lookup"><span data-stu-id="521c7-144">The WCF Caching Client</span></span>  
 <span data-ttu-id="521c7-145">Tato část ukazuje implementaci třídy, která je odvozena z <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> a která deleguje volání do služby ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="521c7-145">This section shows the implementation of a class that derives from <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> and that delegates calls to the caching service.</span></span> <span data-ttu-id="521c7-146">Aplikaci RP nakonfigurujete tak, aby tuto třídu používala prostřednictvím [ \<elementu sessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) , jako v následujícím kódu XML.</span><span class="sxs-lookup"><span data-stu-id="521c7-146">You configure the RP application to use this class through the [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element as in the following XML</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
 <span data-ttu-id="521c7-147">Třída přepíše <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> metodu pro získání koncového bodu služby z vlastního `<cacheServiceAddress>` podřízeného prvku `<sessionSecurityTokenCache>` elementu.</span><span class="sxs-lookup"><span data-stu-id="521c7-147">The class overrides the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> method to get the service endpoint from the custom `<cacheServiceAddress>` child element of the `<sessionSecurityTokenCache>` element.</span></span> <span data-ttu-id="521c7-148">Pomocí tohoto koncového bodu inicializuje `ISessionSecurityTokenCacheService` kanál, přes který může komunikovat se službou.</span><span class="sxs-lookup"><span data-stu-id="521c7-148">It uses this endpoint to initialize an `ISessionSecurityTokenCacheService` channel over which it can communicate with the service.</span></span>  <span data-ttu-id="521c7-149">V tomto příkladu nejsou zobrazeny všechny metody vyžadované k implementaci <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> třídy pro zkrácení.</span><span class="sxs-lookup"><span data-stu-id="521c7-149">In this example, not all of the methods required to implement the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class are shown for brevity.</span></span>  
  
```  
using System;  
using System.Configuration;  
using System.IdentityModel.Configuration;  
using System.IdentityModel.Tokens;  
using System.ServiceModel;  
using System.Xml;  
  
namespace CacheLibrary  
{  
    /// <summary>  
    /// This class acts as a proxy to the WcfSessionSecurityTokenCacheService.  
    /// </summary>  
    public class SharedSessionSecurityTokenCache : SessionSecurityTokenCache, ICustomIdentityConfiguration  
    {  
        private ISessionSecurityTokenCacheService WcfSessionSecurityTokenCacheServiceClient;  
  
        internal SharedSessionSecurityTokenCache()  
        {  
        }  
  
        /// <summary>  
        /// Creates a client channel to call the service host.  
        /// </summary>  
        protected void Initialize(string cacheServiceAddress)  
        {  
            if (this.WcfSessionSecurityTokenCacheServiceClient != null)  
            {  
                return;  
            }  
  
            ChannelFactory<ISessionSecurityTokenCacheService> cf = new ChannelFactory<ISessionSecurityTokenCacheService>(  
                new WS2007HttpBinding(SecurityMode.None),  
                new EndpointAddress(cacheServiceAddress));  
            this.WcfSessionSecurityTokenCacheServiceClient = cf.CreateChannel();  
        }  
  
        #region SessionSecurityTokenCache Members  
        // Delegates the following operations to the centralized session security token cache service in the web farm.  
  
        ...  
  
        public override SessionSecurityToken Get(SessionSecurityTokenCacheKey key)  
        {  
            return this.WcfSessionSecurityTokenCacheServiceClient.Get(key.EndpointId, GetContextIdString(key), GetKeyGenerationString(key));  
        }  
  
        ...  
  
        #endregion  
  
        #region ICustomIdentityConfiguration Members  
        // Called from configuration infrastructure to load custom elements  
        public void LoadCustomConfiguration(XmlNodeList nodeList)  
        {  
            // Retrieve the endpoint address of the centralized session security token cache service running in the web farm  
            if (nodeList.Count == 0)  
            {  
                throw new ConfigurationException("No child config element found under <sessionSecurityTokenCache>.");  
            }  
  
            XmlElement cacheServiceAddressElement = nodeList.Item(0) as XmlElement;  
            if (cacheServiceAddressElement.LocalName != "cacheServiceAddress")  
            {  
                throw new ConfigurationException("First child config element under <sessionSecurityTokenCache> is expected to be <cacheServiceAddress>.");  
            }  
  
            string cacheServiceAddress = null;  
            if (cacheServiceAddressElement.Attributes["url"] != null)  
            {  
                cacheServiceAddress = cacheServiceAddressElement.Attributes["url"].Value;  
            }  
            else  
            {  
                throw new ConfigurationException("<cacheServiceAddress> is expected to contain a 'url' attribute.");  
            }  
  
            // Initialize the proxy to the WebFarmSessionSecurityTokenCacheService  
            this.Initialize(cacheServiceAddress);  
        }  
        #endregion  
  
        private static string GetKeyGenerationString(SessionSecurityTokenCacheKey key)  
        {  
            return key.KeyGeneration == null ? null : key.KeyGeneration.ToString();  
        }  
  
        private static string GetContextIdString(SessionSecurityTokenCacheKey key)  
        {  
            return GetContextIdString(key.ContextId);  
        }  
  
        private static string GetContextIdString(UniqueId contextId)  
        {  
            return contextId == null ? null : contextId.ToString();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="521c7-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="521c7-150">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>
- <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>
- [<span data-ttu-id="521c7-151">Správa relací WIF</span><span class="sxs-lookup"><span data-stu-id="521c7-151">WIF Session Management</span></span>](../../../docs/framework/security/wif-session-management.md)
