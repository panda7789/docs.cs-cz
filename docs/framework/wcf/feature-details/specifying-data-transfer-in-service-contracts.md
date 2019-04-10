---
title: Určování přenosu dat v kontraktech služby
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
ms.openlocfilehash: 88bdfe6e659e6e83365b3d17c9067581f209d154
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331517"
---
# <a name="specifying-data-transfer-in-service-contracts"></a><span data-ttu-id="5afb8-102">Určování přenosu dat v kontraktech služby</span><span class="sxs-lookup"><span data-stu-id="5afb8-102">Specifying Data Transfer in Service Contracts</span></span>
<span data-ttu-id="5afb8-103">Windows Communication Foundation (WCF) můžete představit jako infrastruktura zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="5afb8-103">The Windows Communication Foundation (WCF) can be thought of as a messaging infrastructure.</span></span> <span data-ttu-id="5afb8-104">Operace služby může přijímat zprávy, jejich zpracování a posílali zprávy.</span><span class="sxs-lookup"><span data-stu-id="5afb8-104">Service operations can receive messages, process them, and send them messages.</span></span> <span data-ttu-id="5afb8-105">Zprávy jsou popsány pomocí operace smluv.</span><span class="sxs-lookup"><span data-stu-id="5afb8-105">Messages are described using operation contracts.</span></span> <span data-ttu-id="5afb8-106">Představte si třeba následující smlouvy.</span><span class="sxs-lookup"><span data-stu-id="5afb8-106">For example, consider the following contract.</span></span>  
  
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
  
 <span data-ttu-id="5afb8-107">Tady `GetAirfare` operace přijímá zprávy s informacemi o `fromCity` a `toCity`a potom vrátí zprávu, která obsahuje číslo.</span><span class="sxs-lookup"><span data-stu-id="5afb8-107">Here, the `GetAirfare` operation accepts a message with information about `fromCity` and `toCity`, and then returns a message that contains a number.</span></span>  
  
 <span data-ttu-id="5afb8-108">Toto téma popisuje různé způsoby, jimiž lze popsat kontrakt operace zprávy.</span><span class="sxs-lookup"><span data-stu-id="5afb8-108">This topic explains the various ways in which an operation contract can describe messages.</span></span>  
  
## <a name="describing-messages-by-using-parameters"></a><span data-ttu-id="5afb8-109">Popis zpráv pomocí parametrů</span><span class="sxs-lookup"><span data-stu-id="5afb8-109">Describing Messages by Using Parameters</span></span>  
 <span data-ttu-id="5afb8-110">Nejjednodušší způsob, jak popisují zprávy je použít seznam parametrů a návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5afb8-110">The simplest way to describe a message is to use a parameter list and the return value.</span></span> <span data-ttu-id="5afb8-111">V předchozím příkladu `fromCity` a `toCity` parametry řetězce se používají k popisu zprávy s požadavkem a návratovou hodnotu typu float se používají k popisu zprávy s odpovědí.</span><span class="sxs-lookup"><span data-stu-id="5afb8-111">In the preceding example, the `fromCity` and `toCity` string parameters were used to describe the request message, and the float return value was used to describe the reply message.</span></span> <span data-ttu-id="5afb8-112">Pokud pouze návratová hodnota není dostatečná k popisu zprávy s odpovědí, výstupní parametry lze.</span><span class="sxs-lookup"><span data-stu-id="5afb8-112">If the return value alone is not enough to describe a reply message, out parameters may be used.</span></span> <span data-ttu-id="5afb8-113">Například následující operace má `fromCity` a `toCity` v jeho zprávy s požadavkem a číslo spolu s měny v jeho zpráva s odpovědí:</span><span class="sxs-lookup"><span data-stu-id="5afb8-113">For example, the following operation has `fromCity` and `toCity` in its request message, and a number together with a currency in its reply message:</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 <span data-ttu-id="5afb8-114">Kromě toho může použití parametrů odkazu k zařazení parametru požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="5afb8-114">Additionally, you may use reference parameters to make a parameter part of both the request and the reply message.</span></span> <span data-ttu-id="5afb8-115">Parametry musí být typy, které lze serializovat (převést na XML).</span><span class="sxs-lookup"><span data-stu-id="5afb8-115">The parameters must be of types that can be serialized (converted to XML).</span></span> <span data-ttu-id="5afb8-116">Ve výchozím nastavení používá WCF komponenty s názvem <xref:System.Runtime.Serialization.DataContractSerializer> třídy provedení tohoto převodu.</span><span class="sxs-lookup"><span data-stu-id="5afb8-116">By default, WCF uses a component called the <xref:System.Runtime.Serialization.DataContractSerializer> class to perform this conversion.</span></span> <span data-ttu-id="5afb8-117">Většina primitivní typy (například `int`, `string`, `float`, a `DateTime`.) jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="5afb8-117">Most primitive types (such as `int`, `string`, `float`, and `DateTime`.) are supported.</span></span> <span data-ttu-id="5afb8-118">Uživatelem definované typy musí mít obvykle kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="5afb8-118">User-defined types must normally have a data contract.</span></span> <span data-ttu-id="5afb8-119">Další informace najdete v tématu [kontraktů dat pomocí](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="5afb8-119">For more information, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
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
  
 <span data-ttu-id="5afb8-120">V některých případech `DataContractSerializer` není dostatečná k serializaci typů.</span><span class="sxs-lookup"><span data-stu-id="5afb8-120">Occasionally, the `DataContractSerializer` is not adequate to serialize your types.</span></span> <span data-ttu-id="5afb8-121">WCF podporuje alternativní Serializační stroj, <xref:System.Xml.Serialization.XmlSerializer>, který můžete také použít k serializaci parametrů.</span><span class="sxs-lookup"><span data-stu-id="5afb8-121">WCF supports an alternative serialization engine, the <xref:System.Xml.Serialization.XmlSerializer>, which you can also use to serialize parameters.</span></span> <span data-ttu-id="5afb8-122"><xref:System.Xml.Serialization.XmlSerializer> Umožňuje použít větší kontrolu nad výsledného souboru XML pomocí atributů, jako `XmlAttributeAttribute`.</span><span class="sxs-lookup"><span data-stu-id="5afb8-122">The <xref:System.Xml.Serialization.XmlSerializer> allows you to use more control over the resultant XML using attributes such as the `XmlAttributeAttribute`.</span></span> <span data-ttu-id="5afb8-123">Přejít na používání <xref:System.Xml.Serialization.XmlSerializer> pro určitou operaci, nebo pro celou službu, použije <xref:System.ServiceModel.XmlSerializerFormatAttribute> atribut operace nebo službu.</span><span class="sxs-lookup"><span data-stu-id="5afb8-123">To switch to using the <xref:System.Xml.Serialization.XmlSerializer> for a particular operation or for the entire service, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to an operation or a service.</span></span> <span data-ttu-id="5afb8-124">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5afb8-124">For example:</span></span>  
  
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
  
 <span data-ttu-id="5afb8-125">Další informace najdete v tématu [horizontálních oddílů pomocí třídy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span><span class="sxs-lookup"><span data-stu-id="5afb8-125">For more information, see [Using the XmlSerializer Class](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span></span> <span data-ttu-id="5afb8-126">Mějte na paměti, že ručně přepnutí na <xref:System.Xml.Serialization.XmlSerializer> jak je znázorněno zde se nedoporučuje, pokud máte konkrétní důvodů, proč se tak uvedené v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="5afb8-126">Remember that manually switching to the <xref:System.Xml.Serialization.XmlSerializer> as shown here is not recommended unless you have specific reasons to do so as detailed in that topic.</span></span>  
  
 <span data-ttu-id="5afb8-127">K izolování .NET názvy parametrů z názvů kontraktu, můžete použít <xref:System.ServiceModel.MessageParameterAttribute> atribut a použít `Name` vlastnosti chcete nastavit název kontraktu.</span><span class="sxs-lookup"><span data-stu-id="5afb8-127">To isolate .NET parameter names from contract names, you can use the <xref:System.ServiceModel.MessageParameterAttribute> attribute, and use the `Name` property to set the contract name.</span></span> <span data-ttu-id="5afb8-128">Například následující operace kontraktu je ekvivalentní k první příklad v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="5afb8-128">For example, the following operation contract is equivalent to the first example in this topic.</span></span>  
  
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
  
## <a name="describing-empty-messages"></a><span data-ttu-id="5afb8-129">Popisující vyprázdnit</span><span class="sxs-lookup"><span data-stu-id="5afb8-129">Describing Empty Messages</span></span>  
 <span data-ttu-id="5afb8-130">Zprávu prázdný žádost lze popsat tak, že žádný vstup nebo odkaz na parametry.</span><span class="sxs-lookup"><span data-stu-id="5afb8-130">An empty request message can be described by having no input or reference parameters.</span></span> <span data-ttu-id="5afb8-131">Například v C#:</span><span class="sxs-lookup"><span data-stu-id="5afb8-131">For example in C#:</span></span>  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 <span data-ttu-id="5afb8-132">Například v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="5afb8-132">For example in VB:</span></span>  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 <span data-ttu-id="5afb8-133">Zpráva odpovědi prázdný lze popsat tak, že `void` návratový typ a žádné parametry výstupu nebo odkaz.</span><span class="sxs-lookup"><span data-stu-id="5afb8-133">An empty reply message can be described by having a `void` return type and no output or reference parameters.</span></span> <span data-ttu-id="5afb8-134">Například:</span><span class="sxs-lookup"><span data-stu-id="5afb8-134">For example in:</span></span>  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 <span data-ttu-id="5afb8-135">Tím se liší od Jednosměrná operace, jako například:</span><span class="sxs-lookup"><span data-stu-id="5afb8-135">This is different from a one-way operation, such as:</span></span>  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 <span data-ttu-id="5afb8-136">`SetTemperatureStatus` Operace vrátí prázdnou zprávu.</span><span class="sxs-lookup"><span data-stu-id="5afb8-136">The `SetTemperatureStatus` operation returns an empty message.</span></span> <span data-ttu-id="5afb8-137">Pokud dojde k potížím při zpracování vstupní zprávy může místo toho vrátit chybu.</span><span class="sxs-lookup"><span data-stu-id="5afb8-137">It may return a fault instead if there is a problem processing the input message.</span></span> <span data-ttu-id="5afb8-138">`SetLightbulbStatus` Operace nic nespouští.</span><span class="sxs-lookup"><span data-stu-id="5afb8-138">The `SetLightbulbStatus` operation returns nothing.</span></span> <span data-ttu-id="5afb8-139">Neexistuje žádný způsob, jak komunikovat závady z této operace.</span><span class="sxs-lookup"><span data-stu-id="5afb8-139">There is no way to communicate a fault condition from this operation.</span></span>  
  
## <a name="describing-messages-by-using-message-contracts"></a><span data-ttu-id="5afb8-140">Použití kontraktů zpráv popisující zpráv</span><span class="sxs-lookup"><span data-stu-id="5afb8-140">Describing Messages by Using Message Contracts</span></span>  
 <span data-ttu-id="5afb8-141">Můžete chtít použít jeden typ představující celé zprávy.</span><span class="sxs-lookup"><span data-stu-id="5afb8-141">You may want to use a single type to represent the entire message.</span></span> <span data-ttu-id="5afb8-142">I když je možné použít kontraktu dat pro tento účel, je doporučeným způsobem, jak to provést pomocí kontraktu zprávy – tím se vyhnete zbytečným úrovně zabalení v výsledného souboru XML.</span><span class="sxs-lookup"><span data-stu-id="5afb8-142">While it is possible to use a data contract for this purpose, the recommended way to do this is to use a message contract—this avoids unnecessary levels of wrapping in the resultant XML.</span></span> <span data-ttu-id="5afb8-143">Kromě toho kontraktů zpráv umožní dosáhnout větší kontrolu nad výsledná zprávy.</span><span class="sxs-lookup"><span data-stu-id="5afb8-143">Additionally, message contracts allow you to exercise more control over resultant messages.</span></span> <span data-ttu-id="5afb8-144">Například můžete rozhodnout, které informace by měly být v textu zprávy a který by měl být v záhlaví zpráv.</span><span class="sxs-lookup"><span data-stu-id="5afb8-144">For instance, you can decide which pieces of information should be in the message body and which should be in the message headers.</span></span> <span data-ttu-id="5afb8-145">Následující příklad ukazuje použití kontraktů zpráv.</span><span class="sxs-lookup"><span data-stu-id="5afb8-145">The following example shows the use of message contracts.</span></span>  
  
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
  
 <span data-ttu-id="5afb8-146">Další informace najdete v tématu [použití kontraktů zpráv](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="5afb8-146">For more information, see [Using Message Contracts](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span></span>  
  
 <span data-ttu-id="5afb8-147">V předchozím příkladu <xref:System.Runtime.Serialization.DataContractSerializer> třída se stále používá ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="5afb8-147">In the previous example, the <xref:System.Runtime.Serialization.DataContractSerializer> class is still used by default.</span></span> <span data-ttu-id="5afb8-148"><xref:System.Xml.Serialization.XmlSerializer> Třídy lze také s kontrakty zpráv.</span><span class="sxs-lookup"><span data-stu-id="5afb8-148">The <xref:System.Xml.Serialization.XmlSerializer> class can also be used with message contracts.</span></span> <span data-ttu-id="5afb8-149">Chcete-li to provést, použijte <xref:System.ServiceModel.XmlSerializerFormatAttribute> atribut operaci nebo smlouvy a používat typy, které jsou kompatibilní s <xref:System.Xml.Serialization.XmlSerializer> třídy v záhlaví zpráv a tělo členy.</span><span class="sxs-lookup"><span data-stu-id="5afb8-149">To do this, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to either the operation or the contract, and use types compatible with the <xref:System.Xml.Serialization.XmlSerializer> class in the message headers and body members.</span></span>  
  
## <a name="describing-messages-by-using-streams"></a><span data-ttu-id="5afb8-150">Popis zprávy s použitím datových proudů</span><span class="sxs-lookup"><span data-stu-id="5afb8-150">Describing Messages by Using Streams</span></span>  
 <span data-ttu-id="5afb8-151">Dalším způsobem, jak popisují zprávy v operacích je použít <xref:System.IO.Stream> třídy nebo některé z odvozených tříd v kontrakt operace nebo jako člen textu zprávy kontraktu (musí být jediným členem v tomto případě).</span><span class="sxs-lookup"><span data-stu-id="5afb8-151">Another way to describe messages in operations is to use the <xref:System.IO.Stream> class or one of its derived classes in an operation contract or as a message contract body member (it must be the only member in this case).</span></span> <span data-ttu-id="5afb8-152">Pro příchozí zprávy, musí být typu `Stream`– odvozené třídy nelze použít.</span><span class="sxs-lookup"><span data-stu-id="5afb8-152">For incoming messages, the type must be `Stream`—you cannot use derived classes.</span></span>  
  
 <span data-ttu-id="5afb8-153">Namísto vyvolání serializátor, WCF načítá data z datového proudu a umístí ho přímo do odchozí zprávy, nebo načítá data z příchozí zprávy a vloží přímo do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="5afb8-153">Instead of invoking the serializer, WCF retrieves data from a stream and puts it directly into an outgoing message, or retrieves data from an incoming message and puts it directly into a stream.</span></span> <span data-ttu-id="5afb8-154">Následující příklad ukazuje použití datových proudů.</span><span class="sxs-lookup"><span data-stu-id="5afb8-154">The following sample shows the use of streams.</span></span>  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 <span data-ttu-id="5afb8-155">Nelze kombinovat `Stream` a jiných streamování dat v jedné zprávy.</span><span class="sxs-lookup"><span data-stu-id="5afb8-155">You cannot combine `Stream` and non-stream data in a single message body.</span></span> <span data-ttu-id="5afb8-156">Pomocí kontraktu zprávy do další data v záhlaví zpráv.</span><span class="sxs-lookup"><span data-stu-id="5afb8-156">Use a message contract to put the extra data in message headers.</span></span> <span data-ttu-id="5afb8-157">Následující příklad ukazuje nesprávné použití datových proudů, při definování kontrakt.</span><span class="sxs-lookup"><span data-stu-id="5afb8-157">The following example shows the incorrect usage of streams when defining the operation contract.</span></span>  
  
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
  
 <span data-ttu-id="5afb8-158">Následující příklad ukazuje správné použití datových proudů, při definování kontrakt operace.</span><span class="sxs-lookup"><span data-stu-id="5afb8-158">The following sample shows the correct usage of streams when defining an operation contract.</span></span>  
  
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
  
 <span data-ttu-id="5afb8-159">Další informace najdete v tématu [velkých objemů dat a datových proudů](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span><span class="sxs-lookup"><span data-stu-id="5afb8-159">For more information, see [Large Data and Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="using-the-message-class"></a><span data-ttu-id="5afb8-160">Používání třídy Message</span><span class="sxs-lookup"><span data-stu-id="5afb8-160">Using the Message Class</span></span>  
 <span data-ttu-id="5afb8-161">Chcete-li mít úplnou kontrolu programový odeslané a přijaté zprávy, můžete použít <xref:System.ServiceModel.Channels.Message> třídy přímo, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="5afb8-161">To have complete programmatic control over messages sent or received, you can use the <xref:System.ServiceModel.Channels.Message> class directly, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 <span data-ttu-id="5afb8-162">Toto je pokročilý scénář, který je podrobně popsán v [používání třídy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span><span class="sxs-lookup"><span data-stu-id="5afb8-162">This is an advanced scenario, which is described in detail in [Using the Message Class](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span></span>  
  
## <a name="describing-fault-messages"></a><span data-ttu-id="5afb8-163">S popisem chybové zprávy</span><span class="sxs-lookup"><span data-stu-id="5afb8-163">Describing Fault Messages</span></span>  
 <span data-ttu-id="5afb8-164">Kromě zprávy, které jsou popsány návratovou hodnotu a výstup, nebo parametr odkazu, můžete jakoukoli operaci, která není jednosměrné vrátí alespoň dva možné zprávy: jeho normální odpověď a zprávu o chybě.</span><span class="sxs-lookup"><span data-stu-id="5afb8-164">In addition to the messages that are described by the return value and output or reference parameters, any operation that is not one-way can return at least two possible messages: its normal response message and a fault message.</span></span> <span data-ttu-id="5afb8-165">Vezměte v úvahu následující operace kontraktu.</span><span class="sxs-lookup"><span data-stu-id="5afb8-165">Consider the following operation contract.</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 <span data-ttu-id="5afb8-166">Tato operace může vrátit buď normální zpráva obsahující text `float` číslo nebo zprávu o chybě, která obsahuje kód chyby a popis.</span><span class="sxs-lookup"><span data-stu-id="5afb8-166">This operation may either return a normal message that contains a `float` number, or a fault message that contains a fault code and a description.</span></span> <span data-ttu-id="5afb8-167">Můžete to udělat po vyvolání výjimky <xref:System.ServiceModel.FaultException> ve vaší implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="5afb8-167">You can accomplish this by throwing a <xref:System.ServiceModel.FaultException> in your service implementation.</span></span>  
  
 <span data-ttu-id="5afb8-168">Můžete zadat další možné chybové zprávy s použitím <xref:System.ServiceModel.FaultContractAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="5afb8-168">You can specify additional possible fault messages by using the <xref:System.ServiceModel.FaultContractAttribute> attribute.</span></span> <span data-ttu-id="5afb8-169">Další chyby musí být serializovatelný pomocí <xref:System.Runtime.Serialization.DataContractSerializer>, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="5afb8-169">The additional faults must be serializable using the <xref:System.Runtime.Serialization.DataContractSerializer>, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="5afb8-170">Tyto další chyby mohou být generovány vyvolávání <xref:System.ServiceModel.FaultException%601> odpovídající datový typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="5afb8-170">These additional faults can be generated by throwing a <xref:System.ServiceModel.FaultException%601> of the appropriate data contract type.</span></span> <span data-ttu-id="5afb8-171">Další informace najdete v tématu [zpracování výjimek a chyb](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span><span class="sxs-lookup"><span data-stu-id="5afb8-171">For more information, see [Handling Exceptions and Faults](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span></span>  
  
 <span data-ttu-id="5afb8-172">Nelze použít <xref:System.Xml.Serialization.XmlSerializer> tříd k popisu chyby.</span><span class="sxs-lookup"><span data-stu-id="5afb8-172">You cannot use the <xref:System.Xml.Serialization.XmlSerializer> class to describe faults.</span></span> <span data-ttu-id="5afb8-173"><xref:System.ServiceModel.XmlSerializerFormatAttribute> Nemá žádný vliv na selhání smluv.</span><span class="sxs-lookup"><span data-stu-id="5afb8-173">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> has no effect on fault contracts.</span></span>  
  
## <a name="using-derived-types"></a><span data-ttu-id="5afb8-174">Pomocí odvozené typy</span><span class="sxs-lookup"><span data-stu-id="5afb8-174">Using Derived Types</span></span>  
 <span data-ttu-id="5afb8-175">Můžete použít základní typ v operaci nebo kontraktu zprávy, a potom pomocí odvozený typ při skutečně vyvolání operace.</span><span class="sxs-lookup"><span data-stu-id="5afb8-175">You may want to use a base type in an operation or a message contract, and then use a derived type when actually invoking the operation.</span></span> <span data-ttu-id="5afb8-176">V takovém případě musíte použít buď <xref:System.ServiceModel.ServiceKnownTypeAttribute> atribut nebo některé alternativní mechanismus pro použití odvozené typy.</span><span class="sxs-lookup"><span data-stu-id="5afb8-176">In this case, you must use either the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute or some alternative mechanism to allow the use of derived types.</span></span> <span data-ttu-id="5afb8-177">Vezměte v úvahu následující operace.</span><span class="sxs-lookup"><span data-stu-id="5afb8-177">Consider the following operation.</span></span>  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 <span data-ttu-id="5afb8-178">Předpokládejme, že dva typy, `Book` a `Magazine`, jsou odvozeny z `LibraryItem`.</span><span class="sxs-lookup"><span data-stu-id="5afb8-178">Assume that two types, `Book` and `Magazine`, derive from `LibraryItem`.</span></span> <span data-ttu-id="5afb8-179">Chcete-li používat tyto typy v `IsLibraryItemAvailable` operace, můžete změnit operace následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5afb8-179">To use these types in the `IsLibraryItemAvailable` operation, you can change the operation as follows:</span></span>  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 <span data-ttu-id="5afb8-180">Alternativně můžete použít <xref:System.Runtime.Serialization.KnownTypeAttribute> kdy atribut výchozí <xref:System.Runtime.Serialization.DataContractSerializer> se používá, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="5afb8-180">Alternatively, you can use the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute when the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="5afb8-181">Můžete použít <xref:System.Xml.Serialization.XmlIncludeAttribute> atribut při použití <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="5afb8-181">You can use the <xref:System.Xml.Serialization.XmlIncludeAttribute> attribute when using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
 <span data-ttu-id="5afb8-182">Můžete použít <xref:System.ServiceModel.ServiceKnownTypeAttribute> atribut operace nebo celou služby.</span><span class="sxs-lookup"><span data-stu-id="5afb8-182">You can apply the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute to an operation or to the entire service.</span></span> <span data-ttu-id="5afb8-183">Přijímá typ nebo název metody pro volání k získání seznamu známých typů, stejně jako <xref:System.Runtime.Serialization.KnownTypeAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="5afb8-183">It accepts either a type or the name of the method to call to get a list of known types, just like the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span> <span data-ttu-id="5afb8-184">Další informace najdete v tématu [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="5afb8-184">For more information, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="specifying-the-use-and-style"></a><span data-ttu-id="5afb8-185">Určení použití a stylu</span><span class="sxs-lookup"><span data-stu-id="5afb8-185">Specifying the Use and Style</span></span>  
 <span data-ttu-id="5afb8-186">Při popisu služby pomocí webové služby WSDL (Description Language), dva běžně používaných styly jsou dokumentu a vzdálené volání procedur (RPC).</span><span class="sxs-lookup"><span data-stu-id="5afb8-186">When describing services using Web Services Description Language (WSDL), the two commonly used styles are Document and remote procedure call (RPC).</span></span> <span data-ttu-id="5afb8-187">Ve stylu dokumentu obsah celé zprávy je popsána pomocí schématu a jazyka WSDL popisuje různé části textu zprávy podle odkazující na prvky v rámci tohoto schématu.</span><span class="sxs-lookup"><span data-stu-id="5afb8-187">In the Document style, the entire message body is described using the schema, and the WSDL describes the various message body parts by referring to elements within that schema.</span></span> <span data-ttu-id="5afb8-188">Ve stylu RPC jazyka WSDL odkazuje na typ schématu pro každá část zprávy spíše než element.</span><span class="sxs-lookup"><span data-stu-id="5afb8-188">In the RPC style, the WSDL refers to a schema type for each message part rather than an element.</span></span> <span data-ttu-id="5afb8-189">V některých případech budete muset ručně vyberte jednu z těchto stylů vyplývají.</span><span class="sxs-lookup"><span data-stu-id="5afb8-189">In some cases, you have to manually select one of these styles.</span></span> <span data-ttu-id="5afb8-190">Můžete to provést použitím <xref:System.ServiceModel.DataContractFormatAttribute> atribut a nastavení `Style` vlastnosti (při <xref:System.Runtime.Serialization.DataContractSerializer> je používán), nebo nastavením `Style` na <xref:System.ServiceModel.XmlSerializerFormatAttribute> atribut (při použití <xref:System.Xml.Serialization.XmlSerializer>).</span><span class="sxs-lookup"><span data-stu-id="5afb8-190">You can do this by applying the <xref:System.ServiceModel.DataContractFormatAttribute> attribute and setting the `Style` property (when the <xref:System.Runtime.Serialization.DataContractSerializer> is in use), or by setting `Style` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute (when using the <xref:System.Xml.Serialization.XmlSerializer>).</span></span>  
  
 <span data-ttu-id="5afb8-191">Kromě toho <xref:System.Xml.Serialization.XmlSerializer> podporuje dvě formy serializovaném kódu XML: `Literal` a `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="5afb8-191">Additionally, the <xref:System.Xml.Serialization.XmlSerializer> supports two forms of serialized XML: `Literal` and `Encoded`.</span></span> `Literal` <span data-ttu-id="5afb8-192">je nejčastěji přijaté formuláře a je jedinou formou <xref:System.Runtime.Serialization.DataContractSerializer> podporuje.</span><span class="sxs-lookup"><span data-stu-id="5afb8-192">is the most commonly accepted form, and is the only form the <xref:System.Runtime.Serialization.DataContractSerializer> supports.</span></span> `Encoded` <span data-ttu-id="5afb8-193">je starší verze formuláře je popsáno v části 5 specifikaci protokolu SOAP a nedoporučuje se používat pro nové služby.</span><span class="sxs-lookup"><span data-stu-id="5afb8-193">is a legacy form described in section 5 of the SOAP specification, and is not recommended for new services.</span></span> <span data-ttu-id="5afb8-194">Přepnout na `Encoded` režimu, nastavte `Use` vlastnost <xref:System.ServiceModel.XmlSerializerFormatAttribute> atribut `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="5afb8-194">To switch to `Encoded` mode, set the `Use` property on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to `Encoded`.</span></span>  
  
 <span data-ttu-id="5afb8-195">Ve většině případů byste neměli měnit výchozí nastavení `Style` a `Use` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5afb8-195">In most cases, you should not change the default settings for the `Style` and `Use` properties.</span></span>  
  
## <a name="controlling-the-serialization-process"></a><span data-ttu-id="5afb8-196">Řízení procesu serializace</span><span class="sxs-lookup"><span data-stu-id="5afb8-196">Controlling the Serialization Process</span></span>  
 <span data-ttu-id="5afb8-197">Můžete provést několik věcí, které přizpůsobit způsob, jakým je serializovaná data.</span><span class="sxs-lookup"><span data-stu-id="5afb8-197">You can do a number of things to customize the way data is serialized.</span></span>  
  
### <a name="changing-server-serialization-settings"></a><span data-ttu-id="5afb8-198">Mění se nastavení serveru serializace</span><span class="sxs-lookup"><span data-stu-id="5afb8-198">Changing Server Serialization Settings</span></span>  
 <span data-ttu-id="5afb8-199">Pokud výchozí <xref:System.Runtime.Serialization.DataContractSerializer> je používán, můžete řídit některé aspekty procesu serializace ve službě s použitím <xref:System.ServiceModel.ServiceBehaviorAttribute> atributu ve službě.</span><span class="sxs-lookup"><span data-stu-id="5afb8-199">When the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, you can control some aspects of the serialization process on the service by applying the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the service.</span></span> <span data-ttu-id="5afb8-200">Konkrétně můžete použít `MaxItemsInObjectGraph` vlastnost nastavit kvótu, která omezuje maximální počet objektů <xref:System.Runtime.Serialization.DataContractSerializer> deserializuje.</span><span class="sxs-lookup"><span data-stu-id="5afb8-200">Specifically, you may use the `MaxItemsInObjectGraph` property to set the quota that limits the maximum number of objects the <xref:System.Runtime.Serialization.DataContractSerializer> deserializes.</span></span> <span data-ttu-id="5afb8-201">Můžete použít `IgnoreExtensionDataObject` vlastnost vypnutí funkce správy verzí verzemi.</span><span class="sxs-lookup"><span data-stu-id="5afb8-201">You can use the `IgnoreExtensionDataObject` property to turn off the round-tripping versioning feature.</span></span> <span data-ttu-id="5afb8-202">Další informace o kvótách najdete v tématu [aspekty zabezpečení pro Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span><span class="sxs-lookup"><span data-stu-id="5afb8-202">For more information about quotas, see [Security Considerations for Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span></span> <span data-ttu-id="5afb8-203">Další informace o verzemi najdete v tématu [kontraktů dat dopřednou](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="5afb8-203">For more information about round-tripping, see [Forward-Compatible Data Contracts](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span></span>  
  
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
  
### <a name="serialization-behaviors"></a><span data-ttu-id="5afb8-204">Chování serializace</span><span class="sxs-lookup"><span data-stu-id="5afb8-204">Serialization Behaviors</span></span>  
 <span data-ttu-id="5afb8-205">Dva chování, které jsou k dispozici ve službě WCF, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> a <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> , které jsou automaticky napájen ze sítě v závislosti na serializátoru, který se používá pro určitou operaci.</span><span class="sxs-lookup"><span data-stu-id="5afb8-205">Two behaviors are available in WCF, the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> and the <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> that are automatically plugged in depending on which serializer is in use for a particular operation.</span></span> <span data-ttu-id="5afb8-206">Protože těchto projevů se použijí automaticky, obvykle není nutné být vědomi.</span><span class="sxs-lookup"><span data-stu-id="5afb8-206">Because these behaviors are applied automatically, you normally do not have to be aware of them.</span></span>  
  
 <span data-ttu-id="5afb8-207">Ale `DataContractSerializerOperationBehavior` má `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, a `DataContractSurrogate` vlastnosti, které můžete použít k přizpůsobení procesu serializace.</span><span class="sxs-lookup"><span data-stu-id="5afb8-207">However, the `DataContractSerializerOperationBehavior` has the `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, and `DataContractSurrogate` properties that you may use to customize the serialization process.</span></span> <span data-ttu-id="5afb8-208">První dvě vlastnosti mají stejný význam, jak je popsáno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="5afb8-208">The first two properties have the same meaning as discussed in the previous section.</span></span> <span data-ttu-id="5afb8-209">Můžete použít `DataContractSurrogate` vlastností pro povolení náhrady kontraktů dat, které jsou efektivní mechanismus pro přizpůsobení a rozšíření procesu serializace.</span><span class="sxs-lookup"><span data-stu-id="5afb8-209">You can use the `DataContractSurrogate` property to enable data contract surrogates, which are a powerful mechanism for customizing and extending the serialization process.</span></span> <span data-ttu-id="5afb8-210">Další informace najdete v tématu [náhrady kontraktů dat](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span><span class="sxs-lookup"><span data-stu-id="5afb8-210">For more information, see [Data Contract Surrogates](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span></span>  
  
 <span data-ttu-id="5afb8-211">Můžete použít `DataContractSerializerOperationBehavior` k přizpůsobení serializaci klienta i serveru.</span><span class="sxs-lookup"><span data-stu-id="5afb8-211">You can use the `DataContractSerializerOperationBehavior` to customize both client and server serialization.</span></span> <span data-ttu-id="5afb8-212">Následující příklad ukazuje, jak zvýšit `MaxItemsInObjectGraph` kvóty na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="5afb8-212">The following example shows how to increase the `MaxItemsInObjectGraph` quota on the client.</span></span>  
  
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
  
 <span data-ttu-id="5afb8-213">Tady je ekvivalentní kód ve službě Service, tak v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="5afb8-213">Following is the equivalent code on the service, in the self-hosted case.</span></span>  
  
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
  
 <span data-ttu-id="5afb8-214">V případě hostovaných webových, musíte vytvořit nový `ServiceHost` odvozené třídy a zařadit ho pomocí vytváření hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="5afb8-214">In the Web-hosted case, you must create a new `ServiceHost` derived class and use a service host factory to plug it in.</span></span>  
  
### <a name="controlling-serialization-settings-in-configuration"></a><span data-ttu-id="5afb8-215">Řízení serializace nastavení v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="5afb8-215">Controlling Serialization Settings in Configuration</span></span>  
 <span data-ttu-id="5afb8-216">`MaxItemsInObjectGraph` a `IgnoreExtensionDataObject` je řídit prostřednictvím konfigurace s použitím `dataContractSerializer` chování koncového bodu nebo služby, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="5afb8-216">The `MaxItemsInObjectGraph` and `IgnoreExtensionDataObject` can be controlled through configuration by using the `dataContractSerializer` endpoint or service behavior, as shown in the following example.</span></span>  
  
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
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a><span data-ttu-id="5afb8-217">Serializace typu, objektu graf uchování a vlastní Serializátory sdílí</span><span class="sxs-lookup"><span data-stu-id="5afb8-217">Shared Type Serialization, Object Graph Preservation, and Custom Serializers</span></span>  
 <span data-ttu-id="5afb8-218"><xref:System.Runtime.Serialization.DataContractSerializer> Serializuje pomocí názvy datových kontraktů a .NET názvy typů.</span><span class="sxs-lookup"><span data-stu-id="5afb8-218">The <xref:System.Runtime.Serialization.DataContractSerializer> serializes using data contract names and not .NET type names.</span></span> <span data-ttu-id="5afb8-219">To je v souladu s principy architektury orientované na služby a umožňuje vysoký stupeň flexibilitu – typy .NET můžete změnit bez ovlivnění kontraktu při přenosu.</span><span class="sxs-lookup"><span data-stu-id="5afb8-219">This is consistent with service-oriented architecture tenets and allows for a great degree of flexibility—the .NET types can change without affecting the wire contract.</span></span> <span data-ttu-id="5afb8-220">Ve výjimečných případech můžete chtít serializovat skutečné názvy typů .NET, a tím Představujeme úzkou svázanost mezi klientem a serverem, podobné technologie vzdálené komunikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5afb8-220">In rare cases, you may want to serialize actual .NET type names, thereby introducing a tight coupling between the client and the server, similar to the .NET Framework remoting technology.</span></span> <span data-ttu-id="5afb8-221">Toto není doporučený postup, s výjimkou ve výjimečných případech, které obvykle dochází při migraci do WCF ze vzdálené komunikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5afb8-221">This is not a recommended practice, except in rare cases that usually occur when migrating to WCF from .NET Framework remoting.</span></span> <span data-ttu-id="5afb8-222">V takovém případě musíte použít <xref:System.Runtime.Serialization.NetDataContractSerializer> místo na třídě <xref:System.Runtime.Serialization.DataContractSerializer> třídy.</span><span class="sxs-lookup"><span data-stu-id="5afb8-222">In this case, you must use the <xref:System.Runtime.Serialization.NetDataContractSerializer> class instead of the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 <span data-ttu-id="5afb8-223"><xref:System.Runtime.Serialization.DataContractSerializer> Obvykle serializuje grafů objektů jako objekt stromové struktury.</span><span class="sxs-lookup"><span data-stu-id="5afb8-223">The <xref:System.Runtime.Serialization.DataContractSerializer> normally serializes object graphs as object trees.</span></span> <span data-ttu-id="5afb8-224">To znamená pokud na stejný objekt je uvedených více než jednou, je serializován více než jednou.</span><span class="sxs-lookup"><span data-stu-id="5afb8-224">That is, if the same object is referred to more than once, it is serialized more than once.</span></span> <span data-ttu-id="5afb8-225">Představte si třeba `PurchaseOrder` instanci, která má dvě pole typu adresa nazývá `billTo` a `shipTo`.</span><span class="sxs-lookup"><span data-stu-id="5afb8-225">For example, consider a `PurchaseOrder` instance that has two fields of type Address called `billTo` and `shipTo`.</span></span> <span data-ttu-id="5afb8-226">Pokud obě pole jsou nastavené na stejnou instanci adres, existují dvě instance stejné adresy po serializace a deserializace.</span><span class="sxs-lookup"><span data-stu-id="5afb8-226">If both fields are set to the same Address instance, there are two identical Address instances after serialization and deserialization.</span></span> <span data-ttu-id="5afb8-227">To se provádí, protože neexistuje žádný standardní interoperabilní způsob, jak reprezentaci grafů objektů ve formátu XML (s výjimkou starší verze standard kódovaný protokol SOAP k dispozici na <xref:System.Xml.Serialization.XmlSerializer>, jak je popsáno v předchozí části na `Style` a `Use`).</span><span class="sxs-lookup"><span data-stu-id="5afb8-227">This is done because there is no standard interoperable way to represent object graphs in XML (except for the legacy SOAP encoded standard available on the <xref:System.Xml.Serialization.XmlSerializer>, as described in the previous section on `Style` and `Use`).</span></span> <span data-ttu-id="5afb8-228">Serializace grafů objektů jako stromů má určité nevýhody, například nejde serializovat, grafy s cyklické odkazy.</span><span class="sxs-lookup"><span data-stu-id="5afb8-228">Serializing object graphs as trees has certain disadvantages, for example, graphs with circular references cannot be serialized.</span></span> <span data-ttu-id="5afb8-229">V některých případech je potřeba přepnout na hodnotu true objektu grafu serializace, i když není interoperabilní.</span><span class="sxs-lookup"><span data-stu-id="5afb8-229">Occasionally, it is necessary to switch to true object graph serialization, even though it is not interoperable.</span></span> <span data-ttu-id="5afb8-230">To můžete udělat pomocí <xref:System.Runtime.Serialization.DataContractSerializer> zkonstruován pomocí `preserveObjectReferences` parametr nastaven na `true`.</span><span class="sxs-lookup"><span data-stu-id="5afb8-230">This can be done by using the <xref:System.Runtime.Serialization.DataContractSerializer> constructed with the `preserveObjectReferences` parameter set to `true`.</span></span>  
  
 <span data-ttu-id="5afb8-231">V některých případech integrované serializátory nejsou dostatečná pro váš scénář.</span><span class="sxs-lookup"><span data-stu-id="5afb8-231">Occasionally, the built-in serializers are not enough for your scenario.</span></span> <span data-ttu-id="5afb8-232">Ve většině případů se můžete stále použít <xref:System.Runtime.Serialization.XmlObjectSerializer> abstrakce, ze kterých <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.NetDataContractSerializer> odvodit.</span><span class="sxs-lookup"><span data-stu-id="5afb8-232">In most cases, you can still use the <xref:System.Runtime.Serialization.XmlObjectSerializer> abstraction from which both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Runtime.Serialization.NetDataContractSerializer> derive.</span></span>  
  
 <span data-ttu-id="5afb8-233">Předchozí tři případy (zachování typu .NET, objekt grafu a zachovávání s rozlišením a zcela vlastní `XmlObjectSerializer`– na základě serializace) všechny vyžadují vlastní serializátor být zapojené do elektrické zásuvky.</span><span class="sxs-lookup"><span data-stu-id="5afb8-233">The previous three cases (.NET type preservation, object graph preservation, and completely custom `XmlObjectSerializer`-based serialization) all require a custom serializer be plugged in.</span></span> <span data-ttu-id="5afb8-234">Chcete-li to provést, postupujte následovně:</span><span class="sxs-lookup"><span data-stu-id="5afb8-234">To do this, perform the following steps:</span></span>  
  
1. <span data-ttu-id="5afb8-235">Zapsat vlastní chování odvozený od <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="5afb8-235">Write your own behavior deriving from the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span></span>  
  
2. <span data-ttu-id="5afb8-236">Přepsat dva `CreateSerializer` metody vracet vlastní serializátor (buď <xref:System.Runtime.Serialization.NetDataContractSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer> s `preserveObjectReferences` nastavena na `true`, nebo vlastní <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span><span class="sxs-lookup"><span data-stu-id="5afb8-236">Override the two `CreateSerializer` methods to return your own serializer (either the <xref:System.Runtime.Serialization.NetDataContractSerializer>, the <xref:System.Runtime.Serialization.DataContractSerializer> with `preserveObjectReferences` set to `true`, or your own custom <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span></span>  
  
3. <span data-ttu-id="5afb8-237">Před otevřením hostitele služby nebo vytvořením kanálu klienta, odeberte existující <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> chování a moduly ve vlastní odvozené třídy, které jste vytvořili v předchozích krocích.</span><span class="sxs-lookup"><span data-stu-id="5afb8-237">Before opening the service host or creating a client channel, remove the existing <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> behavior and plug in the custom derived class that you created in the previous steps.</span></span>  
  
 <span data-ttu-id="5afb8-238">Další informace o konceptech pokročilé serializace naleznete v tématu [serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="5afb8-238">For more information about advanced serialization concepts, see [Serialization and Deserialization](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5afb8-239">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5afb8-239">See also</span></span>

- [<span data-ttu-id="5afb8-240">Používání třídy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="5afb8-240">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)
- [<span data-ttu-id="5afb8-241">Postupy: Povolení streamování</span><span class="sxs-lookup"><span data-stu-id="5afb8-241">How to: Enable Streaming</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
- [<span data-ttu-id="5afb8-242">Postupy: Vytvoření základního kontraktu dat pro třídu nebo strukturu</span><span class="sxs-lookup"><span data-stu-id="5afb8-242">How to: Create a Basic Data Contract for a Class or Structure</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
