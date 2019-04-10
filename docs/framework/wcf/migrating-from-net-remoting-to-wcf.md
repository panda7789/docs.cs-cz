---
title: Migrace z .NET Remoting do WCF
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: c6bc16e97a87461be7b2c4877777329a0005a497
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296196"
---
# <a name="migrating-from-net-remoting-to-wcf"></a>Migrace z .NET Remoting do WCF
Tento článek popisuje, jak migrovat aplikace, která používá vzdálené komunikace .NET na použití služby Windows Communication Foundation (WCF). Porovná podobné koncepty mezi tyto produkty a pak popisuje, jak provádět několik běžných scénářů vzdálené komunikace v WCF.  
  
 Vzdálené komunikace .NET je starší verze produktu, který je podporován pouze z důvodu zpětné kompatibility. Není zabezpečení napříč prostředími ve smíšeném vztahu důvěryhodnosti, protože ho nejde Udržovat úrovně důvěryhodnosti samostatných mezi klientem a serverem. Například byste nikdy neměli zveřejňovat koncový bod vzdálené komunikace .NET na Internetu nebo nedůvěryhodné klienty. Doporučujeme, abyste existující vzdálenou komunikaci aplikace migrovat na novější a bezpečnější technologií. Pokud návrh aplikace používá pouze protokol HTTP a je RESTful, doporučujeme rozhraní ASP.NET Web API. Další informace najdete v tématu rozhraní ASP.NET Web API. Pokud aplikace je založená na protokolu SOAP nebo vyžaduje jiným protokolem než Http protokoly, například TCP, doporučujeme vám WCF.  

## <a name="comparing-net-remoting-to-wcf"></a>Porovnání služeb vzdálené komunikace .NET na WCF  
 Tato část se porovná se základními stavebními bloky vzdálené komunikace .NET s jejich ekvivalenty WCF. Použijeme tyto stavební bloky později vytvořit některé obvyklé scénáře, klient server ve službě WCF. Následující diagram obsahuje souhrn hlavní podobnosti a rozdíly mezi vzdálené komunikace .NET a WCF.  
  
||Vzdálené komunikace pomocí rozhraní .NET|WCF|  
|-|-------------------|---------|  
|Typ serveru|Podtřídy třídy MarshalByRefObject|Označit pomocí atributu [ServiceContract]|  
|Operace služby|Veřejné metody pro typ serveru|Označit pomocí atributu [OperationContract]|  
|Serializace|ISerializable nebo [Serializable]|DataContractSerializer nebo XmlSerializer|  
|Objekty předané|Podle hodnoty nebo podle odkazu|Podle hodnoty pouze|  
|Chyby a výjimky|Jakoukoli serializovatelný výjimku|FaultContract\<TDetail>|  
|Objekty proxy serveru klienta|Silného typu transparentních proxy se automaticky vytvořen z kolekci MarshalByRefObjects|Silného typu proxy servery jsou generovány, vyžádaná použití třídy ChannelFactory\<TChannel >|  
|Požadované platformy|Klient i server musí používat Microsoft OS a .NET|Různé platformy|  
|Formát zprávy|Soukromé|Oborové standardy (SOAP, WS-*, atd.)|  
  
### <a name="server-implementation-comparison"></a>Porovnání implementace serveru  
  
#### <a name="creating-a-server-in-net-remoting"></a>Vytvoření serveru ve vzdálené komunikace .NET  
 Vzdálené komunikace .NET serveru typy musí odvodit z třídy MarshalByRefObject a definovat metody, které klient volat, jako je následující:  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Veřejné metody tohoto typu serveru budou dostupné klientům veřejný kontrakt.  Není bez jakéhokoli oddělení veřejného rozhraní serveru a jeho implementaci – jeden typ zpracovává obojí.  
  
 Po definování typu serveru to můžete provést k dispozici pro klienty, jako v následujícím příkladu:  
  
```csharp
TcpChannel channel = new TcpChannel(8080);  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingConfiguration.RegisterWellKnownServiceType(  
    typeof(RemotingServer),   
    "RemotingServer",   
    WellKnownObjectMode.Singleton);  
Console.WriteLine("RemotingServer is running.  Press ENTER to terminate...");  
Console.ReadLine();  
```  
  
 Existuje mnoho způsobů, jak zpřístupnit typ vzdálené komunikace jako server, včetně použití konfiguračních souborů. Toto je pouze jeden z příkladů.  
  
#### <a name="creating-a-server-in-wcf"></a>Vytvoření serveru ve službě WCF  
 Ekvivalentní krok ve službě WCF zahrnuje vytvoření dva typy – public "servisní smlouva" a konkrétní implementaci. První je deklarován jako rozhraní označené [ServiceContract]. Metody dostupné pro klienty jsou označené [OperationContract]:  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 Implementace serveru je definován v samostatných konkrétní třída, stejně jako v následujícím příkladu:  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Po definování těchto typů WCF serveru můžete provést k dispozici pro klienty, jako v následujícím příkladu:  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
Uri baseAddress = new Uri("net.tcp://localhost:8000/wcfserver");  
  
using (ServiceHost serviceHost = new ServiceHost(typeof(WCFServer), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(IWCFServer), binding, baseAddress);  
    serviceHost.Open();  
  
    Console.WriteLine($"The WCF server is ready at {baseAddress}.");
    Console.WriteLine("Press <ENTER> to terminate service...");  
    Console.WriteLine();  
    Console.ReadLine();  
}  
```  
  
> [!NOTE]
>  TCP se používá v obou příkladech Novoroční co. Naleznete v následujících názorných postupech scénář dále v tomto tématu příklady použití protokolu HTTP.  
  
 Existuje mnoho způsobů, jak nakonfigurovat a hostování služeb WCF. Toto je pouze jeden z příkladů, známé jako "v místním prostředí". Další informace naleznete v následujících tématech:  
  
-   [Postupy: Definování kontraktu služby](how-to-define-a-wcf-service-contract.md)  
  
-   [Konfigurace služeb pomocí konfiguračních souborů](configuring-services-using-configuration-files.md)  
  
-   [Služby hostování](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a>Porovnání implementace klienta  
  
#### <a name="creating-a-client-in-net-remoting"></a>Vytvoření klienta ve vzdálené komunikace .NET  
 Jakmile je objekt serveru vzdálené komunikace .NET byla k dispozici, může být upotřebena klienty, stejně jako v následujícím příkladu:  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),   
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 Vrácená z Activator.GetObject() RemotingServer instance se označuje jako "transparentní proxy server." Implementuje veřejné rozhraní API pro typ RemotingServer na straně klienta, ale všechny metody volání objektu server běží na jiný proces nebo počítače.  
  
#### <a name="creating-a-client-in-wcf"></a>Vytvoření klienta ve službě WCF  
 Ekvivalentní krok ve službě WCF spočívá v použití objektu pro vytváření kanálů explicitně vytvořit proxy serveru. Podobně jako vzdálené komunikace objekt proxy serveru slouží k vyvolání operací na serveru, stejně jako v následujícím příkladu:  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
String url = "net.tcp://localhost:8000/wcfserver";  
EndpointAddress address = new EndpointAddress(url);  
ChannelFactory<IWCFServer> channelFactory =   
    new ChannelFactory<IWCFServer>(binding, address);  
IWCFServer server = channelFactory.CreateChannel();  
  
Customer customer = server.GetCustomer(42);  
Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 Tento příklad ukazuje programování na úrovni kanálu, protože je nejvíce podobně jako v příkladu vzdálené komunikace. K dispozici je také **přidat odkaz na službu** přístup v sadě Visual Studio, který generuje kód pro zjednodušení programování klienta. Další informace naleznete v následujících tématech:  
  
-   [Programování na úrovni kanálu klienta](./extending/client-channel-level-programming.md)  
  
-   [Postupy: Přidání, aktualizace nebo odebrání odkazu na službu](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a>Použití serializace  
 Vzdálené komunikace .NET a WCF používat k odesílání objektů mezi klientem a serverem serializace, ale liší se v těchto důležitých směrech –:  
  
1. Používají různé serializátory a konvence lze označit, jaký k serializaci.  
  
2. Vzdálené komunikace .NET podporuje "podle odkazu" serializace, která umožňuje přístup metody nebo vlastnosti na jednu vrstvu k provádění kódu na jiné úrovni, což je hranice zabezpečení. Tato funkce zpřístupňuje ohrožení zabezpečení a je jedním z hlavních důvodů, proč koncové body vzdálené komunikace by měly být vystaveny nikdy k nedůvěryhodné klienty.  
  
3. Vzdálená komunikace používá serializace je odhlásit (explicitně vyloučit jaké není určená k serializaci) a WCF serializace je vyjádřit výslovný souhlas (explicitně označit členy k serializaci).  
  
#### <a name="serialization-in-net-remoting"></a>Serializace v .NET Remoting  
 Vzdálené komunikace .NET podporuje dva způsoby, jak k serializaci a deserializaci objektů mezi klientem a serverem:  
  
-   *Podle hodnoty* – hodnoty objektu serializují hranicemi důvěryhodnosti úroveň a je vytvořena nová instance tohoto objektu na jiné úrovni. Všechna volání do metody nebo vlastnosti této nové instance pouze místně spouštějí a nemají vliv na původní objekt nebo úroveň.  
  
-   *Pomocí odkazu* – speciální "odkaz na objekt" serializován hranicemi důvěryhodnosti úroveň. Při jedné vrstvy interakci s metodami nebo vlastnostmi tohoto objektu, komunikuje zpět na původní objekt na původní úroveň. Objekty podle odkazu můžete tok v obou směrech – serveru ke klientovi nebo klienta na server.  
  
 Typy podle hodnot ve vzdálené komunikace onačené atributem [Serializable] nebo implementujte rozhraní ISerializable, stejně jako v následujícím příkladu:  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Typy podle odkazu odvozen od třídy MarshalByRefObject, stejně jako v následujícím příkladu:  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Je velmi důležité si uvědomit důsledky objekty podle odkazu na vzdálené komunikace. Pokud buď úroveň (klienta nebo serveru) odešle pomocí referenční objekt na úrovni, všechna volání metody spuštění zpět na úrovni vlastnící objekt. Klienta volání metod na objekt odkazem vrácená serverem bude třeba spustit kód na serveru. Na serveru, volání metod na objekt podle odkazu, který klient poskytl podobně, spustí kód zpět na straně klienta. Z tohoto důvodu se doporučuje použití vzdálené komunikace .NET pouze v rámci plně důvěryhodného prostředí. Vystavení veřejný koncový bod vzdálené komunikace .NET na nedůvěryhodní klienti způsobí, že vzdálený server snadno napadnutelný.  
  
#### <a name="serialization-in-wcf"></a>Serializace ve službě WCF  
 WCF podporuje pouze podle hodnoty serializace. Nejběžnější způsob, jak definovat typ vyměňovat mezi klientem a serverem je stejně jako v následujícím příkladu:  
  
```csharp
[DataContract]  
public class WCFCustomer  
{  
    [DataMember]  
    public string FirstName { get; set; }  
  
    [DataMember]  
    public string LastName { get; set; }  
  
    [DataMember]  
    public int CustomerId { get; set; }  
}  
```  
  
 Atribut [kontraktu dat DataContract] identifikuje tento typ jako jednu, která může serializovat a deserializovat mezi klientem a serverem. Atribut [DataMember] identifikuje jednotlivé vlastnosti nebo pole k serializaci.  
  
 Když WCF odešle objekt napříč úrovněmi, serializuje pouze hodnoty a vytvoří novou instanci objektu na jiné úrovni. Všechny interakce s hodnotami objektu dojít pouze místně – nekomunikují s úrovní, které objekty podle odkazu způsob, jak vzdálené komunikace .NET. Další informace najdete v tématu [serializace a deserializace](./feature-details/serialization-and-deserialization.md).  
  
### <a name="exception-handling-capabilities"></a>Možnosti zpracování výjimek  
  
#### <a name="exceptions-in-net-remoting"></a>Výjimky ve vzdálené komunikace .NET  
 Výjimky vyvolané v serveru vzdálené komunikace se serializovat, může odeslat klientovi a vyvolána místně na straně klienta, stejně jako jakoukoli jinou výjimku. Dílčí classing typ výjimky a označením [Serializable] je možné vytvořit vlastní výjimky.   Většina výjimek framework jsou již označen tímto způsobem umožňuje většina vyvolání serverem serializovat a znovu vyvolána na straně klienta. I když tento návrh je vhodné při vývoji, neúmyslně být odhalena klientovi informace na straně serveru. Toto je jeden z mnoha důvodů, které vzdálené komunikace by měla sloužit pouze v plně důvěryhodném prostředí.  
  
#### <a name="exceptions-and-faults-in-wcf"></a>Výjimky a chyby ve službě WCF  
 WCF nepovoluje typy libovolného výjimek, který se má vrátit ze serveru klientovi vzhledem k tomu by mohlo vést k neúmyslnému zpřístupnění informací. Pokud operace služby dojde k neočekávané výjimce, dojde k obecné výjimce FaultException, která je vyvolána na straně klienta. Tato výjimka neobsahuje žádné informace, proč nebo kde k problému došlo, a u některých aplikací to stačí. Aplikace, které potřebují komunikovat bohatší informace o chybě klienta to definováním kontrakt chyby.  
  
 K tomuto účelu nejprve vytvořte typ [kontraktu dat DataContract] k přenosu informací o selhání.  
  
```csharp
[DataContract]  
public class CustomerServiceFault  
{  
    [DataMember]  
    public string ErrorMessage { get; set; }  
  
    [DataMember]  
    public int CustomerId {get;set;}  
}  
```  
  
 Určete kontrakt chyby pro každou operaci služby.  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 Server sestav vyvoláním FaultException chybové stavy.  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {   
        CustomerId = customerId,   
        ErrorMessage = "Illegal customer Id"   
    });  
```  
  
 A pokaždé, když klient odešle požadavek na server, můžete zachytit chyby jako normální výjimky.  
  
```csharp
try  
{  
    Customer customer = server.GetCustomer(-1);  
}  
catch (FaultException<CustomerServiceFault> fault)  
{  
    Console.WriteLine($"Fault received: {fault.Detail.ErrorMessage}");
}  
```  
  
 Další informace o selhání kontrakty, naleznete v tématu <xref:System.ServiceModel.FaultException>.  
  
### <a name="security-considerations"></a>Důležité informace o zabezpečení  
  
#### <a name="security-in-net-remoting"></a>Zabezpečení vzdálené komunikace .NET  
 Některé kanálů řízení vzdálené komunikace .NET podporují funkce zabezpečení, jako je například ověřování a šifrování ve vrstvě kanálu (IPC a TCP). Kanál protokolu HTTP spoléhá v Internetové informační služby (IIS) pro ověřování a šifrování. Bez ohledu na tato podpora by měl vezměte v úvahu vzdálené komunikace .NET nezabezpečené komunikační protokol a použít pouze v rámci plně důvěryhodného prostředí. Nikdy vystavit veřejný koncový bod vzdálené komunikace na Internetu nebo nedůvěryhodné klienty.  
  
#### <a name="security-in-wcf"></a>Zabezpečení ve službě WCF  
 WCF byla navržena s na bezpečnost, v části řešení typy v .NET Remoting zjištěná ohrožení zabezpečení. WCF nabízí zabezpečení na úrovni přenosu i zprávu a nabízí celou řadu možností pro ověřování, autorizace, šifrování a tak dále. Další informace naleznete v následujících tématech:  
  
-   [Zabezpečení](./feature-details/security.md)  
  
-   [Doprovodné materiály zabezpečení WCF](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a>Migrace na WCF  
  
### <a name="why-migrate-from-remoting-to-wcf"></a>Proč migrovat Remoting do WCF?  
  
-   **Vzdálené komunikace .NET je starší verze produktu.** Jak je popsáno v [vzdálené komunikace .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), se považuje za starší verzi produktu a nedoporučuje se používat pro vývoj nových projektů. WCF a ASP.NET Web API se doporučuje pro nová a existující aplikace.  
  
-   **WCF využívá multiplatformní standardy.** WCF byla navržena s vzájemná funkční spolupráce napříč platformami v úvahu a podporuje mnoho oborových standardů (SOAP, WS-Security, WS-Trust, atd.). Služby WCF můžete spolupráci s klienty běžící na jiných operačních systémech než Windows. Vzdálená komunikace je navržená především pro prostředí, kde server i klient aplikace běží, pomocí rozhraní .NET framework v operačním systému Windows.  
  
-   **WCF má integrované zabezpečení.** WCF byla navržena s ohledem na bezpečnost a nabízí celou řadu možností pro ověřování, zabezpečení na úrovni přenosu, zabezpečení na úrovni zpráv atd. Vzdálené komunikace byl navržen k tomu, aby pro aplikace pro spolupráci, ale nebyl navržen, aby bylo zabezpečené v nedůvěryhodné prostředí. WCF byla navržena pro práci v obou důvěryhodné a nedůvěryhodné prostředích.  
  
### <a name="migration-recommendations"></a>Doporučení pro migraci  
 Tady jsou doporučené kroky migrace z .NET Remoting do WCF:  
  
-   **Vytvoření kontraktu služby.** Definování typů rozhraní služby a označit pomocí atributu [ServiceContract]. Označte všechny metody, klienti budou moct volat [OperationContract].  
  
-   **Vytvoření kontraktu dat.** Definování typů dat, které se vyměňují mezi serverem a klientem a označit pomocí atributu [kontraktu dat DataContract]. Označte všechna pole a vlastnosti, které klienta se bude moct používat s [DataMember].  
  
-   **Vytvoření kontraktu selhání (nepovinné).** Vytvoření typů, které se vyměňují mezi serverem a klientem, pokud nedojde k chybám. Označte tyto typy s [kontraktu dat DataContract] a [DataMember], aby se daly serializovatelný. Pro všechny operace služby, které jste označili [OperationContract] také označte je pomocí [FaultContract] pro označení chyb, které můžou vrátit.  
  
-   **Konfigurace a hostitelem služby.** Po vytvoření kontraktu služby, dalším krokem je ke konfiguraci vazby pro vystavení služby na koncový bod. Další informace najdete v tématu [koncové body: Adresy, vazby a kontrakty](./feature-details/endpoints-addresses-bindings-and-contracts.md).  
  
 Po použití vzdálené komunikace se migroval na WCF, je stále potřeba odebrat závislosti na vzdálené komunikace .NET. Tím se zajistí, že z aplikace odeberou se všechny chyby zabezpečení vzdálené komunikace. Tyto kroky zahrnují následující:  
  
-   **Přestat používat MarshalByRefObject.** Typ třídy MarshalByRefObject existuje pouze pro vzdálenou komunikaci a není používán WCF. Všechny typy aplikací, které dílčí třídy MarshalByRefObject by měla odebrat nebo změnit.  
  
-   **Ukončení použití [Serializable] a rozhraní ISerializable.** Atribut [Serializable] a rozhraní ISerializable byly původně navržen k serializaci typů v rámci důvěryhodného prostředí a jejich používání vzdálené komunikace. Serializace WCF spoléhá na typy, které jsou označené [kontraktu dat DataContract] a [DataMember]. Datové typy používané aplikací by měl být upraven použití [kontraktu dat DataContract] a nepoužívat ISerializable nebo [Serializable].  
  
### <a name="migration-scenarios"></a>Scénáře migrace  
 Nyní Pojďme zjistit, jak provést následující běžné scénáře vzdálené komunikace v WCF:  
  
1. Server vrátí klientovi objektu podle hodnoty  
  
2. Server vrátí klientovi pomocí – odkaz na objekt  
  
3. Klient odešle na server objektu podle hodnoty  
  
> [!NOTE]
>  Odesílání pomocí – odkaz na objekt z klienta na server není povolena ve službě WCF.  
  
 Při čtení prostřednictvím těchto scénářů, se předpokládá, že naše základní rozhraní pro .NET Remoting vypadat jako v následujícím příkladu. Implementace .NET Remoting důležité zde není vzhledem k tomu, že chceme, aby si ukážeme, jak pouze pomocí WCF implementovat ekvivalentní funkce.  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    // Demonstrates server returning object by-value  
    public Customer GetCustomer(int customerId) {…}  
  
    // Demonstrates server returning object by-reference  
    public CustomerReference GetCustomerReference(int customerId) {…}  
  
    // Demonstrates client passing object to server by-value  
    public bool UpdateCustomer(Customer customer) {…}  
}  
```  
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a>Scénář 1: Služba vrátí objekt podle hodnoty  
 Tento scénář předvádí server objektu podle hodnoty vrácením klientovi. WCF vždy vrátí objekty ze serveru podle hodnoty, takže takto jednoduše popisují, jak vytvářet běžné služby WCF.  
  
1. Začněte tím, že definování veřejného rozhraní pro službu WCF a označte ji pomocí atributu [ServiceContract]. K identifikaci metody na straně serveru, který bude volat naše klientské používáme [OperationContract].  
  
   ```csharp
   [ServiceContract]  
   public interface ICustomerService  
   {  
       [OperationContract]  
       Customer GetCustomer(int customerId);  
  
       [OperationContract]  
       bool UpdateCustomer(Customer customer);  
   }  
   ```  
  
2. Dalším krokem je vytvoření kontraktu dat pro tuto službu. To provedeme vytvořením tříd (nikoli rozhraní) označená pomocí atributu [kontraktu dat DataContract]. Jednotlivé vlastnosti nebo pole, která chceme, aby viditelné pro klienta a serveru jsou označené [DataMember]. Pokud se mají povolit odvozené typy, musíme použít atribut [Třída KnownType] jejich identifikaci. Pouze typy WCF umožní serializován nebo deserializován pro tuto službu jsou v rozhraní služby a tyto "známé typy". Pokus o výměně jakýkoli jiný typ není v tomto seznamu budou odmítnuty.  
  
   ```csharp
   [DataContract]  
   [KnownType(typeof(PremiumCustomer))]  
   public class Customer  
   {  
       [DataMember]  
       public string FirstName { get; set; }  
  
       [DataMember]  
       public string LastName { get; set; }  
  
       [DataMember]  
       public int CustomerId { get; set; }  
   }  
  
   [DataContract]  
   public class PremiumCustomer : Customer   
   {  
       [DataMember]  
       public int AccountId { get; set; }  
   }  
   ```  
  
3. Dále poskytujeme implementace rozhraní služby.  
  
   ```csharp  
   public class CustomerService : ICustomerService  
   {  
       public Customer GetCustomer(int customerId)  
       {  
           // read from database  
       }  
  
       public bool UpdateCustomer(Customer customer)  
       {  
           // write to database  
       }  
   }  
   ```  
  
4. Ke spuštění služby WCF, musíme deklarovat koncový bod, který zpřístupňuje rozhraní služby na konkrétní adrese URL použití konkrétní vazeb WCF. To se obvykle provádí přidáním následující části souboru web.config a server project.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
5. Služby WCF může být spuštěn s následujícím kódem:  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     Při spuštění tohoto hostitele ServiceHost pomocí souboru web.config zřizuje správné kontrakt, vazbu a koncový bod. Další informace o konfiguračních souborech najdete v tématu [konfigurace služeb pomocí konfiguračních souborů](./configuring-services-using-configuration-files.md). Tento styl spouštění na serveru se označuje jako s vlastním hostováním. Další informace o další možnosti hostování služby WCF, naleznete v tématu [hostování služeb](./hosting-services.md).  
  
6. Klientský projekt app.config musí deklarovat odpovídající informace o vazbě pro koncový bod služby. Nejjednodušší způsob, jak to provést v sadě Visual Studio je určený **přidat odkaz na službu**, která bude automaticky aktualizovat soubor app.config. Můžete také tyto stejné změny je možné přidat ručně.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     Další informace o používání **přidat odkaz na službu**, naleznete v tématu [jak: Přidání, aktualizace nebo odebrání odkazu na službu](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).  
  
7. Nyní jsme volat službu WCF z klienta. Můžeme to udělat tak vytvoření objektu pro vytváření kanálů pro tuto službu požadujícího kanál a přímo volat metodu, kterou chceme, aby na tomto kanálu. Můžeme to udělat, protože kanál implementuje rozhraní služby a zpracuje požadavek nebo odpověď logiku pro nás. Návratová hodnota z volání této metody je deserializovat kopie odpověď serveru.  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 Objektů vrácených službou WCF ze serveru do klienta jsou vždy podle hodnoty. Jsou objekty deserializovat kopie dat odeslaných serverem. Klient může volat metody na tyto místní kopie bez jakékoli nebezpečí vyvolání kódu serveru pomocí zpětných volání.  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a>Scénář 2: Server vrací objekt odkazem.  
 Tento scénář předvádí serveru, který poskytuje objekt pro klienta podle odkazu. Ve vzdálené komunikace .NET, to je automaticky zpracována pro libovolného typu odvozeného od třídy MarshalByRefObject, což je serializován podle odkazu. Příkladem tohoto scénáře je povolení více klientům mají nezávislé objekty s relacemi na straně serveru. Jak už jsme zmínili, objektů vrácených službou WCF neustále podle hodnoty, takže není žádný přímý ekvivalent objektu podle odkazu, ale je možné dosáhnout něco podobného pomocí sémantiky odkazem <xref:System.ServiceModel.EndpointAddress10> objektu. Toto je objekt serializovatelný podle hodnoty, který je možné k získání objektu s relacemi odkazem na serveru klientem. To umožňuje scénáře s více klienty s nezávislé objekty s relacemi na straně serveru.  
  
1. Nejdřív potřebujeme definování kontraktu služby WCF, která odpovídá na samotný objekt s relacemi.  
  
   ```csharp
   [ServiceContract(SessionMode = SessionMode.Allowed)]  
       public interface ISessionBoundObject  
       {  
           [OperationContract]  
           string GetCurrentValue();  
  
           [OperationContract]  
           void SetCurrentValue(string value);  
       }  
   ```  
  
    > [!TIP]
    >  Všimněte si, že objekt s relacemi je označená pomocí [ServiceContract], což normální rozhraní služby WCF. Nastavení režim SessionMode vlastnost určuje, že bude služba s relacemi. Relace ve službě WCF, je způsob, jak korelace více posílané mezi dva koncové body. To znamená, že Jakmile klient získá připojení pro tuto službu, relace navázat mezi klientem a serverem. Klient použije jeden jedinečný instance objektu na straně serveru pro všechny jeho interakce v rámci této jedné relace.  
  
2. V dalším kroku potřebujeme pro poskytování implementací rozhraní této služby. Označující s [ServiceBehavior] a nastavením režim InstanceContextMode, můžeme říct WCF, které že chceme pro každou relaci pomocí jedinečných instance tohoto typu.  
  
   ```csharp
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
       public class MySessionBoundObject : ISessionBoundObject  
       {  
           private string _value;  
  
           public string GetCurrentValue()  
           {  
               return _value;  
           }  
  
           public void SetCurrentValue(string val)  
           {  
               _value = val;  
           }  
  
       }  
   ```  
  
3. Nyní potřebujeme způsob, jak získat instanci tohoto objektu s relacemi. Uděláme to tak, že vytvoříte jiného rozhraní služby WCF, která vrací objekt EndpointAddress10. Toto je serializovatelného tvaru koncového bodu, který může klient použít k vytvoření objektu s relacemi.  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     A jsme implementaci této služby WCF:  
  
   ```csharp
   public class SessionBoundFactory : ISessionBoundFactory  
       {  
           public static ChannelFactory<ISessionBoundObject> _factory =   
               new ChannelFactory<ISessionBoundObject>("sessionbound");  
 
           public SessionBoundFactory()  
           {  
           }  
  
           public EndpointAddress10 GetInstanceAddress()  
           {  
               IClientChannel channel = (IClientChannel)_factory.CreateChannel();  
               return EndpointAddress10.FromEndpointAddress(channel.RemoteAddress);  
           }  
       }  
   ```  
  
     Tato implementace udržuje typu singleton objektu pro vytváření kanálů vytváření relací objektů. Při volání GetInstanceAddress() vytvoří kanál a vytvoří EndpointAddress10 objekt, který efektivně odkazuje na vzdálenou adresu spojený s tímto kanálem. EndpointAddress10 je jednoduše datový typ, který může být vrácen do klienta podle hodnota.  
  
4. Potřebujeme upravit konfigurační soubor serveru tímto způsobem následující dvě věci, jak je znázorněno v následujícím příkladu:  
  
    1.  Deklarace \<klienta > část popisující koncový bod pro objekt s relacemi. To je nezbytné, protože server také funguje jako klient v této situaci.  
  
    2.  Deklarujte koncové body pro objekt factory a který neobsahuje relace. To je potřeba povolit klienta ke komunikaci s koncovými body služby a získat EndpointAddress10 vytvořte kanál s relacemi.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
         <client>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
        </client>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
          <service name="Server.MySessionBoundObject">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundObject"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundObject" />  
          </service>  
          <service name="Server.SessionBoundFactory">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundFactory"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundFactory" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     A pak můžeme začít tyto služby:  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5. Nakonfigurujeme deklarováním tyto stejné koncové body v souboru app.config jeho projektu klienta.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
          <endpoint name="factory"  
                    address="net.tcp://localhost:8081/SessionBoundFactory"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundFactory"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
6. Pokud chcete vytvořit a použít tento objekt s relacemi, musí klient proveďte následující kroky:  
  
    1.  Vytvořte kanál ke službě ISessionBoundFactory.  
  
    2.  Tento kanál používaná k volání této služby k získání EndpointAddress10.  
  
    3.  Použijte EndpointAddress10 k vytvoření kanálu pro získání objektu s relacemi.  
  
    4.  Pracovat s relacemi objekt prokázat, že zůstane stejné instance napříč více volání.  
  
   ```csharp
   ChannelFactory<ISessionBoundFactory> channelFactory =   
       new ChannelFactory<ISessionBoundFactory>("factory");  
   ISessionBoundFactory sessionFactory = channelFactory.CreateChannel();  
  
   EndpointAddress10 address1 = sessionFactory.GetInstanceAddress();  
   EndpointAddress10 address2 = sessionFactory.GetInstanceAddress();  
  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory1 =   
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),   
                                               address1.ToEndpointAddress());  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory2 =   
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),   
                                               address2.ToEndpointAddress());  
  
   ISessionBoundObject sessionInstance1 = sessionObjectFactory1.CreateChannel();  
   ISessionBoundObject sessionInstance2 = sessionObjectFactory2.CreateChannel();  
  
   sessionInstance1.SetCurrentValue("Hello");  
   sessionInstance2.SetCurrentValue("World");  
  
   if (sessionInstance1.GetCurrentValue() == "Hello" &&  
       sessionInstance2.GetCurrentValue() == "World")  
   {  
       Console.WriteLine("sessionful server object works as expected");  
   }  
   ```  
  
 WCF vždy vrátí objekty podle hodnoty, ale je možné pro podporu ekvivalent pomocí odkazové sémantiky prostřednictvím EndpointAddress10. To umožňuje klientům žádosti s relacemi instance služby WCF, po jejímž uplynutí ho s ním mohli pracovat stejně jako jakoukoli jinou službu WCF.  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a>Scénář 3: Klient odešle serveru Instance podle hodnoty  
 Tento scénář předvádí klientů v odesílání instance objektu jiného než primitivního typu serveru podle hodnoty. Protože WCF odesílá pouze objekty podle hodnoty, tento scénář předvádí normálního využití WCF.  
  
1. Používaly stejnou službu WCF z scénář 1.  
  
2. Klienta můžete použijte k vytvoření nového objektu podle hodnoty (zákazníka), vytvořit kanál ke komunikaci se službou ICustomerService a posílat objektu.  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   PremiumCustomer customer = new PremiumCustomer {   
   FirstName = "Bob",   
   LastName = "Jones",   
   CustomerId = 43,   
   AccountId = 99};  
   bool success = service.UpdateCustomer(customer);  
   Console.WriteLine($"  Server returned {success}.");
   ```  
  
     Objekt zákazníka se serializovat a odeslat na server, kde je deserializovat do novou kopii tohoto objektu.  
  
    > [!NOTE]
    >  Tento kód také ukazuje odesílání odvozeného typu (PremiumCustomer). Rozhraní služby očekává, že objekt zákazníků, ale zákazníka pomocí atributu [Třída KnownType] označil že premiumcustomer také byla povolena. WCF se nezdaří jakýkoliv pokus o serializaci nebo deserializaci jakýkoli jiný typ prostřednictvím tohoto rozhraní služby.  
  
 Normální WCF výměny dat jsou podle hodnoty. Zaručí se tak, že volání metod na jednom z těchto datových objektů provádí pouze místně – nebude volat kód na jiné úrovni. I když je možné dosáhnout něco jako vrácených objektů podle odkazu *z* server, není možné pro klienta k předání objektu podle odkazu *k* serveru. Tento scénář vyžaduje konverzace vpřed a zpět mezi klientem a serverem lze dosáhnout pomocí duplexní služby WCF. Další informace najdete v tématu [duplexní služby](./feature-details/duplex-services.md).  
  
## <a name="summary"></a>Souhrn  
 Vzdálené komunikace .NET je určena pro použití pouze v rámci plně důvěryhodného prostředí rozhraní komunikace. Je starší verze produktu a pouze kvůli zpětné kompatibilitě podporované. Není vhodné používat k vytváření nových aplikací. WCF a naopak, byla navržena s ohledem na bezpečnost a se doporučuje pro nová a existující aplikace. Společnost Microsoft doporučuje tento existující aplikací vzdálené komunikace migrovat místo toho použít WCF a ASP.NET Web API.
