---
title: Trvanlivý kontext instance
ms.date: 03/30/2017
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
ms.openlocfilehash: 25772e7f119ddd5a144d223f402e815380b3eba5
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316931"
---
# <a name="durable-instance-context"></a>Trvanlivý kontext instance
Tento příklad ukazuje, jak přizpůsobit modul runtime Windows Communication Foundation (WCF) umožňuje trvalý instance kontexty. Jako svůj záložní úložiště (SQL Server 2005 Express v tomto případě) používá SQL Server 2005. Ale také poskytuje způsob, jak přistupovat k mechanismy vlastního úložiště.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Tento příklad zahrnuje rozšíření vrstvy kanálu a vrstva modelu služby WCF. Proto je potřeba pochopit základní koncepty před přechodem k podrobnostem implementace.  
  
 Kontexty trvalý instance najdete ve skutečných scénářích velmi často. Nákupní košík aplikaci například má schopnost pozastavit nákupní uprostřed prostřednictvím a pokračovat na další den. Takže pokud používáte nákupního košíku dalšího dne, naše původního kontextu se obnoví. Je důležité si uvědomit, že aplikaci nákupního košíku (na serveru) nespravuje nákupního košíku instance odpojené jsme se. Místo toho uchovává stavu do trvalého úložiště médií a používá se při vytváření nové instance pro obnovený kontext. Proto instance služby, která může obsluhovat pro stejný kontext není stejný jako předchozí instanci (to znamená, nemá stejnou adresu paměti).  
  
 Trvanlivý kontext instance je možné díky malé protokol, který vyměňuje ID kontextu mezi klientem a službou. Toto ID kontextu je vytvořen na straně klienta a do služby. Při vytvoření instance služby je modul runtime služby se pokouší načíst trvalého stavu, který odpovídá toto ID kontextu z trvalého úložiště (ve výchozím nastavení je databáze systému SQL Server 2005). Pokud je k dispozici žádný stav má novou instanci výchozího stavu. Implementace služby používá k označení operace, které změní stav implementace služby tak, aby modul runtime můžete uložit instanci služby po vyvolání je vlastní atribut.  
  
 Podle předchozího popisu lze dva kroky snadno rozlišit k dosažení cíle:  
  
1. Změňte zprávu, která přejde na lince provádět ID kontextu.  
  
2. Místní chování služby k implementaci vlastní logiky vytvoření instance změňte.  
  
 Vzhledem k tomu, že první z nich v seznamu ovlivňuje zpráv na lince by měla být implementována jako vlastního kanálu a připojili k vrstvě kanálu. Druhá možnost se týká pouze místní chování služby a proto může být implementována rozšíření několik bodů rozšiřitelnosti služby. V následujících částech jsou popsány každý z těchto rozšíření.  
  
## <a name="durable-instancecontext-channel"></a>Kanál kontextu InstanceContext durable  
 První věc, kterou si prohlédnout je rozšíření vrstvy kanálu. Prvním krokem při psaní vlastního kanálu je rozhodnout strukturu komunikační kanál. Jak je uvedena nová přenosový protokol kanálu by měla fungovat s téměř jakémkoli jiném kanálu v zásobníku kanálu. Proto má podporovat všechny vzorky zprávy exchange. Základní funkce kanálu je však stejný bez ohledu na jeho strukturu komunikace. Přesněji řečeno z klienta by měl zápis ID kontextu do zprávy a ze služby by toto ID kontextu četlo zprávy a předejte jej do vyšší úrovně. Proto `DurableInstanceContextChannelBase` je vytvořená třída, která slouží jako abstraktní základní třída pro všechny implementace kanálu kontextu trvalé instanci. Tato třída obsahuje běžným funkcím správy stavu počítače a dvou chráněné členy pro použití a přečtěte si informace o kontextu do a ze zprávy.  
  
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
  
 Tyto dvě metody využívání `IContextManager` implementace pro zápis a čtení ID kontextu do nebo ze zprávy. (`IContextManager` je vlastní rozhraní používá k definování kontraktů pro všechny místní správce.) Kanál může obsahovat buď ID kontextu, v záhlaví SOAP, které vlastní nebo v hlavičce souboru cookie HTTP. Každá implementace správce kontextu dědí z `ContextManagerBase` třídu, která obsahuje běžné funkce pro všechny správce kontextu. `GetContextId` Metody této třídy se používá k pocházejí z ID kontextové z klienta. Když kontextu, který je ID pochází poprvé, tato metoda uloží ho do textového souboru, jehož název je vytvářený adresu vzdáleného koncového bodu (neplatné znaky názvu souboru v typické identifikátory URI jsou nahrazeny @ znaků).  
  
 Později je vyžadováno pro stejný koncový bod vzdáleného ID kontextu, zkontroluje, zda existuje příslušný soubor. Pokud ano, přečte ID kontextu a vrátí. V opačném případě vrátí ID nově generovaným kontextem a uloží jej do souboru. Ve výchozí konfiguraci tyto soubory jsou umístěny v adresáři s názvem ContextStore, který je umístěný v adresáři temp aktuálního uživatele. Ale toto umístění je možné konfigurovat pomocí elementu vazby.  
  
 Mechanismus, který se používá k přenosu ID kontextu je možné konfigurovat. To může být buď napsaná hlavičky souborů cookie protokolu HTTP nebo vlastní hlavičky SOAP. Vlastní přístup záhlaví SOAP umožňuje tento protokol pomocí jiných protokolů než HTTP (například TCP nebo pojmenované kanály). Existují dvě třídy, a to `MessageHeaderContextManager` a `HttpCookieContextManager`, který implementovat tyto dvě možnosti.  
  
 Jejich zapsat kontextu ID zprávy odpovídajícím způsobem. Například `MessageHeaderContextManager` zapíše do záhlaví SOAP ve třídě `WriteContext` metoda.  
  
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
  
 Jak `ApplyContext` a `ReadContextId` metody v `DurableInstanceContextChannelBase` vyvolání třídy `IContextManager.ReadContext` a `IContextManager.WriteContext`v uvedeném pořadí. Ale tyto místní správci nejsou vytvořené přímo `DurableInstanceContextChannelBase` třídy. Místo toho používá `ContextManagerFactory` třídě, aby provedl tuto úlohu.  
  
```  
IContextManager contextManager =  
                ContextManagerFactory.CreateContextManager(contextType,   
                this.contextStoreLocation,   
                this.endpointAddress);  
```  
  
 `ApplyContext` Vyvolá metodu odesílajícího kanály. Ho vkládá ID kontextu pro odchozí zprávy. `ReadContextId` Vyvolá metoda přijímající kanály. Tato metoda zajišťuje, že ID kontextu je k dispozici v příchozích zprávách a přidá jej do `Properties` kolekce `Message` třídy. Také vyvolá výjimku `CommunicationException` v případě selhání přečíst ID kontextu a proto způsobí, že kanál ho.  
  
```  
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);  
```  
  
 Než budete pokračovat, je důležité porozumět využití `Properties` kolekce `Message` třídy. Obvykle to `Properties` kolekce se používá při předání dat z snížit na vyšší úrovně z vrstvy kanálu. Tímto způsobem požadovaná data je možné poskytnout vyšší úrovně konzistentním způsobem bez ohledu na podrobnosti protokolu. Jinými slovy vrstvy kanálu můžete odesílat a přijímat ID kontextu jako záhlaví SOAP nebo Hlavička cookie HTTP. Ale to není nezbytné pro vyšší úrovně vědět o tyto podrobnosti, protože vrstvy kanálu zpřístupňuje tyto informace v `Properties` kolekce.  
  
 Teď se `DurableInstanceContextChannelBase` třídy v místě všech deset rozhraní nezbytné (IOutputChannel IInputChannel, IOutputSessionChannel, IInputSessionChannel, třídu IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, Musí být implementované IDuplexChannel, IDuplexSessionChannel). Se podobají každý vzoru výměny zpráv k dispozici (datagramu, simplexně, duplexní režim a jejich s relacemi varianty). Každá z těchto implementací základní třídy výše popsaný a volání Zdědit `ApplyContext` a `ReadContexId` odpovídajícím způsobem. Například `DurableInstanceContextOutputChannel` – který implementuje rozhraní IOutputChannel – zavolá `ApplyContext` metoda z každé metody, která odesílá zprávy.  
  
```  
public void Send(Message message, TimeSpan timeout)  
{  
    // Apply the context information before sending the message.  
    this.ApplyContext(message);  
    //…  
}   
```  
  
 Na druhé straně `DurableInstanceContextInputChannel` – která implementuje `IInputChannel` rozhraní - volání `ReadContextId` metoda v každé metodě, která přijímá zprávy.  
  
```  
public Message Receive(TimeSpan timeout)  
{  
    //…  
      ReadContextId(message);  
      return message;  
}  
```  
  
 Kromě toho tyto implementace kanálu delegáta volání metod na kanál pod nimi v zásobníku kanálu. S relacemi varianty však mít základní logiku, abyste měli jistotu, že ID kontextu se odesílají a je pro čtení jenom pro první zprávu, která způsobí, že relace, který se má vytvořit.  
  
```  
if (isFirstMessage)  
{  
//…  
    this.ApplyContext(message);  
    isFirstMessage = false;  
}  
```  
  
 Tyto implementace kanálu se pak přidá do modulu runtime kanál WCF `DurableInstanceContextBindingElement` třídy a `DurableInstanceContextBindingElementSection` třídy odpovídajícím způsobem. Zobrazit [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) ukázková dokumentace pro další podrobnosti o elementů vazby a oddíly elementů vazby kanálu.  
  
## <a name="service-model-layer-extensions"></a>Rozšíření modelu vrstvy služeb  
 Teď, když má ID kontextu přenést přes kanál vrstvu, je možné implementovat chování služby k přizpůsobení instance. V této ukázce Správce úložiště slouží k načtení a uložení stavu z nebo do trvalého úložiště. Jak jsme vysvětlili dříve, tato ukázka poskytuje správce úložiště, který používá SQL Server 2005 jako svůj záložní úložiště. Je však také možné přidat vlastní úložiště mechanismy pro toto rozšíření. K tomu veřejného rozhraní je teď deklarována, který musí implementovat všechny správce úložiště.  
  
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
  
 V `GetInstance` metoda serializovaných dat je pro čtení pro daný kontext ID a přiřazený objekt vytvořený z něj je vrátit zpět volajícímu.  
  
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
  
 Uživatelé těchto úložiště správce neměl konkretizovat přímo. Používají `StorageManagerFactory` třídy, který abstrahuje od podrobnosti o vytvoření Správce úložiště. Tato třída obsahuje jeden statický člen `GetStorageManager`, která vytvoří instanci typu správce daného úložiště. Pokud je parametr typu `null`, tato metoda vytvoří instanci výchozí `SqlServerStorageManager` třídy a vrátí jej. Také ověří daného typu, abyste měli jistotu, že implementuje `IStorageManager` rozhraní.  
  
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
  
 Je implementován potřebnou infrastrukturu pro čtení a zápis instance z trvalého úložiště. Teď mají nezbytné kroky, chcete-li změnit chování služby mají být provedeny.  
  
 Prvním krokem tohoto procesu máme uložte kontextu ID, které pochází z vrstvy kanálu na aktuálním kontextu InstanceContext. Třída InstanceContext je součástí modulu runtime, který slouží jako propojení mezi dispečer WCF a instance služby. Je možné poskytnout další stav a chování v instanci služby. To je nezbytné, protože při komunikaci s relacemi je odesláno ID kontext pouze s první zprávou.  
  
 WCF umožňuje rozšíření komponenty modulu runtime InstanceContext tak, že přidáte nový stav a chování pomocí způsobu rozšiřitelném objektu. Vzor rozšiřitelném objektu se používá ve službě WCF buď rozšířit existující třídy modulu runtime s novými funkcemi nebo přidávání nových funkcí stavu k objektu. Existují tři rozhraní ve vzoru extensible object - IExtensibleObject\<T >, IExtension\<T > a IExtensionCollection\<T >:  
  
-   IExtensibleObject\<T > rozhraní implementují objekty, které umožňují rozšíření, která přizpůsobit jejich funkce.  
  
-   IExtension\<T > rozhraní implementují objekty, které jsou rozšíření třídy typu T.  
  
-   IExtensionCollection\<T > rozhraní je kolekce IExtensions, který umožňuje načítání IExtensions podle jejich typu.  
  
 Proto třídu InstanceContextExtension by měl být vytvořen, který implementuje rozhraní IExtension a definuje požadovaný stav uložení ID kontextu. Tato třída rovněž poskytuje stavu k uložení úložiště správce používá. Po uložení nového stavu by neměla být možné jej upravit. Stav je proto k dispozici a uloží do instance v době, kdy je právě vytvořený a pak dostupná jenom pomocí vlastnosti jen pro čtení.  
  
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
  
 InstanceContextInitializer třída implementuje rozhraní IInstanceContextInitializer a přidá do kolekce rozšíření kontextu InstanceContext vytváří rozšíření místní instance.  
  
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
  
 Jak bylo popsáno dříve ID kontextu je číst z `Properties` kolekce `Message` třídy a předat konstruktoru třídy rozšíření. Tento příklad ukazuje, jak nelze vyměňovat informace mezi vrstvami konzistentním způsobem.  
  
 Dalším důležitým krokem přepisuje proces vytvoření instance služby. WCF umožňuje implementovat vlastní instance chování a zapojení do modulu runtime pomocí IInstanceProvider rozhraní. Nové `InstanceProvider` třídy je implementováno s cílem provést tuto úlohu. V konstruktoru je přijat typ služby očekává od instance zprostředkovatele. Později to slouží k vytvoření nové instance. V `GetInstance` implementace Správce úložiště je vytvořena instance hledáte trvalé instanci. Vrátí-li `null` novou instanci daného typu služby je vytvořena instance a vrátit zpět volajícímu.  
  
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
  
 Dalším důležitým krokem je instalace `InstanceContextExtension`, `InstanceContextInitializer` a `InstanceProvider` třídy do modulu runtime service model. Vlastní atribut může použít k označení třídy implementace služby k instalaci chování. `DurableInstanceContextAttribute` Obsahuje implementaci pro tento atribut a implementuje `IServiceBehavior` rozhraní pro rozšíření modulu runtime celé služby.  
  
 Tato třída obsahuje vlastnosti, která přijímá typ Správce úložiště, který se má použít. Tímto způsobem implementace umožňuje uživatelům zadat vlastní `IStorageManager` implementace jako parametr tohoto atributu.  
  
 V `ApplyDispatchBehavior` implementace `InstanceContextMode` aktuálního `ServiceBehavior` atribut se ověřuje. Pokud tato vlastnost nastavená na jednotlivý prvek, povolení trvalý vytváření instancí není možné a `InvalidOperationException` je vyvolána výjimka, aby upozornil hostitele.  
  
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
  
 Po této instance Správce úložiště, inicializátor instance kontextu a poskytovatele instance jsou vytvořeny a nainstalován v `DispatchRuntime` vytvořena pro každý koncový bod.  
  
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
  
 Stručně řečeno, pokud tuto ukázku vytvořil kanál, který povolené vlastní přenosový protokol pro kontext vlastní ID exchange a přepíše výchozí chování pro načtení instance z trvalého úložiště vytváření instancí.  
  
 Co je ponecháno je způsob, jak ušetřit instance služby do trvalého úložiště. Jak je popsáno výše, již existuje požadovanou funkci pro uložení stavu v `IStorageManager` implementace. Nyní musíte integrujeme to s modulem runtime WCF. Je vyžadován jiný atribut, který se vztahuje na metody ve třídě implementaci služby. Tento atribut se má použít pro metody, které ke změně stavu instance služby.  
  
 `SaveStateAttribute` Třída implementuje tuto funkci. Implementuje navíc `IOperationBehavior` třídy změnit modul runtime WCF pro každou operaci. Když metoda je označena pomocí tohoto atributu, vyvolá modul runtime WCF `ApplyBehavior` metody odpovídající `DispatchOperation` se vytváří. V této implementaci metody je jediný řádek kódu:  
  
```  
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);  
```  
  
 Tento pokyn vytvoří instanci `OperationInvoker` zadejte a přiřadí ji k `Invoker` vlastnost `DispatchOperation` vytváří. `OperationInvoker` Třídy tvoří obálku pro původce volání operace výchozí vytvořené pro `DispatchOperation`. Tato třída implementuje `IOperationInvoker` rozhraní. V `Invoke` implementace metody volání skutečné metody se deleguje na původce volání vnitřní operace. Však teprve potom se informuje správce úložiště v výsledky `InstanceContext` se používá pro uložení instance služby.  
  
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
 Dokončení vrstvy kanálu a rozšíření modelu vrstvy služeb i se teď dá v aplikacích WCF. Služby se mají přidat do kanálu zásobníku použití vlastní vazby kanálu a pak označit třídy implementace služby s příslušnými atributy.  
  
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
  
 Klientské aplikace, musíte přidat DurableInstanceContextChannel do zásobníku kanál použití vlastní vazby. Ke konfiguraci kanálu deklarativně v konfiguračním souboru, v části elementu vazby musí být přidán do kolekce rozšíření elementu vazby.  
  
```xml  
<system.serviceModel>  
 <extensions>  
   <bindingElementExtensions>  
     <add name="durableInstanceContext"  
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
   </bindingElementExtensions>  
 </extensions>  
```  
  
 Prvek vazby můžete jej použít s vlastní vazby, stejně jako ostatní standardní vazbu prvky:  
  
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
 Tuto ukázku jsme si ukázali, jak vytvořit vlastní protokol kanál a přizpůsobit chování služby, aby je.  
  
 Rozšíření lze dále zvýšit tím, že uživatelům určit, `IStorageManager` implementace pomocí konfiguračního oddílu. Díky tomu je možné změnit bez opětovné kompilace kódu služby záložního úložiště.  
  
 Kromě toho by se mohl pokusit implementace třídy (například `StateBag`), který zapouzdří stav instance. Třídy je zodpovědné za trvalost stavu pokaždé, když se změní. Díky tomu můžete předejít použití `SaveState` atribut a přesněji provedení zachování práce (například může zachování stavu, když ve skutečnosti je změněn stav místo uložení pokaždé, když při metodu s `SaveState` atribut volá se).  
  
 Když spustíte ukázku, zobrazí se následující výstup. Klient přidá dvě položky do jeho nákupního košíku a potom získá seznam položek v jeho nákupního košíku ze služby. Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby.  
  
```  
Enter the name of the product: apples  
Enter the name of the product: bananas  
  
Shopping cart currently contains the following items.  
apples  
bananas  
Press ENTER to shut down client  
```  
  
> [!NOTE]
>  Znovu sestavit službu přepíše soubor databáze. Sledovat stavů zachovaný během různých spuštění ukázky, se ujistěte, že znovu sestavte ukázku mezi spuštění.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  SQL Server 2005 nebo SQL Express 2005. tuto ukázku spustit, musí běžet. Pokud používáte systém SQL Server 2005, je třeba upravit konfigurace služby připojovací řetězec. Při spuštění mezi počítači systému SQL Server je potřeba jenom na počítači serveru.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`  
