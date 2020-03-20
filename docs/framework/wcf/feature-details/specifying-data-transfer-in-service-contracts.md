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
# <a name="specifying-data-transfer-in-service-contracts"></a><span data-ttu-id="8fbdc-102">Určování přenosu dat v kontraktech služby</span><span class="sxs-lookup"><span data-stu-id="8fbdc-102">Specifying Data Transfer in Service Contracts</span></span>
<span data-ttu-id="8fbdc-103">Windows Communication Foundation (WCF) si lze myslet jako infrastruktury zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-103">The Windows Communication Foundation (WCF) can be thought of as a messaging infrastructure.</span></span> <span data-ttu-id="8fbdc-104">Operace služby mohou přijímat zprávy, zpracovávat je a odesílat jim zprávy.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-104">Service operations can receive messages, process them, and send them messages.</span></span> <span data-ttu-id="8fbdc-105">Zprávy jsou popsány pomocí smluv operace.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-105">Messages are described using operation contracts.</span></span> <span data-ttu-id="8fbdc-106">Zvažte například následující smlouvu.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-106">For example, consider the following contract.</span></span>  
  
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
  
 <span data-ttu-id="8fbdc-107">Zde `GetAirfare` operace přijme zprávu s informacemi o `fromCity` a `toCity`a potom vrátí zprávu, která obsahuje číslo.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-107">Here, the `GetAirfare` operation accepts a message with information about `fromCity` and `toCity`, and then returns a message that contains a number.</span></span>  
  
 <span data-ttu-id="8fbdc-108">Toto téma vysvětluje různé způsoby, ve kterém může smlouva operace popisovat zprávy.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-108">This topic explains the various ways in which an operation contract can describe messages.</span></span>  
  
## <a name="describing-messages-by-using-parameters"></a><span data-ttu-id="8fbdc-109">Popis zpráv pomocí parametrů</span><span class="sxs-lookup"><span data-stu-id="8fbdc-109">Describing Messages by Using Parameters</span></span>  
 <span data-ttu-id="8fbdc-110">Nejjednodušší způsob, jak popsat zprávu, je použít seznam parametrů a vrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-110">The simplest way to describe a message is to use a parameter list and the return value.</span></span> <span data-ttu-id="8fbdc-111">V předchozím příkladu `fromCity` a `toCity` parametry řetězce byly použity k popisu zprávy požadavku a float vrácená hodnota byla použita k popisu zprávy odpovědi.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-111">In the preceding example, the `fromCity` and `toCity` string parameters were used to describe the request message, and the float return value was used to describe the reply message.</span></span> <span data-ttu-id="8fbdc-112">Pokud samotná vrácená hodnota nestačí k popisu odpovědi, mohou být použity parametry out.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-112">If the return value alone is not enough to describe a reply message, out parameters may be used.</span></span> <span data-ttu-id="8fbdc-113">Například následující operace `fromCity` má `toCity` a ve své zprávě požadavku a číslo spolu s měnou ve své odpovědi:</span><span class="sxs-lookup"><span data-stu-id="8fbdc-113">For example, the following operation has `fromCity` and `toCity` in its request message, and a number together with a currency in its reply message:</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 <span data-ttu-id="8fbdc-114">Kromě toho můžete použít referenční parametry, aby se parametr součástí požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-114">Additionally, you may use reference parameters to make a parameter part of both the request and the reply message.</span></span> <span data-ttu-id="8fbdc-115">Parametry musí být typy, které mohou být serializovány (převedeny na XML).</span><span class="sxs-lookup"><span data-stu-id="8fbdc-115">The parameters must be of types that can be serialized (converted to XML).</span></span> <span data-ttu-id="8fbdc-116">Ve výchozím nastavení WCF používá <xref:System.Runtime.Serialization.DataContractSerializer> komponentu s názvem třída k provedení tohoto převodu.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-116">By default, WCF uses a component called the <xref:System.Runtime.Serialization.DataContractSerializer> class to perform this conversion.</span></span> <span data-ttu-id="8fbdc-117">Jsou podporovány nejprimivnější `int`typy (například `string`, `float`, a `DateTime`.).</span><span class="sxs-lookup"><span data-stu-id="8fbdc-117">Most primitive types (such as `int`, `string`, `float`, and `DateTime`.) are supported.</span></span> <span data-ttu-id="8fbdc-118">Uživatelem definované typy musí mít obvykle kontrakt dat.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-118">User-defined types must normally have a data contract.</span></span> <span data-ttu-id="8fbdc-119">Další informace naleznete [v tématu Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="8fbdc-119">For more information, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
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
  
 <span data-ttu-id="8fbdc-120">V některých `DataContractSerializer` případě není adekvátní serializovat typy.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-120">Occasionally, the `DataContractSerializer` is not adequate to serialize your types.</span></span> <span data-ttu-id="8fbdc-121">WCF podporuje alternativní serializace <xref:System.Xml.Serialization.XmlSerializer>motoru , který můžete také použít k serializaci parametrů.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-121">WCF supports an alternative serialization engine, the <xref:System.Xml.Serialization.XmlSerializer>, which you can also use to serialize parameters.</span></span> <span data-ttu-id="8fbdc-122">Umožňuje <xref:System.Xml.Serialization.XmlSerializer> použít větší kontrolu nad výsledným XML pomocí atributů, jako je například `XmlAttributeAttribute`.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-122">The <xref:System.Xml.Serialization.XmlSerializer> allows you to use more control over the resultant XML using attributes such as the `XmlAttributeAttribute`.</span></span> <span data-ttu-id="8fbdc-123">Chcete-li přepnout na použití <xref:System.Xml.Serialization.XmlSerializer> pro konkrétní operaci <xref:System.ServiceModel.XmlSerializerFormatAttribute> nebo pro celou službu, použijte atribut pro operaci nebo službu.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-123">To switch to using the <xref:System.Xml.Serialization.XmlSerializer> for a particular operation or for the entire service, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to an operation or a service.</span></span> <span data-ttu-id="8fbdc-124">Například:</span><span class="sxs-lookup"><span data-stu-id="8fbdc-124">For example:</span></span>  
  
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
  
 <span data-ttu-id="8fbdc-125">Další informace naleznete [v tématu Použití třídy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span><span class="sxs-lookup"><span data-stu-id="8fbdc-125">For more information, see [Using the XmlSerializer Class](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span></span> <span data-ttu-id="8fbdc-126">Nezapomeňte, že ruční přepnutí <xref:System.Xml.Serialization.XmlSerializer> na, jak je znázorněno zde, se nedoporučuje, pokud k tomu nemáte konkrétní důvody, jak je podrobně popsáno v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-126">Remember that manually switching to the <xref:System.Xml.Serialization.XmlSerializer> as shown here is not recommended unless you have specific reasons to do so as detailed in that topic.</span></span>  
  
 <span data-ttu-id="8fbdc-127">Chcete-li izolovat názvy parametrů .NET od <xref:System.ServiceModel.MessageParameterAttribute> názvů smluv, `Name` můžete použít atribut a použít vlastnost k nastavení názvu smlouvy.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-127">To isolate .NET parameter names from contract names, you can use the <xref:System.ServiceModel.MessageParameterAttribute> attribute, and use the `Name` property to set the contract name.</span></span> <span data-ttu-id="8fbdc-128">Například následující smlouva operace je ekvivalentní první příklad v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-128">For example, the following operation contract is equivalent to the first example in this topic.</span></span>  
  
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
  
## <a name="describing-empty-messages"></a><span data-ttu-id="8fbdc-129">Popis prázdných zpráv</span><span class="sxs-lookup"><span data-stu-id="8fbdc-129">Describing Empty Messages</span></span>  
 <span data-ttu-id="8fbdc-130">Prázdnou zprávu požadavku lze popsat bez vstupních nebo referenčních parametrů.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-130">An empty request message can be described by having no input or reference parameters.</span></span> <span data-ttu-id="8fbdc-131">Například v c#:</span><span class="sxs-lookup"><span data-stu-id="8fbdc-131">For example, in C#:</span></span>  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 <span data-ttu-id="8fbdc-132">Například v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="8fbdc-132">For example, in Visual Basic:</span></span>  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 <span data-ttu-id="8fbdc-133">Prázdná odpověď zpráva může být `void` popsána s návratový typ a žádný výstup nebo referenční parametry.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-133">An empty reply message can be described by having a `void` return type and no output or reference parameters.</span></span> <span data-ttu-id="8fbdc-134">Například v:</span><span class="sxs-lookup"><span data-stu-id="8fbdc-134">For example in:</span></span>  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 <span data-ttu-id="8fbdc-135">To se liší od jednosměrné operace, například:</span><span class="sxs-lookup"><span data-stu-id="8fbdc-135">This is different from a one-way operation, such as:</span></span>  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 <span data-ttu-id="8fbdc-136">Operace `SetTemperatureStatus` vrátí prázdnou zprávu.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-136">The `SetTemperatureStatus` operation returns an empty message.</span></span> <span data-ttu-id="8fbdc-137">Může vrátit chybu místo toho, pokud je problém zpracování vstupní zprávy.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-137">It may return a fault instead if there is a problem processing the input message.</span></span> <span data-ttu-id="8fbdc-138">Operace `SetLightbulbStatus` vrátí nic.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-138">The `SetLightbulbStatus` operation returns nothing.</span></span> <span data-ttu-id="8fbdc-139">Neexistuje žádný způsob, jak komunikovat poruchový stav z této operace.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-139">There is no way to communicate a fault condition from this operation.</span></span>  
  
## <a name="describing-messages-by-using-message-contracts"></a><span data-ttu-id="8fbdc-140">Popis zpráv pomocí smluv se zprávami</span><span class="sxs-lookup"><span data-stu-id="8fbdc-140">Describing Messages by Using Message Contracts</span></span>  
 <span data-ttu-id="8fbdc-141">Můžete použít jeden typ představující celou zprávu.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-141">You may want to use a single type to represent the entire message.</span></span> <span data-ttu-id="8fbdc-142">I když je možné použít kontrakt dat pro tento účel, doporučený způsob, jak to provést, je použít zprávu smlouvy – tím se zabrání zbytečné úrovně zabalení ve výslednéxml.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-142">While it is possible to use a data contract for this purpose, the recommended way to do this is to use a message contract—this avoids unnecessary levels of wrapping in the resultant XML.</span></span> <span data-ttu-id="8fbdc-143">Smlouvy se zprávami navíc umožňují vykonávat větší kontrolu nad výsledné zprávy.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-143">Additionally, message contracts allow you to exercise more control over resultant messages.</span></span> <span data-ttu-id="8fbdc-144">Můžete například rozhodnout, které informace by měly být v textu zprávy a které by měly být v záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-144">For instance, you can decide which pieces of information should be in the message body and which should be in the message headers.</span></span> <span data-ttu-id="8fbdc-145">Následující příklad ukazuje použití smluv zpráv.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-145">The following example shows the use of message contracts.</span></span>  
  
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
  
 <span data-ttu-id="8fbdc-146">Další informace naleznete [v tématu Using Message Contracts](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="8fbdc-146">For more information, see [Using Message Contracts](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span></span>  
  
 <span data-ttu-id="8fbdc-147">V předchozím příkladu <xref:System.Runtime.Serialization.DataContractSerializer> je třída stále používána ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-147">In the previous example, the <xref:System.Runtime.Serialization.DataContractSerializer> class is still used by default.</span></span> <span data-ttu-id="8fbdc-148">Třídu <xref:System.Xml.Serialization.XmlSerializer> lze také použít se smlouvami zpráv.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-148">The <xref:System.Xml.Serialization.XmlSerializer> class can also be used with message contracts.</span></span> <span data-ttu-id="8fbdc-149">Chcete-li to <xref:System.ServiceModel.XmlSerializerFormatAttribute> provést, použijte atribut buď operace nebo smlouvy <xref:System.Xml.Serialization.XmlSerializer> a použijte typy kompatibilní s třídou v záhlaví zprávy a členy těla.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-149">To do this, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to either the operation or the contract, and use types compatible with the <xref:System.Xml.Serialization.XmlSerializer> class in the message headers and body members.</span></span>  
  
## <a name="describing-messages-by-using-streams"></a><span data-ttu-id="8fbdc-150">Popis zpráv pomocí datových proudů</span><span class="sxs-lookup"><span data-stu-id="8fbdc-150">Describing Messages by Using Streams</span></span>  
 <span data-ttu-id="8fbdc-151">Dalším způsobem, jak popsat zprávy <xref:System.IO.Stream> v operacích je použití třídy nebo jedné z jejích odvozených tříd v operaci smlouvy nebo jako člen těla smlouvy zprávy (musí být jediným členem v tomto případě).</span><span class="sxs-lookup"><span data-stu-id="8fbdc-151">Another way to describe messages in operations is to use the <xref:System.IO.Stream> class or one of its derived classes in an operation contract or as a message contract body member (it must be the only member in this case).</span></span> <span data-ttu-id="8fbdc-152">Pro příchozí zprávy musí být `Stream`typ – nelze použít odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-152">For incoming messages, the type must be `Stream`—you cannot use derived classes.</span></span>  
  
 <span data-ttu-id="8fbdc-153">Místo vyvolání serializátoru WCF načte data z datového proudu a vloží je přímo do odchozí zprávy nebo načte data z příchozí zprávy a vloží je přímo do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-153">Instead of invoking the serializer, WCF retrieves data from a stream and puts it directly into an outgoing message, or retrieves data from an incoming message and puts it directly into a stream.</span></span> <span data-ttu-id="8fbdc-154">Následující ukázka ukazuje použití datových proudů.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-154">The following sample shows the use of streams.</span></span>  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 <span data-ttu-id="8fbdc-155">Nelze kombinovat `Stream` a nestreamovat data v jednom textu zprávy.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-155">You cannot combine `Stream` and non-stream data in a single message body.</span></span> <span data-ttu-id="8fbdc-156">Pomocí kontraktu zpráv vložte další data do záhlaví zpráv.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-156">Use a message contract to put the extra data in message headers.</span></span> <span data-ttu-id="8fbdc-157">Následující příklad ukazuje nesprávné použití datových proudů při definování smlouvy operace.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-157">The following example shows the incorrect usage of streams when defining the operation contract.</span></span>  
  
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
  
 <span data-ttu-id="8fbdc-158">Následující ukázka ukazuje správné použití datových proudů při definování smlouvy operace.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-158">The following sample shows the correct usage of streams when defining an operation contract.</span></span>  
  
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
  
 <span data-ttu-id="8fbdc-159">Další informace naleznete v [tématu Velká data a streamování](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span><span class="sxs-lookup"><span data-stu-id="8fbdc-159">For more information, see [Large Data and Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="using-the-message-class"></a><span data-ttu-id="8fbdc-160">Používání třídy Message</span><span class="sxs-lookup"><span data-stu-id="8fbdc-160">Using the Message Class</span></span>  
 <span data-ttu-id="8fbdc-161">Chcete-li mít úplnou programovou kontrolu nad <xref:System.ServiceModel.Channels.Message> odeslané nebo přijaté zprávy, můžete použít třídu přímo, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-161">To have complete programmatic control over messages sent or received, you can use the <xref:System.ServiceModel.Channels.Message> class directly, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 <span data-ttu-id="8fbdc-162">Toto je pokročilý scénář, který je podrobně popsán v [použití třídy message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span><span class="sxs-lookup"><span data-stu-id="8fbdc-162">This is an advanced scenario, which is described in detail in [Using the Message Class](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span></span>  
  
## <a name="describing-fault-messages"></a><span data-ttu-id="8fbdc-163">Popisující chybové zprávy</span><span class="sxs-lookup"><span data-stu-id="8fbdc-163">Describing Fault Messages</span></span>  
 <span data-ttu-id="8fbdc-164">Kromě zpráv, které jsou popsány vrácená hodnota a výstupní nebo referenční parametry, všechny operace, které není jednosměrný můžete vrátit alespoň dvě možné zprávy: jeho normální odpověď zprávy a chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-164">In addition to the messages that are described by the return value and output or reference parameters, any operation that is not one-way can return at least two possible messages: its normal response message and a fault message.</span></span> <span data-ttu-id="8fbdc-165">Zvažte následující smlouvu o operaci.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-165">Consider the following operation contract.</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 <span data-ttu-id="8fbdc-166">Tato operace může vrátit normální zprávu, která obsahuje `float` číslo, nebo zprávu o chybě, která obsahuje kód poruchy a popis.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-166">This operation may either return a normal message that contains a `float` number, or a fault message that contains a fault code and a description.</span></span> <span data-ttu-id="8fbdc-167">Toho lze dosáhnout vyvoláním <xref:System.ServiceModel.FaultException> v implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-167">You can accomplish this by throwing a <xref:System.ServiceModel.FaultException> in your service implementation.</span></span>  
  
 <span data-ttu-id="8fbdc-168">Pomocí atributu <xref:System.ServiceModel.FaultContractAttribute> můžete zadat další možné chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-168">You can specify additional possible fault messages by using the <xref:System.ServiceModel.FaultContractAttribute> attribute.</span></span> <span data-ttu-id="8fbdc-169">Další chyby musí být serializovatelné <xref:System.Runtime.Serialization.DataContractSerializer>pomocí , jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-169">The additional faults must be serializable using the <xref:System.Runtime.Serialization.DataContractSerializer>, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="8fbdc-170">Tyto další chyby mohou být generovány vyvoláním <xref:System.ServiceModel.FaultException%601> příslušného typu smlouvy dat.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-170">These additional faults can be generated by throwing a <xref:System.ServiceModel.FaultException%601> of the appropriate data contract type.</span></span> <span data-ttu-id="8fbdc-171">Další informace naleznete v [tématu Zpracování výjimek a poruch](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span><span class="sxs-lookup"><span data-stu-id="8fbdc-171">For more information, see [Handling Exceptions and Faults](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span></span>  
  
 <span data-ttu-id="8fbdc-172">Třídu <xref:System.Xml.Serialization.XmlSerializer> nelze použít k popisu chyb.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-172">You cannot use the <xref:System.Xml.Serialization.XmlSerializer> class to describe faults.</span></span> <span data-ttu-id="8fbdc-173">Nemá <xref:System.ServiceModel.XmlSerializerFormatAttribute> žádný vliv na chybové smlouvy.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-173">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> has no effect on fault contracts.</span></span>  
  
## <a name="using-derived-types"></a><span data-ttu-id="8fbdc-174">Použití odvozených typů</span><span class="sxs-lookup"><span data-stu-id="8fbdc-174">Using Derived Types</span></span>  
 <span data-ttu-id="8fbdc-175">Můžete chtít použít základní typ v operaci nebo smlouvy zprávy a potom použít odvozený typ při skutečném vyvolání operace.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-175">You may want to use a base type in an operation or a message contract, and then use a derived type when actually invoking the operation.</span></span> <span data-ttu-id="8fbdc-176">V takovém případě je nutné <xref:System.ServiceModel.ServiceKnownTypeAttribute> použít atribut nebo některé alternativní mechanismus povolit použití odvozené typy.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-176">In this case, you must use either the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute or some alternative mechanism to allow the use of derived types.</span></span> <span data-ttu-id="8fbdc-177">Zvažte následující operaci.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-177">Consider the following operation.</span></span>  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 <span data-ttu-id="8fbdc-178">Předpokládejme, `Book` že `Magazine`dva typy `LibraryItem`a , odvozují z .</span><span class="sxs-lookup"><span data-stu-id="8fbdc-178">Assume that two types, `Book` and `Magazine`, derive from `LibraryItem`.</span></span> <span data-ttu-id="8fbdc-179">Chcete-li použít `IsLibraryItemAvailable` tyto typy v operaci, můžete změnit operaci takto:</span><span class="sxs-lookup"><span data-stu-id="8fbdc-179">To use these types in the `IsLibraryItemAvailable` operation, you can change the operation as follows:</span></span>  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 <span data-ttu-id="8fbdc-180">Případně můžete použít atribut, <xref:System.Runtime.Serialization.KnownTypeAttribute> pokud <xref:System.Runtime.Serialization.DataContractSerializer> je používána výchozí, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-180">Alternatively, you can use the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute when the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="8fbdc-181">Atribut můžete <xref:System.Xml.Serialization.XmlIncludeAttribute> použít při <xref:System.Xml.Serialization.XmlSerializer>použití .</span><span class="sxs-lookup"><span data-stu-id="8fbdc-181">You can use the <xref:System.Xml.Serialization.XmlIncludeAttribute> attribute when using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
 <span data-ttu-id="8fbdc-182"><xref:System.ServiceModel.ServiceKnownTypeAttribute> Atribut můžete použít na operaci nebo na celou službu.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-182">You can apply the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute to an operation or to the entire service.</span></span> <span data-ttu-id="8fbdc-183">Přijímá buď typ nebo název metody volat získat seznam známých typů, stejně <xref:System.Runtime.Serialization.KnownTypeAttribute> jako atribut.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-183">It accepts either a type or the name of the method to call to get a list of known types, just like the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span> <span data-ttu-id="8fbdc-184">Další informace naleznete v [tématu Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="8fbdc-184">For more information, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="specifying-the-use-and-style"></a><span data-ttu-id="8fbdc-185">Určení použití a stylu</span><span class="sxs-lookup"><span data-stu-id="8fbdc-185">Specifying the Use and Style</span></span>  
 <span data-ttu-id="8fbdc-186">Při popisu služeb pomocí jazyka popisu webových služeb (WSDL) jsou dva běžně používané styly dokument a vzdálené volání procedur (RPC).</span><span class="sxs-lookup"><span data-stu-id="8fbdc-186">When describing services using Web Services Description Language (WSDL), the two commonly used styles are Document and remote procedure call (RPC).</span></span> <span data-ttu-id="8fbdc-187">Ve stylu Document je celé tělo zprávy popsáno pomocí schématu a WSDL popisuje různé části textu zprávy odkazem na prvky v rámci tohoto schématu.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-187">In the Document style, the entire message body is described using the schema, and the WSDL describes the various message body parts by referring to elements within that schema.</span></span> <span data-ttu-id="8fbdc-188">Ve stylu Vzdálenévolání procedur wsdl odkazuje na typ schématu pro každou část zprávy spíše než prvek.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-188">In the RPC style, the WSDL refers to a schema type for each message part rather than an element.</span></span> <span data-ttu-id="8fbdc-189">V některých případech je nutné ručně vybrat jeden z těchto stylů.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-189">In some cases, you have to manually select one of these styles.</span></span> <span data-ttu-id="8fbdc-190">Můžete to provést použitím <xref:System.ServiceModel.DataContractFormatAttribute> atributu `Style` a nastavením <xref:System.Runtime.Serialization.DataContractSerializer> vlastnosti (když `Style` se <xref:System.ServiceModel.XmlSerializerFormatAttribute> používá) nebo <xref:System.Xml.Serialization.XmlSerializer>nastavením atributu (při použití ).</span><span class="sxs-lookup"><span data-stu-id="8fbdc-190">You can do this by applying the <xref:System.ServiceModel.DataContractFormatAttribute> attribute and setting the `Style` property (when the <xref:System.Runtime.Serialization.DataContractSerializer> is in use), or by setting `Style` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute (when using the <xref:System.Xml.Serialization.XmlSerializer>).</span></span>  
  
 <span data-ttu-id="8fbdc-191">Navíc <xref:System.Xml.Serialization.XmlSerializer> podporuje dvě formy serializované XML: `Literal` a `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-191">Additionally, the <xref:System.Xml.Serialization.XmlSerializer> supports two forms of serialized XML: `Literal` and `Encoded`.</span></span> <span data-ttu-id="8fbdc-192">`Literal`je nejčastěji přijímaný formulář a <xref:System.Runtime.Serialization.DataContractSerializer> je jedinou formou podpěry.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-192">`Literal` is the most commonly accepted form, and is the only form the <xref:System.Runtime.Serialization.DataContractSerializer> supports.</span></span> <span data-ttu-id="8fbdc-193">`Encoded`je starší formulář popsaný v části 5 specifikace SOAP a nedoporučuje se pro nové služby.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-193">`Encoded` is a legacy form described in section 5 of the SOAP specification, and is not recommended for new services.</span></span> <span data-ttu-id="8fbdc-194">Chcete-li `Encoded` přepnout `Use` do režimu, nastavte vlastnost atributu <xref:System.ServiceModel.XmlSerializerFormatAttribute> na `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-194">To switch to `Encoded` mode, set the `Use` property on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to `Encoded`.</span></span>  
  
 <span data-ttu-id="8fbdc-195">Ve většině případů byste neměli měnit `Style` výchozí `Use` nastavení vlastností a.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-195">In most cases, you should not change the default settings for the `Style` and `Use` properties.</span></span>  
  
## <a name="controlling-the-serialization-process"></a><span data-ttu-id="8fbdc-196">Řízení procesu serializace</span><span class="sxs-lookup"><span data-stu-id="8fbdc-196">Controlling the Serialization Process</span></span>  
 <span data-ttu-id="8fbdc-197">Můžete provést řadu věcí přizpůsobit způsob serializace dat.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-197">You can do a number of things to customize the way data is serialized.</span></span>  
  
### <a name="changing-server-serialization-settings"></a><span data-ttu-id="8fbdc-198">Změna nastavení serializace serveru</span><span class="sxs-lookup"><span data-stu-id="8fbdc-198">Changing Server Serialization Settings</span></span>  
 <span data-ttu-id="8fbdc-199">Pokud je <xref:System.Runtime.Serialization.DataContractSerializer> výchozí používáno, můžete řídit některé aspekty procesu serializace <xref:System.ServiceModel.ServiceBehaviorAttribute> ve službě použitím atributu služby.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-199">When the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, you can control some aspects of the serialization process on the service by applying the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the service.</span></span> <span data-ttu-id="8fbdc-200">Konkrétně můžete použít `MaxItemsInObjectGraph` vlastnost k nastavení kvóty, která omezuje <xref:System.Runtime.Serialization.DataContractSerializer> maximální počet objektů, které reserializuje.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-200">Specifically, you may use the `MaxItemsInObjectGraph` property to set the quota that limits the maximum number of objects the <xref:System.Runtime.Serialization.DataContractSerializer> deserializes.</span></span> <span data-ttu-id="8fbdc-201">Pomocí této `IgnoreExtensionDataObject` vlastnosti můžete vypnout funkci zakopnutí verzí.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-201">You can use the `IgnoreExtensionDataObject` property to turn off the round-tripping versioning feature.</span></span> <span data-ttu-id="8fbdc-202">Další informace o kvótách naleznete v [tématu Důležité informace o zabezpečení dat](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span><span class="sxs-lookup"><span data-stu-id="8fbdc-202">For more information about quotas, see [Security Considerations for Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span></span> <span data-ttu-id="8fbdc-203">Další informace o zaokrouhlování naleznete v tématu [Forward-Compatible Data Contracts](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="8fbdc-203">For more information about round-tripping, see [Forward-Compatible Data Contracts](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span></span>  
  
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
  
### <a name="serialization-behaviors"></a><span data-ttu-id="8fbdc-204">Chování serializace</span><span class="sxs-lookup"><span data-stu-id="8fbdc-204">Serialization Behaviors</span></span>  
 <span data-ttu-id="8fbdc-205">Dvě chování jsou k dispozici <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> v <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> WCF, a které jsou automaticky zapojeny v závislosti na serializátor u použití pro konkrétní operaci.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-205">Two behaviors are available in WCF, the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> and the <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> that are automatically plugged in depending on which serializer is in use for a particular operation.</span></span> <span data-ttu-id="8fbdc-206">Vzhledem k tomu, že toto chování jsou použity automaticky, obvykle není třeba být vědomi nich.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-206">Because these behaviors are applied automatically, you normally do not have to be aware of them.</span></span>  
  
 <span data-ttu-id="8fbdc-207">Má však `DataContractSerializerOperationBehavior` `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`a `DataContractSurrogate` vlastnosti, které můžete použít k přizpůsobení procesu serializace.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-207">However, the `DataContractSerializerOperationBehavior` has the `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, and `DataContractSurrogate` properties that you may use to customize the serialization process.</span></span> <span data-ttu-id="8fbdc-208">První dvě vlastnosti mají stejný význam jako v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-208">The first two properties have the same meaning as discussed in the previous section.</span></span> <span data-ttu-id="8fbdc-209">Vlastnost můžete `DataContractSurrogate` použít k povolení náhradní smlouvy dat, které jsou výkonný mechanismus pro přizpůsobení a rozšíření procesu serializace.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-209">You can use the `DataContractSurrogate` property to enable data contract surrogates, which are a powerful mechanism for customizing and extending the serialization process.</span></span> <span data-ttu-id="8fbdc-210">Další informace naleznete v [tématu Náhradníkdatové smlouvy](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span><span class="sxs-lookup"><span data-stu-id="8fbdc-210">For more information, see [Data Contract Surrogates](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span></span>  
  
 <span data-ttu-id="8fbdc-211">Serializaci klienta `DataContractSerializerOperationBehavior` i serveru můžete použít k přizpůsobení serializace klienta i serveru.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-211">You can use the `DataContractSerializerOperationBehavior` to customize both client and server serialization.</span></span> <span data-ttu-id="8fbdc-212">Následující příklad ukazuje, jak `MaxItemsInObjectGraph` zvýšit kvótu na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-212">The following example shows how to increase the `MaxItemsInObjectGraph` quota on the client.</span></span>  
  
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
  
<span data-ttu-id="8fbdc-213">Následuje ekvivalentní kód ve službě v případě, že je hostován samostatně:</span><span class="sxs-lookup"><span data-stu-id="8fbdc-213">The following is the equivalent code on the service, in the self-hosted case:</span></span>
  
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
  
 <span data-ttu-id="8fbdc-214">V případě hostované webem je nutné `ServiceHost` vytvořit novou odvozenou třídu a připojit ji pomocí hostitelské továrny služby.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-214">In the Web-hosted case, you must create a new `ServiceHost` derived class and use a service host factory to plug it in.</span></span>  
  
### <a name="controlling-serialization-settings-in-configuration"></a><span data-ttu-id="8fbdc-215">Řízení nastavení serializace v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="8fbdc-215">Controlling Serialization Settings in Configuration</span></span>  
 <span data-ttu-id="8fbdc-216">A `MaxItemsInObjectGraph` `IgnoreExtensionDataObject` lze řídit prostřednictvím konfigurace `dataContractSerializer` pomocí koncového bodu nebo chování služby, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-216">The `MaxItemsInObjectGraph` and `IgnoreExtensionDataObject` can be controlled through configuration by using the `dataContractSerializer` endpoint or service behavior, as shown in the following example.</span></span>  
  
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
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a><span data-ttu-id="8fbdc-217">Serializace sdíleného typu, zachování objektového grafu a vlastní serializátory</span><span class="sxs-lookup"><span data-stu-id="8fbdc-217">Shared Type Serialization, Object Graph Preservation, and Custom Serializers</span></span>  
 <span data-ttu-id="8fbdc-218">Serializuje <xref:System.Runtime.Serialization.DataContractSerializer> pomocí názvů datových smluv a nikoli názvů typů .NET.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-218">The <xref:System.Runtime.Serialization.DataContractSerializer> serializes using data contract names and not .NET type names.</span></span> <span data-ttu-id="8fbdc-219">To je v souladu s principy architektury orientované na služby a umožňuje velkou míru flexibility – typy .NET se mohou změnit bez ovlivnění smlouvy o drátu.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-219">This is consistent with service-oriented architecture tenets and allows for a great degree of flexibility—the .NET types can change without affecting the wire contract.</span></span> <span data-ttu-id="8fbdc-220">Ve výjimečných případech můžete chtít serializovat skutečné názvy typů .NET, a tím zavést těsné párování mezi klientem a serverem, podobně jako technologie vzdálené komunikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-220">In rare cases, you may want to serialize actual .NET type names, thereby introducing a tight coupling between the client and the server, similar to the .NET Framework remoting technology.</span></span> <span data-ttu-id="8fbdc-221">Toto není doporučená praxe, s výjimkou ve výjimečných případech, které se obvykle vyskytují při migraci do WCF z rozhraní .NET Framework vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-221">This is not a recommended practice, except in rare cases that usually occur when migrating to WCF from .NET Framework remoting.</span></span> <span data-ttu-id="8fbdc-222">V takovém případě je <xref:System.Runtime.Serialization.NetDataContractSerializer> nutné použít <xref:System.Runtime.Serialization.DataContractSerializer> třídu namísto třídy.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-222">In this case, you must use the <xref:System.Runtime.Serialization.NetDataContractSerializer> class instead of the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 <span data-ttu-id="8fbdc-223">Obvykle <xref:System.Runtime.Serialization.DataContractSerializer> serializuje objektgrafy jako stromy objektů.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-223">The <xref:System.Runtime.Serialization.DataContractSerializer> normally serializes object graphs as object trees.</span></span> <span data-ttu-id="8fbdc-224">To znamená, že pokud stejný objekt je označována více než jednou, je serializován více než jednou.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-224">That is, if the same object is referred to more than once, it is serialized more than once.</span></span> <span data-ttu-id="8fbdc-225">Zvažte například `PurchaseOrder` instanci, která má `billTo` `shipTo`dvě pole typu Adresa s názvem a .</span><span class="sxs-lookup"><span data-stu-id="8fbdc-225">For example, consider a `PurchaseOrder` instance that has two fields of type Address called `billTo` and `shipTo`.</span></span> <span data-ttu-id="8fbdc-226">Pokud jsou obě pole nastavena na stejnou instanci Address, existují dvě identické instance adresy po serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-226">If both fields are set to the same Address instance, there are two identical Address instances after serialization and deserialization.</span></span> <span data-ttu-id="8fbdc-227">Důvodem je, že neexistuje žádný standardní interoperabilní způsob, jak reprezentovat objektové grafy <xref:System.Xml.Serialization.XmlSerializer>v XML (s výjimkou `Style` staršího standardu kódovaného SOAP, který je k dispozici v oblasti , jak je popsáno v předchozí části dne a). `Use`</span><span class="sxs-lookup"><span data-stu-id="8fbdc-227">This is done because there is no standard interoperable way to represent object graphs in XML (except for the legacy SOAP encoded standard available on the <xref:System.Xml.Serialization.XmlSerializer>, as described in the previous section on `Style` and `Use`).</span></span> <span data-ttu-id="8fbdc-228">Serializace objektových grafů jako stromy má určité nevýhody, například grafy s cyklické odkazy nelze serializovat.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-228">Serializing object graphs as trees has certain disadvantages, for example, graphs with circular references cannot be serialized.</span></span> <span data-ttu-id="8fbdc-229">V některých případě je nutné přepnout na serializaci grafu true objektu, i když není interoperabilní.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-229">Occasionally, it is necessary to switch to true object graph serialization, even though it is not interoperable.</span></span> <span data-ttu-id="8fbdc-230">To lze provést pomocí <xref:System.Runtime.Serialization.DataContractSerializer> konstruované `preserveObjectReferences` s parametrem nastaveným na `true`.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-230">This can be done by using the <xref:System.Runtime.Serialization.DataContractSerializer> constructed with the `preserveObjectReferences` parameter set to `true`.</span></span>  
  
 <span data-ttu-id="8fbdc-231">V některých případech předdefinované serializátory nestačí pro váš scénář.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-231">Occasionally, the built-in serializers are not enough for your scenario.</span></span> <span data-ttu-id="8fbdc-232">Ve většině případů můžete stále <xref:System.Runtime.Serialization.XmlObjectSerializer> použít abstrakce, ze kterého ataka <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.NetDataContractSerializer> odvodit.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-232">In most cases, you can still use the <xref:System.Runtime.Serialization.XmlObjectSerializer> abstraction from which both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Runtime.Serialization.NetDataContractSerializer> derive.</span></span>  
  
 <span data-ttu-id="8fbdc-233">Předchozí tři případy (zachování typu.NET, zachování grafu `XmlObjectSerializer`objektu a zcela vlastní serializace) vyžadují připojení vlastního serializátoru.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-233">The previous three cases (.NET type preservation, object graph preservation, and completely custom `XmlObjectSerializer`-based serialization) all require a custom serializer be plugged in.</span></span> <span data-ttu-id="8fbdc-234">Postupujte při tom podle následujících pokynů:</span><span class="sxs-lookup"><span data-stu-id="8fbdc-234">To do this, perform the following steps:</span></span>  
  
1. <span data-ttu-id="8fbdc-235">Napište své vlastní chování vyplývající <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>z .</span><span class="sxs-lookup"><span data-stu-id="8fbdc-235">Write your own behavior deriving from the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span></span>  
  
2. <span data-ttu-id="8fbdc-236">Přepište dvě `CreateSerializer` metody vrátit <xref:System.Runtime.Serialization.NetDataContractSerializer>vlastní serializátor <xref:System.Runtime.Serialization.DataContractSerializer> (buď , s `preserveObjectReferences` nastavena na `true`, nebo vlastní ). <xref:System.Runtime.Serialization.XmlObjectSerializer></span><span class="sxs-lookup"><span data-stu-id="8fbdc-236">Override the two `CreateSerializer` methods to return your own serializer (either the <xref:System.Runtime.Serialization.NetDataContractSerializer>, the <xref:System.Runtime.Serialization.DataContractSerializer> with `preserveObjectReferences` set to `true`, or your own custom <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span></span>  
  
3. <span data-ttu-id="8fbdc-237">Před otevřením hostitele služby nebo vytvořením <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> kanálu klienta odeberte existující chování a připojte vlastní odvozenou třídu, kterou jste vytvořili v předchozích krocích.</span><span class="sxs-lookup"><span data-stu-id="8fbdc-237">Before opening the service host or creating a client channel, remove the existing <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> behavior and plug in the custom derived class that you created in the previous steps.</span></span>  
  
 <span data-ttu-id="8fbdc-238">Další informace o pokročilých konceptech serializace naleznete [v tématu Serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="8fbdc-238">For more information about advanced serialization concepts, see [Serialization and Deserialization](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fbdc-239">Viz také</span><span class="sxs-lookup"><span data-stu-id="8fbdc-239">See also</span></span>

- [<span data-ttu-id="8fbdc-240">Používání třídy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="8fbdc-240">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)
- [<span data-ttu-id="8fbdc-241">Postupy: Povolení streamování</span><span class="sxs-lookup"><span data-stu-id="8fbdc-241">How to: Enable Streaming</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
- [<span data-ttu-id="8fbdc-242">Postupy: Vytvoření základního kontraktu dat pro třídu nebo strukturu</span><span class="sxs-lookup"><span data-stu-id="8fbdc-242">How to: Create a Basic Data Contract for a Class or Structure</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
