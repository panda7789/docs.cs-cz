---
title: Migrace z .NET Remoting do WCF
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: 8dcc019017195fd55231fbea3493d4c53d500cb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183967"
---
# <a name="migrating-from-net-remoting-to-wcf"></a>Migrace z .NET Remoting do WCF
Tento článek popisuje, jak migrovat aplikaci, která používá vzdálené komunikace .NET k použití Windows Communication Foundation (WCF). Porovnává podobné koncepty mezi těmito produkty a pak popisuje, jak provést několik běžných scénářů vzdálené komunikace v WCF.  
  
 Vzdálené komunikace rozhraní .NET je starší produkt, který je podporován pouze pro zpětnou kompatibilitu. Není zabezpečená v prostředích se smíšenými důvěryhodnostmi, protože nemůže udržovat samostatné úrovně důvěryhodnosti mezi klientem a serverem. Například byste nikdy neměli vystavit koncový bod vzdálené komunikace .NET do Internetu nebo nedůvěryhodným klientům. Doporučujeme, aby stávající aplikace vzdálené komunikace byly migrovány na novější a bezpečnější technologie. Pokud návrh aplikace používá pouze protokol HTTP a je restful, doporučujeme ASP.NET webové rozhraní API. Další informace naleznete v tématu ASP.NET web API. Pokud je aplikace založena na SOAP nebo vyžaduje protokoly bez http, jako je například TCP, doporučujeme WCF.  

## <a name="comparing-net-remoting-to-wcf"></a>Porovnání vzdálené komunikace rozhraní .NET s wcf  
 Tato část porovnává základní stavební bloky .NET Vzdálené komunikace s jejich wcf ekvivalenty. Tyto stavební bloky použijeme později k vytvoření některých běžných scénářů klient-server v WCF. Následující graf shrnuje hlavní podobnosti a rozdíly mezi .NET Vzdálené komunikace a WCF.  
  
||Vzdálené komunikace pomocí rozhraní .NET|WCF|  
|-|-------------------|---------|  
|Typ serveru|Třída MarshalByRefObject|Označit atributem [ServiceContract]|  
|Servisní operace|Veřejné metody na typu serveru|Označit atributem [OperationContract]|  
|Serializace|ISerializable nebo [Serializovatelné]|Serializátor datakontraktu nebo xmlserializátor|  
|Předané objekty|Podle hodnoty nebo odkaz|Pouze podle hodnoty|  
|Chyby/výjimky|Jakákoli serializovatelná výjimka|ChybaContract\<TDetail>|  
|Objekty proxy klienta|Silně zadané průhledné proxy servery jsou vytvořeny automaticky z MarshalByRefObjects|Servery proxy silného typu jsou generovány na\<vyžádání pomocí ChannelFactory TChannel>|  
|Požadovaná platforma|Klient i server musí používat operační systém Microsoft OS a rozhraní .NET.|Různé platformy|  
|Formát zprávy|Private|Průmyslové standardy (SOAP, WS-*atd.)|  
  
### <a name="server-implementation-comparison"></a>Porovnání implementace serveru  
  
#### <a name="creating-a-server-in-net-remoting"></a>Vytvoření serveru ve vzdálené remotingu rozhraní .NET  
 Typy serveru vzdálené komunikace sítě .NET musí být odvozeny z MarshalByRefObject a definovat metody, které může klient volat, například následující:  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Veřejné metody tohoto typu serveru se stanou veřejnou smlouvou dostupnou klientům.  Neexistuje žádné oddělení mezi veřejným rozhraním serveru a jeho implementací – jeden typ zpracovává oba.  
  
 Jakmile je definován typ serveru, může být k dispozici klientům, jako v následujícím příkladu:  
  
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
  
 Existuje mnoho způsobů, jak zpřístupnit typ vzdálené komunikace jako server, včetně použití konfiguračních souborů. To je jen jeden příklad.  
  
#### <a name="creating-a-server-in-wcf"></a>Vytvoření serveru v wcf  
 Ekvivalentní krok v WCF zahrnuje vytvoření dvou typů – veřejné "smlouvy o poskytování služeb" a konkrétní implementace. První je deklarována jako rozhraní označené [ServiceContract]. Metody, které jsou klientům k dispozici, jsou označeny [OperationContract]:  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 Implementace serveru je definována v samostatné konkrétní třídy, jako v následujícím příkladu:  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Jakmile jsou tyto typy definovány, wcf server může být k dispozici klientům, jako v následujícím příkladu:  
  
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
> TCP se používá v obou příkladech, aby byly co nejpodobnější. Naleznete scénář návody dále v tomto tématu příklady pomocí protokolu HTTP.  
  
 Existuje mnoho způsobů konfigurace a hostování služeb WCF. Toto je jen jeden příklad, známý jako "self-hosted". Další informace najdete v následujících tématech:  
  
- [Postupy: Definování kontraktu služby](how-to-define-a-wcf-service-contract.md)  
  
- [Konfigurace služeb pomocí konfiguračních souborů](configuring-services-using-configuration-files.md)  
  
- [Služby hostování](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a>Porovnání implementace klienta  
  
#### <a name="creating-a-client-in-net-remoting"></a>Vytvoření klienta ve vzdálené remotingu rozhraní .NET  
 Jakmile je objekt serveru vzdálené komunikace .NET zpřístupněn, mohou jej spotřebovávat klienti, například v následujícím příkladu:  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 Instance RemotingServer vrácená z Activator.GetObject() se označuje jako "transparentní proxy server". Implementuje veřejné rozhraní API pro typ RemotingServer na straně klienta, ale všechny metody volají objekt serveru spuštěný v jiném procesu nebo počítači.  
  
#### <a name="creating-a-client-in-wcf"></a>Vytvoření klienta v WCF  
 Ekvivalentní krok v WCF zahrnuje použití kanálu factory k vytvoření proxy explicitně. Stejně jako vzdálené komunikace, proxy objekt lze vyvolat operace na serveru, jako v následujícím příkladu:  
  
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
  
 Tento příklad ukazuje programování na úrovni kanálu, protože je nejvíce podobný příkladu vzdálené komunikace. K dispozici je také přístup **Přidat odkaz na službu** v sadě Visual Studio, který generuje kód pro zjednodušení programování klienta. Další informace najdete v následujících tématech:  
  
- [Programování na úrovni kanálu klienta](./extending/client-channel-level-programming.md)  
  
- [Postup: Přidání, aktualizace nebo odebrání odkazu na službu](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a>Použití serializace  
 Vzdálené komunikace rozhraní .NET i WCF používají serializaci k odesílání objektů mezi klientem a serverem, ale liší se těmito důležitými způsoby:  
  
1. Používají různé serializátory a konvence k označení, co serializovat.  
  
2. Vzdálené volání podporuje serializaci "odkazem", která umožňuje přístup metody nebo vlastnosti na jedné vrstvě ke spuštění kódu na druhé vrstvě, která je přes hranice zabezpečení. Tato funkce zveřejňuje chyby zabezpečení a je jedním z hlavních důvodů, proč vzdálené komunikace koncové body by nikdy být vystaveny nedůvěryhodným klientům.  
  
3. Serializace používá vzdálené volání je opt-out (explicitně vyloučit, co není serializovat) a WCF serializace je opt-in (explicitně označit členy serializovat).  
  
#### <a name="serialization-in-net-remoting"></a>Serializace ve vzdálené remotingu .NET  
 Vzdálené komunikace rozhraní .NET podporují dva způsoby serializace a deserializace objektů mezi klientem a serverem:  
  
- *Podle hodnoty* – hodnoty objektu jsou serializovány přes hranice vrstvy a nová instance tohoto objektu je vytvořena na druhé vrstvě. Všechna volání metod nebo vlastností této nové instance spustit pouze místně a nemají vliv na původní objekt nebo vrstvu.  
  
- *Odkaz* – speciální "odkaz na objekt" je serializován přes hranice vrstvy. Když jedna vrstva interaguje s metodami nebo vlastnostmi tohoto objektu, komunikuje zpět k původnímu objektu na původní úrovni. Odkaz na objekty mohou tok v obou směrech – server ke klientovi nebo klientka na server.  
  
 Typy podle hodnot ve vzdálené remotingu jsou označeny atributem [Serializable] nebo implementují ISerializable, jako v následujícím příkladu:  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Typy odkazů odvozené z Třídy MarshalByRefObject, stejně jako v následujícím příkladu:  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Je nesmírně důležité pochopit důsledky remoting je by-referenční objekty. Pokud buď vrstva (klient nebo server) odešle objekt podle odkazu na druhou vrstvu, všechna volání metody spustit zpět na vrstvě vlastnící objekt. Například metody volání klienta na objekt u odkazu vrácené serverem spustí kód na serveru. Podobně server volající metody na odkaz na objekt poskytnutý klientem spustí kód zpět na straně klienta. Z tohoto důvodu se doporučuje použití vzdálené komunikace .NET pouze v plně důvěryhodných prostředích. Vystavení veřejného koncového bodu vzdálené komunikace .NET nedůvěryhodným klientům způsobí, že server vzdálené komunikace bude zranitelný vůči útoku.  
  
#### <a name="serialization-in-wcf"></a>Serializace v WCF  
 WCF podporuje pouze serializace podle hodnoty. Nejběžnější způsob, jak definovat typ pro výměnu mezi klientem a serverem je jako v následujícím příkladu:  
  
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
  
 Atribut [DataContract] identifikuje tento typ jako typ, který lze serializovat a rekonstruovat mezi klientem a serverem. Atribut [DataMember] identifikuje jednotlivé vlastnosti nebo pole serializovat.  
  
 Když WCF odešle objekt napříč vrstvami, serializuje pouze hodnoty a vytvoří novou instanci objektu na druhé vrstvě. Všechny interakce s hodnotami objektu dojít pouze místně – nekomunikují s druhou vrstvou způsobem .NET Vzdálené komunikace podle referenční objekty. Další informace naleznete [v tématu Serializace a deserializace](./feature-details/serialization-and-deserialization.md).  
  
### <a name="exception-handling-capabilities"></a>Možnosti zpracování výjimek  
  
#### <a name="exceptions-in-net-remoting"></a>Výjimky ve vzdálené remotingu .NET  
 Výjimky vyvolané serverem vzdálené komunikace jsou serializovány, odeslány klientovi a vyvolány místně na straně klienta jako jakákoli jiná výjimka. Vlastní výjimky lze vytvořit pomocí sub-classing exception typu a označení s [Serializovat].   Většina výjimky rozhraní jsou již označeny tímto způsobem, což umožňuje většinu být vyvolána serverem, serializované a znovu vyvolána na straně klienta. Ačkoli tento návrh je vhodný během vývoje, informace na straně serveru mohou být neúmyslně zpřístupněny klientovi. To je jeden z mnoha důvodů, proč by vzdálené komunikace měla být používána pouze v plně důvěryhodných prostředích.  
  
#### <a name="exceptions-and-faults-in-wcf"></a>Výjimky a chyby v WCF  
 WCF neumožňuje libovolné typy výjimek, které mají být vráceny ze serveru klientovi, protože by mohlo vést k neúmyslnému zpřístupnění informací. Pokud operace služby vyvolá neočekávanou výjimku, způsobí, že na straně klienta bude vyvolána výjimka pro obecné účely. Tato výjimka neobsahuje žádné informace, proč nebo kde došlo k problému a pro některé aplikace je to dostačující. Aplikace, které je třeba komunikovat bohatší informace o chybě klientovi to definováním chybové smlouvy.  
  
 Chcete-li to provést, nejprve vytvořte typ [DataContract] pro přenos informací o chybě.  
  
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
  
 Zadejte kontrakt poruchy, který se má použít pro každou operaci služby.  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 Server hlásí chybové stavy vyvoláním výjimky FaultException.  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {
        CustomerId = customerId,
        ErrorMessage = "Illegal customer Id"
    });  
```  
  
 A vždy, když klient provede požadavek na server, může zachytit chyby jako normální výjimky.  
  
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
  
 Další informace o kontraktech <xref:System.ServiceModel.FaultException>poruch naleznete v tématu .  
  
### <a name="security-considerations"></a>Aspekty zabezpečení  
  
#### <a name="security-in-net-remoting"></a>Zabezpečení ve vzdálené remotingu .NET  
 Některé kanály vzdálené komunikace .NET podporují funkce zabezpečení, jako je ověřování a šifrování ve vrstvě kanálu (IPC a TCP). Kanál HTTP závisí na internetové informační službě (IIS) pro ověřování i šifrování. Navzdory této podpoře byste měli zvážit přenos dat .NET vzdálené komunikace jako nezabezpečeného komunikačního protokolu a používat jej pouze v plně důvěryhodných prostředích. Nikdy nezveřejňujte veřejný koncový bod vzdálené komunikace pro internet nebo nedůvěryhodné klienty.  
  
#### <a name="security-in-wcf"></a>Zabezpečení ve službě WCF  
 WCF byl navržen s ohledem na zabezpečení, částečně k řešení druhů chyb zabezpečení nalezených v .NET Remoting. WCF nabízí zabezpečení na úrovni přenosu i zprávy a nabízí mnoho možností pro ověřování, autorizace, šifrování a tak dále. Další informace najdete v následujících tématech:  
  
- [Zabezpečení](./feature-details/security.md)  
  
- [Pokyny wcf zabezpečení](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a>Migrace na WCF  
  
### <a name="why-migrate-from-remoting-to-wcf"></a>Proč migrovat z vzdálené komunikace na WCF?  
  
- **Vzdálené komunikace .NET je starší produkt.** Jak je popsáno v [.NET Vzdálené komunikace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), je považován za starší produkt a není doporučeno pro nový vývoj. WCF nebo ASP.NET webové rozhraní API se doporučuje pro nové i existující aplikace.  
  
- **WCF používá standardy pro různé platformy.** WCF byl navržen s ohledem na interoperabilitu napříč platformami a podporuje mnoho oborových standardů (SOAP, WS-Security, WS-Trust atd.). Služba WCF může spolupracovat s klienty spuštěnými v jiných operačních systémech než v systému Windows. Vzdálené volání do vzdálené komunikace bylo navrženo především pro prostředí, kde serverové i klientské aplikace běží pomocí rozhraní .NET Framework v operačním systému Windows.
  
- **WCF má integrované zabezpečení.** WCF byl navržen s ohledem na zabezpečení a nabízí mnoho možností pro ověřování, zabezpečení na úrovni přenosu, zabezpečení na úrovni zpráv atd. Vzdálené komunikace byla navržena tak, aby usnadnila vzájemné působení aplikací, ale nebyla navržena tak, aby byla zabezpečena v nedůvěryhodných prostředích. WCF byl navržen tak, aby fungoval v důvěryhodných i nedůvěryhodných prostředích.  
  
### <a name="migration-recommendations"></a>Doporučení pro migraci  
 Následující kroky jsou doporučené pro migraci z vzdálené komunikace rozhraní .NET do wcf:  
  
- **Vytvořte servisní smlouvu.** Definujte typy rozhraní služby a označte je atributem [ServiceContract]. Označte všechny metody, které budou moci klienti volat pomocí [OperationContract].  
  
- **Vytvořte kontrakt dat.** Definujte datové typy, které budou vyměňovány mezi serverem a klientem, a označte je atributem [DataContract]. Označte všechna pole a vlastnosti, které bude klient moci používat s uživatelem [DataMember].  
  
- **Vytvořte kontrakt poruchy (volitelné).** Vytvořte typy, které budou vyměňovány mezi serverem a klientem, pokud dojde k chybám. Označte tyto typy [DataContract] a [DataMember], aby byly serializovatelné. Pro všechny servisní operace, které jste označili [OperationContract], také označte je [FaultContract] k označení, které chyby mohou vrátit.  
  
- **Konfigurace a hostování služby.** Po vytvoření smlouvy o poskytování služeb je dalším krokem konfigurace vazby pro vystavení služby v koncovém bodě. Další informace naleznete [v tématu Koncové body: Adresy, vazby a smlouvy](./feature-details/endpoints-addresses-bindings-and-contracts.md).  
  
 Po migraci vzdálené aplikace do WCF, je stále důležité odebrat závislosti na .NET Vzdálené komunikace. Tím zajistíte, že všechny chyby zabezpečení vzdálené komunikace budou odebrány z aplikace. Mezi tyto kroky patří následující:  
  
- **Přestaňte používat MarshalByRefObject.** Typ MarshalByRefObject existuje pouze pro vzdálené komunikace a wcf nepoužívá. Všechny typy aplikací, které podtřídy MarshalByRefObject by měly být odebrány nebo změněny.  
  
- **Přestaňte používat [Serializable] a ISerializable.** Atribut [Serializable] a rozhraní ISerializable byly původně navrženy tak, aby serializovaly typy v důvěryhodných prostředích a jsou používány vzdálené komunikace. Serializace WCF závisí na typech označených [DataContract] a [DataMember]. Datové typy používané aplikací by měly být upraveny tak, aby používaly [DataContract] a nepoužívaly iSerializable nebo [Serializable].  
  
### <a name="migration-scenarios"></a>Scénáře migrace  
 Nyní se podívejme, jak dosáhnout následujících běžných scénářů vzdálené komunikace v WCF:  
  
1. Server vrátí klientovi hodnotu podle objektu.  
  
2. Server vrátí objekt odkaz na klienta  
  
3. Klient odešle na server hodnotu podle hodnoty objektu.  
  
> [!NOTE]
> Odeslání odkazu na objekt z klienta na server není v wcf povoleno.  
  
 Při čtení těchto scénářů předpokládejme, že naše základní rozhraní pro vzdálené čtení .NET vypadají jako v následujícím příkladu. Implementace vzdálené komunikace .NET není důležité, protože chceme ilustrovat pouze jak použít WCF implementovat ekvivalentní funkce.  
  
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
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a>Scénář 1: Služba vrátí objekt podle hodnoty.  
 Tento scénář ukazuje server vrací objekt klientovi podle hodnoty. WCF vždy vrací objekty ze serveru podle hodnoty, takže následující kroky jednoduše popisují, jak vytvořit normální službu WCF.  
  
1. Začněte definováním veřejného rozhraní pro službu WCF a označte ji atributem [ServiceContract]. Používáme [OperationContract] k identifikaci metod na straně serveru, které bude náš klient volat.  
  
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
  
2. Dalším krokem je vytvoření kontraktu dat pro tuto službu. Děláme to vytvořením třídy (ne rozhraní) označené atributem [DataContract]. Jednotlivé vlastnosti nebo pole, které chceme zobrazit jak pro klienta, tak pro server, jsou označeny [DataMember]. Pokud chceme, aby byly odvozené typy povoleny, musíme k jejich identifikaci použít atribut [KnownType]. Pouze typy WCF umožní serializovat nebo rekonstruovat pro tuto službu jsou ty v rozhraní služby a tyto "známé typy". Pokus o výměnu jiného typu, který není v tomto seznamu, bude odmítnut.  
  
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
  
3. Dále poskytujeme implementaci pro rozhraní služby.  
  
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
  
4. Chcete-li spustit službu WCF, musíme deklarovat koncový bod, který zveřejňuje toto rozhraní služby na konkrétní adresu URL pomocí konkrétní wcf vazby. To se obvykle provádí přidáním následujících částí do souboru web.config projektu serveru.  
  
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
  
5. Službu WCF lze spustit pomocí následujícího kódu:  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     Při spuštění tohoto ServiceHost, používá soubor web.config k vytvoření správné smlouvy, vazby a koncového bodu. Další informace o konfiguračních souborech naleznete [v tématu Konfigurace služeb pomocí konfiguračních souborů](./configuring-services-using-configuration-files.md). Tento styl spuštění serveru je známý jako self-hosting. Další informace o dalších možnostech hostování služeb WCF najdete v [tématu Hostingové služby](./hosting-services.md).  
  
6. Soubor app.config klientského projektu musí deklarovat odpovídající informace o vazbě pro koncový bod služby. Nejjednodušší způsob, jak to udělat v sadě Visual Studio, je použít **add service reference**, který automaticky aktualizuje soubor app.config. Alternativně tyto stejné změny lze přidat ručně.  
  
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
  
     Další informace o použití **funkce Přidat odkaz na službu**naleznete v [tématu How to: Add, Update, or Remove a Service Reference](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).  
  
7. Nyní můžeme volat službu WCF z klienta. Děláme to vytvořením továrny kanálu pro tuto službu, žádostí o kanál a přímým voláním metody, kterou chceme na tomto kanálu. Můžeme to udělat, protože kanál implementuje rozhraní služby a zpracovává základní logiku požadavku/odpovědi pro nás. Vrácená hodnota z tohoto volání metody je rekonstruovaná kopie odpovědi serveru.  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 Objekty vrácené WCF ze serveru do klienta jsou vždy podle hodnoty. Objekty jsou rekonstruovány kopie dat odeslaných serverem. Klient může volat metody na těchto místních kopiíbez nebezpečí vyvolání kódu serveru prostřednictvím zpětná volání.  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a>Scénář 2: Server vrátí odkaz na objekt.  
 Tento scénář ukazuje server poskytující objekt klientovi odkazem. Ve vzdálené remotingu rozhraní .NET je tato funkce zpracována automaticky pro libovolný typ odvozený z marshalByRefObject, který je serializován podle odkazu. Příkladem tohoto scénáře je povolení více klientů mít nezávislé sessionful objekty na straně serveru. Jak již bylo zmíněno, objekty vrácené službou WCF jsou vždy podle hodnoty, takže neexistuje žádný přímý ekvivalent objektu podle odkazu, <xref:System.ServiceModel.EndpointAddress10> ale je možné dosáhnout něco podobného sémantiku odkaz pomocí objektu. Jedná se o serializovatelný objekt podle hodnoty, který může klient použít k získání objektu relace odkazem na serveru. To umožňuje scénář mít více klientů s nezávislými sessionful objekty na straně serveru.  
  
1. Nejprve musíme definovat wcf servisní smlouvy, která odpovídá sessionful objektu sám.  
  
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
    > Všimněte si, že objekt relace je označen [ServiceContract], což je normální wcf rozhraní služby. Nastavení SessionMode vlastnost označuje, že bude relace služby. V WCF relace je způsob korelace více zpráv odeslaných mezi dvěma koncovými body. To znamená, že jakmile klient získá připojení k této službě, bude mezi klientem a serverem vytvořena relace. Klient použije jednu jedinečnou instanci objektu na straně serveru pro všechny jeho interakce v rámci této jedné relace.  
  
2. Dále musíme zajistit implementaci tohoto rozhraní služby. Tím, že jej opatříte [ServiceBehavior] a nastavíme InstanceContextMode, řekneme WCF, že chceme použít jedinečnou instanci tohoto typu pro každou relaci.  
  
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
  
3. Nyní potřebujeme způsob, jak získat instanci tohoto sessionful objektu. Děláme to vytvořením jiného rozhraní služby WCF, který vrací endpointaddress10 objektu. Toto je serializovatelná forma koncového bodu, který může klient použít k vytvoření objektu relačného.  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     A implementujeme tuto službu WCF:  
  
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
  
     Tato implementace udržuje totokanálovou továrnu pro vytváření objektů relací. Při getInstanceAddress() je volána, vytvoří kanál a vytvoří EndpointAddress10 objekt, který účinně odkazuje na vzdálenou adresu přidruženou k tomuto kanálu. EndpointAddress10 je jednoduše datový typ, který lze vrátit klientovi podle hodnoty.  
  
4. Potřebujeme upravit konfigurační soubor serveru provedením následujících dvou věcí, jak je znázorněno v následujícím příkladu:  
  
    1. Deklarovat klienta \<> části, která popisuje koncový bod pro sessionful objektu. To je nezbytné, protože server také funguje jako klient v této situaci.  
  
    2. Deklarovat koncové body pro objekt výroby a sessionful. To je nezbytné, aby klient komunikovat s koncovými body služby získat EndpointAddress10 a vytvořit sessionful kanálu.  
  
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
  
5. Klienta nakonfigurujeme deklarováním stejných koncových bodů v souboru app.config svého projektu.  
  
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
  
6. Chcete-li vytvořit a použít tento objekt relace, musí klient provést následující kroky:  
  
    1. Vytvořte kanál ke službě ISessionBoundFactory.  
  
    2. Pomocí tohoto kanálu vyvolat tuto službu získat EndpointAddress10.  
  
    3. Pomocí endpointaddress10 vytvořit kanál pro získání sessionful objektu.  
  
    4. Interakci s sessionful objektu prokázat, že zůstane stejná instance přes více volání.  
  
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
  
 WCF vždy vrátí objekty podle hodnoty, ale je možné podporovat ekvivalent sémantiku odkaz pomocí EndpointAddress10. To umožňuje klientovi požadovat sessionful WCF instance služby, po kterém může komunikovat s ním jako všechny ostatní služby WCF.  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a>Scénář 3: Klient odešle serveru instanci by-Value  
 Tento scénář ukazuje klienta odesílání neprimitivní objekt instance na server podle hodnoty. Vzhledem k tomu, že WCF odesílá pouze objekty podle hodnoty, tento scénář demonstruje normální wcf použití.  
  
1. Použijte stejnou službu WCF ze scénáře 1.  
  
2. Pomocí klienta vytvořte nový objekt podle hodnoty (Zákazník), vytvořte kanál pro komunikaci se službou ICustomerService a odešlete do něj objekt.  
  
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
  
     Objekt zákazníka bude serializován a odeslán na server, kde je deserializován do nové kopie tohoto objektu.  
  
    > [!NOTE]
    > Tento kód také ilustruje odeslání odvozeného typu (PremiumCustomer). Rozhraní služby očekává objekt Customer, ale atribut [KnownType] ve třídě Customer uvedl, že byl povolen také premiumcustomer. WCF se nezdaří jakýkoli pokus o serializovat nebo rekonstruovat jakýkoli jiný typ prostřednictvím tohoto rozhraní služby.  
  
 Normální WCF výměny dat jsou podle hodnoty. To zaručuje, že vyvolání metody na jednom z těchto datových objektů provede pouze místně – nebude vyvolat kód na druhé vrstvě. I když je možné dosáhnout něco jako odkaz na objekty vrácené *ze* serveru, není možné pro klienta předat objekt odkazu *na* server. Scénář, který vyžaduje konverzaci tam a zpět mezi klientem a serverem lze dosáhnout v WCF pomocí duplexní služby. Další informace naleznete v tématu [Duplex Services](./feature-details/duplex-services.md).  
  
## <a name="summary"></a>Souhrn  
 Vzdálené volání .NET je komunikační rámec určený k použití pouze v plně důvěryhodných prostředích. Jedná se o starší produkt a je podporován pouze pro zpětnou kompatibilitu. Neměl by být používán k vytváření nových aplikací. Naopak WCF byl navržen s ohledem na zabezpečení a je doporučeno pro nové i stávající aplikace. Společnost Microsoft doporučuje, aby existující vzdálené komunikace aplikace migrovat použít WCF nebo ASP.NET webové rozhraní API místo.
