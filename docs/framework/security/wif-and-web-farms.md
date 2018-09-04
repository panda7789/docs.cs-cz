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
# <a name="wif-and-web-farms"></a>Technologie WIF a webové farmy
Při použití technologie Windows Identity Foundation (WIF) k zabezpečení prostředků aplikace předávající stranu, která je nasazená ve webové farmě, musíte provést určité kroky k zajištění, že technologie WIF zpracovávat tokeny z instancí aplikace předávající strany, který běží na různých počítače ve farmě. Dané zpracování zahrnuje ověřování podpisů tokenu relace, šifrování a dešifrování tokenů relace, ukládání do mezipaměti relace tokeny a zjišťování, odesílal tokeny zabezpečení.  
  
 V typické případy Pokud technologie WIF slouží k zabezpečení prostředků aplikace předávající strany – zda RP běží na jednom počítači nebo ve webové farmě--relaci pokládáme stav, pomocí klienta na základě tokenu zabezpečení, který byl získán od služby tokenů zabezpečení (STS). To je vyhnout se vynutí, aby měl k ověření na službu tokenů zabezpečení pro každý prostředek aplikace, která je zabezpečena pomocí technologie WIF klient. Další informace o zpracování relací WIF najdete v tématu [Správa relací WIF](../../../docs/framework/security/wif-session-management.md).  
  
 Pokud použijete výchozí nastavení technologie WIF provede následující akce:  
  
-   Používá instanci <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> třídy ke čtení a zápisu tokenu relace (instance <xref:System.IdentityModel.Tokens.SessionSecurityToken> třídy), který představuje deklarace identity a další informace o tokenu zabezpečení, která byla použita pro ověřování, a také informace o relaci samotný. Token relace je zabalená a uložená v souboru cookie relace. Ve výchozím nastavení <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> používá <xref:System.IdentityModel.ProtectedDataCookieTransform> třídu, která používá Data Protection API (DPAPI), k ochraně tokenu relace. Rozhraní DPAPI poskytuje ochranu s použitím přihlašovacích údajů uživatele nebo počítače a uloží klíčových dat v profilu uživatele.  
  
-   Použije výchozí, implementace v paměti <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> třídy k ukládání a zpracování tokenu relace.  
  
 Tato výchozí nastavení fungují v situacích, ve kterých je aplikace předávající strany nasazené na jednom počítači; ale při nasazení ve webové farmě, každý požadavek HTTP může být zaslána a zpracovává jinou instanci aplikace předávající strany, který běží na jiném počítači. V tomto scénáři nebude fungovat nastavení technologie WIF je popsáno výše, protože token ochranu a ukládání tokenu do mezipaměti jsou závislé na určitém počítači.  
  
 Pokud chcete nasadit aplikaci předávající strany ve webové farmě, musíte zajistit, že zpracování relace tokenů (a také přehraná tokenů) není závislá na aplikaci spuštěné na určitém počítači. Můžete provést například jde implementovat vaše aplikace předávající strany, tak, aby používala funkce poskytované službou ASP.NET `<machineKey>` element konfigurace a nabízí distribuované ukládání do mezipaměti pro zpracování relace tokenů a znovu přehrát tokeny. `<machineKey>` Element slouží k určení klíče potřebné k ověření, šifrování a dešifrování tokenů v konfiguračním souboru, který umožňuje určit stejnými klíči na různých počítačích ve webové farmě. Technologie WIF umožňuje obslužnou rutinu tokenu relace specializované <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>, tokeny, které chrání pomocí klíče specifikované v `<machineKey>` elementu. K implementaci této strategie, můžete postupujte podle těchto pokynů:  
  
-   Použití technologie ASP.NET `<machineKey>` element v konfiguraci s ohledem na podepisování a šifrování klíče, které lze použít na počítačích ve farmě. Následující kód XML ukazuje specifikaci `<machineKey>` element v rámci `<system.web>` element v konfiguračním souboru.  
  
    ```xml  
    <machineKey compatibilityMode="Framework45" decryptionKey="CC510D … 8925E6" validationKey="BEAC8 … 6A4B1DE" />  
    ```  
  
-   Konfigurace aplikace pro použití <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> přidáním do kolekce obslužné rutiny tokenů. Je nutno nejprve odstranit <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (nebo libovolné obslužné rutiny odvozených z <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> třídy) z obslužné rutiny tokenů kolekce, pokud tato obslužná rutina je k dispozici. <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> Používá <xref:System.IdentityModel.Services.MachineKeyTransform> třídu, která chrání data souboru cookie relace pomocí kryptografický materiál podle `<machineKey>` elementu. Následující kód XML ukazuje, jak přidat <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> ke kolekci obslužné rutiny tokenů.  
  
    ```xml  
    <securityTokenHandlers>  
      <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
      <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </securityTokenHandlers>  
    ```  
  
-   Jsou odvozeny z <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> a implementujte distribuované ukládání do mezipaměti, to znamená, mezipaměť, která je přístupná ze všech počítačů ve farmě, na kterém můžou spouštět RP. Nakonfigurovat předávající strana často tak, že určíte pomocí distribuované mezipaměti [ \<sessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element v konfiguračním souboru. Můžete přepsat <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> metoda v odvozené třídy k implementaci podřízených elementů `<sessionSecurityTokenCache>` elementu, jestliže jsou povinné.  
  
    ```xml  
    <caches>  
      <sessionSecurityTokenCache type="MyCacheLibrary.MySharedSessionSecurityTokenCache, MyCacheLibrary">  
        <!—optional child configuration elements, if implemented by the derived class -->  
      </sessionSecurityTokenCache>  
    </caches>  
    ```  
  
     Jedním ze způsobů implementace distribuované ukládání do mezipaměti je poskytnout WCF front-endu pro vaše vlastní mezipaměti. Další informace o implementaci ukládání do mezipaměti služby WCF najdete v tématu [služba ukládání do mezipaměti WCF](#BKMK_TheWCFCachingService). Další informace o implementaci klienta WCF, která aplikace předávající strany můžete použít k volání službu ukládání do mezipaměti najdete v tématu [The WCF ukládání do mezipaměti klienta](#BKMK_TheWCFClient).  
  
-   Pokud aplikace zjistí přehraná tokeny je třeba dodržet podobná distribuované ukládání do mezipaměti strategie pro ukládání do mezipaměti opětovného přehrání tokenu odvozením z <xref:System.IdentityModel.Tokens.TokenReplayCache> a odkazuje na vaše opětovného přehrání tokenu, ukládání do mezipaměti služby [ \< tokenReplayCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) konfiguračního prvku.  
  
> [!IMPORTANT]
>  Všechny ukázkový soubor XML a kód v tomto tématu je převzata z [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) vzorku.  
  
> [!IMPORTANT]
>  Příklady v tomto tématu jsou k dispozici jako-je a není určena pro použití v produkčním kódu bez jakýchkoli úprav.  
  
<a name="BKMK_TheWCFCachingService"></a>   
## <a name="the-wcf-caching-service"></a>Ukládání do mezipaměti služby WCF  
 Následující rozhraní definuje kontrakt mezi klienta WCF používá aplikaci předávající strany ke komunikaci s ním a ukládání do mezipaměti služby WCF. V podstatě zveřejňuje metody <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> třídu jako servisní operace.  
  
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
  
 Následující kód ukazuje implementaci WCF služby ukládání do mezipaměti. V tomto příkladu, ve výchozím nastavení se používá mezipaměť tokenu relace v paměti pomocí technologie WIF implementovat. Alternativně je možné implementovat trvalý mezipaměti databázi. `ISessionSecurityTokenCacheService` definuje rozhraní uvedené výše. V tomto příkladu některé z metod požadovaných k implementaci rozhraní jsou zobrazeny pro zkrácení.  
  
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
 Tato část ukazuje implementaci třídy, která je odvozena z <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> a že delegáti volání službu ukládání do mezipaměti. Konfigurace aplikace předávající strany k použití této třídy prostřednictvím [ \<sessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element jako v následujícím souboru XML  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
 Třída přepsání <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> metodu k získání koncového bodu služby z vlastního `<cacheServiceAddress>` podřízený prvek `<sessionSecurityTokenCache>` elementu. Tento koncový bod se používá k inicializaci `ISessionSecurityTokenCacheService` kanál, přes který může komunikovat se službou.  V tomto příkladu všechny metody potřebnou k implementaci <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> třídy jsou platné pro zkrácení.  
  
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
