---
title: Trvanlivý kontext instance
ms.date: 03/30/2017
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
ms.openlocfilehash: 4c2e39aa257d4b4b9b3bd28e0cd469f09cae0766
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351622"
---
# <a name="durable-instance-context"></a>Trvanlivý kontext instance

Tato ukázka předvádí, jak přizpůsobit modul runtime Windows Communication Foundation (WCF), aby umožňoval trvalé kontexty instancí. Jako své záložní úložiště používá SQL Server 2005 (SQL Server 2005 Express v tomto případě). Poskytuje ale taky způsob, jak získat přístup k vlastním mechanismům úložiště.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

Tato ukázka zahrnuje rozšíření vrstvy kanálu a vrstvy modelu služby WCF. Proto je nutné před použitím podrobností implementace pochopit základní koncepty.

Trvalé kontexty instance můžete najít ve scénářích reálného světa často. Aplikace nákupního košíku má například možnost pozastavit nákup uprostřed a pokračovat v dalším dni. Takže když na příští den navštívíme nákupní košík, náš původní kontext se obnoví. Je důležité si uvědomit, že aplikace nákupního košíku (na serveru) neudržuje během odpojování instanci nákupního košíku. Místo toho uchovává svůj stav na trvalé paměťové médium a používá ho při vytváření nové instance pro obnovený kontext. Proto instance služby, která se může nabývat stejným kontextem, není stejná jako předchozí instance (to znamená, že nemá stejnou adresu paměti).

Je možné, že kontext trvalé instance je možný malým protokolem, který vyměňuje ID kontextu mezi klientem a službou. Toto ID kontextu se vytvoří v klientovi a přenáší do služby. Když je instance služby vytvořená, pokusí se modul runtime služby načíst trvalý stav, který odpovídá tomuto ID kontextu z trvalého úložiště (ve výchozím nastavení je to databáze SQL Server 2005). Pokud není k dispozici žádný stav, má nová instance svůj výchozí stav. Implementace služby používá vlastní atribut k označení operací, které mění stav implementace služby, aby modul runtime po jejich vyvolání mohl uložit instanci služby.

V předchozím popisu lze snadno odlišit dva kroky, aby bylo možné dosáhnout tohoto cíle:

1. Změňte zprávu, která je na lince, aby převedla ID kontextu.

2. Pokud chcete implementovat vlastní logiku vytváření instancí, změňte místní chování služby.

Vzhledem k tomu, že první v seznamu má vliv na zprávy, měly by být implementované jako vlastní kanál a musí se připojit ke vrstvě kanálu. Ta má vliv pouze na místní chování služby, a proto může být implementována rozšířením několika bodů rozšiřitelnosti služby. V následujících částech jsou popsána všechna tato rozšíření.

## <a name="durable-instancecontext-channel"></a>Trvalý kanál InstanceContext

První věc, kterou si můžete prohlédnout, je rozšíření vrstvy kanálu. Prvním krokem při psaní vlastního kanálu je určení komunikační struktury kanálu. V rámci zavedení nového přenosového protokolu by kanál měl spolupracovat s prakticky jakýmkoli jiným kanálem v zásobníku kanálů. Proto by měl podporovat všechny vzory výměny zpráv. Základní funkce kanálu jsou však stejné bez ohledu na jeho komunikační strukturu. Konkrétně z klienta by měl z klienta napsat ID kontextu pro zprávy a ze služby, které by mělo číst toto ID kontextu ze zpráv a předávat je do horních úrovní. Z tohoto `DurableInstanceContextChannelBase` důvodu je vytvořena třída, která funguje jako abstraktní základní třída pro všechny implementace kontextu trvalého kanálu instance. Tato třída obsahuje funkce správy běžných stavových počítačů a dva chráněné členy pro použití a čtení informací o kontextu do a ze zpráv.

```csharp
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

Tyto dvě metody využívají `IContextManager` implementace pro zápis a čtení ID kontextu do nebo ze zprávy. (`IContextManager` je vlastní rozhraní používané k definování kontraktu pro všechny správce kontextu.) Kanál může buď zahrnout ID kontextu ve vlastní hlavičce SOAP, nebo v hlavičce souboru cookie protokolu HTTP. Každá implementace správce kontextu dědí z `ContextManagerBase` třídy, která obsahuje společné funkce pro všechny správce kontextu. `GetContextId` Metoda v této třídě slouží k původnímu ID kontextu z klienta. Při prvním pokusu o ID kontextu je tato metoda uložena do textového souboru, jehož název je vytvořen pomocí adresy vzdáleného koncového bodu (neplatné znaky názvu souboru v typických identifikátorech URI jsou nahrazeny znakem @).

Později, když je ID kontextu vyžadováno pro stejný vzdálený koncový bod, kontroluje, zda existuje příslušný soubor. V takovém případě přečte ID kontextu a vrátí. V opačném případě vrátí nově generované ID kontextu a uloží jej do souboru. S výchozí konfigurací jsou tyto soubory umístěny v adresáři s názvem ContextStore, který se nachází v dočasném adresáři aktuálního uživatele. Toto umístění však lze konfigurovat pomocí elementu vazby.

Mechanismus použitý k přenosu ID kontextu je možné nakonfigurovat. Mohl by být buď zapsaný do hlavičky souboru cookie protokolu HTTP, nebo do vlastní hlavičky SOAP. Vlastní přístup k hlavičkám SOAP umožňuje používat tento protokol u jiných protokolů než HTTP (například TCP nebo Named Pipes). Existují dvě třídy, konkrétně `MessageHeaderContextManager` a `HttpCookieContextManager`, které implementují tyto dvě možnosti.

Oba Oba napíší ID kontextu do zprávy odpovídajícím způsobem. Například `MessageHeaderContextManager` třída ji zapíše do hlavičky SOAP `WriteContext` v metodě.

```csharp
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

`ApplyContext` Metody a `ReadContextId` ve`DurableInstanceContextChannelBase` třídě vyvolávají a`IContextManager.WriteContext`vuvedenémpořadí. `IContextManager.ReadContext` Tyto správce kontextu však nejsou přímo vytvořeny `DurableInstanceContextChannelBase` třídou. Místo toho používá `ContextManagerFactory` třídu k provedení této úlohy.

```csharp
IContextManager contextManager =
                ContextManagerFactory.CreateContextManager(contextType,
                this.contextStoreLocation,
                this.endpointAddress);
```

`ApplyContext` Metoda je vyvolána odesílajícími kanály. Vloží ID kontextu do odchozích zpráv. `ReadContextId` Metoda je vyvolána přijímacími kanály. Tato metoda zajistí, že ID kontextu je k dispozici v příchozích zprávách a přidá je do `Properties` kolekce `Message` třídy. Vyvolá `CommunicationException` také v případě, že dojde k selhání při čtení ID kontextu, čímž dojde k přerušení kanálu.

```csharp
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);
```

Než budete pokračovat, je důležité pochopit použití `Properties` kolekce `Message` ve třídě. Tato `Properties` kolekce se obvykle používá při předávání dat z nižší úrovně do horních úrovní z vrstvy kanálu. Tímto způsobem je možné zajistit, aby se požadovaná data poskytovala na nejvyšší úrovni konzistentním způsobem bez ohledu na podrobnosti protokolu. Jinými slovy, vrstva kanálu může odeslat a přijmout ID kontextu buď jako hlavičku protokolu SOAP, nebo jako hlavičku souboru cookie protokolu HTTP. Není ale nutné, aby horní úrovně věděli o těchto podrobnostech, protože vrstva kanálu zpřístupňuje tyto informace v `Properties` kolekci.

Nyní s `DurableInstanceContextChannelBase` třídou místo všech deseti z nezbytných rozhraní (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, třídu IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) musí být implementovány. Podobají se každému dostupnému vzoru výměny zpráv (datagram, simplexní, duplexní a jejich variantě v relaci). Každá z těchto implementací dědí základní třídu, která byla dříve `ApplyContext` popsána, a `ReadContextId` správné volání. Například, `DurableInstanceContextOutputChannel` který implementuje rozhraní IOutputChannel – `ApplyContext` zavolá metodu z každé metody, která odesílá zprávy.

```csharp
public void Send(Message message, TimeSpan timeout)
{
    // Apply the context information before sending the message.
    this.ApplyContext(message);
    //…
}
```

Na druhé straně – to `DurableInstanceContextInputChannel` `IInputChannel` implementuje rozhraní – volá `ReadContextId` metodu v každé metodě, která přijímá zprávy.

```csharp
public Message Receive(TimeSpan timeout)
{
    //…
      ReadContextId(message);
      return message;
}
```

Kromě toho tato implementace kanálu deleguje volání metody do kanálu pod nimi v zásobníku kanálu. Varianty v relaci však mají základní logiku, aby bylo zajištěno, že ID kontextu je odesláno a je určeno pouze pro první zprávu, která způsobí vytvoření relace.

```csharp
if (isFirstMessage)
{
//…
    this.ApplyContext(message);
    isFirstMessage = false;
}
```

Tato implementace kanálu se pak do modulu runtime `DurableInstanceContextBindingElement` kanálu WCF přidají odpovídající třídou a `DurableInstanceContextBindingElementSection` třídou. Další podrobnosti o prvcích vazby a oddílech prvků vazby najdete v ukázkové dokumentaci k [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) kanálu.

## <a name="service-model-layer-extensions"></a>Rozšíření vrstvy modelu služby

Teď, když je ID kontextu přenášeno přes vrstvu kanálu, může být implementováno chování služby pro přizpůsobení vytváření instancí. V této ukázce se k načtení a uložení stavu z nebo do trvalého úložiště používá správce úložiště. Jak bylo vysvětleno dříve, Tato ukázka poskytuje Správce úložiště, který jako své záložní úložiště používá SQL Server 2005. Do tohoto rozšíření je ale také možné přidat vlastní mechanismy úložiště. K tomu, aby bylo deklarováno veřejné rozhraní, které musí být implementováno všemi Správci úložiště.

```csharp
public interface IStorageManager
{
    object GetInstance(string contextId, Type type);
    void SaveInstance(string contextId, object state);
}
```

Třída obsahuje výchozí `IStorageManager`implementaci. `SqlServerStorageManager` Ve své `SaveInstance` metodě je daný objekt serializován pomocí objektu XmlSerializer a je uložen do databáze SQL Server.

```csharp
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

`GetInstance` V metodě jsou pro dané ID kontextu čtena Serializovaná data a objekt sestavený z něj je vrácen volajícímu.

```csharp
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

Uživatelé těchto správců úložiště by nemuseli vytvářet instance přímo. Používají `StorageManagerFactory` třídu, která je abstraktní z podrobností o vytváření Správce úložiště. Tato třída má jednoho statického člena `GetStorageManager`, který vytvoří instanci daného typu Správce úložiště. Pokud je `null`parametrem typu, tato metoda vytvoří instanci výchozí `SqlServerStorageManager` třídy a vrátí ji. Ověří také daný typ, aby zajistil, že implementuje `IStorageManager` rozhraní.

```csharp
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

Je implementována potřebná infrastruktura pro čtení a zápis instancí z trvalého úložiště. Teď je potřeba udělat kroky ke změně chování služby.

Jako první krok tohoto procesu musíme Uložit ID kontextu, které bylo předáno přes vrstvu kanálu, do aktuálního rozhraní InstanceContext. InstanceContext je komponenta modulu runtime, která funguje jako propojení mezi dispečerem WCF a instancí služby. Dá se použít k poskytnutí dalšího stavu a chování instance služby. To je nezbytné proto, že při komunikaci v relaci je ID kontextu odesláno pouze s první zprávou.

Služba WCF umožňuje rozšířit svou komponentu běhového prostředí InstanceContext přidáním nového stavu a chování pomocí jeho modelu rozšiřitelného objektu. Model rozšiřitelného objektu se používá ve službě WCF pro rozšiřující existující běhové třídy s novými funkcemi nebo pro přidání nových funkcí stavu do objektu. Existují tři rozhraní ve vzoru rozšiřitelného objektu – IExtensibleObject\<t >, IExtension\<t > a IExtensionCollection\<t >:

- Rozhraní IExtensibleObject\<T > je implementováno objekty, které umožňují rozšíření, která přizpůsobují jejich fungování.

- Rozhraní IExtension\<T > je implementováno objekty, které jsou příponami tříd typu T.

- Rozhraní IExtensionCollection\<T > je kolekce IExtensions, která umožňuje načíst IExtensions podle jejich typu.

Proto by měla být vytvořena třída InstanceContextExtension, která implementuje rozhraní IExtension a definuje požadovaný stav pro uložení ID kontextu. Tato třída také poskytuje stav pro uchování používaného Správce úložiště. Jakmile je nový stav uložený, neměl by být možné ho upravovat. Proto je stav poskytován a uložen do instance v době, kdy je vytvořen, a je přístupný pouze pomocí vlastností jen pro čtení.

```csharp
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

Třída InstanceContextInitializer implementuje rozhraní IInstanceContextInitializer a přidá rozšíření kontextu instance do kolekce rozšíření konstruované konstrukce InstanceContext.

```csharp
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

Jak je popsáno výše, ID kontextu je načteno `Properties` z kolekce `Message` třídy a předáno do konstruktoru třídy rozšíření. Ukazuje, jak lze informace mezi vrstvami konzistentně vyměňovat.

Dalším důležitým krokem je přepsání procesu vytváření instancí služby. WCF umožňuje implementovat vlastní chování vytváření instancí a zapojit je do modulu runtime pomocí rozhraní IInstanceProvider. Nová `InstanceProvider` třída je implementována k provedení této úlohy. V konstruktoru je přijat typ služby očekávaný od zprostředkovatele instance. Později se použije k vytvoření nových instancí. V části `GetInstance` implementace je vytvořena instance Správce úložiště, kde se hledá trvalá instance. Pokud se vrátí `null` , vytvoří se nová instance typu služby, která se vrátí volajícímu.

```csharp
public object GetInstance(InstanceContext instanceContext, Message message)
{
    object instance = null;

    DurableInstanceContextExtension extension =
    instanceContext.Extensions.Find<DurableInstanceContextExtension>();

    string contextId = extension.ContextId;
    IStorageManager storageManager = extension.StorageManager;

    instance = storageManager.GetInstance(contextId, serviceType);

    instance ??= Activator.CreateInstance(serviceType);
    return instance;
}
```

Dalším důležitým krokem je instalace `InstanceContextExtension` `InstanceContextInitializer` tříd a `InstanceProvider` do modulu runtime modelu služby. Vlastní atribut lze použít k označení tříd implementace služby pro instalaci chování. Obsahuje implementaci pro tento atribut a `IServiceBehavior` implementuje rozhraní pro rozšiřování celého modulu runtime služby. `DurableInstanceContextAttribute`

Tato třída má vlastnost, která přijímá typ Správce úložiště, který se má použít. Tímto způsobem implementace umožňuje uživatelům zadat vlastní `IStorageManager` implementaci jako parametr tohoto atributu.

`ApplyDispatchBehavior` V `ServiceBehavior` implementaci seověřujeaktuálníatribut.`InstanceContextMode` Pokud je tato vlastnost nastavená na singleton, není možné povolit trvalé vytváření instancí a `InvalidOperationException` k oznamování hostitele je vyvolána výjimka.

```csharp
ServiceBehaviorAttribute serviceBehavior =
    serviceDescription.Behaviors.Find<ServiceBehaviorAttribute>();

if (serviceBehavior != null &&
     serviceBehavior.InstanceContextMode == InstanceContextMode.Single)
{
    throw new InvalidOperationException(
       ResourceHelper.GetString("ExSingletonInstancingNotSupported"));
}
```

Po této instanci se vytvoří a nainstalují instance Správce úložiště, inicializátor kontextu instance a zprostředkovatele instancí v rámci `DispatchRuntime` vytvoření pro každý koncový bod.

```csharp
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

V dosavadním přehledu vytvořila Tato ukázka kanál, který povolil vlastní přenosový protokol pro výměnu vlastního ID kontextu a také přepisuje výchozí chování vytváření instancí, aby načetl instance z trvalého úložiště.

Levou z možností je uložit instanci služby do trvalého úložiště. Jak bylo popsáno dříve, již existuje požadovaná funkce pro uložení stavu v `IStorageManager` implementaci. Teď je potřeba ji integrovat s modulem runtime WCF. Je vyžadován jiný atribut, který platí pro metody ve třídě implementace služby. Tento atribut by měl být použit pro metody, které mění stav instance služby.

`SaveStateAttribute` Třída implementuje tuto funkci. Implementuje `IOperationBehavior` také třídu pro úpravu modulu runtime WCF pro každou operaci. Když je metoda označena pomocí tohoto atributu, modul runtime WCF vyvolá `ApplyBehavior` metodu, zatímco je vytvořena vhodná. `DispatchOperation` V této implementaci metody je jeden řádek kódu:

```csharp
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);
```

Tato instrukce vytvoří instanci `OperationInvoker` typu a přiřadí ji `Invoker` k vlastnosti objektu `DispatchOperation` , který je konstruován. Třída je obálkou pro výchozí operaci původce vytvořenou `DispatchOperation`pro. `OperationInvoker` Tato třída implementuje `IOperationInvoker` rozhraní. V implementaci `Invoke` metody je vlastní volání metody delegováno na původce vnitřní operace. Před vrácením výsledků však správce úložiště v `InstanceContext` nástroji slouží k uložení instance služby.

```csharp
object result = innerOperationInvoker.Invoke(instance,
    inputs, out outputs);

// Save the instance using the storage manager saved in the
// current InstanceContext.
InstanceContextExtension extension =
    OperationContext.Current.InstanceContext.Extensions.Find<InstanceContextExtension>();

extension.StorageManager.SaveInstance(extension.ContextId, instance);
return result;
```

## <a name="using-the-extension"></a>Použití rozšíření

Vrstva kanálu i rozšíření vrstvy modelu služby jsou hotové a dají se teď použít v aplikacích WCF. Služby musí přidat kanál do zásobníku kanálů pomocí vlastní vazby a pak označit třídy implementace služby příslušnými atributy.

```csharp
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

Klientské aplikace musí přidat DurableInstanceContextChannel do zásobníku kanálů pomocí vlastní vazby. Chcete-li konfigurovat kanál deklarativně v konfiguračním souboru, musí být oddíl elementu vazby přidán do kolekce rozšíření prvků vazby.

```xml
<system.serviceModel>
 <extensions>
   <bindingElementExtensions>
     <add name="durableInstanceContext"
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>
   </bindingElementExtensions>
 </extensions>
```

Prvek vazby lze nyní použít s vlastní vazbou stejným způsobem jako jiné standardní prvky vazby:

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

Tato ukázka ukázala, jak vytvořit vlastní kanál protokolu a jak přizpůsobit chování služby, abyste ho povolili.

Rozšíření lze dále zlepšit tím, že uživatelům umožníte zadat `IStorageManager` implementaci pomocí konfiguračního oddílu. Díky tomu je možné změnit záložní úložiště, aniž by bylo nutné znovu kompilovat kód služby.

Kromě toho můžete zkusit implementovat třídu (například `StateBag`), která zapouzdřuje stav instance. Tato třída zodpovídá za zachování stavu vždy, když se změní. Tímto způsobem se můžete vyhnout použití `SaveState` atributu a přesnější provedení trvalé práce (například můžete zachovat stav, pokud je změněn stav místo uložení pokaždé, když je metoda `SaveState` s atributem voláno).

Při spuštění ukázky se zobrazí následující výstup. Klient přidá do nákupního košíku dvě položky a pak ze služby získá seznam položek v rámci svého nákupního košíku. V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.

```console
Enter the name of the product: apples
Enter the name of the product: bananas

Shopping cart currently contains the following items.
apples
bananas
Press ENTER to shut down client
```

> [!NOTE]
> Opakované sestavení služby přepíše soubor databáze. Chcete-li sledovat stav zachované napříč několika spuštěními vzorku, nezapomeňte, že není nutné znovu sestavovat ukázku mezi spuštěními.

#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

> [!NOTE]
> Pro spuštění této ukázky musíte mít spuštěný SQL Server 2005 nebo SQL Express 2005. Pokud používáte SQL Server 2005, musíte upravit konfiguraci připojovacího řetězce služby. Při spuštění křížového počítače se SQL Server vyžaduje jenom na serverovém počítači.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`
