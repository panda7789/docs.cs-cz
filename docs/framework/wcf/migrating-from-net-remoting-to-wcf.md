---
title: Migrace z .NET Remoting do WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b387e100ff881c5394b6a77716a733b3928eae9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="migrating-from-net-remoting-to-wcf"></a>Migrace z .NET Remoting do WCF
Tento článek popisuje, jak k migraci aplikace, která používá .NET Remoting používat Windows Communication Foundation (WCF). Porovnává podobné koncepty mezi tyto produkty a pak popisuje, jak provést několik běžných scénářů vzdálené komunikace v WCF.  
  
 .NET remoting je starší verze produktu, který je podporován pouze z důvodů zpětné kompatibility. Není zabezpečené přes důvěryhodnosti ve smíšeném prostředí, protože jej nelze udržovat úrovně samostatné vztah důvěryhodnosti mezi klientem a serverem. Například byste nikdy neměli zveřejňovat koncový bod .NET Remoting k Internetu nebo nedůvěryhodné klientům. Doporučujeme, abyste existující vzdálenou komunikaci aplikace migrovat do technologie novější a bezpečnější. Pokud aplikace návrhu používá jen protokol HTTP a je dosáhl standardu RESTful, doporučujeme rozhraní ASP.NET Web API. Další informace najdete v tématu rozhraní ASP.NET Web API. Pokud aplikace je založena na protokolu SOAP nebo vyžaduje jiných protokolů než Http například TCP, doporučujeme WCF.  

## <a name="comparing-net-remoting-to-wcf"></a>Porovnání .NET Remoting do WCF  
 Tato část porovná základní stavební bloky .NET Remoting s jejich ekvivalenty u WCF. Použijeme tyto stavební bloky později vytvořit některé běžné scénáře klient server ve WCF. Následující graf shrnuje hlavní podobnosti a rozdíly mezi .NET Remoting a WCF.  
  
||Vzdálené komunikace pomocí rozhraní .NET|WCF|  
|-|-------------------|---------|  
|Typ serveru|Podtřída MarshalByRefObject|Označit atributem [ServiceContract]|  
|Operace služby|Veřejné metody na typ serveru|Označit pomocí atributu [OperationContract]|  
|Serializace|ISerializable nebo [Serializable]|DataContractSerializer nebo třídy XmlSerializer|  
|Objekty předané|Hodnotou nebo odkazem|Podle hodnoty jenom|  
|Chyby nebo výjimky|Všechny serializovatelný výjimky|FaultContract\<TDetail >|  
|Objekty proxy serveru klienta|Silného typu transparentní proxy jsou automaticky vytvořen z MarshalByRefObjects|Silného typu proxy se generují pomocí ChannelFactory na vyžádání\<TChannel >|  
|Platforma požadované|Klient i server musí používat Microsoft OS a rozhraní .NET|Více platforem|  
|Formát zprávy|Soukromé|Oborové standardy (SOAP, WS-* atd.)|  
  
### <a name="server-implementation-comparison"></a>Porovnání implementace serveru  
  
#### <a name="creating-a-server-in-net-remoting"></a>Vytvoření serveru ve vzdálené komunikace .NET  
 Typy .NET remoting server musí odvozena od třídy MarshalByRefObject a definovat metody, které klient může volat, podobně jako tento:  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Veřejné metody tohoto typu serveru stanou veřejného kontraktu, která je k dispozici pro klienty.  Neexistuje žádné oddělení mezi veřejné rozhraní serveru a jeho implementace – jeden typ zpracuje obě.  
  
 Po definování typ serveru, se může být dostupné pro klienty, jako v následujícím příkladu:  
  
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
 Ekvivalentní krok ve WCF zahrnuje vytvoření dva typy – veřejných "kontrakt služby" a konkrétní implementaci. První je deklarován jako rozhraní označené jako [ServiceContract]. [OperationContract] jsou označené metody, které jsou dostupné klientům:  
  
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
  
 Po definování těchto typů WCF serveru může být dostupné pro klienty, jako v následujícím příkladu:  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
Uri baseAddress = new Uri("net.tcp://localhost:8000/wcfserver");  
  
using (ServiceHost serviceHost = new ServiceHost(typeof(WCFServer), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(IWCFServer), binding, baseAddress);  
    serviceHost.Open();  
  
    Console.WriteLine(String.Format("The WCF server is ready at {0}.",  
                                    baseAddress));  
    Console.WriteLine("Press <ENTER> to terminate service...");  
    Console.WriteLine();  
    Console.ReadLine();  
}  
```  
  
> [!NOTE]
>  TCP se používá v obou příkladech jejich udržování v co. Naleznete návodů scénář dále v tomto tématu příklady pomocí protokolu HTTP.  
  
 Existuje mnoho způsobů, jak nakonfigurovat a hostování služeb WCF. Toto je pouze jeden z příkladů, označuje jako "samoobslužně hostovaná". Další informace naleznete v následujících tématech:  
  
-   [Postupy: Definování kontraktu služby](how-to-define-a-wcf-service-contract.md)  
  
-   [Konfigurace služeb pomocí konfiguračních souborů](configuring-services-using-configuration-files.md)  
  
-   [Služby hostování](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a>Porovnání implementace klienta  
  
#### <a name="creating-a-client-in-net-remoting"></a>Vytvoření klienta v rozhraní .NET Remoting  
 Jakmile objekt .NET Remoting serveru dojde k dispozici, se mohou být spotřebovávána klientů, jako v následujícím příkladu:  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),   
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine(String.Format("Customer {0} {1} received.",   
                                 customer.FirstName, customer.LastName));  
```  
  
 Instance RemotingServer vrácená z Activator.GetObject() se označuje jako "transparentní proxy." Implementuje veřejné rozhraní API pro typ RemotingServer na straně klienta, ale všechny metody volat objekt serveru s jiným procesem nebo počítače.  
  
#### <a name="creating-a-client-in-wcf"></a>Vytvoření klienta ve WCF  
 Ekvivalentní krok ve WCF, která využívá kanálu explicitně vytvořit proxy server. Jako Vzdálená komunikace objekt proxy serveru slouží k vyvolání operace na serveru, jako v následujícím příkladu:  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
String url = "net.tcp://localhost:8000/wcfserver";  
EndpointAddress address = new EndpointAddress(url);  
ChannelFactory<IWCFServer> channelFactory =   
    new ChannelFactory<IWCFServer>(binding, address);  
IWCFServer server = channelFactory.CreateChannel();  
  
Customer customer = server.GetCustomer(42);  
Console.WriteLine(String.Format("  Customer {0} {1} received.",  
                    customer.FirstName, customer.LastName));  
```  
  
 Tento příklad ukazuje, programování na úrovni kanálu, protože je nejvíce podobně jako v příkladu vzdálenou komunikaci. Je také k dispozici **přidat odkaz na službu** přístup v sadě Visual Studio, který generuje kód pro zjednodušení programování klienta. Další informace naleznete v následujících tématech:  
  
-   [Programování klienta na úrovni kanálu](./extending/client-channel-level-programming.md)  
  
-   [Postupy: Přidání, aktualizace nebo odebrání odkazu na službu](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a>Serializace využití  
 .NET Remoting a WCF používat serializace k odesílání objektů mezi klientem a serverem, ale liší se tyto důležité způsoby:  
  
1.  Používají různé serializátorů a konvence lze označit, jaký k serializaci.  
  
2.  .NET remoting podporuje "odkazem" serializace, které umožňuje metody nebo vlastnosti přístup na jednu úroveň ke spouštění kódu na další úroveň, která je v rámci hranice zabezpečení. Tato funkce zpřístupňuje ohrožení zabezpečení a je jedním z hlavních důvodů, proč koncové body vzdálené komunikace by měly být vystaveny nikdy nedůvěryhodné klientům.  
  
3.  Serializace používá vzdálené komunikace je výslovný nesouhlas s (výslovně vyloučili jaké není určená k serializaci) a serializace WCF je výslovný souhlas (explicitně označit které členy k serializaci).  
  
#### <a name="serialization-in-net-remoting"></a>Serializace v .NET Remoting  
 .NET remoting podporuje dva způsoby, jak serializaci a deserializaci objektů mezi klientem a serverem:  
  
-   *Podle hodnoty* – hodnoty objektu se serializují napříč hranicemi vrstvy a vytvořit novou instanci tohoto objektu, na jiné vrstvě. Volání metody nebo vlastnosti této nové instance provést pouze místně a neovlivní původní objekt nebo vrstvě.  
  
-   *Odkazem* – speciální "odkaz na objekt" je serializováno napříč hranicemi vrstvy. Když jedné vrstvy pracuje s metody nebo vlastnosti daného objektu, komunikuje se zpět na původní objekt na původní vrstvě. Objekty podle odkazu můžete procházet v obou směrech – serveru ke klientovi nebo klienta k serveru.  
  
 Typy podle hodnot v vzdálené komunikace jsou označené atributem [Serializable] nebo implementovat ISerializable, jako v následujícím příkladu:  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Typy odkazem odvozena od třídy MarshalByRefObject, jako v následujícím příkladu:  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Je velmi důležité pochopit důsledky objekty odkazem na vzdálenou komunikaci. Pokud buď vrstvy (klienta nebo serveru) odešle objekt odkazem k jiné vrstvě, všechna volání metody spouštění zpět na úroveň, který vlastní objekt. Klienta voláním metody na objekt odkazem vrácená serverem bude třeba spustit kód na serveru. Podobně serveru, volání metod na objekt odkazem klient poskytl spustí kód zpět na straně klienta. Z tohoto důvodu se doporučuje použití .NET Remoting pouze ve plně důvěryhodná prostředích. Vystavení veřejný koncový bod .NET Remoting do nedůvěryhodní klienti budou vzdálenou komunikaci server bude zranitelný vůči útoku.  
  
#### <a name="serialization-in-wcf"></a>Serializace ve WCF  
 WCF podporuje pouze serializace-hodnota. Nejběžnější způsob, jak definovat typů Exchange mezi klientem a serverem je jako v následujícím příkladu:  
  
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
  
 Atribut [kontraktu] Určuje tento typ jako jednu, která může serializovat a deserializovat mezi klientem a serverem. Atribut [DataMember] identifikuje jednotlivé vlastnosti nebo pole určená k serializaci.  
  
 Pokud WCF odešle objekt mezi vrstvami, serializuje jenom hodnoty a vytvoří novou instanci objektu na jiné vrstvě. Všechny interakce s hodnotami objektu dojít pouze místně – tito klienti nekomunikují s další vrstvou, které objekty způsob .NET Remoting odkazem. Další informace naleznete v následujících tématech:  
  
-   [Serializace a deserializace](./feature-details/serialization-and-deserialization.md)  
  
-   [Serializace ve službě Windows Communication Foundation](http://msdn.microsoft.com/magazine/cc163569.aspx)  
  
### <a name="exception-handling-capabilities"></a>Možnosti zpracování výjimek  
  
#### <a name="exceptions-in-net-remoting"></a>Výjimky v .NET Remoting  
 Výjimky vyvolané vzdálenou komunikaci serveru jsou serializovat, může odeslat klientovi a vyvolána místně na straně klienta jako všechny ostatní výjimky. Dílčí classing typ výjimky a označení [Serializable] možné vytvářet vlastní výjimky.   Většina framework výjimky jsou již označené tímto způsobem, povolení většina vyvolání serverem serializovat a znovu vyvolány na straně klienta. I když tento návrh je vhodné při vývoji, můžete informace serverové nechtěně zveřejněna do klienta. Toto je jedním z mnoha důvodů, vzdálené komunikace by měla být používána pouze ve plně důvěryhodná prostředích.  
  
#### <a name="exceptions-and-faults-in-wcf"></a>Výjimek a chyb ve WCF  
 WCF nepovoluje typy libovolný výjimek má být vrácen ze serveru klientovi protože by mohlo vést k neúmyslnému zpřístupnění informací. Pokud je operace služby neočekávanou výjimku, způsobí obecné účely FaultException vyvolání na straně klienta. Tato výjimka neobsahuje žádné informace, proč nebo kde k problému došlo, a pro některé aplikace jde dostatečná. Aplikace, které je třeba komunikovat bohatší informace o chybě úkol klienta to tak, že definujete kontraktu selhání.  
  
 Uděláte to tak, nejdřív vytvořte typ [kontraktu] k přenosu informací o selhání.  
  
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
  
 Zadejte kontrakt odolnost pro každou operaci služby.  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 Server sestav po vyvolání výjimky FaultException chybové stavy.  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {   
        CustomerId = customerId,   
        ErrorMessage = "Illegal customer Id"   
    });  
```  
  
 A vždy, když klient odešle požadavek na server, můžete ho catch chyb jako normální výjimky.  
  
```csharp
try  
{  
    Customer customer = server.GetCustomer(-1);  
}  
catch (FaultException<CustomerServiceFault> fault)  
{  
    Console.WriteLine(String.Format("Fault received: {0}",  
    fault.Detail.ErrorMessage));  
}  
```  
  
 Další informace o selhání kontrakty najdete v tématu <xref:System.ServiceModel.FaultException>.  
  
### <a name="security-considerations"></a>Důležité informace o zabezpečení  
  
#### <a name="security-in-net-remoting"></a>Zabezpečení v rozhraní .NET Remoting  
 Některé .NET Remoting kanály podpory funkce zabezpečení, jako je například ověřování a šifrování ve vrstvě kanálu (IPC a TCP). Kanál protokolu HTTP spoléhá na Internetové informační služby (IIS) pro ověřování a šifrování. I přes tato podpora měli vzít v úvahu .NET Remoting protokol nezabezpečená komunikace a použít ho pouze ve plně důvěryhodná prostředích. Nikdy neměli zveřejňovat veřejný koncový bod Vzdálená komunikace na Internetu nebo nedůvěryhodné klientů.  
  
#### <a name="security-in-wcf"></a>Zabezpečení ve službě WCF  
 WCF byla navržena s důrazem na bezpečnost, v části vyřešit druhy ohrožení zabezpečení v rozhraní .NET Remoting nalezen. WCF nabízí zabezpečení na úrovni přenosu i zprávu a nabízí mnoho možností pro ověřování, autorizace, šifrování a tak dále. Další informace naleznete v následujících tématech:  
  
-   [Zabezpečení](./feature-details/security.md)  
  
-   [Doprovodné materiály zabezpečení WCF](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a>Migrace na službu WCF  
  
### <a name="why-migrate-from-remoting-to-wcf"></a>Proč migrace Remoting do WCF?  
  
-   **.NET remoting je starší verze produktu.** Jak je popsáno v [.NET Remoting](http://msdn.microsoft.com/library/vstudio/72x4h507\(v=vs.100\).aspx), se považuje za starší verze produktu a nedoporučuje se používat pro vývoj. WCF nebo rozhraní ASP.NET Web API se doporučují pro nových nebo stávajících aplikací.  
  
-   **WCF používá standardy napříč platformami.** WCF byl navržen s interoperabilitu napříč platformami v paměti a podporuje mnoho oborových standardů (SOAP, WS-zabezpečení, WS-Trust, atd.). Služby WCF můžete zajistit vzájemnou funkční spolupráci s klienty běžící na operačních systémech než Windows. Vzdálená komunikace byla určena především pro prostředí, kde spustit serverových a klientských aplikací pomocí rozhraní .NET framework v operačním systému Windows.  
  
-   **WCF je integrované zabezpečení.** WCF byla navržena s důrazem na bezpečnost a nabízí mnoho možností pro ověřování, zabezpečení na úrovni přenosu, úroveň zabezpečení zpráv atd. Vzdálená komunikace byla navržená tak, aby mohl snadno aplikace pro spolupráci, ale nebyl navržen, aby bylo zabezpečené v nedůvěryhodné prostředích. WCF byla navržená tak, aby fungovaly v prostředí důvěryhodné i nedůvěryhodné.  
  
### <a name="migration-recommendations"></a>Migrace doporučení  
 Následující části jsou doporučené kroky migrace z .NET Remoting do WCF:  
  
-   **Vytvoření kontraktu služby.** Definování typů rozhraní vaší služby a označit je pomocí atributu [ServiceContract]. Označte všechny metody, klienti nebudou mít dovoleno volání s [OperationContract].  
  
-   **Vytvoření kontraktu dat.** Definování typů dat, které se vyměňují mezi serverem a klientem a označit je pomocí atributu [kontraktu]. Označte všechny polí a vlastností, které se bude moct klient pomocí [DataMember].  
  
-   **Vytvoření kontraktu selhání (nepovinné).** Vytvoření typů, které se vyměňují mezi serverem a klientem, když dojde k chybám. Označte tyto typy s [kontraktu] a [DataMember] tak, aby byly serializable. Pro všechny operace služby, které jste označili [OperationContract] také označte je pomocí [FaultContract] k označení chyb, které se můžou vrátit.  
  
-   **Nakonfigurujte a hostitelem služby.** Po vytvoření kontraktu služby, dalším krokem je konfigurace vazbu ke zveřejnění službu na koncový bod. Další informace najdete v tématu [koncové body: adresy, vazby a kontrakty](./feature-details/endpoints-addresses-bindings-and-contracts.md).  
  
 Jakmile aplikaci Vzdálená komunikace byla migrována do WCF, je stále důležité odebrání závislostí na .NET Remoting. Tím se zajistí, že žádné ohrožení zabezpečení vzdálené komunikace se odeberou z aplikace. Tyto kroky zahrnují následující:  
  
-   **Přestat používat MarshalByRefObject.** Typ MarshalByRefObject existuje pouze pro vzdálenou komunikaci a není používán WCF. Všechny typy aplikací, které dílčí třídy MarshalByRefObject by měla být odebrán nebo změněn. Typ MarshalByRefObject existuje pouze pro vzdálenou komunikaci a není používán WCF. Všechny typy aplikací, které dílčí třídy MarshalByRefObject by měla být odebrán nebo změněn.  
  
-   **Ukončí použití [Serializable] a ISerializable.** Atribut [Serializable] a ISerializable rozhraní byly původně navrženy k serializaci typů v rámci důvěryhodné prostředí a jsou používány vzdálenou komunikaci. Serializace WCF spoléhá na typy, které je označené jako [kontraktu] a [DataMember]. Datové typy používané aplikace by měl být upraven, abyste mohli používat [kontraktu] a nepoužívat ISerializable nebo [Serializable]. Atribut [Serializable] a ISerializable rozhraní byly původně navrženy k serializaci typů v rámci důvěryhodné prostředí a jsou používány vzdálenou komunikaci. Serializace WCF spoléhá na typy, které je označené jako [kontraktu] a [DataMember]. Datové typy používané aplikace by měl být upraven, abyste mohli používat [kontraktu] a nepoužívat ISerializable nebo [Serializable].  
  
### <a name="migration-scenarios"></a>Scénáře migrace  
 Nyní Podíváme se, jak provést následující běžné scénáře vzdálené komunikace ve WCF:  
  
1.  Server vrátí klientovi pomocí hodnota objektu  
  
2.  Server vrátí odkaz na objekt podle – pro klienta  
  
3.  Klient odešle na server pomocí hodnota objektu  
  
> [!NOTE]
>  Odesílání odkaz na objekt podle-od klienta k serveru není povolen ve WCF.  
  
 Při čtení prostřednictvím těchto scénářů, předpokládá, že naše základní rozhraní pro .NET Remoting vypadat podobně jako v následujícím příkladu. Implementace .NET Remoting důležité zde není vzhledem k tomu, že chceme ilustrují pouze způsob implementace ekvivalentní funkce pomocí služby WCF.  
  
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
 Tento scénář předvádí, server vrátí objekt, do klienta podle hodnoty. WCF vždy vrátí objekty ze serveru podle hodnoty, takže následující kroky popisují jednoduše jak sestavit normální služby WCF.  
  
1.  Začněte definováním veřejné rozhraní pro službu WCF a označte ji s atributem [ServiceContract]. [OperationContract] používáme k identifikaci metody na straně serveru, který bude volat naše klienta.  
  
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
  
2.  Dalším krokem je vytvoření kontraktu dat pro tuto službu. Provedeme to vytvořením třídy (ne rozhraní) s atributem [kontraktu]. Jednotlivé vlastnosti nebo pole, která má být viditelná pro klientské a serverové jsou označené [DataMember]. Pokud odvozené typy smí chceme, jsme musí identifikovat pomocí atributu [Třída KnownType]. Pouze typy WCF umožní serializován nebo deserializován pro tuto službu, jsou rozhraní služby a tyto "známé typy". Probíhá pokus o exchange libovolného typu nejsou v tomto seznamu budou odmítnuty.  
  
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
  
3.  V dalším kroku poskytujeme implementaci pro rozhraní služby.  
  
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
  
4.  Pokud chcete spustit službu WCF, je potřeba deklarovat koncový bod, který zpřístupňuje rozhraní této služby na konkrétní adrese URL, pomocí konkrétní vazby WCF. To se obvykle provádí přidáním následující části souboru web.config serverový projekt.  
  
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
  
5.  Pak se spuštění služby WCF s následujícím kódem:  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     Při spuštění této ServiceHost pomocí souboru web.config zřizuje správné kontrakt, vazbu a koncového bodu. Další informace o konfiguračních souborech najdete v tématu [konfigurace služeb pomocí konfiguračních souborů](./configuring-services-using-configuration-files.md). Tento styl spouštění serveru se označuje jako vlastní hostování. Další informace o další možnosti pro hostování služby WCF najdete v tématu [hostování služeb](./hosting-services.md).  
  
6.  App.config projektu klienta je třeba deklarovat odpovídající informace o vazbě pro koncový bod služby. Nejjednodušší způsob, jak to udělat v sadě Visual Studio je použití **přidat odkaz na službu**, který se automaticky aktualizuje soubor app.config. Tyto změny budou stejně Alternativně lze přidat ručně.  
  
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
  
     Další informace o používání **přidat odkaz na službu**, najdete v části [postupy: Přidání, aktualizace nebo odebrání odkazu na službu](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).  
  
7.  Služby WCF jsme teď můžete volat z klienta. Jsme to udělat vytvoření postupu kanálu pro tuto službu požadující kanál a přímo volání metody, které má být v tomto kanálu. Jsme lze provést, protože kanál implementuje rozhraní služby a zpracuje požadavek nebo odpověď logiku pro nás. Vrácená hodnota z volání této metody se deserializovat kopii odpověď serveru.  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine(String.Format("  Customer {0} {1} received.",  
           customer.FirstName, customer.LastName));  
   ```  
  
 Objektů vrácený WCF ze serveru do klienta se vždycky hodnotou. Objekty jsou deserializovat kopie data odeslaná na server. Klienta můžete volat metody pro tyto místní kopie bez jakékoli nebezpečí vyvolání kódu serveru prostřednictvím zpětných volání.  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a>Scénář 2: Server vrátí objekt odkazem  
 Tento scénář předvádí serveru, který poskytuje objekt klientovi odkazem. V .NET Remoting, to je automaticky zpracována pro jakéhokoli typu odvozeného z MarshalByRefObject, což je serializovat odkazem. Příkladem tento scénář umožňuje více klientů mít nezávislé relacemi server na straně objektů. Jak už jsme zmínili, objektů vrácený služby WCF jsou vždy podle hodnoty, takže není ekvivalent objektu odkazem, ale je možné dosáhnout podobný pomocí sémantiky odkazem <xref:System.ServiceModel.EndpointAddress10> objektu. Toto je objekt serializovatelný podle hodnoty, které je možné klientem pro získání objektu relacemi odkazem na serveru. To umožňuje scénáře s více klientů s nezávislé objekty relací na straně serveru.  
  
1.  Nejprve musíme definování kontraktu služby WCF, která odpovídá relacemi odkaz sám na sebe.  
  
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
    >  Všimněte si, že objekt relacemi označeno [ServiceContract], což normální rozhraní služby WCF. Nastavení SessionMode vlastnost značí, že bude relacemi služby. Ve službě WCF relace je způsob korelace více zprávy odeslané mezi dva koncové body. To znamená, že Jakmile klient obdrží připojení k této službě, relace navázat mezi klientem a serverem. Klient použije jeden jedinečný výskyt serverový objekt pro všechny jeho interakce v rámci této jedné relace.  
  
2.  V dalším kroku potřebujeme k zajištění implementace tohoto rozhraní služby. Představující s [ServiceBehavior] a nastavením InstanceContextMode, jsme zjistit WCF, že nám chcete použít pro každou relaci jedinečné instance tohoto typu.  
  
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
  
3.  Nyní potřebujeme způsob, jak získat instanci tohoto objektu relacemi. Provedeme to tak, že vytvoříte jiné rozhraní služby WCF, která vrací objekt EndpointAddress10. Toto je serializovatelný formu koncový bod, který může klient použít k vytvoření relací objektu.  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     A implementaci této služby WCF:  
  
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
  
     Tato implementace udržuje singleton postup kanálu k vytváření relací objektů. Při volání GetInstanceAddress() vytvoří kanál a vytvoří objekt EndpointAddress10 efektivně odkazující na vzdálené adresy přidružené k tomuto kanálu. EndpointAddress10 je jednoduše datový typ, který může být vrácen do klienta pomocí hodnota.  
  
4.  Je potřeba upravit konfigurační soubor serveru pomocí tohoto postupu následující dva postupy, jak je znázorněno v následujícím příkladu:  
  
    1.  Deklarace \<klienta > oddíl, který popisuje koncový bod pro objekt relacemi. To je nezbytné, protože server taky funguje jako klient v této situaci.  
  
    2.  Koncové body pro objekt factory a sessionful deklarujte. To je potřeba povolit klientům komunikovat pomocí koncových bodů služby získat EndpointAddress10 a k vytvoření kanálu relací.  
  
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
  
     A potom můžeme začít tyto služby:  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5.  Nakonfigurujeme klienta deklarováním tyto stejné koncové body v souboru app.config jeho projektu.  
  
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
  
6.  Chcete-li vytvořit a použít tento objekt relacemi, musíte klienta udělat následující kroky:  
  
    1.  Vytvoření kanálu pro službu ISessionBoundFactory.  
  
    2.  Tento kanál používaná k volání této služby k získání EndpointAddress10.  
  
    3.  Pomocí EndpointAddress10 k vytvoření kanálu pro získání objektu relacemi.  
  
    4.  Komunikovat s relacemi objekt, který má ukazují, že zůstane na stejnou instanci napříč více volání.  
  
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
  
 Objekty WCF vždy vrátí hodnotu, ale je možné podporovat ekvivalent odkazem sémantiku prostřednictvím EndpointAddress10. To umožňuje klientovi požadavku relacemi instance služby WCF, po který může komunikovat s ním stejně jako ostatní služby WCF.  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a>Scénář 3: Klient odešle serveru Instance-hodnota  
 Tento scénář předvádí, klient pro odeslání na server instance objektu není primitivní hodnotou. Protože WCF odesílá pouze objekty podle hodnoty, tento scénář předvádí normálního využití WCF.  
  
1.  Použijte stejnou službu WCF z scénář 1.  
  
2.  Pomocí klienta můžete vytvořit nový objekt-hodnota (zákazníka), vytvořit kanál ke komunikaci se službou ICustomerService a poslat objektu.  
  
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
   Console.WriteLine(String.Format("  Server returned {0}.", success));  
   ```  
  
     Objekt zákazníka bude serializován a odesílá na server, kde je deserializovat do novou kopii tohoto objektu.  
  
    > [!NOTE]
    >  Tento kód také ukazuje odesílání odvozený typ (PremiumCustomer). Rozhraní služby očekává objekt zákazníků, ale atribut [Třída KnownType] k třídě zákazníka označil že premiumcustomer také povolený. WCF se nezdaří pokusy o serializaci nebo deserializaci žádným jiným typem prostřednictvím tohoto rozhraní služby.  
  
 Normální WCF výměny dat jsou hodnotou. To zaručuje, že volání metod v jednom z těchto objektů dat provádí pouze místně – ho nebude vyvolání kódu v jiné vrstvě. Když je možné dosáhnout něco podobného jako vrácených objektů odkazem *z* serveru, není možné pro klienta předat objekt odkazem *k* serveru. Ve službě WCF pomocí duplexní služby se dá dosáhnout scénáře, který vyžaduje konverzace přepínat mezi klientem a serverem. Další informace najdete v tématu [duplexní služby](./feature-details/duplex-services.md).  
  
## <a name="summary"></a>Souhrn  
 .NET remoting je určena pro použití pouze v rámci prostředí plně důvěryhodná komunikace rozhraní. Je starší verze produktu a podporované pouze z důvodů zpětné kompatibility. Není vhodné používat k vytvoření nové aplikace. Naopak WCF byl navržen s důrazem na bezpečnost a doporučuje se pro nových nebo stávajících aplikací. Společnost Microsoft doporučuje, že existující aplikací vzdálené komunikace migrovat místo toho použít WCF nebo webové rozhraní API ASP.NET.