---
title: "Určování přenosu dat v kontraktech služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
caps.latest.revision: "38"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: be6262714ad2753d3a6f62a2956a31529641a246
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="specifying-data-transfer-in-service-contracts"></a>Určování přenosu dat v kontraktech služby
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Lze považovat za infrastrukturu zasílání zpráv. Operace služby můžete přijímat zprávy, jejich zpracování a jejich odeslání zprávy. Zprávy jsou popsány použití kontraktů operaci. Zvažte například následující kontrakt.  
  
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
  
 Zde `GetAirfare` operaci přijme zprávu s informacemi o `fromCity` a `toCity`a vrátí zprávu, která obsahuje několik.  
  
 Toto téma popisuje různé způsoby, ve kterých můžete popsat operaci kontrakt zprávy.  
  
## <a name="describing-messages-by-using-parameters"></a>Pomocí parametrů s popisem zprávy  
 Nejjednodušší způsob, jak popisuje zprávu je použít seznam parametrů a návratovou hodnotu. V předchozím příkladu `fromCity` a `toCity` parametrů řetězce se používají k popisu zprávu požadavku a návratovou hodnotu float byl použit k popisu zprávy s odpovědí. Pokud návratovou hodnotu samostatně není dost k popisu zprávu odpovědi, výstupní parametry mohou být použity. Například následující operace obsahuje `fromCity` a `toCity` v jeho zprávu žádosti a číslem společně s měny v jeho zpráva s odpovědí:  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 Kromě toho můžete použít odkaz na parametry aby parametr součástí požadavku a odpovědi. Parametry musí být typy, které lze serializovat (převést na XML). Ve výchozím nastavení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá komponenty s názvem <xref:System.Runtime.Serialization.DataContractSerializer> třída provést tento převod. Většina primitivní typy (například `int`, `string`, `float`, a `DateTime`.) jsou podporovány. Uživatelem definované typy musí mít normálně kontraktu dat. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
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
  
 V některých případech `DataContractSerializer` není vhodný k serializaci vaší typy. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]podporuje modul alternativní serializace <xref:System.Xml.Serialization.XmlSerializer>, který můžete použít také k serializaci parametrů. <xref:System.Xml.Serialization.XmlSerializer> Umožňuje používat větší kontrolu nad výsledné XML pomocí atributů, jako `XmlAttributeAttribute`. Chcete-li přejít k používání <xref:System.Xml.Serialization.XmlSerializer> určité operace nebo s celou službou, použít <xref:System.ServiceModel.XmlSerializerFormatAttribute> atribut operace nebo službu. Příklad:  
  
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
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Používání třídy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md). Mějte na paměti, že ručně přepnutí na <xref:System.Xml.Serialization.XmlSerializer> jak je vidět tady se nedoporučuje, pokud máte konkrétní důvodů, proč se tak podrobné v tomto tématu.  
  
 Pokud chcete izolovat názvy parametrů .NET z názvů kontraktu, můžete použít <xref:System.ServiceModel.MessageParameterAttribute> atribut a použít `Name` vlastnost nastavující název kontraktu. Například následující operace kontrakt je ekvivalentní v prvním příkladu v tomto tématu.  
  
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
  
## <a name="describing-empty-messages"></a>Popisující prázdný zprávy  
 Zprávu požadavku je prázdné lze popsat tak, že žádné parametry vstup nebo odkaz. Například v jazyce C#:  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 Například v jazyce Visual Basic:  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 Zprávu prázdný odpovědi lze popsat tak, že `void` návratový typ a parametry žádný výstup nebo odkaz. Například v:  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 To se liší od Jednosměrná operace, jako například:  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 `SetTemperatureStatus` Operace vrátí prázdnou zprávu. Pokud dojde k potížím při zpracování vstupní zprávy může místo toho vrátit chybu. `SetLightbulbStatus` Nic operaci. Neexistuje žádný způsob, jak sdělit podmínku chyby z této operace.  
  
## <a name="describing-messages-by-using-message-contracts"></a>S popisem zprávy pomocí kontrakty zpráv  
 Můžete použít jeden typ představují celé zprávy. I když je možné použít kontraktu dat pro tento účel, je použití kontrakt zprávy doporučeným způsobem, jak to udělat – tím zabraňuje zbytečným úrovně zabalení ve výsledné souboru XML. Kontrakty zpráv navíc umožňují větší kontrolu nad výsledné zprávy. Například můžete rozhodnout, které informace by měly být v textu zprávy a hodnota by měla být v záhlaví zprávy. Následující příklad ukazuje použití kontrakty zpráv.  
  
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
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Použití kontraktů zpráv](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
 V předchozím příkladu <xref:System.Runtime.Serialization.DataContractSerializer> třída se stále používá ve výchozím nastavení. <xref:System.Xml.Serialization.XmlSerializer> Třídu lze také použít s kontrakty zpráv. K tomu použít <xref:System.ServiceModel.XmlSerializerFormatAttribute> atribut operaci nebo smlouvy a používat kompatibilní s typy <xref:System.Xml.Serialization.XmlSerializer> třídy v záhlaví zpráv a členy textu.  
  
## <a name="describing-messages-by-using-streams"></a>S popisem zprávy pomocí datové proudy  
 Dalším způsobem popisují zprávy v operacích je používat <xref:System.IO.Stream> třídu nebo jedna z jeho odvozených tříd ve smlouvě operaci, nebo jako člen textu kontrakt zprávy (v takovém případě se musí být jediným členem). Pro příchozí zprávy, musí být typ `Stream`– odvozené třídy nelze použít.  
  
 Místo vyvolání serializátor, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] načítá data z datového proudu a vloží ho přímo do odchozí zprávy, nebo načítá data z příchozí zprávy a vloží ho přímo do datového proudu. Následující příklad ukazuje použití datových proudů.  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 Nelze kombinovat `Stream` a data datový proud v textu jedné zprávy. Pomocí kontrakt zprávy vložit doplňující data v záhlaví zprávy. Následující příklad ukazuje nesprávné použití datové proudy při definování kontraktu operaci.  
  
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
  
 Následující příklad ukazuje správné použití datové proudy při definování kontraktu operaci.  
  
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
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Velkého množství dat a vysílání datového proudu](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
## <a name="using-the-message-class"></a>Používání třídy Message  
 Chcete-li mít úplnou programový kontrolu nad odeslané a přijaté zprávy, můžete použít <xref:System.ServiceModel.Channels.Message> třídy přímo, jak je znázorněno v následujícím příkladu kódu.  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 Toto je složitější scénář, který je podrobně popsaná v [používání třídy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="describing-fault-messages"></a>S popisem chybové zprávy  
 Kromě zprávy, které jsou popsány návratovou hodnotu a výstup nebo odkaz parametry, všechny operace, která není jednosměrný vrátit alespoň dvě možné zprávy: zprávu jeho normální odpovědi a zprávu o chybě. Vezměte v úvahu následující operace kontrakt.  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 Tato operace může vrátit buď normální zpráva, která obsahuje `float` číslo nebo zprávu o chybě, která obsahuje kód chyby a popis. To můžete udělat po vyvolání výjimky <xref:System.ServiceModel.FaultException> v implementaci služby.  
  
 Můžete určit další možné chyby zprávy pomocí <xref:System.ServiceModel.FaultContractAttribute> atribut. Další chyby musí být serializovatelný pomocí <xref:System.Runtime.Serialization.DataContractSerializer>, jak ukazuje následující příklad kódu.  
  
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
  
 Tyto další chyby může být generována vyvolání <xref:System.ServiceModel.FaultException%601> typu kontraktu příslušná data. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Zpracování výjimek a chyb](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
 Nelze použít <xref:System.Xml.Serialization.XmlSerializer> třída k popisu chyby. <xref:System.ServiceModel.XmlSerializerFormatAttribute> Nemá žádný vliv na kontrakty selhání.  
  
## <a name="using-derived-types"></a>Pomocí odvozené typy  
 Můžete chtít použít základní typ operace nebo kontrakt zprávy a pak použít odvozený typ pro ve skutečnosti vyvolání operace. V takovém případě musíte použít buď <xref:System.ServiceModel.ServiceKnownTypeAttribute> atribut nebo některé alternativní mechanismus povolit použití odvozených typů. Vezměte v úvahu následující operace.  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 Předpokládejme, že dva typy, `Book` a `Magazine`, jsou odvozeny od `LibraryItem`. Používat tyto typy v `IsLibraryItemAvailable` operace, můžete změnit operaci následujícím způsobem:  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 Alternativně můžete použít <xref:System.Runtime.Serialization.KnownTypeAttribute> atributu při výchozí <xref:System.Runtime.Serialization.DataContractSerializer> se používá, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
 Můžete použít <xref:System.Xml.Serialization.XmlIncludeAttribute> atributu při použití <xref:System.Xml.Serialization.XmlSerializer>.  
  
 Můžete použít <xref:System.ServiceModel.ServiceKnownTypeAttribute> atribut operace nebo celé služby. Přijímá buď typ nebo název metody k volání k získání seznamu ze známých typů, stejně jako <xref:System.Runtime.Serialization.KnownTypeAttribute> atribut. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="specifying-the-use-and-style"></a>Určení použití a stylu  
 Při popisu služby pomocí webové služby WSDL (Description Language), dva běžně používané styly jsou dokumentu a volání vzdálených procedur (RPC). V dokumentu styl textu celé zprávy je popsán pomocí schématu a schématu WSDL popisuje různých částí textu zprávy tím, že odkazuje na elementy v rámci schéma této. Ve stylu RPC schématu WSDL odkazuje na typ schématu pro každou část zprávy, nikoli element. V některých případech budete muset ručně vyberte jednu z těchto stylů. To provedete použitím <xref:System.ServiceModel.DataContractFormatAttribute> atribut a nastavení `Style` vlastnost (při <xref:System.Runtime.Serialization.DataContractSerializer> se používá), nebo nastavením `Style` na <xref:System.ServiceModel.XmlSerializerFormatAttribute> atribut (při použití <xref:System.Xml.Serialization.XmlSerializer>).  
  
 Kromě toho <xref:System.Xml.Serialization.XmlSerializer> podporuje dvě formy serializovaných XML: `Literal` a `Encoded`. `Literal`je nejčastěji přijatý formuláře a je jediným <xref:System.Runtime.Serialization.DataContractSerializer> podporuje. `Encoded`je starší verze formuláře popsané v části 5 specifikace protokolu SOAP a nedoporučuje se používat pro nové služby. Přejděte na `Encoded` nastaven režim, `Use` vlastnost <xref:System.ServiceModel.XmlSerializerFormatAttribute> atribut `Encoded`.  
  
 Ve většině případů byste neměli měnit výchozí nastavení `Style` a `Use` vlastnosti.  
  
## <a name="controlling-the-serialization-process"></a>Řízení serializace procesu  
 Můžete to udělat několik věcí, chcete-li přizpůsobit způsob, jakým se serializovat data.  
  
### <a name="changing-server-serialization-settings"></a>Změna nastavení serveru serializace  
 Pokud výchozí <xref:System.Runtime.Serialization.DataContractSerializer> je používán, můžete řídit některé aspekty procesu serializace ve službě s použitím <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut ke službě. Konkrétně můžete použít `MaxItemsInObjectGraph` vlastnost možné nastavit kvótu, která omezuje maximální počet objektů, které <xref:System.Runtime.Serialization.DataContractSerializer> deserializuje. Můžete použít `IgnoreExtensionDataObject` vlastnost vypnout funkci správy verzí odezvy. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]kvóty, najdete v části [důležité informace o zabezpečení pro Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]odezvy, najdete v části [kontrakty dat dopřednou](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
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
 Jsou k dispozici ve dvou chování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> a <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> , jsou automaticky připojena v závislosti na serializátoru, který je používán pro konkrétní operaci. Protože tyto chování platí automaticky, obvykle nemáte zajímat, z nich.  
  
 Ale `DataContractSerializerOperationBehavior` má `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, a `DataContractSurrogate` vlastnosti, které můžete použít k přizpůsobení procesu serializace. První dvě vlastnosti mají stejný význam, jak je popsáno v předchozí části. Můžete použít `DataContractSurrogate` vlastnost umožňující náhrady kontraktů dat, které jsou výkonný mechanismus pro přizpůsobení a rozšíření procesu serializace. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Náhrady kontraktů dat](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).  
  
 Můžete použít `DataContractSerializerOperationBehavior` přizpůsobit serializace klient i server. Následující příklad ukazuje, jak zvýšit `MaxItemsInObjectGraph` kvóta na straně klienta.  
  
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
  
 Následuje kód ekvivalentní na službu, v případě, že vlastním hostováním.  
  
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
  
 V případě hostuje Web, musíte vytvořit nový `ServiceHost` odvozené třídy a zařadit ho pomocí vytváření hostitele služby.  
  
### <a name="controlling-serialization-settings-in-configuration"></a>Řízení serializace nastavení v konfiguraci  
 `MaxItemsInObjectGraph` a `IgnoreExtensionDataObject` lze řídit prostřednictvím konfigurace pomocí `dataContractSerializer` chování koncového bodu nebo služby, jak je znázorněno v následujícím příkladu.  
  
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
            <endpoint address=http://example.com/myservice  
                  behaviorConfiguration="LargeQuotaBehavior"  
                binding="basicHttpBinding" bindingConfiguration=""   
                            contract="IDataService"  
                name="" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a>Sdílené serializace typu, objekt grafu zachovávání a vlastní Serializátorů  
 <xref:System.Runtime.Serialization.DataContractSerializer> Serializuje pomocí názvy kontraktu dat a .NET názvy typů. To je konzistentní s principů architektura orientovaná na služby a umožňuje pro vysoký stupeň flexibilitu – typy .NET můžete změnit bez ovlivnění přenosová kontrakt. Ve výjimečných případech můžete k serializaci skutečné názvy typů rozhraní .NET, a tím představení úzkou párování mezi klientem a serverem, podobné technologie vzdálené komunikace rozhraní .NET Framework. Toto není doporučený postup, s výjimkou ve výjimečných případech, které obvykle dochází při migraci na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ze vzdálené komunikace rozhraní .NET Framework. V takovém případě musíte použít <xref:System.Runtime.Serialization.NetDataContractSerializer> místo <xref:System.Runtime.Serialization.DataContractSerializer> třídy.  
  
 <xref:System.Runtime.Serialization.DataContractSerializer> Normálně serializuje grafy objektu jako objekt stromy. To znamená pokud na stejný objekt odkazuje víc než jednou, ho je serializováno více než jednou. Představte si třeba `PurchaseOrder` instanci, která má dvě pole typu s názvem adresu `billTo` a `shipTo`. Pokud jsou obě pole nastavená na stejnou instanci adresu, existují dvě instance stejné adresy po serializace a deserializace. To se provádí, protože neexistuje žádný standardní umožňuje vzájemnou spolupráci způsob k reprezentaci objektu grafy v XML (s výjimkou k dispozici na starší verze protokolu SOAP kódovaný standard <xref:System.Xml.Serialization.XmlSerializer>, jak je popsáno v předchozí části na `Style` a `Use`). Serializace grafů objektu jako stromy má určité nevýhody, například nejde serializovat, grafy s cyklické odkazy. V některých případech je nutné přepnout na true objekt serializace grafů, i když není umožňuje vzájemnou spolupráci. To můžete provést pomocí <xref:System.Runtime.Serialization.DataContractSerializer> zkonstruovat s `preserveObjectReferences` parametr nastaven na `true`.  
  
 V některých případech integrované serializátorů nejsou dost pro váš scénář. Ve většině případů můžete pořád použít <xref:System.Runtime.Serialization.XmlObjectSerializer> abstrakce, ze které oba <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.NetDataContractSerializer> odvozena.  
  
 Předchozí třech případech (zachovávání typ rozhraní .NET, zachovávání grafu objektu a úplně vlastní `XmlObjectSerializer`– na základě serializace) všechny vyžadují vlastní serializátor být napájený ze sítě. Chcete-li to provést, postupujte takto:  
  
1.  Zápis vlastní chování odvozování z <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.  
  
2.  Přepsání dva `CreateSerializer` metody vrátit vlastní serializátor (buď <xref:System.Runtime.Serialization.NetDataContractSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer> s `preserveObjectReferences` nastavena na `true`, nebo vlastní vlastní <xref:System.Runtime.Serialization.XmlObjectSerializer>).  
  
3.  Před otevřením hostitele služby nebo vytvoření kanálu klienta, odeberte existující <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> chování a moduly vlastní odvozené třídy, kterou jste vytvořili v předchozích krocích.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Rozšířené koncepty serializace, najdete v části [serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
## <a name="see-also"></a>Viz také  
 [Používání třídy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 [Postupy: povolení streamování](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)  
 [Postupy: vytvoření kontraktu základní Data pro třídu nebo strukturu](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
