---
title: 'Postupy: Serializace a deserializace dat protokolu JSON'
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 0c56b298737dc9b9902f13c586edffb3d05257f8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783011"
---
# <a name="how-to-serialize-and-deserialize-json-data"></a><span data-ttu-id="9213f-102">Postupy: Serializace a deserializace dat protokolu JSON</span><span class="sxs-lookup"><span data-stu-id="9213f-102">How to: Serialize and deserialize JSON data</span></span>
<span data-ttu-id="9213f-103">JSON (JavaScript Object Notation) je formát kódování efektivní data, která umožňuje rychlé výměny malé množství dat mezi prohlížeče klienta a s povoleným AJAX webové služby.</span><span class="sxs-lookup"><span data-stu-id="9213f-103">JSON (JavaScript Object Notation) is an efficient data encoding format that enables fast exchanges of small amounts of data between client browsers and AJAX-enabled Web services.</span></span>  
  
 <span data-ttu-id="9213f-104">Tento článek ukazuje, jak serializovat objekty typu .NET na data zakódovaná ve formátu JSON a potom deserializovat data ve formátu JSON zpět do instance typů .NET.</span><span class="sxs-lookup"><span data-stu-id="9213f-104">This article demonstrates how to serialize .NET type objects into JSON-encoded data and then deserialize data in the JSON format back into instances of .NET types.</span></span> <span data-ttu-id="9213f-105">Tento příklad používá kontrakt dat k předvedení serializace a deserializace uživatelem definované `Person` typu a používá <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="9213f-105">This example uses a data contract to demonstrate serialization and deserialization of a user-defined `Person` type and uses <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
 <span data-ttu-id="9213f-106">Za normálních okolností JSON serializace a deserializace provádí automaticky pomocí Windows Communication Foundation (WCF) při použití typy kontraktů dat v servisní operace, které jsou zveřejněné prostřednictvím koncových bodů s povoleným AJAX.</span><span class="sxs-lookup"><span data-stu-id="9213f-106">Normally, JSON serialization and deserialization are handled automatically by Windows Communication Foundation (WCF) when you use data contract types in service operations that are exposed over AJAX-enabled endpoints.</span></span> <span data-ttu-id="9213f-107">Nicméně v některých případech budete muset pracovat s daty JSON přímo.</span><span class="sxs-lookup"><span data-stu-id="9213f-107">However, in some cases you may need to work with JSON data directly.</span></span>   
  
> [!NOTE]
>  <span data-ttu-id="9213f-108">Pokud dojde k chybě při serializaci odpovědi na odchozí na serveru nebo z nějakého důvodu, se nesmí získat vrácen do klienta jako chyba.</span><span class="sxs-lookup"><span data-stu-id="9213f-108">If an error occurs during serialization of an outgoing reply on the server or for some other reason, it may not get returned to the client as a fault.</span></span>  
  
 <span data-ttu-id="9213f-109">Tento článek je založen na [serializace JSON](../samples/json-serialization.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="9213f-109">This article is based on the [JSON serialization](../samples/json-serialization.md) sample.</span></span>  
  
## <a name="to-define-the-data-contract-for-a-person-type"></a><span data-ttu-id="9213f-110">Definování kontraktu dat pro typ osoby</span><span class="sxs-lookup"><span data-stu-id="9213f-110">To define the data contract for a Person type</span></span> 
  
1. <span data-ttu-id="9213f-111">Definování kontraktu dat pro `Person` připojením <xref:System.Runtime.Serialization.DataContractAttribute> do třídy a <xref:System.Runtime.Serialization.DataMemberAttribute> atribut členům chcete serializovat.</span><span class="sxs-lookup"><span data-stu-id="9213f-111">Define the data contract for `Person` by attaching the <xref:System.Runtime.Serialization.DataContractAttribute> to the class and <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the members you want to serialize.</span></span> <span data-ttu-id="9213f-112">Další informace o kontraktech dat najdete v tématu [navrhování kontraktů služby](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="9213f-112">For more information about data contracts, see [Designing service contracts](../designing-service-contracts.md).</span></span>  
  
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
  
## <a name="to-serialize-an-instance-of-type-person-to-json"></a><span data-ttu-id="9213f-113">K serializaci instancí typu osoba do formátu JSON</span><span class="sxs-lookup"><span data-stu-id="9213f-113">To serialize an instance of type Person to JSON</span></span>  
  
1. <span data-ttu-id="9213f-114">Vytvoření instance `Person` typu.</span><span class="sxs-lookup"><span data-stu-id="9213f-114">Create an instance of the `Person` type.</span></span>  
  
    ```csharp  
    var p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2. <span data-ttu-id="9213f-115">Serializace `Person` objektu do datový proud paměti pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="9213f-115">Serialize the `Person` object to a memory stream by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    var stream1 = new MemoryStream();  
    var ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3. <span data-ttu-id="9213f-116">Použití <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> metody zapsat JSON data do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="9213f-116">Use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> method to write JSON data to the stream.</span></span>  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4. <span data-ttu-id="9213f-117">Zobrazit výstup JSON.</span><span class="sxs-lookup"><span data-stu-id="9213f-117">Show the JSON output.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    var sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
## <a name="to-deserialize-an-instance-of-type-person-from-json"></a><span data-ttu-id="9213f-118">K deserializaci instance typu osoby z formátu JSON</span><span class="sxs-lookup"><span data-stu-id="9213f-118">To deserialize an instance of type Person from JSON</span></span>  
  
1. <span data-ttu-id="9213f-119">Deserializuje data zakódovaná ve formátu JSON do nové instance `Person` pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> metodu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="9213f-119">Deserialize the JSON-encoded data into a new instance of `Person` by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> method of the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    var p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2. <span data-ttu-id="9213f-120">Zobrazte výsledky.</span><span class="sxs-lookup"><span data-stu-id="9213f-120">Show the results.</span></span>  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a><span data-ttu-id="9213f-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="9213f-121">Example</span></span>  
  
```csharp  
// Create a User object and serialize it to a JSON stream.  
public static string WriteFromObject()  
{  
    // Create User object.  
    var user = new User("Bob", 42);  
  
    // Create a stream to serialize the object to.  
    var ms = new MemoryStream();  
  
    // Serializer the User object to the stream.  
    var ser = new DataContractJsonSerializer(typeof(User));  
    ser.WriteObject(ms, user);  
    byte[] json = ms.ToArray();  
    ms.Close();  
    return Encoding.UTF8.GetString(json, 0, json.Length);  
}  
  
// Deserialize a JSON stream to a User object.  
public static User ReadToObject(string json)  
{  
    var deserializedUser = new User();  
    var ms = new MemoryStream(Encoding.UTF8.GetBytes(json));  
    var ser = new DataContractJsonSerializer(deserializedUser.GetType());  
    deserializedUser = ser.ReadObject(ms) as User;  
    ms.Close();  
    return deserializedUser;  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="9213f-122">Serializátor JSON výjimku serializaci dat smlouvy, které mají víc členů se stejným názvem, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="9213f-122">The JSON serializer throws a serialization exception for data contracts that have multiple members with the same name, as shown in the following sample code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9213f-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9213f-123">See also</span></span>

- [<span data-ttu-id="9213f-124">Samostatná serializace JSON</span><span class="sxs-lookup"><span data-stu-id="9213f-124">Stand-alone JSON serialization</span></span>](stand-alone-json-serialization.md)
- [<span data-ttu-id="9213f-125">Podpora JSON a dalších přenosu dat formátů</span><span class="sxs-lookup"><span data-stu-id="9213f-125">Support for JSON and other data transfer formats</span></span>](support-for-json-and-other-data-transfer-formats.md)
