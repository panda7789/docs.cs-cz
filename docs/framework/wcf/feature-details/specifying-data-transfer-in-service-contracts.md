---
title: Určování přenosu dat v kontraktech služby
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
ms.openlocfilehash: 47544cf74b4fa09fd8ee868ea940ef24a453840e
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834637"
---
# <a name="specifying-data-transfer-in-service-contracts"></a><span data-ttu-id="300b9-102">Určování přenosu dat v kontraktech služby</span><span class="sxs-lookup"><span data-stu-id="300b9-102">Specifying Data Transfer in Service Contracts</span></span>
<span data-ttu-id="300b9-103">Windows Communication Foundation (WCF) si můžete představit jako infrastrukturu zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="300b9-103">The Windows Communication Foundation (WCF) can be thought of as a messaging infrastructure.</span></span> <span data-ttu-id="300b9-104">Operace služby mohou přijímat zprávy, zpracovávat je a odesílat zprávy.</span><span class="sxs-lookup"><span data-stu-id="300b9-104">Service operations can receive messages, process them, and send them messages.</span></span> <span data-ttu-id="300b9-105">Zprávy jsou popsány pomocí kontraktů operací.</span><span class="sxs-lookup"><span data-stu-id="300b9-105">Messages are described using operation contracts.</span></span> <span data-ttu-id="300b9-106">Zvažte například následující kontrakt.</span><span class="sxs-lookup"><span data-stu-id="300b9-106">For example, consider the following contract.</span></span>  
  
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
  
 <span data-ttu-id="300b9-107">V tomto případě `GetAirfare` operace přijímá zprávu s informacemi o `fromCity` a `toCity`a potom vrátí zprávu, která obsahuje číslo.</span><span class="sxs-lookup"><span data-stu-id="300b9-107">Here, the `GetAirfare` operation accepts a message with information about `fromCity` and `toCity`, and then returns a message that contains a number.</span></span>  
  
 <span data-ttu-id="300b9-108">Toto téma popisuje různé způsoby, kterými může kontrakt operace popsat zprávy.</span><span class="sxs-lookup"><span data-stu-id="300b9-108">This topic explains the various ways in which an operation contract can describe messages.</span></span>  
  
## <a name="describing-messages-by-using-parameters"></a><span data-ttu-id="300b9-109">Popis zpráv pomocí parametrů</span><span class="sxs-lookup"><span data-stu-id="300b9-109">Describing Messages by Using Parameters</span></span>  
 <span data-ttu-id="300b9-110">Nejjednodušší způsob, jak popsat zprávu, je použít seznam parametrů a návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="300b9-110">The simplest way to describe a message is to use a parameter list and the return value.</span></span> <span data-ttu-id="300b9-111">V předchozím příkladu byly použity parametry řetězce `fromCity` a `toCity` pro popis zprávy požadavku a návratovou hodnotu typu float byl použit k popisu zprávy s odpovědí.</span><span class="sxs-lookup"><span data-stu-id="300b9-111">In the preceding example, the `fromCity` and `toCity` string parameters were used to describe the request message, and the float return value was used to describe the reply message.</span></span> <span data-ttu-id="300b9-112">Pokud není k dispozici pouze vrácená hodnota k popisu zprávy s odpovědí, lze použít výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="300b9-112">If the return value alone is not enough to describe a reply message, out parameters may be used.</span></span> <span data-ttu-id="300b9-113">Například následující operace má `fromCity` a `toCity` ve zprávě s požadavkem a číslo společně s měnou ve zprávě s odpovědí:</span><span class="sxs-lookup"><span data-stu-id="300b9-113">For example, the following operation has `fromCity` and `toCity` in its request message, and a number together with a currency in its reply message:</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 <span data-ttu-id="300b9-114">Kromě toho můžete použít referenční parametry k vytvoření parametru v rámci požadavku i zprávy s odpovědí.</span><span class="sxs-lookup"><span data-stu-id="300b9-114">Additionally, you may use reference parameters to make a parameter part of both the request and the reply message.</span></span> <span data-ttu-id="300b9-115">Parametry musí být typy, které mohou být serializovány (převedeno do XML).</span><span class="sxs-lookup"><span data-stu-id="300b9-115">The parameters must be of types that can be serialized (converted to XML).</span></span> <span data-ttu-id="300b9-116">Ve výchozím nastavení používá WCF k provedení tohoto převodu komponentu s názvem <xref:System.Runtime.Serialization.DataContractSerializer> třídy.</span><span class="sxs-lookup"><span data-stu-id="300b9-116">By default, WCF uses a component called the <xref:System.Runtime.Serialization.DataContractSerializer> class to perform this conversion.</span></span> <span data-ttu-id="300b9-117">Jsou podporovány nejvíce primitivní typy (například `int`, `string`, `float`a `DateTime`).</span><span class="sxs-lookup"><span data-stu-id="300b9-117">Most primitive types (such as `int`, `string`, `float`, and `DateTime`.) are supported.</span></span> <span data-ttu-id="300b9-118">Uživatelsky definované typy musí mít obvykle kontrakt dat.</span><span class="sxs-lookup"><span data-stu-id="300b9-118">User-defined types must normally have a data contract.</span></span> <span data-ttu-id="300b9-119">Další informace najdete v tématu [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="300b9-119">For more information, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
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
  
 <span data-ttu-id="300b9-120">V některých případech je `DataContractSerializer` nevhodný k serializaci vašich typů.</span><span class="sxs-lookup"><span data-stu-id="300b9-120">Occasionally, the `DataContractSerializer` is not adequate to serialize your types.</span></span> <span data-ttu-id="300b9-121">WCF podporuje alternativní Serializační modul, <xref:System.Xml.Serialization.XmlSerializer>, který můžete použít také k serializaci parametrů.</span><span class="sxs-lookup"><span data-stu-id="300b9-121">WCF supports an alternative serialization engine, the <xref:System.Xml.Serialization.XmlSerializer>, which you can also use to serialize parameters.</span></span> <span data-ttu-id="300b9-122"><xref:System.Xml.Serialization.XmlSerializer> umožňuje použít větší kontrolu nad výsledným XML pomocí atributů, jako je `XmlAttributeAttribute`.</span><span class="sxs-lookup"><span data-stu-id="300b9-122">The <xref:System.Xml.Serialization.XmlSerializer> allows you to use more control over the resultant XML using attributes such as the `XmlAttributeAttribute`.</span></span> <span data-ttu-id="300b9-123">Chcete-li přepnout na použití <xref:System.Xml.Serialization.XmlSerializer> pro určitou operaci nebo pro celou službu, použijte atribut <xref:System.ServiceModel.XmlSerializerFormatAttribute> na operaci nebo službu.</span><span class="sxs-lookup"><span data-stu-id="300b9-123">To switch to using the <xref:System.Xml.Serialization.XmlSerializer> for a particular operation or for the entire service, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to an operation or a service.</span></span> <span data-ttu-id="300b9-124">Příklad:</span><span class="sxs-lookup"><span data-stu-id="300b9-124">For example:</span></span>  
  
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
  
 <span data-ttu-id="300b9-125">Další informace naleznete v tématu [použití třídy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span><span class="sxs-lookup"><span data-stu-id="300b9-125">For more information, see [Using the XmlSerializer Class](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span></span> <span data-ttu-id="300b9-126">Pamatujte, že ruční přepnutí na <xref:System.Xml.Serialization.XmlSerializer>, jak je znázorněno zde, se nedoporučuje, pokud nemáte konkrétní důvody k tomu, jak je popsáno v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="300b9-126">Remember that manually switching to the <xref:System.Xml.Serialization.XmlSerializer> as shown here is not recommended unless you have specific reasons to do so as detailed in that topic.</span></span>  
  
 <span data-ttu-id="300b9-127">Chcete-li izolovat názvy parametrů rozhraní .NET od názvů kontraktů, můžete použít atribut <xref:System.ServiceModel.MessageParameterAttribute> a k nastavení názvu kontraktu použít vlastnost `Name`.</span><span class="sxs-lookup"><span data-stu-id="300b9-127">To isolate .NET parameter names from contract names, you can use the <xref:System.ServiceModel.MessageParameterAttribute> attribute, and use the `Name` property to set the contract name.</span></span> <span data-ttu-id="300b9-128">Například následující kontrakt operace je stejný jako první příklad v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="300b9-128">For example, the following operation contract is equivalent to the first example in this topic.</span></span>  
  
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
  
## <a name="describing-empty-messages"></a><span data-ttu-id="300b9-129">Popisující prázdné zprávy</span><span class="sxs-lookup"><span data-stu-id="300b9-129">Describing Empty Messages</span></span>  
 <span data-ttu-id="300b9-130">Prázdná zpráva požadavku může být popsána tak, že neobsahuje žádné vstupní ani referenční parametry.</span><span class="sxs-lookup"><span data-stu-id="300b9-130">An empty request message can be described by having no input or reference parameters.</span></span> <span data-ttu-id="300b9-131">Například v C#:</span><span class="sxs-lookup"><span data-stu-id="300b9-131">For example in C#:</span></span>  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 <span data-ttu-id="300b9-132">Například v jazyce VB:</span><span class="sxs-lookup"><span data-stu-id="300b9-132">For example in VB:</span></span>  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 <span data-ttu-id="300b9-133">Prázdná zpráva odpovědi může být popsána s `void` návratový typ a žádné výstupní ani referenční parametry.</span><span class="sxs-lookup"><span data-stu-id="300b9-133">An empty reply message can be described by having a `void` return type and no output or reference parameters.</span></span> <span data-ttu-id="300b9-134">Například v:</span><span class="sxs-lookup"><span data-stu-id="300b9-134">For example in:</span></span>  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 <span data-ttu-id="300b9-135">To se liší od jednosměrné operace, například:</span><span class="sxs-lookup"><span data-stu-id="300b9-135">This is different from a one-way operation, such as:</span></span>  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 <span data-ttu-id="300b9-136">Operace `SetTemperatureStatus` vrátí prázdnou zprávu.</span><span class="sxs-lookup"><span data-stu-id="300b9-136">The `SetTemperatureStatus` operation returns an empty message.</span></span> <span data-ttu-id="300b9-137">Pokud při zpracování vstupní zprávy dojde k problému, může to vrátit chybu.</span><span class="sxs-lookup"><span data-stu-id="300b9-137">It may return a fault instead if there is a problem processing the input message.</span></span> <span data-ttu-id="300b9-138">Operace `SetLightbulbStatus` nevrátí žádnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="300b9-138">The `SetLightbulbStatus` operation returns nothing.</span></span> <span data-ttu-id="300b9-139">Neexistuje žádný způsob, jak sdělit stav chyby z této operace.</span><span class="sxs-lookup"><span data-stu-id="300b9-139">There is no way to communicate a fault condition from this operation.</span></span>  
  
## <a name="describing-messages-by-using-message-contracts"></a><span data-ttu-id="300b9-140">Popis zpráv pomocí kontraktů zpráv</span><span class="sxs-lookup"><span data-stu-id="300b9-140">Describing Messages by Using Message Contracts</span></span>  
 <span data-ttu-id="300b9-141">Můžete použít jeden typ pro reprezentaci celé zprávy.</span><span class="sxs-lookup"><span data-stu-id="300b9-141">You may want to use a single type to represent the entire message.</span></span> <span data-ttu-id="300b9-142">I když je možné pro tento účel použít kontrakt dat, doporučuje se to použít k tomu, abyste se vyhnuli zbytečným úrovním balení ve výsledném XML.</span><span class="sxs-lookup"><span data-stu-id="300b9-142">While it is possible to use a data contract for this purpose, the recommended way to do this is to use a message contract—this avoids unnecessary levels of wrapping in the resultant XML.</span></span> <span data-ttu-id="300b9-143">Kontrakty zpráv navíc umožňují lepší kontrolu nad výslednými zprávami.</span><span class="sxs-lookup"><span data-stu-id="300b9-143">Additionally, message contracts allow you to exercise more control over resultant messages.</span></span> <span data-ttu-id="300b9-144">Například se můžete rozhodnout, jaké informace by měly být v textu zprávy a které by měly být v záhlavích zpráv.</span><span class="sxs-lookup"><span data-stu-id="300b9-144">For instance, you can decide which pieces of information should be in the message body and which should be in the message headers.</span></span> <span data-ttu-id="300b9-145">Následující příklad ukazuje použití kontraktů zpráv.</span><span class="sxs-lookup"><span data-stu-id="300b9-145">The following example shows the use of message contracts.</span></span>  
  
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
  
 <span data-ttu-id="300b9-146">Další informace najdete v tématu [Použití kontraktů zpráv](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="300b9-146">For more information, see [Using Message Contracts](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span></span>  
  
 <span data-ttu-id="300b9-147">V předchozím příkladu je třída <xref:System.Runtime.Serialization.DataContractSerializer> ve výchozím nastavení stále používána.</span><span class="sxs-lookup"><span data-stu-id="300b9-147">In the previous example, the <xref:System.Runtime.Serialization.DataContractSerializer> class is still used by default.</span></span> <span data-ttu-id="300b9-148">Třídu <xref:System.Xml.Serialization.XmlSerializer> lze také použít se kontrakty zpráv.</span><span class="sxs-lookup"><span data-stu-id="300b9-148">The <xref:System.Xml.Serialization.XmlSerializer> class can also be used with message contracts.</span></span> <span data-ttu-id="300b9-149">Chcete-li to provést, použijte atribut <xref:System.ServiceModel.XmlSerializerFormatAttribute> buď na operaci, nebo na kontrakt a použijte typy kompatibilní s třídou <xref:System.Xml.Serialization.XmlSerializer> v záhlaví a v těle zprávy.</span><span class="sxs-lookup"><span data-stu-id="300b9-149">To do this, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to either the operation or the contract, and use types compatible with the <xref:System.Xml.Serialization.XmlSerializer> class in the message headers and body members.</span></span>  
  
## <a name="describing-messages-by-using-streams"></a><span data-ttu-id="300b9-150">Popis zpráv pomocí datových proudů</span><span class="sxs-lookup"><span data-stu-id="300b9-150">Describing Messages by Using Streams</span></span>  
 <span data-ttu-id="300b9-151">Dalším způsobem, jak popsat zprávy v rámci operací, je použít třídu <xref:System.IO.Stream> nebo jednu z jejích odvozených tříd v kontraktu operace nebo jako člena těla zprávy (musí se jednat o jediného člena v tomto případě).</span><span class="sxs-lookup"><span data-stu-id="300b9-151">Another way to describe messages in operations is to use the <xref:System.IO.Stream> class or one of its derived classes in an operation contract or as a message contract body member (it must be the only member in this case).</span></span> <span data-ttu-id="300b9-152">U příchozích zpráv musí být typ `Stream`– nemůžete použít odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="300b9-152">For incoming messages, the type must be `Stream`—you cannot use derived classes.</span></span>  
  
 <span data-ttu-id="300b9-153">Místo vyvolání serializátoru načte WCF Data z datového proudu a převede ho přímo do odchozí zprávy, nebo načte data z příchozí zprávy a převede je přímo do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="300b9-153">Instead of invoking the serializer, WCF retrieves data from a stream and puts it directly into an outgoing message, or retrieves data from an incoming message and puts it directly into a stream.</span></span> <span data-ttu-id="300b9-154">Následující příklad ukazuje použití datových proudů.</span><span class="sxs-lookup"><span data-stu-id="300b9-154">The following sample shows the use of streams.</span></span>  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 <span data-ttu-id="300b9-155">V těle jedné zprávy nelze kombinovat `Stream` a nestreamovaná data.</span><span class="sxs-lookup"><span data-stu-id="300b9-155">You cannot combine `Stream` and non-stream data in a single message body.</span></span> <span data-ttu-id="300b9-156">Pomocí kontraktu zprávy umístěte další data do záhlaví zpráv.</span><span class="sxs-lookup"><span data-stu-id="300b9-156">Use a message contract to put the extra data in message headers.</span></span> <span data-ttu-id="300b9-157">Následující příklad ukazuje nesprávné použití datových proudů při definování kontraktu operace.</span><span class="sxs-lookup"><span data-stu-id="300b9-157">The following example shows the incorrect usage of streams when defining the operation contract.</span></span>  
  
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
  
 <span data-ttu-id="300b9-158">Následující příklad ukazuje správné použití datových proudů při definování kontraktu operace.</span><span class="sxs-lookup"><span data-stu-id="300b9-158">The following sample shows the correct usage of streams when defining an operation contract.</span></span>  
  
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
  
 <span data-ttu-id="300b9-159">Další informace najdete v tématu [velké objemy dat a streamování](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span><span class="sxs-lookup"><span data-stu-id="300b9-159">For more information, see [Large Data and Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="using-the-message-class"></a><span data-ttu-id="300b9-160">Používání třídy Message</span><span class="sxs-lookup"><span data-stu-id="300b9-160">Using the Message Class</span></span>  
 <span data-ttu-id="300b9-161">Chcete-li mít úplnou programovou kontrolu nad odeslanými nebo přijímanými zprávami, můžete použít třídu <xref:System.ServiceModel.Channels.Message> přímo, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="300b9-161">To have complete programmatic control over messages sent or received, you can use the <xref:System.ServiceModel.Channels.Message> class directly, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 <span data-ttu-id="300b9-162">Toto je pokročilý scénář, který je podrobně popsán v tématu [použití třídy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span><span class="sxs-lookup"><span data-stu-id="300b9-162">This is an advanced scenario, which is described in detail in [Using the Message Class](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span></span>  
  
## <a name="describing-fault-messages"></a><span data-ttu-id="300b9-163">Popisující chybové zprávy</span><span class="sxs-lookup"><span data-stu-id="300b9-163">Describing Fault Messages</span></span>  
 <span data-ttu-id="300b9-164">Kromě zpráv popsaných návratovou hodnotou a výstupním parametrem nebo referenčními parametry může jakákoliv operace, která není jednosměrná, vracet alespoň dvě možné zprávy: jeho obvyklá zpráva odpovědi a chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="300b9-164">In addition to the messages that are described by the return value and output or reference parameters, any operation that is not one-way can return at least two possible messages: its normal response message and a fault message.</span></span> <span data-ttu-id="300b9-165">Vezměte v úvahu následující kontrakt operace.</span><span class="sxs-lookup"><span data-stu-id="300b9-165">Consider the following operation contract.</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 <span data-ttu-id="300b9-166">Tato operace může buď vracet normální zprávu obsahující `float` číslo, nebo chybovou zprávu, která obsahuje kód chyby a popis.</span><span class="sxs-lookup"><span data-stu-id="300b9-166">This operation may either return a normal message that contains a `float` number, or a fault message that contains a fault code and a description.</span></span> <span data-ttu-id="300b9-167">To můžete provést vyvoláním <xref:System.ServiceModel.FaultException> v implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="300b9-167">You can accomplish this by throwing a <xref:System.ServiceModel.FaultException> in your service implementation.</span></span>  
  
 <span data-ttu-id="300b9-168">Pomocí atributu <xref:System.ServiceModel.FaultContractAttribute> můžete určit další možné zprávy o chybách.</span><span class="sxs-lookup"><span data-stu-id="300b9-168">You can specify additional possible fault messages by using the <xref:System.ServiceModel.FaultContractAttribute> attribute.</span></span> <span data-ttu-id="300b9-169">Další chyby musí být serializovatelný pomocí <xref:System.Runtime.Serialization.DataContractSerializer>, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="300b9-169">The additional faults must be serializable using the <xref:System.Runtime.Serialization.DataContractSerializer>, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="300b9-170">Tyto další chyby mohou být vygenerovány vyvoláním <xref:System.ServiceModel.FaultException%601> příslušného typu kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="300b9-170">These additional faults can be generated by throwing a <xref:System.ServiceModel.FaultException%601> of the appropriate data contract type.</span></span> <span data-ttu-id="300b9-171">Další informace najdete v tématu [zpracování výjimek a chyb](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span><span class="sxs-lookup"><span data-stu-id="300b9-171">For more information, see [Handling Exceptions and Faults](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span></span>  
  
 <span data-ttu-id="300b9-172">Třídu <xref:System.Xml.Serialization.XmlSerializer> nelze použít k popisu chyb.</span><span class="sxs-lookup"><span data-stu-id="300b9-172">You cannot use the <xref:System.Xml.Serialization.XmlSerializer> class to describe faults.</span></span> <span data-ttu-id="300b9-173"><xref:System.ServiceModel.XmlSerializerFormatAttribute> nemá žádný vliv na smlouvy o selhání.</span><span class="sxs-lookup"><span data-stu-id="300b9-173">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> has no effect on fault contracts.</span></span>  
  
## <a name="using-derived-types"></a><span data-ttu-id="300b9-174">Použití odvozených typů</span><span class="sxs-lookup"><span data-stu-id="300b9-174">Using Derived Types</span></span>  
 <span data-ttu-id="300b9-175">Můžete chtít použít základní typ v operaci nebo kontraktu zprávy a potom použít odvozený typ při skutečném vyvolání operace.</span><span class="sxs-lookup"><span data-stu-id="300b9-175">You may want to use a base type in an operation or a message contract, and then use a derived type when actually invoking the operation.</span></span> <span data-ttu-id="300b9-176">V tomto případě je nutné použít buď atribut <xref:System.ServiceModel.ServiceKnownTypeAttribute>, nebo nějaký alternativní mechanismus pro povolení použití odvozených typů.</span><span class="sxs-lookup"><span data-stu-id="300b9-176">In this case, you must use either the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute or some alternative mechanism to allow the use of derived types.</span></span> <span data-ttu-id="300b9-177">Zvažte následující operaci.</span><span class="sxs-lookup"><span data-stu-id="300b9-177">Consider the following operation.</span></span>  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 <span data-ttu-id="300b9-178">Předpokládá, že dva typy, `Book` a `Magazine`, jsou odvozeny z `LibraryItem`.</span><span class="sxs-lookup"><span data-stu-id="300b9-178">Assume that two types, `Book` and `Magazine`, derive from `LibraryItem`.</span></span> <span data-ttu-id="300b9-179">Chcete-li použít tyto typy v operaci `IsLibraryItemAvailable`, můžete operaci změnit následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="300b9-179">To use these types in the `IsLibraryItemAvailable` operation, you can change the operation as follows:</span></span>  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 <span data-ttu-id="300b9-180">Alternativně můžete použít atribut <xref:System.Runtime.Serialization.KnownTypeAttribute>, pokud je použit výchozí <xref:System.Runtime.Serialization.DataContractSerializer>, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="300b9-180">Alternatively, you can use the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute when the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="300b9-181">Atribut <xref:System.Xml.Serialization.XmlIncludeAttribute> lze použít při použití <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="300b9-181">You can use the <xref:System.Xml.Serialization.XmlIncludeAttribute> attribute when using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
 <span data-ttu-id="300b9-182">Můžete použít atribut <xref:System.ServiceModel.ServiceKnownTypeAttribute> na operaci nebo na celou službu.</span><span class="sxs-lookup"><span data-stu-id="300b9-182">You can apply the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute to an operation or to the entire service.</span></span> <span data-ttu-id="300b9-183">Přijímá buď typ, nebo název metody, která má být volána, aby získal seznam známých typů, stejně jako atribut <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="300b9-183">It accepts either a type or the name of the method to call to get a list of known types, just like the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span> <span data-ttu-id="300b9-184">Další informace najdete v tématu [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="300b9-184">For more information, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="specifying-the-use-and-style"></a><span data-ttu-id="300b9-185">Určení použití a stylu</span><span class="sxs-lookup"><span data-stu-id="300b9-185">Specifying the Use and Style</span></span>  
 <span data-ttu-id="300b9-186">Při popisu služeb pomocí jazyka WSDL (Web Services Description Language) jsou dva běžně používané styly dokumenty a vzdálené volání procedur (RPC).</span><span class="sxs-lookup"><span data-stu-id="300b9-186">When describing services using Web Services Description Language (WSDL), the two commonly used styles are Document and remote procedure call (RPC).</span></span> <span data-ttu-id="300b9-187">Ve stylu dokumentu je celý text zprávy popsán pomocí schématu a WSDL popisuje různé části těla zprávy odkazem na prvky v tomto schématu.</span><span class="sxs-lookup"><span data-stu-id="300b9-187">In the Document style, the entire message body is described using the schema, and the WSDL describes the various message body parts by referring to elements within that schema.</span></span> <span data-ttu-id="300b9-188">Ve stylu RPC odkazuje WSDL na typ schématu pro každou část zprávy, nikoli na element.</span><span class="sxs-lookup"><span data-stu-id="300b9-188">In the RPC style, the WSDL refers to a schema type for each message part rather than an element.</span></span> <span data-ttu-id="300b9-189">V některých případech je nutné ručně vybrat jeden z těchto stylů.</span><span class="sxs-lookup"><span data-stu-id="300b9-189">In some cases, you have to manually select one of these styles.</span></span> <span data-ttu-id="300b9-190">To lze provést použitím atributu <xref:System.ServiceModel.DataContractFormatAttribute> a nastavením vlastnosti `Style` (Pokud se <xref:System.Runtime.Serialization.DataContractSerializer> používá), nebo nastavením `Style` atributu <xref:System.ServiceModel.XmlSerializerFormatAttribute> (při použití <xref:System.Xml.Serialization.XmlSerializer>).</span><span class="sxs-lookup"><span data-stu-id="300b9-190">You can do this by applying the <xref:System.ServiceModel.DataContractFormatAttribute> attribute and setting the `Style` property (when the <xref:System.Runtime.Serialization.DataContractSerializer> is in use), or by setting `Style` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute (when using the <xref:System.Xml.Serialization.XmlSerializer>).</span></span>  
  
 <span data-ttu-id="300b9-191">Kromě toho <xref:System.Xml.Serialization.XmlSerializer> podporuje dva formy serializovaného XML: `Literal` a `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="300b9-191">Additionally, the <xref:System.Xml.Serialization.XmlSerializer> supports two forms of serialized XML: `Literal` and `Encoded`.</span></span> <span data-ttu-id="300b9-192">`Literal` je nejčastěji přijatý formulář, který je jediným formulářem, který <xref:System.Runtime.Serialization.DataContractSerializer> podporuje.</span><span class="sxs-lookup"><span data-stu-id="300b9-192">`Literal` is the most commonly accepted form, and is the only form the <xref:System.Runtime.Serialization.DataContractSerializer> supports.</span></span> <span data-ttu-id="300b9-193">`Encoded` je starší verze formuláře popsané v části 5 specifikace protokolu SOAP a nedoporučuje se pro nové služby.</span><span class="sxs-lookup"><span data-stu-id="300b9-193">`Encoded` is a legacy form described in section 5 of the SOAP specification, and is not recommended for new services.</span></span> <span data-ttu-id="300b9-194">Chcete-li přepnout do režimu `Encoded`, nastavte vlastnost `Use` atributu <xref:System.ServiceModel.XmlSerializerFormatAttribute> na `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="300b9-194">To switch to `Encoded` mode, set the `Use` property on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to `Encoded`.</span></span>  
  
 <span data-ttu-id="300b9-195">Ve většině případů byste neměli měnit výchozí nastavení `Style` a `Use` vlastností.</span><span class="sxs-lookup"><span data-stu-id="300b9-195">In most cases, you should not change the default settings for the `Style` and `Use` properties.</span></span>  
  
## <a name="controlling-the-serialization-process"></a><span data-ttu-id="300b9-196">Řízení procesu serializace</span><span class="sxs-lookup"><span data-stu-id="300b9-196">Controlling the Serialization Process</span></span>  
 <span data-ttu-id="300b9-197">K přizpůsobení způsobu serializace dat můžete provést několik věcí.</span><span class="sxs-lookup"><span data-stu-id="300b9-197">You can do a number of things to customize the way data is serialized.</span></span>  
  
### <a name="changing-server-serialization-settings"></a><span data-ttu-id="300b9-198">Mění se nastavení serializace serveru.</span><span class="sxs-lookup"><span data-stu-id="300b9-198">Changing Server Serialization Settings</span></span>  
 <span data-ttu-id="300b9-199">Pokud se používá výchozí <xref:System.Runtime.Serialization.DataContractSerializer>, můžete určit některé aspekty procesu serializace ve službě použitím atributu <xref:System.ServiceModel.ServiceBehaviorAttribute> na službu.</span><span class="sxs-lookup"><span data-stu-id="300b9-199">When the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, you can control some aspects of the serialization process on the service by applying the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the service.</span></span> <span data-ttu-id="300b9-200">Konkrétně můžete pomocí vlastnosti `MaxItemsInObjectGraph` nastavit kvótu, která omezuje maximální počet objektů, které <xref:System.Runtime.Serialization.DataContractSerializer> deserializace.</span><span class="sxs-lookup"><span data-stu-id="300b9-200">Specifically, you may use the `MaxItemsInObjectGraph` property to set the quota that limits the maximum number of objects the <xref:System.Runtime.Serialization.DataContractSerializer> deserializes.</span></span> <span data-ttu-id="300b9-201">Pomocí vlastnosti `IgnoreExtensionDataObject` můžete vypnout funkci verze Round-Trip.</span><span class="sxs-lookup"><span data-stu-id="300b9-201">You can use the `IgnoreExtensionDataObject` property to turn off the round-tripping versioning feature.</span></span> <span data-ttu-id="300b9-202">Další informace o kvótách najdete v tématu věnovaném [bezpečnostním hlediskům pro data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span><span class="sxs-lookup"><span data-stu-id="300b9-202">For more information about quotas, see [Security Considerations for Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span></span> <span data-ttu-id="300b9-203">Další informace o kulatých Trip najdete v článku [kontrakty dat kompatibilní s dopředně](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="300b9-203">For more information about round-tripping, see [Forward-Compatible Data Contracts](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span></span>  
  
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
  
### <a name="serialization-behaviors"></a><span data-ttu-id="300b9-204">Chování serializace</span><span class="sxs-lookup"><span data-stu-id="300b9-204">Serialization Behaviors</span></span>  
 <span data-ttu-id="300b9-205">Ve službě WCF jsou k dispozici dvě chování, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> a <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>, která jsou automaticky zapojená v závislosti na tom, který serializátor se používá pro určitou operaci.</span><span class="sxs-lookup"><span data-stu-id="300b9-205">Two behaviors are available in WCF, the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> and the <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> that are automatically plugged in depending on which serializer is in use for a particular operation.</span></span> <span data-ttu-id="300b9-206">Vzhledem k tomu, že se toto chování aplikuje automaticky, obvykle je nemusíte znát.</span><span class="sxs-lookup"><span data-stu-id="300b9-206">Because these behaviors are applied automatically, you normally do not have to be aware of them.</span></span>  
  
 <span data-ttu-id="300b9-207">`DataContractSerializerOperationBehavior` však obsahuje vlastnosti `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`a `DataContractSurrogate`, které lze použít k přizpůsobení procesu serializace.</span><span class="sxs-lookup"><span data-stu-id="300b9-207">However, the `DataContractSerializerOperationBehavior` has the `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, and `DataContractSurrogate` properties that you may use to customize the serialization process.</span></span> <span data-ttu-id="300b9-208">První dvě vlastnosti mají stejný význam, jak je popsáno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="300b9-208">The first two properties have the same meaning as discussed in the previous section.</span></span> <span data-ttu-id="300b9-209">Pomocí vlastnosti `DataContractSurrogate` můžete povolit náhrady kontraktů dat, což jsou účinný mechanismus pro přizpůsobení a rozšíření procesu serializace.</span><span class="sxs-lookup"><span data-stu-id="300b9-209">You can use the `DataContractSurrogate` property to enable data contract surrogates, which are a powerful mechanism for customizing and extending the serialization process.</span></span> <span data-ttu-id="300b9-210">Další informace najdete v tématu [náhrada za kontrakty dat](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span><span class="sxs-lookup"><span data-stu-id="300b9-210">For more information, see [Data Contract Surrogates](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span></span>  
  
 <span data-ttu-id="300b9-211">K přizpůsobení serializace klienta i serveru můžete použít `DataContractSerializerOperationBehavior`.</span><span class="sxs-lookup"><span data-stu-id="300b9-211">You can use the `DataContractSerializerOperationBehavior` to customize both client and server serialization.</span></span> <span data-ttu-id="300b9-212">Následující příklad ukazuje, jak zvýšit kvótu `MaxItemsInObjectGraph` klienta.</span><span class="sxs-lookup"><span data-stu-id="300b9-212">The following example shows how to increase the `MaxItemsInObjectGraph` quota on the client.</span></span>  
  
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
  
<span data-ttu-id="300b9-213">Toto je ekvivalentní kód ve službě v případě v místním prostředí:</span><span class="sxs-lookup"><span data-stu-id="300b9-213">The following is the equivalent code on the service, in the self-hosted case:</span></span>
  
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
  
 <span data-ttu-id="300b9-214">V případě hostování webu je nutné vytvořit novou `ServiceHost` odvozenou třídu a použít továrnu hostitele služby k jejímu připojení.</span><span class="sxs-lookup"><span data-stu-id="300b9-214">In the Web-hosted case, you must create a new `ServiceHost` derived class and use a service host factory to plug it in.</span></span>  
  
### <a name="controlling-serialization-settings-in-configuration"></a><span data-ttu-id="300b9-215">Řízení nastavení serializace v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="300b9-215">Controlling Serialization Settings in Configuration</span></span>  
 <span data-ttu-id="300b9-216">`MaxItemsInObjectGraph` a `IgnoreExtensionDataObject` je možné řídit pomocí konfigurace pomocí `dataContractSerializer`ho koncového bodu nebo služby, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="300b9-216">The `MaxItemsInObjectGraph` and `IgnoreExtensionDataObject` can be controlled through configuration by using the `dataContractSerializer` endpoint or service behavior, as shown in the following example.</span></span>  
  
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
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a><span data-ttu-id="300b9-217">Serializace sdíleného typu, zachování grafu objektů a vlastní serializace</span><span class="sxs-lookup"><span data-stu-id="300b9-217">Shared Type Serialization, Object Graph Preservation, and Custom Serializers</span></span>  
 <span data-ttu-id="300b9-218"><xref:System.Runtime.Serialization.DataContractSerializer> serializace pomocí názvů kontraktů dat, nikoli názvů typů .NET.</span><span class="sxs-lookup"><span data-stu-id="300b9-218">The <xref:System.Runtime.Serialization.DataContractSerializer> serializes using data contract names and not .NET type names.</span></span> <span data-ttu-id="300b9-219">To je konzistentní s architekturou principy orientované na služby a umožňuje skvělou flexibilitu – typy .NET se můžou měnit bez ovlivnění kontraktu v rámci vedení.</span><span class="sxs-lookup"><span data-stu-id="300b9-219">This is consistent with service-oriented architecture tenets and allows for a great degree of flexibility—the .NET types can change without affecting the wire contract.</span></span> <span data-ttu-id="300b9-220">Ve výjimečných případech možná budete chtít serializovat skutečné názvy typů .NET, čímž zavedete těsné spojení mezi klientem a serverem, podobně jako technologie vzdálené komunikace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="300b9-220">In rare cases, you may want to serialize actual .NET type names, thereby introducing a tight coupling between the client and the server, similar to the .NET Framework remoting technology.</span></span> <span data-ttu-id="300b9-221">Nejedná se o doporučený postup, s výjimkou případů, kdy se při migraci na WCF z .NET Framework vzdálené komunikace obvykle objevuje.</span><span class="sxs-lookup"><span data-stu-id="300b9-221">This is not a recommended practice, except in rare cases that usually occur when migrating to WCF from .NET Framework remoting.</span></span> <span data-ttu-id="300b9-222">V takovém případě je nutné místo <xref:System.Runtime.Serialization.DataContractSerializer> třídy použít třídu <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="300b9-222">In this case, you must use the <xref:System.Runtime.Serialization.NetDataContractSerializer> class instead of the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 <span data-ttu-id="300b9-223"><xref:System.Runtime.Serialization.DataContractSerializer> obvykle serializace grafy objektů jako stromy objektů.</span><span class="sxs-lookup"><span data-stu-id="300b9-223">The <xref:System.Runtime.Serialization.DataContractSerializer> normally serializes object graphs as object trees.</span></span> <span data-ttu-id="300b9-224">To znamená, že pokud je stejný objekt odkazován více než jednou, je serializován více než jednou.</span><span class="sxs-lookup"><span data-stu-id="300b9-224">That is, if the same object is referred to more than once, it is serialized more than once.</span></span> <span data-ttu-id="300b9-225">Představte si například `PurchaseOrder` instanci, která má dvě pole typu Address nazvané `billTo` a `shipTo`.</span><span class="sxs-lookup"><span data-stu-id="300b9-225">For example, consider a `PurchaseOrder` instance that has two fields of type Address called `billTo` and `shipTo`.</span></span> <span data-ttu-id="300b9-226">Pokud jsou obě pole nastavena na stejnou instanci adresy, existují dvě stejné instance adres po serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="300b9-226">If both fields are set to the same Address instance, there are two identical Address instances after serialization and deserialization.</span></span> <span data-ttu-id="300b9-227">K tomu dochází, protože neexistuje žádný standardní způsob, jak znázornit grafy objektů v XML (s výjimkou standardně dostupného standardu SOAP kódovaného v <xref:System.Xml.Serialization.XmlSerializer>, jak je popsáno v předchozí části `Style` a `Use`).</span><span class="sxs-lookup"><span data-stu-id="300b9-227">This is done because there is no standard interoperable way to represent object graphs in XML (except for the legacy SOAP encoded standard available on the <xref:System.Xml.Serialization.XmlSerializer>, as described in the previous section on `Style` and `Use`).</span></span> <span data-ttu-id="300b9-228">Serializace grafů objektů jako stromů má určité nevýhody, například grafy s cyklickými odkazy nemohou být serializovány.</span><span class="sxs-lookup"><span data-stu-id="300b9-228">Serializing object graphs as trees has certain disadvantages, for example, graphs with circular references cannot be serialized.</span></span> <span data-ttu-id="300b9-229">V některých případech je nutné přepnout na skutečnou serializaci grafu objektů, i když není interoperabilní.</span><span class="sxs-lookup"><span data-stu-id="300b9-229">Occasionally, it is necessary to switch to true object graph serialization, even though it is not interoperable.</span></span> <span data-ttu-id="300b9-230">To lze provést pomocí <xref:System.Runtime.Serialization.DataContractSerializer> vytvořené s parametrem `preserveObjectReferences` nastaveným na `true`.</span><span class="sxs-lookup"><span data-stu-id="300b9-230">This can be done by using the <xref:System.Runtime.Serialization.DataContractSerializer> constructed with the `preserveObjectReferences` parameter set to `true`.</span></span>  
  
 <span data-ttu-id="300b9-231">V některých případech nejsou předdefinované serializátory pro váš scénář dostatečné.</span><span class="sxs-lookup"><span data-stu-id="300b9-231">Occasionally, the built-in serializers are not enough for your scenario.</span></span> <span data-ttu-id="300b9-232">Ve většině případů můžete stále používat abstrakci <xref:System.Runtime.Serialization.XmlObjectSerializer>, ze které jsou odvozeny <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="300b9-232">In most cases, you can still use the <xref:System.Runtime.Serialization.XmlObjectSerializer> abstraction from which both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Runtime.Serialization.NetDataContractSerializer> derive.</span></span>  
  
 <span data-ttu-id="300b9-233">Předchozí tři případy (zachování typu .NET, zachování grafu objektů a úplné vlastní serializace založené na `XmlObjectSerializer`) vyžadují, aby byl do sítě zapojen vlastní serializátor.</span><span class="sxs-lookup"><span data-stu-id="300b9-233">The previous three cases (.NET type preservation, object graph preservation, and completely custom `XmlObjectSerializer`-based serialization) all require a custom serializer be plugged in.</span></span> <span data-ttu-id="300b9-234">Provedete to provedením následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="300b9-234">To do this, perform the following steps:</span></span>  
  
1. <span data-ttu-id="300b9-235">Pište vlastní chování vyplývající z <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="300b9-235">Write your own behavior deriving from the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span></span>  
  
2. <span data-ttu-id="300b9-236">Přepište dvě `CreateSerializer` metody a vraťte vlastní serializátor (buď <xref:System.Runtime.Serialization.NetDataContractSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer> s `preserveObjectReferences` nastavenou na `true`, nebo na vlastní <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span><span class="sxs-lookup"><span data-stu-id="300b9-236">Override the two `CreateSerializer` methods to return your own serializer (either the <xref:System.Runtime.Serialization.NetDataContractSerializer>, the <xref:System.Runtime.Serialization.DataContractSerializer> with `preserveObjectReferences` set to `true`, or your own custom <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span></span>  
  
3. <span data-ttu-id="300b9-237">Před otevřením hostitele služby nebo vytvořením klientského kanálu odeberte stávající chování <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> a připojte vlastní odvozenou třídu, kterou jste vytvořili v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="300b9-237">Before opening the service host or creating a client channel, remove the existing <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> behavior and plug in the custom derived class that you created in the previous steps.</span></span>  
  
 <span data-ttu-id="300b9-238">Další informace o principech pokročilé serializace naleznete v tématu [serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="300b9-238">For more information about advanced serialization concepts, see [Serialization and Deserialization](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="300b9-239">Viz také:</span><span class="sxs-lookup"><span data-stu-id="300b9-239">See also</span></span>

- [<span data-ttu-id="300b9-240">Používání třídy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="300b9-240">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)
- [<span data-ttu-id="300b9-241">Postupy: Povolení streamování</span><span class="sxs-lookup"><span data-stu-id="300b9-241">How to: Enable Streaming</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
- [<span data-ttu-id="300b9-242">Postupy: Vytvoření základního kontraktu dat pro třídu nebo strukturu</span><span class="sxs-lookup"><span data-stu-id="300b9-242">How to: Create a Basic Data Contract for a Class or Structure</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
