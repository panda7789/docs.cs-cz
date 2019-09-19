---
title: WIF a webové farmy
ms.date: 03/30/2017
ms.assetid: fc3cd7fa-2b45-4614-a44f-8fa9b9d15284
author: BrucePerlerMS
ms.openlocfilehash: 32d2875ebe0a46b9f9b1856ed70a30114793e492
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045253"
---
# <a name="wif-and-web-farms"></a>WIF a webové farmy
Použijete-li technologii Windows Identity Foundation (WIF) k zabezpečení prostředků aplikace předávající strany (RP), která je nasazena ve webové farmě, je nutné provést konkrétní kroky, abyste zajistili, že WIF může zpracovávat tokeny z instancí aplikace RP spuštěné v různých počítače ve farmě. Toto zpracování zahrnuje ověřování signatury tokenů relace, šifrování a dešifrování tokenů relací, ukládání tokenů relací do mezipaměti a zjišťování přehraných tokenů zabezpečení.  
  
 V typickém případě, když se WIF používá k zabezpečení prostředků aplikace RP – to, jestli je RP spuštěný v jednom počítači nebo ve webové farmě – relace se naváže s klientem na základě tokenu zabezpečení, který se získal ze služby tokenu zabezpečení (STS). K tomu je potřeba zabránit vynucení ověřování klienta na STS pro každý prostředek aplikace, který je zabezpečený pomocí WIF. Další informace o tom, jak WIF zpracovává relace, najdete v tématu [Správa relací WIF](wif-session-management.md).  
  
 Při použití výchozího nastavení provede WIF následující:  
  
- Používá instanci <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> třídy pro čtení a zápis tokenu relace (instance <xref:System.IdentityModel.Tokens.SessionSecurityToken> třídy), který přináší deklarace identity a další informace o tokenu zabezpečení, který se použil pro ověřování, a také informace o relaci. využít. Token relace je zabalený a uložený v souboru cookie relace. Ve výchozím nastavení <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> <xref:System.IdentityModel.ProtectedDataCookieTransform> používá k ochraně tokenu relace třídu, která používá rozhraní data Protection API (DPAPI). Rozhraní DPAPI zajišťuje ochranu pomocí přihlašovacích údajů uživatele nebo počítače a ukládá klíčová data v profilu uživatele.  
  
- Používá výchozí implementaci <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> třídy v paměti pro ukládání a zpracování tokenu relace.  
  
 Tato výchozí nastavení fungují ve scénářích, ve kterých je aplikace RP nasazena v jednom počítači. Při nasazení ve webové farmě je však možné každý požadavek HTTP odeslat a zpracovat jinou instancí aplikace RP běžící v jiném počítači. V tomto scénáři nebudou výchozí nastavení WIF popsaná výše fungovat, protože ochrana tokenů a ukládání tokenů do mezipaměti je závislé na konkrétním počítači.  
  
 Chcete-li nasadit aplikaci RP ve webové farmě, je nutné zajistit, aby zpracování tokenů relace (a také předaných tokenů) nefungovalo na aplikaci spuštěné v určitém počítači. Jedním ze způsobů, jak to provést, je implementovat aplikaci RP, aby používala funkce poskytované prvkem ASP.NET `<machineKey>` Configuration a poskytovala distribuované ukládání do mezipaměti pro zpracování tokenů relací a přehrání tokenů. `<machineKey>` Element umožňuje určit klíče potřebné k ověřování, šifrování a dešifrování tokenů v konfiguračním souboru, což umožňuje zadat stejné klíče v různých počítačích ve webové farmě. WIF poskytuje specializované obslužné rutiny <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>tokenů relace, které chrání tokeny pomocí klíčů určených `<machineKey>` v elementu. Při implementaci této strategie můžete postupovat podle těchto pokynů:  
  
- Použijte element ASP.NET `<machineKey>` v konfiguraci k explicitnímu zadání podpisových a šifrovacích klíčů, které lze použít v počítačích ve farmě. Následující kód XML ukazuje specifikaci `<machineKey>` prvku `<system.web>` pod prvkem v konfiguračním souboru.  
  
    ```xml  
    <machineKey compatibilityMode="Framework45" decryptionKey="CC510D … 8925E6" validationKey="BEAC8 … 6A4B1DE" />  
    ```  
  
- Nakonfigurujte aplikaci tak, aby používala <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> ji přidáním do kolekce obslužných rutin tokenu. Je nutné nejprve odebrat <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (nebo jakékoli obslužné rutiny odvozené <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> z třídy) z kolekce obslužných rutin tokenu, pokud je taková obslužná rutina přítomna. Používá třídu, která chrání data souborů cookie relace pomocí `<machineKey>` kryptografického materiálu zadaného v elementu. <xref:System.IdentityModel.Services.MachineKeyTransform> <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> Následující kód XML ukazuje, jak přidat <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> do kolekce obslužných rutin tokenu.  
  
    ```xml  
    <securityTokenHandlers>  
      <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
      <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </securityTokenHandlers>  
    ```  
  
- Je nutné <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> odvozovat z a implementovat distribuované ukládání do mezipaměti, tj. mezipaměť, která je přístupná ze všech počítačů ve farmě, na které se může spustit RP. Nakonfigurujte RP tak, aby používal distribuovanou mezipaměť, zadáním [ \<prvku sessionSecurityTokenCache >](../configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) v konfiguračním souboru. Můžete přepsat <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> metodu v odvozené třídě pro implementaci podřízených elementů `<sessionSecurityTokenCache>` elementu, pokud jsou požadovány.  
  
    ```xml  
    <caches>  
      <sessionSecurityTokenCache type="MyCacheLibrary.MySharedSessionSecurityTokenCache, MyCacheLibrary">  
        <!--optional child configuration elements, if implemented by the derived class -->  
      </sessionSecurityTokenCache>  
    </caches>  
    ```  
  
     Jedním ze způsobů, jak implementovat distribuované ukládání do mezipaměti, je poskytnout front-endu WCF pro vlastní mezipaměť. Další informace o implementaci služby ukládání do mezipaměti WCF najdete v tématu [Služba pro ukládání do mezipaměti WCF](#BKMK_TheWCFCachingService). Další informace o implementaci klienta WCF, který může aplikace RP použít k volání služby ukládání do mezipaměti, najdete v tématu [klient mezipaměti WCF](#BKMK_TheWCFClient).  
  
- Pokud vaše aplikace zjistí přesměrované tokeny, musíte dodržovat podobnou strategii distribuovaného ukládání do mezipaměti pro mezipaměť tokenu, která <xref:System.IdentityModel.Tokens.TokenReplayCache> se odvozuje z a odkazuje na službu ukládání do mezipaměti tokenů [ \<v tokenReplayCache >](../configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element konfigurace.  
  
> [!IMPORTANT]
> Všechny příklady XML a kód v tomto tématu jsou pořízeny z ukázky [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) .  
  
> [!IMPORTANT]
> Příklady v tomto tématu jsou k dispozici tak, jak jsou, a nejsou určeny pro použití v produkčním kódu beze změny.  
  
<a name="BKMK_TheWCFCachingService"></a>   
## <a name="the-wcf-caching-service"></a>Služba pro ukládání do mezipaměti WCF  
 Následující rozhraní definuje kontrakt mezi službou pro ukládání do mezipaměti WCF a klientem WCF používaným aplikací předávající strany ke komunikaci s ním. V podstatě zveřejňuje metody <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> třídy jako operace služby.  
  
```csharp
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
  
 Následující kód ukazuje implementaci služby pro ukládání do mezipaměti WCF. V tomto příkladu se používá výchozí mezipaměť tokenu relace v paměti, kterou implementuje WIF. Alternativně můžete implementovat trvalou mezipaměť zálohovanou databází. `ISessionSecurityTokenCacheService`Definuje rozhraní zobrazené výše. V tomto příkladu nejsou zobrazeny všechny metody vyžadované k implementaci rozhraní pro zkrácení.  
  
```csharp
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
## <a name="the-wcf-caching-client"></a>Klient mezipaměti WCF  
 Tato část ukazuje implementaci třídy, která je odvozena z <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> a která deleguje volání do služby ukládání do mezipaměti. Aplikaci RP nakonfigurujete tak, aby tuto třídu používala prostřednictvím [ \<elementu sessionSecurityTokenCache >](../configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) , jako v následujícím kódu XML.  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
 Třída přepíše <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> metodu pro získání koncového bodu služby z vlastního `<cacheServiceAddress>` podřízeného prvku `<sessionSecurityTokenCache>` elementu. Pomocí tohoto koncového bodu inicializuje `ISessionSecurityTokenCacheService` kanál, přes který může komunikovat se službou.  V tomto příkladu nejsou zobrazeny všechny metody vyžadované k implementaci <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> třídy pro zkrácení.  
  
```csharp
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>
- <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>
- [Správa relací WIF](wif-session-management.md)
