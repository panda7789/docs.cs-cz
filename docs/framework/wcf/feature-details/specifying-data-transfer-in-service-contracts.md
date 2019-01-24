---
title: Určování přenosu dat v kontraktech služby
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
ms.openlocfilehash: a9066054c82fdb2e25dace0b7611df4cbbf4ec93
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617262"
---
# <a name="specifying-data-transfer-in-service-contracts"></a>Určování přenosu dat v kontraktech služby
Windows Communication Foundation (WCF) můžete představit jako infrastruktura zasílání zpráv. Operace služby může přijímat zprávy, jejich zpracování a posílali zprávy. Zprávy jsou popsány pomocí operace smluv. Představte si třeba následující smlouvy.  
  
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
  
 Tady `GetAirfare` operace přijímá zprávy s informacemi o `fromCity` a `toCity`a potom vrátí zprávu, která obsahuje číslo.  
  
 Toto téma popisuje různé způsoby, jimiž lze popsat kontrakt operace zprávy.  
  
## <a name="describing-messages-by-using-parameters"></a>Popis zpráv pomocí parametrů  
 Nejjednodušší způsob, jak popisují zprávy je použít seznam parametrů a návratové hodnoty. V předchozím příkladu `fromCity` a `toCity` parametry řetězce se používají k popisu zprávy s požadavkem a návratovou hodnotu typu float se používají k popisu zprávy s odpovědí. Pokud pouze návratová hodnota není dostatečná k popisu zprávy s odpovědí, výstupní parametry lze. Například následující operace má `fromCity` a `toCity` v jeho zprávy s požadavkem a číslo spolu s měny v jeho zpráva s odpovědí:  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 Kromě toho může použití parametrů odkazu k zařazení parametru požadavku a odpovědi. Parametry musí být typy, které lze serializovat (převést na XML). Ve výchozím nastavení používá WCF komponenty s názvem <xref:System.Runtime.Serialization.DataContractSerializer> třídy provedení tohoto převodu. Většina primitivní typy (například `int`, `string`, `float`, a `DateTime`.) jsou podporovány. Uživatelem definované typy musí mít obvykle kontraktu dat. Další informace najdete v tématu [kontraktů dat pomocí](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
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
  
 V některých případech `DataContractSerializer` není dostatečná k serializaci typů. WCF podporuje alternativní Serializační stroj, <xref:System.Xml.Serialization.XmlSerializer>, který můžete také použít k serializaci parametrů. <xref:System.Xml.Serialization.XmlSerializer> Umožňuje použít větší kontrolu nad výsledného souboru XML pomocí atributů, jako `XmlAttributeAttribute`. Přejít na používání <xref:System.Xml.Serialization.XmlSerializer> pro určitou operaci, nebo pro celou službu, použije <xref:System.ServiceModel.XmlSerializerFormatAttribute> atribut operace nebo službu. Příklad:  
  
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
  
 Další informace najdete v tématu [horizontálních oddílů pomocí třídy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md). Mějte na paměti, že ručně přepnutí na <xref:System.Xml.Serialization.XmlSerializer> jak je znázorněno zde se nedoporučuje, pokud máte konkrétní důvodů, proč se tak uvedené v tomto tématu.  
  
 K izolování .NET názvy parametrů z názvů kontraktu, můžete použít <xref:System.ServiceModel.MessageParameterAttribute> atribut a použít `Name` vlastnosti chcete nastavit název kontraktu. Například následující operace kontraktu je ekvivalentní k první příklad v tomto tématu.  
  
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
  
## <a name="describing-empty-messages"></a>Popisující vyprázdnit  
 Zprávu prázdný žádost lze popsat tak, že žádný vstup nebo odkaz na parametry. Například v C#:  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 Například v jazyce Visual Basic:  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 Zpráva odpovědi prázdný lze popsat tak, že `void` návratový typ a žádné parametry výstupu nebo odkaz. Například:  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 Tím se liší od Jednosměrná operace, jako například:  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 `SetTemperatureStatus` Operace vrátí prázdnou zprávu. Pokud dojde k potížím při zpracování vstupní zprávy může místo toho vrátit chybu. `SetLightbulbStatus` Operace nic nespouští. Neexistuje žádný způsob, jak komunikovat závady z této operace.  
  
## <a name="describing-messages-by-using-message-contracts"></a>Použití kontraktů zpráv popisující zpráv  
 Můžete chtít použít jeden typ představující celé zprávy. I když je možné použít kontraktu dat pro tento účel, je doporučeným způsobem, jak to provést pomocí kontraktu zprávy – tím se vyhnete zbytečným úrovně zabalení v výsledného souboru XML. Kromě toho kontraktů zpráv umožní dosáhnout větší kontrolu nad výsledná zprávy. Například můžete rozhodnout, které informace by měly být v textu zprávy a který by měl být v záhlaví zpráv. Následující příklad ukazuje použití kontraktů zpráv.  
  
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
  
 Další informace najdete v tématu [použití kontraktů zpráv](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
 V předchozím příkladu <xref:System.Runtime.Serialization.DataContractSerializer> třída se stále používá ve výchozím nastavení. <xref:System.Xml.Serialization.XmlSerializer> Třídy lze také s kontrakty zpráv. Chcete-li to provést, použijte <xref:System.ServiceModel.XmlSerializerFormatAttribute> atribut operaci nebo smlouvy a používat typy, které jsou kompatibilní s <xref:System.Xml.Serialization.XmlSerializer> třídy v záhlaví zpráv a tělo členy.  
  
## <a name="describing-messages-by-using-streams"></a>Popis zprávy s použitím datových proudů  
 Dalším způsobem, jak popisují zprávy v operacích je použít <xref:System.IO.Stream> třídy nebo některé z odvozených tříd v kontrakt operace nebo jako člen textu zprávy kontraktu (musí být jediným členem v tomto případě). Pro příchozí zprávy, musí být typu `Stream`– odvozené třídy nelze použít.  
  
 Namísto vyvolání serializátor, WCF načítá data z datového proudu a umístí ho přímo do odchozí zprávy, nebo načítá data z příchozí zprávy a vloží přímo do datového proudu. Následující příklad ukazuje použití datových proudů.  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 Nelze kombinovat `Stream` a jiných streamování dat v jedné zprávy. Pomocí kontraktu zprávy do další data v záhlaví zpráv. Následující příklad ukazuje nesprávné použití datových proudů, při definování kontrakt.  
  
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
  
 Následující příklad ukazuje správné použití datových proudů, při definování kontrakt operace.  
  
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
  
 Další informace najdete v tématu [velkých objemů dat a datových proudů](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
## <a name="using-the-message-class"></a>Používání třídy Message  
 Chcete-li mít úplnou kontrolu programový odeslané a přijaté zprávy, můžete použít <xref:System.ServiceModel.Channels.Message> třídy přímo, jak je znázorněno v následujícím příkladu kódu.  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 Toto je pokročilý scénář, který je podrobně popsán v [používání třídy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="describing-fault-messages"></a>S popisem chybové zprávy  
 Kromě zprávy, které jsou popsány návratovou hodnotu a výstup, nebo parametr odkazu, můžete jakoukoli operaci, která není jednosměrné vrátí alespoň dva možné zprávy: jeho normální odpověď a zprávu o chybě. Vezměte v úvahu následující operace kontraktu.  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 Tato operace může vrátit buď normální zpráva obsahující text `float` číslo nebo zprávu o chybě, která obsahuje kód chyby a popis. Můžete to udělat po vyvolání výjimky <xref:System.ServiceModel.FaultException> ve vaší implementaci služby.  
  
 Můžete zadat další možné chybové zprávy s použitím <xref:System.ServiceModel.FaultContractAttribute> atribut. Další chyby musí být serializovatelný pomocí <xref:System.Runtime.Serialization.DataContractSerializer>, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
 Tyto další chyby mohou být generovány vyvolávání <xref:System.ServiceModel.FaultException%601> odpovídající datový typ kontraktu. Další informace najdete v tématu [zpracování výjimek a chyb](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
 Nelze použít <xref:System.Xml.Serialization.XmlSerializer> tříd k popisu chyby. <xref:System.ServiceModel.XmlSerializerFormatAttribute> Nemá žádný vliv na selhání smluv.  
  
## <a name="using-derived-types"></a>Pomocí odvozené typy  
 Můžete použít základní typ v operaci nebo kontraktu zprávy, a potom pomocí odvozený typ při skutečně vyvolání operace. V takovém případě musíte použít buď <xref:System.ServiceModel.ServiceKnownTypeAttribute> atribut nebo některé alternativní mechanismus pro použití odvozené typy. Vezměte v úvahu následující operace.  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 Předpokládejme, že dva typy, `Book` a `Magazine`, jsou odvozeny z `LibraryItem`. Chcete-li používat tyto typy v `IsLibraryItemAvailable` operace, můžete změnit operace následujícím způsobem:  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 Alternativně můžete použít <xref:System.Runtime.Serialization.KnownTypeAttribute> kdy atribut výchozí <xref:System.Runtime.Serialization.DataContractSerializer> se používá, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
 Můžete použít <xref:System.Xml.Serialization.XmlIncludeAttribute> atribut při použití <xref:System.Xml.Serialization.XmlSerializer>.  
  
 Můžete použít <xref:System.ServiceModel.ServiceKnownTypeAttribute> atribut operace nebo celou služby. Přijímá typ nebo název metody pro volání k získání seznamu známých typů, stejně jako <xref:System.Runtime.Serialization.KnownTypeAttribute> atribut. Další informace najdete v tématu [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="specifying-the-use-and-style"></a>Určení použití a stylu  
 Při popisu služby pomocí webové služby WSDL (Description Language), dva běžně používaných styly jsou dokumentu a vzdálené volání procedur (RPC). Ve stylu dokumentu obsah celé zprávy je popsána pomocí schématu a jazyka WSDL popisuje různé části textu zprávy podle odkazující na prvky v rámci tohoto schématu. Ve stylu RPC jazyka WSDL odkazuje na typ schématu pro každá část zprávy spíše než element. V některých případech budete muset ručně vyberte jednu z těchto stylů vyplývají. Můžete to provést použitím <xref:System.ServiceModel.DataContractFormatAttribute> atribut a nastavení `Style` vlastnosti (při <xref:System.Runtime.Serialization.DataContractSerializer> je používán), nebo nastavením `Style` na <xref:System.ServiceModel.XmlSerializerFormatAttribute> atribut (při použití <xref:System.Xml.Serialization.XmlSerializer>).  
  
 Kromě toho <xref:System.Xml.Serialization.XmlSerializer> podporuje dvě formy serializovaném kódu XML: `Literal` a `Encoded`. `Literal` je nejčastěji přijaté formuláře a je jedinou formou <xref:System.Runtime.Serialization.DataContractSerializer> podporuje. `Encoded` je starší verze formuláře je popsáno v části 5 specifikaci protokolu SOAP a nedoporučuje se používat pro nové služby. Přepnout na `Encoded` režimu, nastavte `Use` vlastnost <xref:System.ServiceModel.XmlSerializerFormatAttribute> atribut `Encoded`.  
  
 Ve většině případů byste neměli měnit výchozí nastavení `Style` a `Use` vlastnosti.  
  
## <a name="controlling-the-serialization-process"></a>Řízení procesu serializace  
 Můžete provést několik věcí, které přizpůsobit způsob, jakým je serializovaná data.  
  
### <a name="changing-server-serialization-settings"></a>Mění se nastavení serveru serializace  
 Pokud výchozí <xref:System.Runtime.Serialization.DataContractSerializer> je používán, můžete řídit některé aspekty procesu serializace ve službě s použitím <xref:System.ServiceModel.ServiceBehaviorAttribute> atributu ve službě. Konkrétně můžete použít `MaxItemsInObjectGraph` vlastnost nastavit kvótu, která omezuje maximální počet objektů <xref:System.Runtime.Serialization.DataContractSerializer> deserializuje. Můžete použít `IgnoreExtensionDataObject` vlastnost vypnutí funkce správy verzí verzemi. Další informace o kvótách najdete v tématu [aspekty zabezpečení pro Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Další informace o verzemi najdete v tématu [kontraktů dat dopřednou](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
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
 Dva chování, které jsou k dispozici ve službě WCF, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> a <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> , které jsou automaticky napájen ze sítě v závislosti na serializátoru, který se používá pro určitou operaci. Protože těchto projevů se použijí automaticky, obvykle není nutné být vědomi.  
  
 Ale `DataContractSerializerOperationBehavior` má `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, a `DataContractSurrogate` vlastnosti, které můžete použít k přizpůsobení procesu serializace. První dvě vlastnosti mají stejný význam, jak je popsáno v předchozí části. Můžete použít `DataContractSurrogate` vlastností pro povolení náhrady kontraktů dat, které jsou efektivní mechanismus pro přizpůsobení a rozšíření procesu serializace. Další informace najdete v tématu [náhrady kontraktů dat](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).  
  
 Můžete použít `DataContractSerializerOperationBehavior` k přizpůsobení serializaci klienta i serveru. Následující příklad ukazuje, jak zvýšit `MaxItemsInObjectGraph` kvóty na straně klienta.  
  
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
  
 Tady je ekvivalentní kód ve službě Service, tak v místním prostředí.  
  
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
  
 V případě hostovaných webových, musíte vytvořit nový `ServiceHost` odvozené třídy a zařadit ho pomocí vytváření hostitele služby.  
  
### <a name="controlling-serialization-settings-in-configuration"></a>Řízení serializace nastavení v konfiguraci  
 `MaxItemsInObjectGraph` a `IgnoreExtensionDataObject` je řídit prostřednictvím konfigurace s použitím `dataContractSerializer` chování koncového bodu nebo služby, jak je znázorněno v následujícím příkladu.  
  
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
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a>Serializace typu, objektu graf uchování a vlastní Serializátory sdílí  
 <xref:System.Runtime.Serialization.DataContractSerializer> Serializuje pomocí názvy datových kontraktů a .NET názvy typů. To je v souladu s principy architektury orientované na služby a umožňuje vysoký stupeň flexibilitu – typy .NET můžete změnit bez ovlivnění kontraktu při přenosu. Ve výjimečných případech můžete chtít serializovat skutečné názvy typů .NET, a tím Představujeme úzkou svázanost mezi klientem a serverem, podobné technologie vzdálené komunikace rozhraní .NET Framework. Toto není doporučený postup, s výjimkou ve výjimečných případech, které obvykle dochází při migraci do WCF ze vzdálené komunikace rozhraní .NET Framework. V takovém případě musíte použít <xref:System.Runtime.Serialization.NetDataContractSerializer> místo na třídě <xref:System.Runtime.Serialization.DataContractSerializer> třídy.  
  
 <xref:System.Runtime.Serialization.DataContractSerializer> Obvykle serializuje grafů objektů jako objekt stromové struktury. To znamená pokud na stejný objekt je uvedených více než jednou, je serializován více než jednou. Představte si třeba `PurchaseOrder` instanci, která má dvě pole typu adresa nazývá `billTo` a `shipTo`. Pokud obě pole jsou nastavené na stejnou instanci adres, existují dvě instance stejné adresy po serializace a deserializace. To se provádí, protože neexistuje žádný standardní interoperabilní způsob, jak reprezentaci grafů objektů ve formátu XML (s výjimkou starší verze standard kódovaný protokol SOAP k dispozici na <xref:System.Xml.Serialization.XmlSerializer>, jak je popsáno v předchozí části na `Style` a `Use`). Serializace grafů objektů jako stromů má určité nevýhody, například nejde serializovat, grafy s cyklické odkazy. V některých případech je potřeba přepnout na hodnotu true objektu grafu serializace, i když není interoperabilní. To můžete udělat pomocí <xref:System.Runtime.Serialization.DataContractSerializer> zkonstruován pomocí `preserveObjectReferences` parametr nastaven na `true`.  
  
 V některých případech integrované serializátory nejsou dostatečná pro váš scénář. Ve většině případů se můžete stále použít <xref:System.Runtime.Serialization.XmlObjectSerializer> abstrakce, ze kterých <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.NetDataContractSerializer> odvodit.  
  
 Předchozí tři případy (zachování typu .NET, objekt grafu a zachovávání s rozlišením a zcela vlastní `XmlObjectSerializer`– na základě serializace) všechny vyžadují vlastní serializátor být zapojené do elektrické zásuvky. Chcete-li to provést, postupujte následovně:  
  
1.  Zapsat vlastní chování odvozený od <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.  
  
2.  Přepsat dva `CreateSerializer` metody vracet vlastní serializátor (buď <xref:System.Runtime.Serialization.NetDataContractSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer> s `preserveObjectReferences` nastavena na `true`, nebo vlastní <xref:System.Runtime.Serialization.XmlObjectSerializer>).  
  
3.  Před otevřením hostitele služby nebo vytvořením kanálu klienta, odeberte existující <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> chování a moduly ve vlastní odvozené třídy, které jste vytvořili v předchozích krocích.  
  
 Další informace o konceptech pokročilé serializace naleznete v tématu [serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
## <a name="see-also"></a>Viz také:
- [Používání třídy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)
- [Postupy: Povolení streamování](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
- [Postupy: Vytvoření základního kontraktu dat pro třídu nebo strukturu](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
