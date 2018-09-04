---
title: Technologie WIF a webové farmy
ms.date: 03/30/2017
ms.assetid: fc3cd7fa-2b45-4614-a44f-8fa9b9d15284
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 365416a82881c32b8fdcd3211aa42acb9f273483
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502726"
---
# <a name="wif-and-web-farms"></a><span data-ttu-id="9e4fc-102">Technologie WIF a webové farmy</span><span class="sxs-lookup"><span data-stu-id="9e4fc-102">WIF and Web Farms</span></span>
<span data-ttu-id="9e4fc-103">Při použití technologie Windows Identity Foundation (WIF) k zabezpečení prostředků aplikace předávající stranu, která je nasazená ve webové farmě, musíte provést určité kroky k zajištění, že technologie WIF zpracovávat tokeny z instancí aplikace předávající strany, který běží na různých počítače ve farmě.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-103">When you use Windows Identity Foundation (WIF) to secure the resources of a relying party (RP) application that is deployed in a web farm, you must take specific steps to ensure that WIF can process tokens from instances of the RP application running on different computers in the farm.</span></span> <span data-ttu-id="9e4fc-104">Dané zpracování zahrnuje ověřování podpisů tokenu relace, šifrování a dešifrování tokenů relace, ukládání do mezipaměti relace tokeny a zjišťování, odesílal tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-104">This processing includes validating session token signatures, encrypting and decrypting session tokens, caching session tokens, and detecting replayed security tokens.</span></span>  
  
 <span data-ttu-id="9e4fc-105">V typické případy Pokud technologie WIF slouží k zabezpečení prostředků aplikace předávající strany – zda RP běží na jednom počítači nebo ve webové farmě--relaci pokládáme stav, pomocí klienta na základě tokenu zabezpečení, který byl získán od služby tokenů zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="9e4fc-105">In the typical case, when WIF is used to secure resources of an RP application – whether the RP is running on a single computer or in a web farm -- a session is established with the client based on the security token that was obtained from the security token service (STS).</span></span> <span data-ttu-id="9e4fc-106">To je vyhnout se vynutí, aby měl k ověření na službu tokenů zabezpečení pro každý prostředek aplikace, která je zabezpečena pomocí technologie WIF klient.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-106">This is to avoid forcing the client to have to authenticate at the STS for every application resource that is secured using WIF.</span></span> <span data-ttu-id="9e4fc-107">Další informace o zpracování relací WIF najdete v tématu [Správa relací WIF](../../../docs/framework/security/wif-session-management.md).</span><span class="sxs-lookup"><span data-stu-id="9e4fc-107">For more information about how WIF handles sessions, see [WIF Session Management](../../../docs/framework/security/wif-session-management.md).</span></span>  
  
 <span data-ttu-id="9e4fc-108">Pokud použijete výchozí nastavení technologie WIF provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="9e4fc-108">When default settings are used, WIF does the following:</span></span>  
  
-   <span data-ttu-id="9e4fc-109">Používá instanci <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> třídy ke čtení a zápisu tokenu relace (instance <xref:System.IdentityModel.Tokens.SessionSecurityToken> třídy), který představuje deklarace identity a další informace o tokenu zabezpečení, která byla použita pro ověřování, a také informace o relaci samotný.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-109">It uses an instance of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class to read and write a session token (an instance of the <xref:System.IdentityModel.Tokens.SessionSecurityToken> class) that carries the claims and other information about the security token that was used for authentication as well as information about the session itself.</span></span> <span data-ttu-id="9e4fc-110">Token relace je zabalená a uložená v souboru cookie relace.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-110">The session token is packaged and stored in a session cookie.</span></span> <span data-ttu-id="9e4fc-111">Ve výchozím nastavení <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> používá <xref:System.IdentityModel.ProtectedDataCookieTransform> třídu, která používá Data Protection API (DPAPI), k ochraně tokenu relace.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-111">By default, <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> uses the <xref:System.IdentityModel.ProtectedDataCookieTransform> class, which uses the Data Protection API (DPAPI), to protect the session token.</span></span> <span data-ttu-id="9e4fc-112">Rozhraní DPAPI poskytuje ochranu s použitím přihlašovacích údajů uživatele nebo počítače a uloží klíčových dat v profilu uživatele.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-112">The DPAPI provides protection by using the user or machine credentials and stores the key data in the user profile.</span></span>  
  
-   <span data-ttu-id="9e4fc-113">Použije výchozí, implementace v paměti <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> třídy k ukládání a zpracování tokenu relace.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-113">It uses a default, in-memory implementation of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class to store and process the session token.</span></span>  
  
 <span data-ttu-id="9e4fc-114">Tato výchozí nastavení fungují v situacích, ve kterých je aplikace předávající strany nasazené na jednom počítači; ale při nasazení ve webové farmě, každý požadavek HTTP může být zaslána a zpracovává jinou instanci aplikace předávající strany, který běží na jiném počítači.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-114">These default settings work in scenarios in which the RP application is deployed on a single computer; however, when deployed in a web farm, each HTTP request may be sent to and processed by a different instance of the RP application running on a different computer.</span></span> <span data-ttu-id="9e4fc-115">V tomto scénáři nebude fungovat nastavení technologie WIF je popsáno výše, protože token ochranu a ukládání tokenu do mezipaměti jsou závislé na určitém počítači.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-115">In this scenario, the default WIF settings described above will not work because both token protection and token caching are dependent on a specific computer.</span></span>  
  
 <span data-ttu-id="9e4fc-116">Pokud chcete nasadit aplikaci předávající strany ve webové farmě, musíte zajistit, že zpracování relace tokenů (a také přehraná tokenů) není závislá na aplikaci spuštěné na určitém počítači.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-116">To deploy an RP application in a web farm, you must ensure that the processing of session tokens (as well as of replayed tokens) is not dependent on the application running on a specific computer.</span></span> <span data-ttu-id="9e4fc-117">Můžete provést například jde implementovat vaše aplikace předávající strany, tak, aby používala funkce poskytované službou ASP.NET `<machineKey>` element konfigurace a nabízí distribuované ukládání do mezipaměti pro zpracování relace tokenů a znovu přehrát tokeny.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-117">One way to do this is to implement your RP application so that it uses the functionality provided by the ASP.NET `<machineKey>` configuration element and provides distributed caching for processing session tokens and replayed tokens.</span></span> <span data-ttu-id="9e4fc-118">`<machineKey>` Element slouží k určení klíče potřebné k ověření, šifrování a dešifrování tokenů v konfiguračním souboru, který umožňuje určit stejnými klíči na různých počítačích ve webové farmě.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-118">The `<machineKey>` element allows you to specify the keys needed to validate, encrypt, and decrypt tokens in a configuration file, which enables you to specify the same keys on different computers in the web farm.</span></span> <span data-ttu-id="9e4fc-119">Technologie WIF umožňuje obslužnou rutinu tokenu relace specializované <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>, tokeny, které chrání pomocí klíče specifikované v `<machineKey>` elementu.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-119">WIF provides a specialized session token handler, the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>, that protects tokens by using the keys specified in the `<machineKey>` element.</span></span> <span data-ttu-id="9e4fc-120">K implementaci této strategie, můžete postupujte podle těchto pokynů:</span><span class="sxs-lookup"><span data-stu-id="9e4fc-120">To implement this strategy, you can follow these guidelines:</span></span>  
  
-   <span data-ttu-id="9e4fc-121">Použití technologie ASP.NET `<machineKey>` element v konfiguraci s ohledem na podepisování a šifrování klíče, které lze použít na počítačích ve farmě.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-121">Use the ASP.NET `<machineKey>` element in configuration to explicitly specify signing and encryption keys that can be used across computers in the farm.</span></span> <span data-ttu-id="9e4fc-122">Následující kód XML ukazuje specifikaci `<machineKey>` element v rámci `<system.web>` element v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-122">The following XML shows the specification of the `<machineKey>` element under the `<system.web>` element in a configuration file.</span></span>  
  
    ```xml  
    <machineKey compatibilityMode="Framework45" decryptionKey="CC510D … 8925E6" validationKey="BEAC8 … 6A4B1DE" />  
    ```  
  
-   <span data-ttu-id="9e4fc-123">Konfigurace aplikace pro použití <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> přidáním do kolekce obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-123">Configure the application to use the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> by adding it to the token handler collection.</span></span> <span data-ttu-id="9e4fc-124">Je nutno nejprve odstranit <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (nebo libovolné obslužné rutiny odvozených z <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> třídy) z obslužné rutiny tokenů kolekce, pokud tato obslužná rutina je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-124">You must first remove the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (or any handler derived from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class) from the token handler collection if such a handler is present.</span></span> <span data-ttu-id="9e4fc-125"><xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> Používá <xref:System.IdentityModel.Services.MachineKeyTransform> třídu, která chrání data souboru cookie relace pomocí kryptografický materiál podle `<machineKey>` elementu.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-125">The <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> uses the <xref:System.IdentityModel.Services.MachineKeyTransform> class, which protects the session cookie data by using the cryptographic material specified in the `<machineKey>` element.</span></span> <span data-ttu-id="9e4fc-126">Následující kód XML ukazuje, jak přidat <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> ke kolekci obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-126">The following XML shows how to add the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> to a token handler collection.</span></span>  
  
    ```xml  
    <securityTokenHandlers>  
      <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
      <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </securityTokenHandlers>  
    ```  
  
-   <span data-ttu-id="9e4fc-127">Jsou odvozeny z <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> a implementujte distribuované ukládání do mezipaměti, to znamená, mezipaměť, která je přístupná ze všech počítačů ve farmě, na kterém můžou spouštět RP.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-127">Derive from <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> and implement distributed caching, that is, a cache that is accessible from all computers in the farm on which the RP might run.</span></span> <span data-ttu-id="9e4fc-128">Nakonfigurovat předávající strana často tak, že určíte pomocí distribuované mezipaměti [ \<sessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-128">Configure the RP to use your distributed cache by specifying the [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element in the configuration file.</span></span> <span data-ttu-id="9e4fc-129">Můžete přepsat <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> metoda v odvozené třídy k implementaci podřízených elementů `<sessionSecurityTokenCache>` elementu, jestliže jsou povinné.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-129">You can override the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> method in your derived class to implement child elements of the `<sessionSecurityTokenCache>` element if they are required.</span></span>  
  
    ```xml  
    <caches>  
      <sessionSecurityTokenCache type="MyCacheLibrary.MySharedSessionSecurityTokenCache, MyCacheLibrary">  
        <!—optional child configuration elements, if implemented by the derived class -->  
      </sessionSecurityTokenCache>  
    </caches>  
    ```  
  
     <span data-ttu-id="9e4fc-130">Jedním ze způsobů implementace distribuované ukládání do mezipaměti je poskytnout WCF front-endu pro vaše vlastní mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-130">One way to implement distributed caching is to provide a WCF front end for your custom cache.</span></span> <span data-ttu-id="9e4fc-131">Další informace o implementaci ukládání do mezipaměti služby WCF najdete v tématu [služba ukládání do mezipaměti WCF](#BKMK_TheWCFCachingService).</span><span class="sxs-lookup"><span data-stu-id="9e4fc-131">For more information about implementing a WCF caching service, see [The WCF Caching Service](#BKMK_TheWCFCachingService).</span></span> <span data-ttu-id="9e4fc-132">Další informace o implementaci klienta WCF, která aplikace předávající strany můžete použít k volání službu ukládání do mezipaměti najdete v tématu [The WCF ukládání do mezipaměti klienta](#BKMK_TheWCFClient).</span><span class="sxs-lookup"><span data-stu-id="9e4fc-132">For more information about implementing a WCF client that the RP application can use to call the caching service, see [The WCF Caching Client](#BKMK_TheWCFClient).</span></span>  
  
-   <span data-ttu-id="9e4fc-133">Pokud aplikace zjistí přehraná tokeny je třeba dodržet podobná distribuované ukládání do mezipaměti strategie pro ukládání do mezipaměti opětovného přehrání tokenu odvozením z <xref:System.IdentityModel.Tokens.TokenReplayCache> a odkazuje na vaše opětovného přehrání tokenu, ukládání do mezipaměti služby [ \< tokenReplayCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) konfiguračního prvku.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-133">If your application detects replayed tokens you must follow a similar distributed caching strategy for the token replay cache by deriving from <xref:System.IdentityModel.Tokens.TokenReplayCache> and pointing to your token replay caching service in the [\<tokenReplayCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) configuration element.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9e4fc-134">Všechny ukázkový soubor XML a kód v tomto tématu je převzata z [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) vzorku.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-134">All of the example XML and code in this topic is taken from the [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9e4fc-135">Příklady v tomto tématu jsou k dispozici jako-je a není určena pro použití v produkčním kódu bez jakýchkoli úprav.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-135">The examples in this topic are provided as-is and are not intended to be used in production code without modification.</span></span>  
  
<a name="BKMK_TheWCFCachingService"></a>   
## <a name="the-wcf-caching-service"></a><span data-ttu-id="9e4fc-136">Ukládání do mezipaměti služby WCF</span><span class="sxs-lookup"><span data-stu-id="9e4fc-136">The WCF Caching Service</span></span>  
 <span data-ttu-id="9e4fc-137">Následující rozhraní definuje kontrakt mezi klienta WCF používá aplikaci předávající strany ke komunikaci s ním a ukládání do mezipaměti služby WCF.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-137">The following interface defines the contract between the WCF caching service and the WCF client used by the relying party application to communicate with it.</span></span> <span data-ttu-id="9e4fc-138">V podstatě zveřejňuje metody <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> třídu jako servisní operace.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-138">It essentially exposes the methods of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class as service operations.</span></span>  
  
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
  
 <span data-ttu-id="9e4fc-139">Následující kód ukazuje implementaci WCF služby ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-139">The following code shows the implementation of the WCF caching service.</span></span> <span data-ttu-id="9e4fc-140">V tomto příkladu, ve výchozím nastavení se používá mezipaměť tokenu relace v paměti pomocí technologie WIF implementovat.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-140">In this example, the default, in-memory session token cache implemented by WIF is used.</span></span> <span data-ttu-id="9e4fc-141">Alternativně je možné implementovat trvalý mezipaměti databázi.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-141">Alternatively, you could implement a durable cache backed by a database.</span></span> <span data-ttu-id="9e4fc-142">`ISessionSecurityTokenCacheService` definuje rozhraní uvedené výše.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-142">`ISessionSecurityTokenCacheService` defines the interface shown above.</span></span> <span data-ttu-id="9e4fc-143">V tomto příkladu některé z metod požadovaných k implementaci rozhraní jsou zobrazeny pro zkrácení.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-143">In this example, not all of the methods required to implement the interface are shown for brevity.</span></span>  
  
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
## <a name="the-wcf-caching-client"></a><span data-ttu-id="9e4fc-144">Ukládání do mezipaměti klienta WCF</span><span class="sxs-lookup"><span data-stu-id="9e4fc-144">The WCF Caching Client</span></span>  
 <span data-ttu-id="9e4fc-145">Tato část ukazuje implementaci třídy, která je odvozena z <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> a že delegáti volání službu ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-145">This section shows the implementation of a class that derives from <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> and that delegates calls to the caching service.</span></span> <span data-ttu-id="9e4fc-146">Konfigurace aplikace předávající strany k použití této třídy prostřednictvím [ \<sessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element jako v následujícím souboru XML</span><span class="sxs-lookup"><span data-stu-id="9e4fc-146">You configure the RP application to use this class through the [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element as in the following XML</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
 <span data-ttu-id="9e4fc-147">Třída přepsání <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> metodu k získání koncového bodu služby z vlastního `<cacheServiceAddress>` podřízený prvek `<sessionSecurityTokenCache>` elementu.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-147">The class overrides the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> method to get the service endpoint from the custom `<cacheServiceAddress>` child element of the `<sessionSecurityTokenCache>` element.</span></span> <span data-ttu-id="9e4fc-148">Tento koncový bod se používá k inicializaci `ISessionSecurityTokenCacheService` kanál, přes který může komunikovat se službou.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-148">It uses this endpoint to initialize an `ISessionSecurityTokenCacheService` channel over which it can communicate with the service.</span></span>  <span data-ttu-id="9e4fc-149">V tomto příkladu všechny metody potřebnou k implementaci <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> třídy jsou platné pro zkrácení.</span><span class="sxs-lookup"><span data-stu-id="9e4fc-149">In this example, not all of the methods required to implement the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class are shown for brevity.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9e4fc-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e4fc-150">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
 <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>  
 [<span data-ttu-id="9e4fc-151">Správa relací WIF</span><span class="sxs-lookup"><span data-stu-id="9e4fc-151">WIF Session Management</span></span>](../../../docs/framework/security/wif-session-management.md)
