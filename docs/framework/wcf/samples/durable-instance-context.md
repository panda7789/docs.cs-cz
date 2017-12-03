---
title: "Trvanlivý kontext instance"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d4a1dfb2f517496cab1dcc2a57be3082c7c6f1a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="durable-instance-context"></a>Trvanlivý kontext instance
Tento příklad ukazuje, jak přizpůsobit [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] runtime umožňující kontexty trvanlivý instance. SQL Server 2005 používá jako své úložiště zálohování (SQL Server 2005 Express v tomto případě). Však také poskytuje přístup k vlastní úložiště mechanismy.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Tato ukázka zahrnuje rozšíření vrstvy kanálu a vrstva modelu služby z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Proto je potřeba pochopit základní koncepty před přechodem do podrobnosti implementace.  
  
 Trvanlivý instance kontexty naleznete ve skutečných scénářích velmi často. Aplikaci nákupního košíku například má možnost pozastavit shopping polovině vzdálenosti prostřednictvím a pokračovat na další den. Takže když jsme navštěvovat nákupní košík následujícího dne, je obnoven naše původní kontextu. Je důležité si uvědomit, nákupní košík aplikace (na serveru) při jsme jsou odpojené nespravuje nákupní košík instance. Místo toho potrvají stavu do média odolná úložiště a použije při vytváření nové instance pro obnovené kontext. Instance služby, která může obsluhovat stejný kontextu není stejný jako předchozí instanci (to znamená, nemá stejnou adresu paměti).  
  
 Trvanlivý kontext instance je možné díky malé protokol, který výměny ID kontextu mezi klientem a službou. Toto ID kontextu je vytvořen v klientovi a odesílané informace ke službě. Při vytvoření instance služby je běh služby se pokusí načíst trvalého stavu, která odpovídá toto ID kontextu z trvalého úložiště (ve výchozím nastavení je databáze systému SQL Server 2005). Pokud je k dispozici žádný stav má novou instanci výchozího stavu. Implementace služby používá k označení operace, které změní stav implementace služby tak, aby modul runtime můžete uložit instanci služby po vyvolání je vlastní atribut.  
  
 Podle předchozích popis může být snadno odlišena dva kroky k dosažení cíle:  
  
1.  Změnit zprávu, která přejde na sítě pro přenos ID kontextu.  
  
2.  Změňte chování místní služby k implementaci vlastní logiky zřizování instancí.  
  
 Vzhledem k tomu, že první z nich v seznamu ovlivňuje zprávy v drátové síti by měla být implementována jako vlastní kanál a být připojených k vrstvy kanálu. Druhá možnost se týká pouze místní chování služby a proto může být implementováno tím, že rozšíří několik bodů rozšiřitelnosti služby. V následujících částech několik každý z těchto rozšíření jsou popsané.  
  
## <a name="durable-instancecontext-channel"></a>Trvale InstanceContext kanálu  
 Nejprve si prohlédněte si je rozšíření vrstvy kanálu. Prvním krokem při psaní vlastní kanál, který se má rozhodnout strukturu komunikační kanál. Jako nový protokol přenosu je uvedena kanál by měla spolupracovat s téměř jakoukoli kanál v zásobníku kanálu. Proto má podporovat všechny vzorky exchange zprávu. Základní funkce služby kanál je však stejný bez ohledu na jeho struktura komunikace. Přesněji řečeno z klienta se zapíše ID kontextu zprávy a ze služby by měl čtení toto ID kontextu ze zprávy a předejte ji do vyšší úrovně. Z tohoto důvodu `DurableInstanceContextChannelBase` vytvořit třídu, která funguje jako abstraktní základní třída pro všechny instance trvanlivý kontext kanál implementace. Tato třída obsahuje běžné funkce správy stavu počítač a dva chráněné členy pro použití a přečtěte si informace o kontextu do a z zprávy.  
  
```  
class DurableInstanceContextChannelBase  
{  
  //…  
  protected void ApplyContext(Message message)  
  {  
    //…              
  }  
  protected string ReadContextId(Message message)  
  {  
    //…              
  }  
}  
```  
  
 Ujistěte se, tyto dvě metody použití `IContextManager` implementace k zápisu a čtení ID kontextu do nebo ze zprávy. (`IContextManager` je vlastní rozhraní používá k definování kontraktu pro všechny správce kontextu.) Kanál může obsahovat buď ID kontextu, ve vlastní hlavičky SOAP nebo v hlavičce souboru cookie HTTP. Každá implementace manager kontextu dědí z `ContextManagerBase` třídu, která obsahuje funkci společné pro všechny správce kontextu. `GetContextId` Metoda v tato třída se používá k pocházejí ID kontextu z klienta. Kontext, ve kterém je ID pochází poprvé, když tato metoda uloží ho do textového souboru, jehož název je vytvořený pomocí adresy vzdálený koncový bod (název souboru je neplatný. znaky v typické identifikátory URI jsou nahrazeny @ znaků).  
  
 Později je požadováno pro stejné vzdálený koncový bod ID kontextu, zkontroluje, zda existuje příslušný soubor. Pokud ano, přečte ID kontextu a vrátí. V opačném případě vrátí ID nově generovaným kontextem a uloží do souboru. U výchozí konfigurace tyto soubory jsou umístěny v adresář s názvem ContextStore, který se nachází v adresáři temp aktuálního uživatele. Toto umístění je ale možné konfigurovat pomocí prvku vazby.  
  
 Tento mechanismus používá k přenosu ID kontextu je možné konfigurovat. Ho může buď zapsat hlavička cookie HTTP nebo vlastní hlavičku protokolu SOAP. Vlastní hlavička přístup protokolu SOAP umožňuje tento protokol pomocí jiných protokolů než HTTP (například TCP nebo pojmenované kanály). Existují dvě třídy, konkrétně `MessageHeaderContextManager` a `HttpCookieContextManager`, který implementovat tyto dvě možnosti.  
  
 Oba dva zapisovat ID kontextu zpráva správně. Například `MessageHeaderContextManager` třída zapíše ho do hlavičku protokolu SOAP v `WriteContext` metoda.  
  
```  
public override void WriteContext(Message message)  
{  
  string contextId = this.GetContextId();  
  
  MessageHeader contextHeader =  
    MessageHeader.CreateHeader(DurableInstanceContextUtility.HeaderName,  
      DurableInstanceContextUtility.HeaderNamespace,  
      contextId,   
      true);  
  
  message.Headers.Add(contextHeader);  
}   
```  
  
 Jak `ApplyContext` a `ReadContextId` metody v `DurableInstanceContextChannelBase` vyvolání třídy `IContextManager.ReadContext` a `IContextManager.WriteContext`, v uvedeném pořadí. Však těmito manažery kontextu nejsou vytvořené přímo `DurableInstanceContextChannelBase` třídy. Místo toho použije `ContextManagerFactory` třídy provést tuto úlohu.  
  
```  
IContextManager contextManager =  
                ContextManagerFactory.CreateContextManager(contextType,   
                this.contextStoreLocation,   
                this.endpointAddress);  
```  
  
 `ApplyContext` Metoda je volána pomocí odesílání kanály. Se vloží ID kontextu do odesílaných zpráv. `ReadContextId` Je volána metoda podle přijímající kanály. Tato metoda zajišťuje, že ID kontextu je k dispozici v příchozí zprávy a přidává ji k `Properties` kolekce `Message` třídy. Také vyvolá `CommunicationException` v případě selhání čtení ID kontextu a proto způsobí, že kanál přerušena.  
  
```  
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);  
```  
  
 Než budete pokračovat, je důležité si uvědomit, použití `Properties` kolekce v `Message` třídy. Obvykle to `Properties` kolekce se používá při předávání dat z snížit na horní úrovně z vrstvy kanálu. Tímto způsobem k požadovaným datům lze zadat do vyšší úrovně konzistentním způsobem bez ohledu na podrobnosti protokolu. Jinými slovy vrstvy kanálu můžete odesílat a přijímat ID kontextu buď jako hlavičku protokolu SOAP nebo soubor cookie hlavičku protokolu HTTP. Není nutné pro vyšší úrovně vědět o tyto podrobnosti, protože vrstvy kanálu zpřístupní tyto informace v, ale `Properties` kolekce.  
  
 Teď se `DurableInstanceContextChannelBase` třídy zavedené všechny deset rozhraní potřebná (IOutputChannel IInputChannel, IOutputSessionChannel, IInputSessionChannel, třídu IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, Musí být implementované IDuplexChannel, IDuplexSessionChannel). Se podobají každých vzorce výměny zpráv k dispozici (datagram, simplex, duplexní režim a jejich relacemi varianty). Každý z těchto implementace dědění základní třída popsaných výše a volání `ApplyContext` a `ReadContexId` správně. Například `DurableInstanceContextOutputChannel` - který implementuje rozhraní IOutputChannel - volá `ApplyContext` metoda z každé metody, která odesílá zprávy.  
  
```  
public void Send(Message message, TimeSpan timeout)  
{  
    // Apply the context information before sending the message.  
    this.ApplyContext(message);  
    //…  
}   
```  
  
 Na druhé straně `DurableInstanceContextInputChannel` – které implementuje `IInputChannel` rozhraní - volání `ReadContextId` metoda dané metody, která přijímá zprávy.  
  
```  
public Message Receive(TimeSpan timeout)  
{  
    //…  
      ReadContextId(message);  
      return message;  
}  
```  
  
 Kromě toho tyto implementace kanál delegovat volání metod kanálu uvedenou pod nimi v zásobníku kanálu. Relacemi variant však mít základní logika a ujistěte se, že ID kontextu je odeslán a se čtou jenom pro první zprávu, která způsobí, že relace, který se má vytvořit.  
  
```  
if (isFirstMessage)  
{  
//…  
    this.ApplyContext(message);  
    isFirstMessage = false;  
}  
```  
  
 Tyto implementace kanál se pak přidají do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime kanál pomocí `DurableInstanceContextBindingElement` třídy a `DurableInstanceContextBindingElementSection` třídy správně. Najdete v článku [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) kanálu ukázková dokumentace pro další podrobnosti o elementů vazby a vazby element oddíly.  
  
## <a name="service-model-layer-extensions"></a>Rozšíření vrstvy modelu služby  
 Teď, když má ID kontextu cesty prostřednictvím vrstvy kanálu, můžete k přizpůsobení instance implementovat chování služby. V této ukázce Správce úložiště slouží k načtení a uložení stavu z nebo do trvalého úložiště. Jak je popsáno dříve, tato ukázka poskytuje správce úložiště, který používá systém SQL Server 2005 jako své úložiště zálohování. Je však také možné přidat vlastní úložiště mechanismy pro tuto příponu. K tomu veřejné rozhraní je deklarovaná, který musí implementovat všechny správce úložiště.  
  
```  
public interface IStorageManager  
{  
    object GetInstance(string contextId, Type type);  
    void SaveInstance(string contextId, object state);  
}  
```  
  
 `SqlServerStorageManager` Třída obsahuje výchozí `IStorageManager` implementace. V jeho `SaveInstance` metoda daný objekt serializován pomocí třídy XmlSerializer a je uložen do databáze SQL serveru.  
  
```  
XmlSerializer serializer = new XmlSerializer(state.GetType());  
string data;  
  
using (StringWriter writer = new StringWriter(CultureInfo.InvariantCulture))  
{  
    serializer.Serialize(writer, state);  
    data = writer.ToString();  
}  
  
using (SqlConnection connection = new SqlConnection(GetConnectionString()))  
{  
    connection.Open();  
  
    string update = @"UPDATE Instances SET Instance = @instance WHERE ContextId = @contextId";  
  
    using (SqlCommand command = new SqlCommand(update, connection))  
    {  
        command.Parameters.Add("@instance", SqlDbType.VarChar, 2147483647).Value = data;  
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;  
  
        int rows = command.ExecuteNonQuery();  
  
        if (rows == 0)  
        {  
            string insert = @"INSERT INTO Instances(ContextId, Instance) VALUES(@contextId, @instance)";  
            command.CommandText = insert;  
            command.ExecuteNonQuery();  
        }  
    }  
}  
```  
  
 V `GetInstance` metoda serializovaná data je pro čtení pro daný kontext ID a je objekt vytvořený z něj vrácen volajícímu.  
  
```  
object data;  
using (SqlConnection connection = new SqlConnection(GetConnectionString()))  
{  
    connection.Open();  
  
    string select = "SELECT Instance FROM Instances WHERE ContextId = @contextId";  
    using (SqlCommand command = new SqlCommand(select, connection))  
    {  
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;  
        data = command.ExecuteScalar();  
    }  
}  
  
if (data != null)  
{  
    XmlSerializer serializer = new XmlSerializer(type);  
    using (StringReader reader = new StringReader((string)data))  
    {  
        object instance = serializer.Deserialize(reader);  
        return instance;  
    }  
}  
```  
  
 Uživatelé těchto úložiště správci nemají co dělat vytvořit přímo instanci. Používají `StorageManagerFactory` třída, která abstrahuje z podrobnosti vytváření Správce úložiště. Tato třída obsahuje jeden statický člen `GetStorageManager`, která vytvoří instanci typu manager dané úložiště. Pokud je parametr typu `null`, tato metoda vytvoří instanci výchozí `SqlServerStorageManager` třídy a vrátí ji. Zároveň ověří, abyste měli jistotu, že implementuje daného typu `IStorageManager` rozhraní.  
  
```  
public static IStorageManager GetStorageManager(Type storageManagerType)  
{  
IStorageManager storageManager = null;  
  
if (storageManagerType == null)  
{  
    return new SqlServerStorageManager();  
}  
else  
{  
    object obj = Activator.CreateInstance(storageManagerType);  
  
    // Throw if the specified storage manager type does not  
    // implement IStorageManager.  
    if (obj is IStorageManager)  
    {  
        storageManager = (IStorageManager)obj;  
    }  
    else  
    {  
        throw new InvalidOperationException(  
                  ResourceHelper.GetString("ExInvalidStorageManager"));  
    }  
  
    return storageManager;  
}                  
}   
```  
  
 Potřebnou infrastrukturu pro čtení a zápisu instancí z trvalého úložiště je implementováno. Nyní musí vzít potřebné kroky, chcete-li změnit chování služby.  
  
 Jako první krok tohoto procesu se musí uložit ID kontextu, které pochází z vrstvy kanálu pro aktuální objekt InstanceContext. Parametr InstanceContext je součástí modulu runtime, která slouží jako propojení mezi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dispečera a instance služby. Slouží k poskytování dalších stavu a chování v instanci služby. To je důležité, protože komunikaci mezi relacemi ID kontextu jsou odeslány pouze s první zprávu.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]umožňuje rozšíření jeho komponenty runtime InstanceContext přidáním nového stavu a chování pomocí jeho vzor extensible objektu. Vzor extensible objektu se používá v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] buď rozšířit existující třídy runtime s novými funkcemi, nebo při přidání nových funkcí stavu do objektu. Existují tři rozhraní ve vzoru extensible objekt - IExtensibleObject\<T >, IExtension\<T > a IExtensionCollection\<T >:  
  
-   IExtensibleObject\<T > rozhraní je implementováno modulem objekty, které umožňují rozšíření, které přizpůsobit jejich funkce.  
  
-   IExtension\<T > rozhraní je implementováno modulem objekty, které jsou rozšíření třídy typu T.  
  
-   IExtensionCollection\<T > rozhraní je kolekce IExtensions, která umožňuje načítání IExtensions dle jejich typu.  
  
 Proto třídu InstanceContextExtension by měl být vytvořen, který implementuje rozhraní IExtension a definuje stav vyžaduje pro uložení ID kontextu. Tato třída rovněž poskytuje stav pro uložení úložiště správce používá. Po uložení nového stavu, neměl by být možné ji upravit. Stav jsou proto zadat a uložit do instance v době, kdy se vytvořený a potom dostupné jenom pomocí vlastnosti jen pro čtení.  
  
```  
// Constructor  
public DurableInstanceContextExtension(string contextId,   
            IStorageManager storageManager)  
{  
    this.contextId = contextId;  
    this.storageManager = storageManager;              
}  
  
// Read only properties  
public string ContextId  
{  
    get { return this.contextId; }  
}  
  
public IStorageManager StorageManager  
{  
    get { return this.storageManager; }              
}   
```  
  
 Třída InstanceContextInitializer implementuje rozhraní IInstanceContextInitializer a přidá do kolekce rozšíření InstanceContext vytvářen rozšíření místní instance.  
  
```  
public void Initialize(InstanceContext instanceContext, Message message)  
{  
    string contextId =   
  (string)message.Properties[DurableInstanceContextUtility.ContextIdProperty];  
  
    DurableInstanceContextExtension extension =  
                new DurableInstanceContextExtension(contextId,   
                     storageManager);  
    instanceContext.Extensions.Add(extension);  
}  
```  
  
 Jak bylo popsáno dříve ID kontextu je pro čtení z `Properties` kolekce `Message` třídy a předaný konstruktoru třídy extension. Tento příklad ukazuje, jak nelze vyměňovat informace mezi vrstvami konzistentním způsobem.  
  
 Další důležitý krok přepisují proces vytvoření instance služby. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Umožňuje implementace chování vlastní vytváření instancí a jejich zapojování až modulu runtime použijte rozhraní IInstanceProvider. Nové `InstanceProvider` implementaci třídy chcete tuto úlohu. V konstruktoru byla přijata od instance zprostředkovatele je očekáván typ služby. To se později používá k vytvoření nové instance. V `GetInstance` implementace instance Správce úložiště je vytvořena hledá trvalou instance. Vrátí-li `null` pak novou instanci typu služby vytvořena a vrácena volajícímu.  
  
```  
public object GetInstance(InstanceContext instanceContext, Message message)  
{  
    object instance = null;  
  
    DurableInstanceContextExtension extension =  
    instanceContext.Extensions.Find<DurableInstanceContextExtension>();  
  
    string contextId = extension.ContextId;  
    IStorageManager storageManager = extension.StorageManager;              
  
    instance = storageManager.GetInstance(contextId, serviceType);          
  
    if (instance == null)  
    {  
        instance = Activator.CreateInstance(serviceType);  
    }  
  
    return instance;  
}  
```  
  
 Dalším důležitým krokem je instalace `InstanceContextExtension`, `InstanceContextInitializer` a `InstanceProvider` tříd do modulu runtime modelu služby. Vlastní atribut může označit implementace třídy služeb pro instalaci chování. `DurableInstanceContextAttribute` Obsahuje implementaci pro tento atribut a implementuje `IServiceBehavior` rozhraní rozšíření modulu runtime celé služby.  
  
 Tato třída obsahuje vlastnosti, která přijímá typ Správce úložiště, který se má použít. Tímto způsobem implementace umožňuje uživatelům zadat vlastní `IStorageManager` implementace jako parametr tohoto atributu.  
  
 V `ApplyDispatchBehavior` implementace `InstanceContextMode` aktuálního `ServiceBehavior` atribut ověření. Pokud je nastavena na Singleton, povolení trvanlivý vytváření instancí není možné a `InvalidOperationException` je vyvolána oznámit hostitele.  
  
```  
ServiceBehaviorAttribute serviceBehavior =  
    serviceDescription.Behaviors.Find<ServiceBehaviorAttribute>();  
  
if (serviceBehavior != null &&  
     serviceBehavior.InstanceContextMode == InstanceContextMode.Single)  
{  
    throw new InvalidOperationException(  
       ResourceHelper.GetString("ExSingeltonInstancingNotSupported"));  
}  
```  
  
 Po této instance Správce úložiště, instance kontextu inicializátoru a poskytovateli instance se vytváří a nainstalované v `DispatchRuntime` vytvořit pro každý koncový bod.  
  
```  
IStorageManager storageManager =   
    StorageManagerFactory.GetStorageManager(storageManagerType);  
  
InstanceContextInitializer contextInitializer =  
    new InstanceContextInitializer(storageManager);  
  
InstanceProvider instanceProvider =  
    new InstanceProvider(description.ServiceType);  
  
foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)  
{  
    ChannelDispatcher cd = cdb as ChannelDispatcher;  
  
    if (cd != null)  
    {  
        foreach (EndpointDispatcher ed in cd.Endpoints)  
        {  
            ed.DispatchRuntime.InstanceContextInitializers.Add(contextInitializer);  
            ed.DispatchRuntime.InstanceProvider = instanceProvider;  
        }  
    }  
}  
```  
  
 V souhrnu, pokud tato ukázka má vytvořeného kanálu, který je povolený protokol vlastní přenosu pro kontext vlastní ID exchange a taky přepíše výchozí chování instance načíst z trvalého úložiště vytváření instancí.  
  
 Co je ponechán je způsob, jak uložit instanci služby do trvalého úložiště. Jak je popsáno dříve, již existuje požadované funkce pro uložení stavu v `IStorageManager` implementace. Jsme teď musíte integrovat o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modulu runtime. Jiný atribut je požadován, se vztahuje na metody ve třídě implementace služby. Tento atribut by měl použít pro metody, které změní stav instance služby.  
  
 `SaveStateAttribute` Třída implementuje tuto funkci. Také implementuje `IOperationBehavior` třída změnit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modul runtime pro každou operaci. Když metoda je označena k tomuto atributu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vyvolá runtime `ApplyBehavior` metoda při odpovídající `DispatchOperation` je vytvářen. V této implementaci metoda je jediný řádek kódu:  
  
```  
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);  
```  
  
 Tento pokyn vytvoří instanci `OperationInvoker` zadejte a přiřadí ji k `Invoker` vlastnost `DispatchOperation` vytvářen. `OperationInvoker` Třída je obálka pro původce volání operace výchozí pro vytvořit `DispatchOperation`. Tato třída implementuje `IOperationInvoker` rozhraní. V `Invoke` implementace metod volání metody skutečné je delegovaný jako původce vnitřní operace. Nicméně před vrácením výsledky Správce úložiště v `InstanceContext` se používá pro uložení instance služby.  
  
```  
object result = innerOperationInvoker.Invoke(instance,  
    inputs, out outputs);  
  
// Save the instance using the storage manager saved in the   
// current InstanceContext.  
InstanceContextExtension extension =  
    OperationContext.Current.InstanceContext.Extensions.Find<InstanceContextExtension>();  
  
extension.StorageManager.SaveInstance(extension.ContextId, instance);  
return result;  
```  
  
## <a name="using-the-extension"></a>Pomocí rozšíření  
 Kanál vrstvy a služby model vrstvy rozšíření hotovi i nyní je možné použít při [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace. Služby mít do zásobníku kanál použití vlastní vazby, přidejte kanál a potom označit implementace třídy služeb s odpovídajícími atributy.  
  
```  
[DurableInstanceContext]  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class ShoppingCart : IShoppingCart  
{  
//…  
     [SaveState]  
     public int AddItem(string item)  
     {  
         //…  
     }  
//…  
 }  
```  
  
 Klientské aplikace, musíte přidat DurableInstanceContextChannel do zásobníku kanál použití vlastní vazby. Ke konfiguraci kanálu deklarativně v konfiguračním souboru, musí být přidán do kolekce element rozšíření vazby sekce prvku vazby.  
  
```xml  
<system.serviceModel>  
 <extensions>  
   <bindingElementExtensions>  
     <add name="durableInstanceContext"  
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
   </bindingElementExtensions>  
 </extensions>  
```  
  
 Nyní prvku vazby použít s vlastní vazby stejně jako další prvky standardní vazby:  
  
```xml  
<bindings>  
 <customBinding>  
   <binding name="TextOverHttp">  
     <durableInstanceContext contextType="HttpCookie"/>             
     <reliableSession />  
     <textMessageEncoding />  
     <httpTransport />  
   </binding>  
 </customBinding>  
</bindings>  
```  
  
## <a name="conclusion"></a>Závěr  
 Tato ukázka vám ukázal, jak vytvořit vlastní protokol kanál a postup přizpůsobení chování služby povolit.  
  
 Rozšíření lze dále zvýšit tím, že uživatelé, zadejte `IStorageManager` implementace pomocí konfigurační oddíl. Díky tomu je možné upravit záložní úložiště bez nutnosti rekompilace kódu služby.  
  
 Kromě toho mohou zkuste implementace třídy (například `StateBag`), který zapouzdří stav instance. Třídy je zodpovědná za uložením stavu, vždy, když se změní. Tímto způsobem můžete vyhnout použitím `SaveState` atribut a provádět zachování pracovní přesněji (například může stav zachována, když je ve skutečnosti změnil stav místo uložení každý čas při metodu s `SaveState` atribut voláno).  
  
 Při spuštění ukázky, zobrazí se následující výstup. Klient přidá dvě položky do jeho nákupní košík a pak získá seznam položek v jeho nákupní košík ze služby. Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby.  
  
```  
Enter the name of the product: apples  
Enter the name of the product: bananas  
  
Shopping cart currently contains the following items.  
apples  
bananas  
Press ENTER to shut down client  
```  
  
> [!NOTE]
>  Znovu sestavit službu přepíše soubor databáze. Chcete-li sledovat stav zachována napříč více spustí vzorku, nezapomeňte znovu sestavit ukázku mezi spustí.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  SQL Server 2005 nebo SQL Express 2005. Chcete tuto ukázku spustit, musíte používat. Pokud používáte systém SQL Server 2005, musíte změnit konfiguraci služby připojovací řetězec. Při spuštění počítače napříč, SQL Server je potřeba jenom na počítači serveru.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`  
  
## <a name="see-also"></a>Viz také
