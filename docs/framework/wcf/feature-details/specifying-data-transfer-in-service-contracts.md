---
title: Určování přenosu dat v kontraktech služby
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
ms.openlocfilehash: ae05fb5ea0ee4962d9889e2a29399a3913a0d9d5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600293"
---
# <a name="specifying-data-transfer-in-service-contracts"></a>Určování přenosu dat v kontraktech služby
Windows Communication Foundation (WCF) si můžete představit jako infrastrukturu zasílání zpráv. Operace služby mohou přijímat zprávy, zpracovávat je a odesílat zprávy. Zprávy jsou popsány pomocí kontraktů operací. Zvažte například následující kontrakt.  
  
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
  
 Tato `GetAirfare` operace přijímá zprávu s informacemi o `fromCity` a a `toCity` potom vrátí zprávu, která obsahuje číslo.  
  
 Toto téma popisuje různé způsoby, kterými může kontrakt operace popsat zprávy.  
  
## <a name="describing-messages-by-using-parameters"></a>Popis zpráv pomocí parametrů  
 Nejjednodušší způsob, jak popsat zprávu, je použít seznam parametrů a návratovou hodnotu. V předchozím příkladu `fromCity` `toCity` byly použity parametry řetězců a k popisu zprávy požadavku a návratové hodnoty typu float byly použity k popisu odpovědi. Pokud není k dispozici pouze vrácená hodnota k popisu zprávy s odpovědí, lze použít výstupní parametry. Například následující operace obsahuje `fromCity` a `toCity` ve zprávě žádosti a číslo společně s měnou ve zprávě pro odpověď:  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 Kromě toho můžete použít referenční parametry k vytvoření parametru v rámci požadavku i zprávy s odpovědí. Parametry musí být typy, které mohou být serializovány (převedeno do XML). Ve výchozím nastavení používá WCF <xref:System.Runtime.Serialization.DataContractSerializer> k provedení tohoto převodu komponentu s názvem třída. Většina primitivních typů (například `int` , `string` , a `float` `DateTime` .) jsou podporovány. Uživatelsky definované typy musí mít obvykle kontrakt dat. Další informace najdete v tématu [Použití kontraktů dat](using-data-contracts.md).  
  
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
  
 V některých případech není `DataContractSerializer` vhodné serializovat vaše typy. WCF podporuje alternativní Serializační modul, <xref:System.Xml.Serialization.XmlSerializer> který můžete použít také k serializaci parametrů. <xref:System.Xml.Serialization.XmlSerializer>Umožňuje použít větší kontrolu nad výsledným XML pomocí atributů, jako je `XmlAttributeAttribute` . Chcete-li přepnout na použití <xref:System.Xml.Serialization.XmlSerializer> konkrétní operace nebo pro celou službu, použijte <xref:System.ServiceModel.XmlSerializerFormatAttribute> atribut na operaci nebo službu. Například:  
  
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
  
 Další informace naleznete v tématu [použití třídy XmlSerializer](using-the-xmlserializer-class.md). Mějte na paměti, že ruční přepnutí na, <xref:System.Xml.Serialization.XmlSerializer> jak je uvedeno zde, se nedoporučuje, pokud nemáte konkrétní důvody k tomu, jak je popsáno v tomto tématu.  
  
 Chcete-li izolovat názvy parametrů rozhraní .NET od názvů kontraktů, můžete použít <xref:System.ServiceModel.MessageParameterAttribute> atribut a pomocí `Name` vlastnosti nastavit název kontraktu. Například následující kontrakt operace je stejný jako první příklad v tomto tématu.  
  
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
  
## <a name="describing-empty-messages"></a>Popisující prázdné zprávy  
 Prázdná zpráva požadavku může být popsána tak, že neobsahuje žádné vstupní ani referenční parametry. Například v jazyce C#:  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 Například v Visual Basic:  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 Prázdná zpráva odpovědi může být popsána s `void` návratovým typem a bez parametrů Output nebo reference. Například v:  
  
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
  
 `SetTemperatureStatus`Operace vrátí prázdnou zprávu. Pokud při zpracování vstupní zprávy dojde k problému, může to vrátit chybu. `SetLightbulbStatus`Operace nevrátí žádnou hodnotu. Neexistuje žádný způsob, jak sdělit stav chyby z této operace.  
  
## <a name="describing-messages-by-using-message-contracts"></a>Popis zpráv pomocí kontraktů zpráv  
 Můžete použít jeden typ pro reprezentaci celé zprávy. I když je možné pro tento účel použít kontrakt dat, doporučuje se to použít k tomu, abyste se vyhnuli zbytečným úrovním balení ve výsledném XML. Kontrakty zpráv navíc umožňují lepší kontrolu nad výslednými zprávami. Například se můžete rozhodnout, jaké informace by měly být v textu zprávy a které by měly být v záhlavích zpráv. Následující příklad ukazuje použití kontraktů zpráv.  
  
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
  
 Další informace najdete v tématu [Použití kontraktů zpráv](using-message-contracts.md).  
  
 V předchozím příkladu <xref:System.Runtime.Serialization.DataContractSerializer> je třída stále používána ve výchozím nastavení. <xref:System.Xml.Serialization.XmlSerializer>Třídu lze také použít se kontrakty zpráv. Chcete-li to provést, použijte <xref:System.ServiceModel.XmlSerializerFormatAttribute> atribut buď na operaci, nebo na kontrakt a použijte typy kompatibilní s <xref:System.Xml.Serialization.XmlSerializer> třídou v záhlaví a v těle zprávy.  
  
## <a name="describing-messages-by-using-streams"></a>Popis zpráv pomocí datových proudů  
 Jiným způsobem, jak popsat zprávy v rámci operací, je použít <xref:System.IO.Stream> třídu nebo jednu z jejích odvozených tříd v kontraktu operace nebo jako člena těla zprávy (musí se jednat o jediného člena v tomto případě). U příchozích zpráv musí být typu `Stream` – nemůžete použít odvozené třídy.  
  
 Místo vyvolání serializátoru načte WCF Data z datového proudu a převede ho přímo do odchozí zprávy, nebo načte data z příchozí zprávy a převede je přímo do datového proudu. Následující příklad ukazuje použití datových proudů.  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 Nemůžete kombinovat `Stream` a nestreamovaná data v jednom těle zprávy. Pomocí kontraktu zprávy umístěte další data do záhlaví zpráv. Následující příklad ukazuje nesprávné použití datových proudů při definování kontraktu operace.  
  
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
  
 Následující příklad ukazuje správné použití datových proudů při definování kontraktu operace.  
  
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
  
 Další informace najdete v tématu [velké objemy dat a streamování](large-data-and-streaming.md).  
  
## <a name="using-the-message-class"></a>Používání třídy Message  
 Chcete-li mít úplnou programovou kontrolu nad odeslanými nebo přijímanými zprávami, můžete použít <xref:System.ServiceModel.Channels.Message> třídu přímo, jak je znázorněno v následujícím příkladu kódu.  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 Toto je pokročilý scénář, který je podrobně popsán v tématu [použití třídy Message](using-the-message-class.md).  
  
## <a name="describing-fault-messages"></a>Popisující chybové zprávy  
 Kromě zpráv popsaných návratovou hodnotou a výstupním parametrem nebo referenčními parametry může jakákoliv operace, která není jednosměrná, vracet alespoň dvě možné zprávy: jeho obvyklá zpráva odpovědi a chybová zpráva. Vezměte v úvahu následující kontrakt operace.  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 Tato operace může buď vrátit normální zprávu obsahující `float` číslo, nebo zprávu o chybě, která obsahuje kód chyby a popis. To můžete provést tak, že <xref:System.ServiceModel.FaultException> v implementaci služby vyplníte.  
  
 Pomocí atributu můžete určit další možné zprávy o selhání <xref:System.ServiceModel.FaultContractAttribute> . Další chyby musí být serializovatelný pomocí <xref:System.Runtime.Serialization.DataContractSerializer> , jak je znázorněno v následujícím příkladu kódu.  
  
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
  
 Tyto další chyby mohou být vygenerovány vyvoláním <xref:System.ServiceModel.FaultException%601> příslušného typu kontraktu dat. Další informace najdete v tématu [zpracování výjimek a chyb](../extending/handling-exceptions-and-faults.md).  
  
 Třídu nelze použít <xref:System.Xml.Serialization.XmlSerializer> k popisu chyb. <xref:System.ServiceModel.XmlSerializerFormatAttribute>Nemá žádný vliv na smlouvy o selhání.  
  
## <a name="using-derived-types"></a>Použití odvozených typů  
 Můžete chtít použít základní typ v operaci nebo kontraktu zprávy a potom použít odvozený typ při skutečném vyvolání operace. V takovém případě je nutné použít buď <xref:System.ServiceModel.ServiceKnownTypeAttribute> atribut, nebo nějaký alternativní mechanismus pro povolení použití odvozených typů. Zvažte následující operaci.  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 Předpokládá, že dva typy, `Book` a `Magazine` , odvozený z `LibraryItem` . Chcete-li použít tyto typy v `IsLibraryItemAvailable` operaci, můžete operaci změnit následujícím způsobem:  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 Alternativně můžete použít <xref:System.Runtime.Serialization.KnownTypeAttribute> atribut, pokud je použita výchozí hodnota <xref:System.Runtime.Serialization.DataContractSerializer> , jak je znázorněno v následujícím příkladu kódu.  
  
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
  
 Atribut lze použít <xref:System.Xml.Serialization.XmlIncludeAttribute> při použití <xref:System.Xml.Serialization.XmlSerializer> .  
  
 Můžete použít <xref:System.ServiceModel.ServiceKnownTypeAttribute> atribut na operaci nebo na celou službu. Přijímá buď typ, nebo název metody, která se má volat, aby získal seznam známých typů, stejně jako u <xref:System.Runtime.Serialization.KnownTypeAttribute> atributu. Další informace najdete v tématu [známé typy kontraktu dat](data-contract-known-types.md).  
  
## <a name="specifying-the-use-and-style"></a>Určení použití a stylu  
 Při popisu služeb pomocí jazyka WSDL (Web Services Description Language) jsou dva běžně používané styly dokumenty a vzdálené volání procedur (RPC). Ve stylu dokumentu je celý text zprávy popsán pomocí schématu a WSDL popisuje různé části těla zprávy odkazem na prvky v tomto schématu. Ve stylu RPC odkazuje WSDL na typ schématu pro každou část zprávy, nikoli na element. V některých případech je nutné ručně vybrat jeden z těchto stylů. To lze provést použitím <xref:System.ServiceModel.DataContractFormatAttribute> atributu a nastavením `Style` vlastnosti (při <xref:System.Runtime.Serialization.DataContractSerializer> použití) nebo nastavením `Style` <xref:System.ServiceModel.XmlSerializerFormatAttribute> atributu (při použití <xref:System.Xml.Serialization.XmlSerializer> ).  
  
 Kromě toho <xref:System.Xml.Serialization.XmlSerializer> podporuje dva formy serializovaného XML: `Literal` a `Encoded` . `Literal`je nejčastěji přijímaným formulářem a je jediným formulářem, který <xref:System.Runtime.Serialization.DataContractSerializer> podporuje. `Encoded`je starší verze formuláře popsané v části 5 specifikace protokolu SOAP a nedoporučuje se pro nové služby. Chcete-li přepnout do `Encoded` režimu, nastavte `Use` vlastnost u <xref:System.ServiceModel.XmlSerializerFormatAttribute> atributu na `Encoded` .  
  
 Ve většině případů byste neměli měnit výchozí nastavení `Style` `Use` vlastností a.  
  
## <a name="controlling-the-serialization-process"></a>Řízení procesu serializace  
 K přizpůsobení způsobu serializace dat můžete provést několik věcí.  
  
### <a name="changing-server-serialization-settings"></a>Mění se nastavení serializace serveru.  
 Pokud je výchozí hodnota <xref:System.Runtime.Serialization.DataContractSerializer> používána, můžete určit některé aspekty procesu serializace ve službě použitím <xref:System.ServiceModel.ServiceBehaviorAttribute> atributu na službu. Konkrétně můžete pomocí `MaxItemsInObjectGraph` vlastnosti nastavit kvótu, která omezuje maximální počet objektů, které jsou <xref:System.Runtime.Serialization.DataContractSerializer> reserializovány. Můžete použít `IgnoreExtensionDataObject` vlastnost k vypnutí funkce pro vypínání verzí Round-Trip. Další informace o kvótách najdete v tématu věnovaném [bezpečnostním hlediskům pro data](security-considerations-for-data.md). Další informace o kulatých Trip najdete v článku [kontrakty dat kompatibilní s dopředně](forward-compatible-data-contracts.md).  
  
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
 Ve službě WCF jsou k dispozici dvě chování, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> a <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> , která jsou automaticky zapojená v závislosti na tom, který serializátor se používá pro určitou operaci. Vzhledem k tomu, že se toto chování aplikuje automaticky, obvykle je nemusíte znát.  
  
 `DataContractSerializerOperationBehavior`Má však `MaxItemsInObjectGraph` `IgnoreExtensionDataObject` vlastnosti, a `DataContractSurrogate` , které lze použít k přizpůsobení procesu serializace. První dvě vlastnosti mají stejný význam, jak je popsáno v předchozí části. Vlastnost můžete použít `DataContractSurrogate` k povolení nahrazení kontraktů dat, což je účinný mechanismus pro přizpůsobení a rozšíření procesu serializace. Další informace najdete v tématu [náhrada za kontrakty dat](../extending/data-contract-surrogates.md).  
  
 Můžete použít `DataContractSerializerOperationBehavior` k přizpůsobení serializace klienta i serveru. Následující příklad ukazuje, jak zvýšit `MaxItemsInObjectGraph` kvótu klienta.  
  
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
  
Toto je ekvivalentní kód ve službě v případě v místním prostředí:
  
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
  
 V případě hostování webu je nutné vytvořit novou `ServiceHost` odvozenou třídu a použít továrnu hostitele služby k jejímu připojení.  
  
### <a name="controlling-serialization-settings-in-configuration"></a>Řízení nastavení serializace v konfiguraci  
 `MaxItemsInObjectGraph`A `IgnoreExtensionDataObject` lze ovládat pomocí konfigurace pomocí `dataContractSerializer` koncového bodu nebo služby, jak je znázorněno v následujícím příkladu.  
  
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
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a>Serializace sdíleného typu, zachování grafu objektů a vlastní serializace  
 <xref:System.Runtime.Serialization.DataContractSerializer>Serializace používá názvy kontraktů dat, nikoli názvy typů .NET. To je konzistentní s architekturou principy orientované na služby a umožňuje skvělou flexibilitu – typy .NET se můžou měnit bez ovlivnění kontraktu v rámci vedení. Ve výjimečných případech možná budete chtít serializovat skutečné názvy typů .NET, čímž zavedete těsné spojení mezi klientem a serverem, podobně jako technologie vzdálené komunikace .NET Framework. Nejedná se o doporučený postup, s výjimkou případů, kdy se při migraci na WCF z .NET Framework vzdálené komunikace obvykle objevuje. V takovém případě je nutné použít <xref:System.Runtime.Serialization.NetDataContractSerializer> třídu namísto <xref:System.Runtime.Serialization.DataContractSerializer> třídy.  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>Obvykle serializace grafy objektů jako stromy objektů. To znamená, že pokud je stejný objekt odkazován více než jednou, je serializován více než jednou. Zvažte například `PurchaseOrder` instanci, která má dvě pole typu Address s názvem `billTo` a `shipTo` . Pokud jsou obě pole nastavena na stejnou instanci adresy, existují dvě stejné instance adres po serializaci a deserializaci. K tomu dochází, protože neexistuje žádný standardní způsob, jak znázornit grafy objektů ve formátu XML (kromě starší verze kódované v protokolu SOAP na portálu <xref:System.Xml.Serialization.XmlSerializer> , jak je popsáno v předchozí části v tématu `Style` a `Use` ). Serializace grafů objektů jako stromů má určité nevýhody, například grafy s cyklickými odkazy nemohou být serializovány. V některých případech je nutné přepnout na skutečnou serializaci grafu objektů, i když není interoperabilní. To lze provést pomocí <xref:System.Runtime.Serialization.DataContractSerializer> vytvořeného s `preserveObjectReferences` parametrem nastaveným na `true` .  
  
 V některých případech nejsou předdefinované serializátory pro váš scénář dostatečné. Ve většině případů můžete stále používat <xref:System.Runtime.Serialization.XmlObjectSerializer> abstrakci, ze které jsou i <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.NetDataContractSerializer> odvozeny.  
  
 Předchozí tři případy (zachování typu .NET, zachování grafu objektů a zcela vlastní `XmlObjectSerializer` serializace) vyžadují, aby byl do systému zapojen vlastní serializátor. Postupujte při tom podle následujících pokynů:  
  
1. Pište vlastní chování odvozené z <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> .  
  
2. Přepište dvě `CreateSerializer` metody pro vrácení vlastního serializátoru (buď <xref:System.Runtime.Serialization.NetDataContractSerializer> , <xref:System.Runtime.Serialization.DataContractSerializer> s `preserveObjectReferences` nastaveným na `true` , nebo vlastní <xref:System.Runtime.Serialization.XmlObjectSerializer> ).  
  
3. Před otevřením hostitele služby nebo vytvořením klientského kanálu odeberte stávající <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> chování a připojte vlastní odvozenou třídu, kterou jste vytvořili v předchozím postupu.  
  
 Další informace o principech pokročilé serializace naleznete v tématu [serializace a deserializace](serialization-and-deserialization.md).  
  
## <a name="see-also"></a>Viz také

- [Používání třídy XmlSerializer](using-the-xmlserializer-class.md)
- [Postupy: Povolení streamování](how-to-enable-streaming.md)
- [Postupy: Vytvoření základního kontraktu dat pro třídu nebo strukturu](how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
