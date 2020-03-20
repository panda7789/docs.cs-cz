---
title: Určování přenosu dat v kontraktech služby
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
ms.openlocfilehash: e68ca46f9d2c562491063ae66754c469dbe0898e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184431"
---
# <a name="specifying-data-transfer-in-service-contracts"></a>Určování přenosu dat v kontraktech služby
Windows Communication Foundation (WCF) si lze myslet jako infrastruktury zasílání zpráv. Operace služby mohou přijímat zprávy, zpracovávat je a odesílat jim zprávy. Zprávy jsou popsány pomocí smluv operace. Zvažte například následující smlouvu.  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    float GetAirfare(string fromCity, string toCity);  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
  
    <OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
End Interface  
```  
  
 Zde `GetAirfare` operace přijme zprávu s informacemi o `fromCity` a `toCity`a potom vrátí zprávu, která obsahuje číslo.  
  
 Toto téma vysvětluje různé způsoby, ve kterém může smlouva operace popisovat zprávy.  
  
## <a name="describing-messages-by-using-parameters"></a>Popis zpráv pomocí parametrů  
 Nejjednodušší způsob, jak popsat zprávu, je použít seznam parametrů a vrácenou hodnotu. V předchozím příkladu `fromCity` a `toCity` parametry řetězce byly použity k popisu zprávy požadavku a float vrácená hodnota byla použita k popisu zprávy odpovědi. Pokud samotná vrácená hodnota nestačí k popisu odpovědi, mohou být použity parametry out. Například následující operace `fromCity` má `toCity` a ve své zprávě požadavku a číslo spolu s měnou ve své odpovědi:  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 Kromě toho můžete použít referenční parametry, aby se parametr součástí požadavku a odpovědi. Parametry musí být typy, které mohou být serializovány (převedeny na XML). Ve výchozím nastavení WCF používá <xref:System.Runtime.Serialization.DataContractSerializer> komponentu s názvem třída k provedení tohoto převodu. Jsou podporovány nejprimivnější `int`typy (například `string`, `float`, a `DateTime`.). Uživatelem definované typy musí mít obvykle kontrakt dat. Další informace naleznete [v tématu Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
```csharp
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    float GetAirfare(Itinerary itinerary, DateTime date);  
  
    [DataContract]  
    public class Itinerary  
    {  
        [DataMember]  
        public string fromCity;  
        [DataMember]  
        public string toCity;  
   }  
}  
```  
  
```vb  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    GetAirfare(itinerary as Itinerary, date as DateTime) as Double  
  
    <DataContract()>  
    Class Itinerary  
  
        <DataMember()>  
        Public fromCity As String  
        <DataMember()>  
        Public toCity As String  
    End Class  
End Interface  
```  
  
 V některých `DataContractSerializer` případě není adekvátní serializovat typy. WCF podporuje alternativní serializace <xref:System.Xml.Serialization.XmlSerializer>motoru , který můžete také použít k serializaci parametrů. Umožňuje <xref:System.Xml.Serialization.XmlSerializer> použít větší kontrolu nad výsledným XML pomocí atributů, jako je například `XmlAttributeAttribute`. Chcete-li přepnout na použití <xref:System.Xml.Serialization.XmlSerializer> pro konkrétní operaci <xref:System.ServiceModel.XmlSerializerFormatAttribute> nebo pro celou službu, použijte atribut pro operaci nebo službu. Například:  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    [XmlSerializerFormat]  
    float GetAirfare(Itinerary itinerary, DateTime date);  
}  
public class Itinerary  
{  
    public string fromCity;  
    public string toCity;  
    [XmlAttribute]  
    public bool isFirstClass;  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    <XmlSerializerFormat>  
    GetAirfare(itinerary as Itinerary, date as DateTime) as Double  
  
End Interface  
  
Class Itinerary  
  
    Public fromCity As String  
    Public toCity As String  
    <XmlSerializerFormat()>  
    Public isFirstClass As Boolean  
End Class  
```  
  
 Další informace naleznete [v tématu Použití třídy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md). Nezapomeňte, že ruční přepnutí <xref:System.Xml.Serialization.XmlSerializer> na, jak je znázorněno zde, se nedoporučuje, pokud k tomu nemáte konkrétní důvody, jak je podrobně popsáno v tomto tématu.  
  
 Chcete-li izolovat názvy parametrů .NET od <xref:System.ServiceModel.MessageParameterAttribute> názvů smluv, `Name` můžete použít atribut a použít vlastnost k nastavení názvu smlouvy. Například následující smlouva operace je ekvivalentní první příklad v tomto tématu.  
  
```csharp  
[OperationContract]  
public float GetAirfare(  
    [MessageParameter(Name="fromCity")] string originCity,  
    [MessageParameter(Name="toCity")] string destinationCity);  
```  
  
```vb  
<OperationContract()>  
  Function GetAirfare(<MessageParameter(Name := "fromCity")> fromCity As String, <MessageParameter(Name := "toCity")> toCity As String) As Double  
```  
  
## <a name="describing-empty-messages"></a>Popis prázdných zpráv  
 Prázdnou zprávu požadavku lze popsat bez vstupních nebo referenčních parametrů. Například v c#:  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 Například v jazyce Visual Basic:  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 Prázdná odpověď zpráva může být `void` popsána s návratový typ a žádný výstup nebo referenční parametry. Například v:  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 To se liší od jednosměrné operace, například:  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 Operace `SetTemperatureStatus` vrátí prázdnou zprávu. Může vrátit chybu místo toho, pokud je problém zpracování vstupní zprávy. Operace `SetLightbulbStatus` vrátí nic. Neexistuje žádný způsob, jak komunikovat poruchový stav z této operace.  
  
## <a name="describing-messages-by-using-message-contracts"></a>Popis zpráv pomocí smluv se zprávami  
 Můžete použít jeden typ představující celou zprávu. I když je možné použít kontrakt dat pro tento účel, doporučený způsob, jak to provést, je použít zprávu smlouvy – tím se zabrání zbytečné úrovně zabalení ve výslednéxml. Smlouvy se zprávami navíc umožňují vykonávat větší kontrolu nad výsledné zprávy. Můžete například rozhodnout, které informace by měly být v textu zprávy a které by měly být v záhlaví zprávy. Následující příklad ukazuje použití smluv zpráv.  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    GetAirfareResponse GetAirfare(GetAirfareRequest request);  
}  
  
[MessageContract]  
public class GetAirfareRequest  
{  
    [MessageHeader] public DateTime date;  
    [MessageBodyMember] public Itinerary itinerary;  
}  
  
[MessageContract]  
public class GetAirfareResponse  
{  
    [MessageBodyMember] public float airfare;  
    [MessageBodyMember] public string currency;  
}  
  
[DataContract]  
public class Itinerary  
{  
    [DataMember] public string fromCity;  
    [DataMember] public string toCity;  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    Function GetAirfare(request As GetAirfareRequest) As GetAirfareResponse  
End Interface  
  
<MessageContract()>  
Public Class GetAirfareRequest  
    <MessageHeader()>
    Public Property date as DateTime  
    <MessageBodyMember()>  
    Public Property itinerary As Itinerary  
End Class  
  
<MessageContract()>  
Public Class GetAirfareResponse  
    <MessageBodyMember()>  
    Public Property airfare As Double  
    <MessageBodyMember()> Public Property currency As String  
End Class  
  
<DataContract()>  
Public Class Itinerary  
    <DataMember()> Public Property fromCity As String  
    <DataMember()> Public Property toCity As String  
End Class  
```  
  
 Další informace naleznete [v tématu Using Message Contracts](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
 V předchozím příkladu <xref:System.Runtime.Serialization.DataContractSerializer> je třída stále používána ve výchozím nastavení. Třídu <xref:System.Xml.Serialization.XmlSerializer> lze také použít se smlouvami zpráv. Chcete-li to <xref:System.ServiceModel.XmlSerializerFormatAttribute> provést, použijte atribut buď operace nebo smlouvy <xref:System.Xml.Serialization.XmlSerializer> a použijte typy kompatibilní s třídou v záhlaví zprávy a členy těla.  
  
## <a name="describing-messages-by-using-streams"></a>Popis zpráv pomocí datových proudů  
 Dalším způsobem, jak popsat zprávy <xref:System.IO.Stream> v operacích je použití třídy nebo jedné z jejích odvozených tříd v operaci smlouvy nebo jako člen těla smlouvy zprávy (musí být jediným členem v tomto případě). Pro příchozí zprávy musí být `Stream`typ – nelze použít odvozené třídy.  
  
 Místo vyvolání serializátoru WCF načte data z datového proudu a vloží je přímo do odchozí zprávy nebo načte data z příchozí zprávy a vloží je přímo do datového proudu. Následující ukázka ukazuje použití datových proudů.  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 Nelze kombinovat `Stream` a nestreamovat data v jednom textu zprávy. Pomocí kontraktu zpráv vložte další data do záhlaví zpráv. Následující příklad ukazuje nesprávné použití datových proudů při definování smlouvy operace.  
  
```csharp  
//Incorrect:  
// [OperationContract]  
// public void UploadFile (string fileName, Stream fileData);  
```  
  
```vb  
'Incorrect:  
    '<OperationContract()>  
    Public Sub UploadFile(fileName As String, fileData As StreamingContext)  
```  
  
 Následující ukázka ukazuje správné použití datových proudů při definování smlouvy operace.  
  
```csharp  
[OperationContract]  
public void UploadFile (UploadFileMessage message);  
//code omitted  
[MessageContract]  
public class UploadFileMessage  
{  
    [MessageHeader] public string fileName;  
    [MessageBodyMember] public Stream fileData;  
}  
```  
  
```vb  
<OperationContract()>  
Public Sub UploadFile(fileName As String, fileData As StreamingContext)  
'Code Omitted  
<MessageContract()>  
Public Class UploadFileMessage  
   <MessageHeader()>  
    Public Property fileName As String  
    <MessageBodyMember()>  
    Public Property fileData As Stream  
End Class  
```  
  
 Další informace naleznete v [tématu Velká data a streamování](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
## <a name="using-the-message-class"></a>Používání třídy Message  
 Chcete-li mít úplnou programovou kontrolu nad <xref:System.ServiceModel.Channels.Message> odeslané nebo přijaté zprávy, můžete použít třídu přímo, jak je znázorněno v následujícím příkladu kódu.  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 Toto je pokročilý scénář, který je podrobně popsán v [použití třídy message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="describing-fault-messages"></a>Popisující chybové zprávy  
 Kromě zpráv, které jsou popsány vrácená hodnota a výstupní nebo referenční parametry, všechny operace, které není jednosměrný můžete vrátit alespoň dvě možné zprávy: jeho normální odpověď zprávy a chybové zprávy. Zvažte následující smlouvu o operaci.  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 Tato operace může vrátit normální zprávu, která obsahuje `float` číslo, nebo zprávu o chybě, která obsahuje kód poruchy a popis. Toho lze dosáhnout vyvoláním <xref:System.ServiceModel.FaultException> v implementaci služby.  
  
 Pomocí atributu <xref:System.ServiceModel.FaultContractAttribute> můžete zadat další možné chybové zprávy. Další chyby musí být serializovatelné <xref:System.Runtime.Serialization.DataContractSerializer>pomocí , jak je znázorněno v následujícím příkladu kódu.  
  
```csharp  
[OperationContract]  
[FaultContract(typeof(ItineraryNotAvailableFault))]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
  
//code omitted  
  
[DataContract]  
public class ItineraryNotAvailableFault  
{  
    [DataMember]  
    public bool IsAlternativeDateAvailable;  
  
    [DataMember]  
    public DateTime alternativeSuggestedDate;  
}  
```  
  
```vb  
<OperationContract()>  
<FaultContract(GetType(ItineraryNotAvailableFault))>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime) As Double  
  
'Code Omitted  
<DataContract()>  
Public Class  
  <DataMember()>  
  Public Property IsAlternativeDateAvailable As Boolean  
  <DataMember()>  
  Public Property alternativeSuggestedDate As DateTime  
End Class  
```  
  
 Tyto další chyby mohou být generovány vyvoláním <xref:System.ServiceModel.FaultException%601> příslušného typu smlouvy dat. Další informace naleznete v [tématu Zpracování výjimek a poruch](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
 Třídu <xref:System.Xml.Serialization.XmlSerializer> nelze použít k popisu chyb. Nemá <xref:System.ServiceModel.XmlSerializerFormatAttribute> žádný vliv na chybové smlouvy.  
  
## <a name="using-derived-types"></a>Použití odvozených typů  
 Můžete chtít použít základní typ v operaci nebo smlouvy zprávy a potom použít odvozený typ při skutečném vyvolání operace. V takovém případě je nutné <xref:System.ServiceModel.ServiceKnownTypeAttribute> použít atribut nebo některé alternativní mechanismus povolit použití odvozené typy. Zvažte následující operaci.  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 Předpokládejme, `Book` že `Magazine`dva typy `LibraryItem`a , odvozují z . Chcete-li použít `IsLibraryItemAvailable` tyto typy v operaci, můžete změnit operaci takto:  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 Případně můžete použít atribut, <xref:System.Runtime.Serialization.KnownTypeAttribute> pokud <xref:System.Runtime.Serialization.DataContractSerializer> je používána výchozí, jak je znázorněno v následujícím příkladu kódu.  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
  
// code omitted
  
[DataContract]  
[KnownType(typeof(Book))]  
[KnownType(typeof(Magazine))]  
public class LibraryItem  
{  
    //code omitted  
}  
```  
  
```vb  
<OperationContract()>  
Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
  
'Code Omitted  
<DataContract()>  
<KnownType(GetType(Book))>  
<KnownType(GetType(Magazine))>  
Public Class LibraryItem  
  'Code Omitted  
End Class  
```  
  
 Atribut můžete <xref:System.Xml.Serialization.XmlIncludeAttribute> použít při <xref:System.Xml.Serialization.XmlSerializer>použití .  
  
 <xref:System.ServiceModel.ServiceKnownTypeAttribute> Atribut můžete použít na operaci nebo na celou službu. Přijímá buď typ nebo název metody volat získat seznam známých typů, stejně <xref:System.Runtime.Serialization.KnownTypeAttribute> jako atribut. Další informace naleznete v [tématu Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="specifying-the-use-and-style"></a>Určení použití a stylu  
 Při popisu služeb pomocí jazyka popisu webových služeb (WSDL) jsou dva běžně používané styly dokument a vzdálené volání procedur (RPC). Ve stylu Document je celé tělo zprávy popsáno pomocí schématu a WSDL popisuje různé části textu zprávy odkazem na prvky v rámci tohoto schématu. Ve stylu Vzdálenévolání procedur wsdl odkazuje na typ schématu pro každou část zprávy spíše než prvek. V některých případech je nutné ručně vybrat jeden z těchto stylů. Můžete to provést použitím <xref:System.ServiceModel.DataContractFormatAttribute> atributu `Style` a nastavením <xref:System.Runtime.Serialization.DataContractSerializer> vlastnosti (když `Style` se <xref:System.ServiceModel.XmlSerializerFormatAttribute> používá) nebo <xref:System.Xml.Serialization.XmlSerializer>nastavením atributu (při použití ).  
  
 Navíc <xref:System.Xml.Serialization.XmlSerializer> podporuje dvě formy serializované XML: `Literal` a `Encoded`. `Literal`je nejčastěji přijímaný formulář a <xref:System.Runtime.Serialization.DataContractSerializer> je jedinou formou podpěry. `Encoded`je starší formulář popsaný v části 5 specifikace SOAP a nedoporučuje se pro nové služby. Chcete-li `Encoded` přepnout `Use` do režimu, nastavte vlastnost atributu <xref:System.ServiceModel.XmlSerializerFormatAttribute> na `Encoded`.  
  
 Ve většině případů byste neměli měnit `Style` výchozí `Use` nastavení vlastností a.  
  
## <a name="controlling-the-serialization-process"></a>Řízení procesu serializace  
 Můžete provést řadu věcí přizpůsobit způsob serializace dat.  
  
### <a name="changing-server-serialization-settings"></a>Změna nastavení serializace serveru  
 Pokud je <xref:System.Runtime.Serialization.DataContractSerializer> výchozí používáno, můžete řídit některé aspekty procesu serializace <xref:System.ServiceModel.ServiceBehaviorAttribute> ve službě použitím atributu služby. Konkrétně můžete použít `MaxItemsInObjectGraph` vlastnost k nastavení kvóty, která omezuje <xref:System.Runtime.Serialization.DataContractSerializer> maximální počet objektů, které reserializuje. Pomocí této `IgnoreExtensionDataObject` vlastnosti můžete vypnout funkci zakopnutí verzí. Další informace o kvótách naleznete v [tématu Důležité informace o zabezpečení dat](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Další informace o zaokrouhlování naleznete v tématu [Forward-Compatible Data Contracts](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
```csharp  
[ServiceBehavior(MaxItemsInObjectGraph=100000)]  
public class MyDataService:IDataService  
{  
    public DataPoint[] GetData()  
    {  
       // Implementation omitted  
    }  
}  
```  
  
```vb  
<ServiceBehavior(MaxItemsInObjectGraph:=100000)>  
Public Class MyDataService Implements IDataService  
  
    Function GetData() As DataPoint()  
         ‘ Implementation omitted  
    End Function  
End Interface  
```  
  
### <a name="serialization-behaviors"></a>Chování serializace  
 Dvě chování jsou k dispozici <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> v <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> WCF, a které jsou automaticky zapojeny v závislosti na serializátor u použití pro konkrétní operaci. Vzhledem k tomu, že toto chování jsou použity automaticky, obvykle není třeba být vědomi nich.  
  
 Má však `DataContractSerializerOperationBehavior` `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`a `DataContractSurrogate` vlastnosti, které můžete použít k přizpůsobení procesu serializace. První dvě vlastnosti mají stejný význam jako v předchozí části. Vlastnost můžete `DataContractSurrogate` použít k povolení náhradní smlouvy dat, které jsou výkonný mechanismus pro přizpůsobení a rozšíření procesu serializace. Další informace naleznete v [tématu Náhradníkdatové smlouvy](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).  
  
 Serializaci klienta `DataContractSerializerOperationBehavior` i serveru můžete použít k přizpůsobení serializace klienta i serveru. Následující příklad ukazuje, jak `MaxItemsInObjectGraph` zvýšit kvótu na straně klienta.  
  
```csharp  
ChannelFactory<IDataService> factory = new ChannelFactory<IDataService>(binding, address);  
foreach (OperationDescription op in factory.Endpoint.Contract.Operations)  
{  
    DataContractSerializerOperationBehavior dataContractBehavior =  
                op.Behaviors.Find<DataContractSerializerOperationBehavior>()  
                as DataContractSerializerOperationBehavior;  
    if (dataContractBehavior != null)  
    {  
        dataContractBehavior.MaxItemsInObjectGraph = 100000;  
    }  
}  
IDataService client = factory.CreateChannel();  
```  
  
```vb  
Dim factory As ChannelFactory(Of IDataService) = New ChannelFactory(Of IDataService)(binding, address)  
For Each op As OperationDescription In factory.Endpoint.Contract.Operations  
        Dim dataContractBehavior As DataContractSerializerOperationBehavior = op.Behaviors.Find(Of DataContractSerializerOperationBehavior)()  
        If dataContractBehavior IsNot Nothing Then  
            dataContractBehavior.MaxItemsInObjectGraph = 100000  
        End If  
     Next  
    Dim client As IDataService = factory.CreateChannel  
```  
  
Následuje ekvivalentní kód ve službě v případě, že je hostován samostatně:
  
```csharp  
ServiceHost serviceHost = new ServiceHost(typeof(IDataService))  
foreach (ServiceEndpoint ep in serviceHost.Description.Endpoints)  
{  
foreach (OperationDescription op in ep.Contract.Operations)  
{  
        DataContractSerializerOperationBehavior dataContractBehavior =  
           op.Behaviors.Find<DataContractSerializerOperationBehavior>()  
                as DataContractSerializerOperationBehavior;  
        if (dataContractBehavior != null)  
        {  
            dataContractBehavior.MaxItemsInObjectGraph = 100000;  
        }  
}  
}  
serviceHost.Open();  
```  
  
```vb  
Dim serviceHost As ServiceHost = New ServiceHost(GetType(IDataService))  
        For Each ep As ServiceEndpoint In serviceHost.Description.Endpoints  
            For Each op As OperationDescription In ep.Contract.Operations  
                Dim dataContractBehavior As DataContractSerializerOperationBehavior = op.Behaviors.Find(Of DataContractSerializerOperationBehavior)()  
  
                If dataContractBehavior IsNot Nothing Then  
                    dataContractBehavior.MaxItemsInObjectGraph = 100000  
                End If  
            Next  
        Next  
        serviceHost.Open()  
```  
  
 V případě hostované webem je nutné `ServiceHost` vytvořit novou odvozenou třídu a připojit ji pomocí hostitelské továrny služby.  
  
### <a name="controlling-serialization-settings-in-configuration"></a>Řízení nastavení serializace v konfiguraci  
 A `MaxItemsInObjectGraph` `IgnoreExtensionDataObject` lze řídit prostřednictvím konfigurace `dataContractSerializer` pomocí koncového bodu nebo chování služby, jak je znázorněno v následujícím příkladu.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="LargeQuotaBehavior">  
                    <dataContractSerializer  
                      maxItemsInObjectGraph="100000" />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <client>  
            <endpoint address="http://example.com/myservice"  
                  behaviorConfiguration="LargeQuotaBehavior"  
                binding="basicHttpBinding" bindingConfiguration=""
                            contract="IDataService"  
                name="" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a>Serializace sdíleného typu, zachování objektového grafu a vlastní serializátory  
 Serializuje <xref:System.Runtime.Serialization.DataContractSerializer> pomocí názvů datových smluv a nikoli názvů typů .NET. To je v souladu s principy architektury orientované na služby a umožňuje velkou míru flexibility – typy .NET se mohou změnit bez ovlivnění smlouvy o drátu. Ve výjimečných případech můžete chtít serializovat skutečné názvy typů .NET, a tím zavést těsné párování mezi klientem a serverem, podobně jako technologie vzdálené komunikace rozhraní .NET Framework. Toto není doporučená praxe, s výjimkou ve výjimečných případech, které se obvykle vyskytují při migraci do WCF z rozhraní .NET Framework vzdálené komunikace. V takovém případě je <xref:System.Runtime.Serialization.NetDataContractSerializer> nutné použít <xref:System.Runtime.Serialization.DataContractSerializer> třídu namísto třídy.  
  
 Obvykle <xref:System.Runtime.Serialization.DataContractSerializer> serializuje objektgrafy jako stromy objektů. To znamená, že pokud stejný objekt je označována více než jednou, je serializován více než jednou. Zvažte například `PurchaseOrder` instanci, která má `billTo` `shipTo`dvě pole typu Adresa s názvem a . Pokud jsou obě pole nastavena na stejnou instanci Address, existují dvě identické instance adresy po serializaci a deserializaci. Důvodem je, že neexistuje žádný standardní interoperabilní způsob, jak reprezentovat objektové grafy <xref:System.Xml.Serialization.XmlSerializer>v XML (s výjimkou `Style` staršího standardu kódovaného SOAP, který je k dispozici v oblasti , jak je popsáno v předchozí části dne a). `Use` Serializace objektových grafů jako stromy má určité nevýhody, například grafy s cyklické odkazy nelze serializovat. V některých případě je nutné přepnout na serializaci grafu true objektu, i když není interoperabilní. To lze provést pomocí <xref:System.Runtime.Serialization.DataContractSerializer> konstruované `preserveObjectReferences` s parametrem nastaveným na `true`.  
  
 V některých případech předdefinované serializátory nestačí pro váš scénář. Ve většině případů můžete stále <xref:System.Runtime.Serialization.XmlObjectSerializer> použít abstrakce, ze kterého ataka <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.NetDataContractSerializer> odvodit.  
  
 Předchozí tři případy (zachování typu.NET, zachování grafu `XmlObjectSerializer`objektu a zcela vlastní serializace) vyžadují připojení vlastního serializátoru. Postupujte při tom podle následujících pokynů:  
  
1. Napište své vlastní chování vyplývající <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>z .  
  
2. Přepište dvě `CreateSerializer` metody vrátit <xref:System.Runtime.Serialization.NetDataContractSerializer>vlastní serializátor <xref:System.Runtime.Serialization.DataContractSerializer> (buď , s `preserveObjectReferences` nastavena na `true`, nebo vlastní ). <xref:System.Runtime.Serialization.XmlObjectSerializer>  
  
3. Před otevřením hostitele služby nebo vytvořením <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> kanálu klienta odeberte existující chování a připojte vlastní odvozenou třídu, kterou jste vytvořili v předchozích krocích.  
  
 Další informace o pokročilých konceptech serializace naleznete [v tématu Serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
## <a name="see-also"></a>Viz také

- [Používání třídy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)
- [Postupy: Povolení streamování](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
- [Postupy: Vytvoření základního kontraktu dat pro třídu nebo strukturu](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
