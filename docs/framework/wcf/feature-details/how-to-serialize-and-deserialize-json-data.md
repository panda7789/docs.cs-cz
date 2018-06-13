---
title: 'Postupy: Serializace a deserializace dat protokolu JSON'
ms.date: 03/30/2017
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: f51ffb180adfc8310c91ff3c1ec7b7725f6b8b15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492587"
---
# <a name="how-to-serialize-and-deserialize-json-data"></a><span data-ttu-id="02671-102">Postupy: Serializace a deserializace dat protokolu JSON</span><span class="sxs-lookup"><span data-stu-id="02671-102">How to: Serialize and Deserialize JSON Data</span></span>
<span data-ttu-id="02671-103">JSON (JavaScript Object Notation) je formát kódování efektivní dat, který umožňuje rychlé výměnu malé množství dat mezi prohlížeče klienta a podporou AJAXU webové služby.</span><span class="sxs-lookup"><span data-stu-id="02671-103">JSON (JavaScript Object Notation) is an efficient data encoding format that enables fast exchanges of small amounts of data between client browsers and AJAX-enabled Web services.</span></span>  
  
 <span data-ttu-id="02671-104">Toto téma ukazuje, jak serializovat objekty typu .NET do data zakódovaná ve formátu JSON a jeho následné deserializaci data ve formátu JSON zpět do instance typy .NET pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="02671-104">This topic demonstrates how to serialize .NET type objects into JSON-encoded data and then deserialize data in the JSON format back into instances of .NET types using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="02671-105">Tento příklad používá kontrakt dat k předvedení serializace a deserializace uživatelem definované `Person` typu.</span><span class="sxs-lookup"><span data-stu-id="02671-105">This example uses a data contract to demonstrate serialization and deserialization of a user-defined `Person` type.</span></span>  
  
 <span data-ttu-id="02671-106">Za normálních okolností JSON serializace a deserializace zpracovává automaticky Windows Communication Foundation (WCF) při použití typy kontraktů dat v operace služby, které jsou přístupné přes podporou AJAXU koncové body.</span><span class="sxs-lookup"><span data-stu-id="02671-106">Normally, JSON serialization and deserialization is handled automatically by Windows Communication Foundation (WCF) when you use data contract types in service operations that are exposed over AJAX-enabled endpoints.</span></span> <span data-ttu-id="02671-107">V některých případech, které budete potřebovat k práci s daty JSON přímo – je to ale scénář, který toto téma popisuje.</span><span class="sxs-lookup"><span data-stu-id="02671-107">However, in some cases you may need to work with JSON data directly - this is the scenario that this topic demonstrates.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02671-108">Pokud dojde k chybě během serializace odchozí odpovědi na serveru nebo odpověď operace vyvolá výjimku z jiného důvodu, se nemusí získat vrácen do klienta jako chybu.</span><span class="sxs-lookup"><span data-stu-id="02671-108">If an error occurs during serialization of an outgoing reply on the server or the reply operation throws an exception for some other reason, it may not get returned to the client as a fault.</span></span>  
  
 <span data-ttu-id="02671-109">Toto téma je založena na [serializace JSON](../../../../docs/framework/wcf/samples/json-serialization.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="02671-109">This topic is based on the [JSON Serialization](../../../../docs/framework/wcf/samples/json-serialization.md) sample.</span></span>  
  
### <a name="to-define-the-data-contract-for-a-person"></a><span data-ttu-id="02671-110">Chcete-li definovat kontrakt dat osoby</span><span class="sxs-lookup"><span data-stu-id="02671-110">To define the data contract for a Person</span></span>  
  
1.  <span data-ttu-id="02671-111">Definovat kontrakt dat pro `Person` připojením <xref:System.Runtime.Serialization.DataContractAttribute> k třídě a <xref:System.Runtime.Serialization.DataMemberAttribute> atribut u členů chcete serializovat.</span><span class="sxs-lookup"><span data-stu-id="02671-111">Define the data contract for `Person` by attaching the <xref:System.Runtime.Serialization.DataContractAttribute> to the class and <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the members you want to serialize.</span></span> <span data-ttu-id="02671-112">Další informace o kontraktech dat najdete v tématu [navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="02671-112">For more information about data contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
    ```csharp  
    [DataContract]  
    internal class Person  
    {  
        [DataMember]  
        internal string name;  
  
        [DataMember]  
        internal int age;  
    }  
    ```  
  
### <a name="to-serialize-an-instance-of-type-person-to-json"></a><span data-ttu-id="02671-113">K serializaci instancí typu osoba do formátu JSON</span><span class="sxs-lookup"><span data-stu-id="02671-113">To serialize an instance of type Person to JSON</span></span>  
  
1.  <span data-ttu-id="02671-114">Vytvoření instance `Person` typu.</span><span class="sxs-lookup"><span data-stu-id="02671-114">Create an instance of the `Person` type.</span></span>  
  
    ```csharp  
    Person p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2.  <span data-ttu-id="02671-115">Serializovat `Person` objekt, který má datový proud paměti pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="02671-115">Serialize the `Person` object to a memory stream using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    MemoryStream stream1 = new MemoryStream();  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3.  <span data-ttu-id="02671-116">Použití <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> metoda při zápisu dat JSON do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="02671-116">Use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> method to write JSON data to the stream.</span></span>  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4.  <span data-ttu-id="02671-117">Zobrazit výstup JSON.</span><span class="sxs-lookup"><span data-stu-id="02671-117">Show the JSON output.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    StreamReader sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
### <a name="to-deserialize-an-instance-of-type-person-from-json"></a><span data-ttu-id="02671-118">K deserializaci instance typu osoby z formátu JSON</span><span class="sxs-lookup"><span data-stu-id="02671-118">To deserialize an instance of type Person from JSON</span></span>  
  
1.  <span data-ttu-id="02671-119">Deserializuje data zakódovaná ve formátu JSON do novou instanci třídy `Person` pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> metodu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="02671-119">Deserialize the JSON-encoded data into a new instance of `Person` by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> method of the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    Person p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2.  <span data-ttu-id="02671-120">Zobrazit výsledky.</span><span class="sxs-lookup"><span data-stu-id="02671-120">Show the results.</span></span>  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a><span data-ttu-id="02671-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="02671-121">Example</span></span>  
  
```csharp  
// Create a User object and serialize it to a JSON stream.  
public static string WriteFromObject()  
{  
    //Create User object.  
    User user = new User("Bob", 42);  
  
    //Create a stream to serialize the object to.  
    MemoryStream ms = new MemoryStream();  
  
    // Serializer the User object to the stream.  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(User));  
    ser.WriteObject(ms, user);  
    byte[] json = ms.ToArray();  
    ms.Close();  
    return Encoding.UTF8.GetString(json, 0, json.Length);  
}  
  
// Deserialize a JSON stream to a User object.  
public static User ReadToObject(string json)  
{  
    User deserializedUser = new User();  
    MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(json));  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(deserializedUser.GetType());  
    deserializedUser = ser.ReadObject(ms) as User;  
    ms.Close();  
    return deserializedUser;  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="02671-122">Serializátor JSON, vyvolá výjimku serializace pro kontrakty dat, které mají více členy se stejným názvem, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="02671-122">The JSON serializer throws a serialization exception for data contracts that have multiple members with the same name, as shown in the following sample code.</span></span>  
  
```csharp  
[DataContract]  
public class TestDuplicateDataBase  
{  
    [DataMember]  
    public int field1 = 123;  
}

[DataContract]  
public class TestDuplicateDataDerived : TestDuplicateDataBase  
{  
    [DataMember]  
    public new int field1 = 999;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="02671-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="02671-123">See Also</span></span>  
 [<span data-ttu-id="02671-124">Samostatná serializace JSON</span><span class="sxs-lookup"><span data-stu-id="02671-124">Stand-Alone JSON Serialization</span></span>](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)  
 [<span data-ttu-id="02671-125">Podpora JSON a dalších formátů přenosu dat</span><span class="sxs-lookup"><span data-stu-id="02671-125">Support for JSON and Other Data Transfer Formats</span></span>](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
