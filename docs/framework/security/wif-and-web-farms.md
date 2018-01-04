---
title: "WIF a webové farmy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc3cd7fa-2b45-4614-a44f-8fa9b9d15284
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 93c3e4251943afa383002043d9259184be82d929
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="wif-and-web-farms"></a>WIF a webové farmy
Pokud používáte Windows Identity Foundation (WIF) k zabezpečení prostředků předávající stranu aplikace, který je nasazen ve webové farmě, je nutné provést určité kroky k zajištění, že WIF může zpracovat tokeny z instancí RP aplikace spuštěné v různých počítače ve farmě. Dané zpracování zahrnuje ověřování token podpisů relace, šifrování a dešifrování tokenů relace, ukládání do mezipaměti relace tokeny a zjišťování odesílal tokeny zabezpečení.  
  
 V případě typické při WIF slouží k zabezpečení prostředků aplikace RP – jestli RP běží v jednom počítači nebo ve webové farmě – relaci se naváže klienta na základě tokenu zabezpečení, který byl získán od služby tokenů zabezpečení (STS). Tím se vyhnete vynucení klienta tak, aby měl k ověření na službu tokenů zabezpečení pro každý zdroj aplikace, která je zabezpečená pomocí WIF. Další informace o zpracování WIF relací najdete v tématu [Správa relací WIF](../../../docs/framework/security/wif-session-management.md).  
  
 Když se použije výchozí nastavení, WIF provede následující akce:  
  
-   Používá instanci <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> třídy ke čtení a zápisu token relace (instance <xref:System.IdentityModel.Tokens.SessionSecurityToken> třída), představuje deklarace identity a další informace o tokenu zabezpečení, která byla použita pro ověřování a také informace o relaci sám sebe. Token relace se zabalí a uložené v souboru cookie relace. Ve výchozím nastavení <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> používá <xref:System.IdentityModel.ProtectedDataCookieTransform> třídy, která používá rozhraní Data Protection API (DPAPI), k ochraně token relace. Rozhraní DPAPI poskytuje ochranu pomocí přihlašovacích údajů uživatele nebo počítače a uloží klíčová data v profilu uživatele.  
  
-   Používá výchozí, implementace v paměti <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> třídy k ukládání a zpracování token relace.  
  
 Tato výchozí nastavení fungují v scénáře, ve kterých je RP aplikace nasazená v jednom počítači; ale při nasazení ve webové farmě, každý požadavek HTTP může být odeslán a zpracovává jiné instance systému RP aplikace běžící na jiném počítači. V tomto scénáři výchozí nastavení WIF popsané výše nebude fungovat, protože token ochranu i ukládání tokenu do mezipaměti jsou závislé na konkrétním počítači.  
  
 Pokud chcete nasadit aplikaci RP ve webové farmě, je nutné zajistit, že zpracování relace tokenů (a také přehraná tokenů) není závislá na aplikace běžící v určitém počítači. Jeden ze způsobů, jak se toto nastavení slouží k implementaci aplikace RP tak, aby používala funkce poskytované službou ASP.NET `<machineKey>` konfigurační prvek a poskytuje distribuované ukládání do mezipaměti pro zpracování relace tokeny a odesílal tokeny. `<machineKey>` Element umožňuje zadat klíče pro ověření, šifrování a dešifrování tokenů v konfiguračním souboru, který umožňuje určit stejné klíče na různých počítačích ve webové farmě. WIF poskytuje obslužnou rutinu tokenu specializované relace, <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>, který chrání tokeny pomocí klíče určené v `<machineKey>` elementu. Implementace této strategie, můžete pomocí následujících pokynů:  
  
-   Pomocí technologie ASP.NET `<machineKey>` element v konfiguraci k explicitnímu zadání podepisování a šifrování klíče, které lze použít na počítačích ve farmě. Následující kód XML ukazuje specifikaci `<machineKey>` prvek v rámci `<system.web>` element v konfiguračním souboru.  
  
    ```xml  
    <machineKey compatibilityMode="Framework45" decryptionKey="CC510D … 8925E6" validationKey="BEAC8 … 6A4B1DE" />  
    ```  
  
-   Konfigurace aplikace pro použití <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> jej přidat do kolekce obslužná rutina tokenu. Je nutné nejprve odebrat <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (nebo všechny obslužné rutiny odvozené od <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> třída) z kolekce obslužná rutina tokenu, pokud se nachází obslužnou rutinu. <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> Používá <xref:System.IdentityModel.Services.MachineKeyTransform> třídy, která chrání data souboru cookie relace pomocí kryptografických materiál uvedený v `<machineKey>` elementu. Následující kód XML ukazuje, jak přidat <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> na kolekci obslužná rutina tokenu.  
  
    ```xml  
    <securityTokenHandlers>  
      <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
      <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </securityTokenHandlers>  
    ```  
  
-   Odvozena od <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> a implementace distribuované ukládání do mezipaměti, který je mezipaměti, která je přístupná ze všech počítačů ve farmě, na kterém může spustit RP. Konfigurace RP používat distribuované mezipaměti zadáním [ \<sessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element v konfiguračním souboru. Je možné přepsat <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> metoda v odvozené třídě implementovat podřízených elementů `<sessionSecurityTokenCache>` elementu, pokud jsou požadována.  
  
    ```xml  
    <caches>  
      <sessionSecurityTokenCache type="MyCacheLibrary.MySharedSessionSecurityTokenCache, MyCacheLibrary">  
        <!—optional child configuration elements, if implemented by the derived class -->  
      </sessionSecurityTokenCache>  
    </caches>  
    ```  
  
     Jeden způsob implementace distribuované ukládání do mezipaměti je poskytnout WCF front-end pro vaše vlastní mezipaměti. Další informace o implementaci ukládání do mezipaměti služby WCF najdete v tématu [služba WCF ukládání do mezipaměti Service](#BKMK_TheWCFCachingService). Další informace o implementaci klienta WCF, RP aplikace můžete použít k volání služby ukládání do mezipaměti najdete v tématu [klient ukládání do mezipaměti WCF](#BKMK_TheWCFClient).  
  
-   Pokud vaše aplikace zjistí přehraná tokeny postupujte podle podobná distribuované ukládání do mezipaměti strategie pro mezipaměť opětovného přehrání tokenu odvozené z <xref:System.IdentityModel.Tokens.TokenReplayCache> a přejdete na vaše opětovného přehrání tokenu, ukládání do mezipaměti služby v rámci [ \< tokenReplayCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) konfigurační prvek.  
  
> [!IMPORTANT]
>  Všechny příklad XML a kódu v tomto tématu jsou převzaty z [ClaimsAwareWebFarm](http://go.microsoft.com/fwlink/?LinkID=248408) ukázkové (http://go.microsoft.com/fwlink/?LinkID=248408).  
  
> [!IMPORTANT]
>  V příkladech v tomto tématu jsou uvedeny jako-je a není určena pro použití v produkčním kódu bez úprav.  
  
<a name="BKMK_TheWCFCachingService"></a>   
## <a name="the-wcf-caching-service"></a>Ukládání do mezipaměti služby WCF  
 Následující rozhraní definuje kontrakt mezi službou WCF ukládání do mezipaměti a klienta WCF používá aplikace předávající strany ke komunikaci s ním. V podstatě zpřístupňuje metody <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> třída jako operací služby.  
  
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
  
 Následující kód ukazuje implementaci WCF služby ukládání do mezipaměti. V tomto příkladu výchozí, se používá implementované WIF tokenu mezipaměť v paměti relace. Alternativně může implementovat trvanlivý mezipaměti databázi. `ISessionSecurityTokenCacheService`definuje rozhraní uvedené výše. V tomto příkladu jsou jako stručný výtah zobrazeny všechny metody potřebnou k implementaci rozhraní.  
  
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
## <a name="the-wcf-caching-client"></a>Ukládání do mezipaměti klienta WCF  
 Tato část ukazuje implementaci třídy, která je odvozena z <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> a že delegáti volání ke službě ukládání do mezipaměti. Konfigurace aplikace RP k použití této třídy prostřednictvím [ \<sessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element jako následující kód XML  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
 Třída přepsání <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> metodu k získání koncový bod služby z vlastní `<cacheServiceAddress>` podřízený prvek `<sessionSecurityTokenCache>` element. Tento koncový bod se používá k inicializaci `ISessionSecurityTokenCacheService` kanál, přes který může komunikovat se službou.  V tomto příkladu všechny metody potřebnou k implementaci <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> třídy jsou uvedeny jako stručný výtah.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
 <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>  
 [Správa relací WIF](../../../docs/framework/security/wif-session-management.md)
