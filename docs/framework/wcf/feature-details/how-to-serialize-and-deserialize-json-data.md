---
title: 'Postupy: Použití DataContractJsonSerializer'
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 3cf8cc52587a64e7273ab9e0de0b1751d00827cf
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901216"
---
# <a name="how-to-use-datacontractjsonserializer"></a><span data-ttu-id="a6164-102">Jak používat DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="a6164-102">How to use DataContractJsonSerializer</span></span>

> [!NOTE]
> <span data-ttu-id="a6164-103">Tento článek se týká <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="a6164-103">This article is about <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="a6164-104">Pro většinu scénářů, které zahrnují serializaci a deserializaci JSON, doporučujeme rozhraní API v [oboru názvů System. text. JSON](../../../standard/serialization/system-text-json-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a6164-104">For most scenarios that involve serializing and deserializing JSON, we recommend the APIs in the [System.Text.Json namespace](../../../standard/serialization/system-text-json-overview.md).</span></span>

<span data-ttu-id="a6164-105">JSON (JavaScript Object Notation) je efektivní formát kódování dat, který umožňuje rychlé výměny malých objemů dat mezi klientskými prohlížeči a webovými službami s podporou AJAX.</span><span class="sxs-lookup"><span data-stu-id="a6164-105">JSON (JavaScript Object Notation) is an efficient data encoding format that enables fast exchanges of small amounts of data between client browsers and AJAX-enabled Web services.</span></span>

<span data-ttu-id="a6164-106">Tento článek ukazuje, jak serializovat objekty typu .NET do dat zakódovaných ve formátu JSON a potom deserializovat data ve formátu JSON zpátky do instancí typů .NET.</span><span class="sxs-lookup"><span data-stu-id="a6164-106">This article demonstrates how to serialize .NET type objects into JSON-encoded data and then deserialize data in the JSON format back into instances of .NET types.</span></span> <span data-ttu-id="a6164-107">V tomto příkladu se používá kontrakt dat k předvedení serializace a deserializace uživatelsky definovaného typu `Person` a používá <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="a6164-107">This example uses a data contract to demonstrate serialization and deserialization of a user-defined `Person` type and uses <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

<span data-ttu-id="a6164-108">V normálním případě je serializace a deserializace JSON zpracovávána automaticky Windows Communication Foundation (WCF) při použití typů kontraktů dat v operacích služby, které jsou zpřístupněny přes koncové body s povoleným AJAX.</span><span class="sxs-lookup"><span data-stu-id="a6164-108">Normally, JSON serialization and deserialization are handled automatically by Windows Communication Foundation (WCF) when you use data contract types in service operations that are exposed over AJAX-enabled endpoints.</span></span> <span data-ttu-id="a6164-109">V některých případech ale možná budete potřebovat přímo pracovat s daty JSON.</span><span class="sxs-lookup"><span data-stu-id="a6164-109">However, in some cases you may need to work with JSON data directly.</span></span>

<span data-ttu-id="a6164-110">Tento článek je založený na [ukázce DataContractJsonSerializer](../samples/json-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="a6164-110">This article is based on the [DataContractJsonSerializer sample](../samples/json-serialization.md).</span></span>

## <a name="to-define-the-data-contract-for-a-person-type"></a><span data-ttu-id="a6164-111">Definování kontraktu dat pro typ osoby</span><span class="sxs-lookup"><span data-stu-id="a6164-111">To define the data contract for a Person type</span></span>

1. <span data-ttu-id="a6164-112">Definujte kontrakt dat pro `Person` připojením <xref:System.Runtime.Serialization.DataContractAttribute> ke třídě a <xref:System.Runtime.Serialization.DataMemberAttribute> atributu členům, které chcete serializovat.</span><span class="sxs-lookup"><span data-stu-id="a6164-112">Define the data contract for `Person` by attaching the <xref:System.Runtime.Serialization.DataContractAttribute> to the class and <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the members you want to serialize.</span></span> <span data-ttu-id="a6164-113">Další informace o kontraktech dat najdete v tématu [Navrhování kontraktů služeb](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="a6164-113">For more information about data contracts, see [Designing service contracts](../designing-service-contracts.md).</span></span>

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

## <a name="to-serialize-an-instance-of-type-person-to-json"></a><span data-ttu-id="a6164-114">Serializace instance typu Person do formátu JSON</span><span class="sxs-lookup"><span data-stu-id="a6164-114">To serialize an instance of type Person to JSON</span></span>

> [!NOTE]
> <span data-ttu-id="a6164-115">Pokud dojde k chybě během serializace odchozí odpovědi na serveru nebo z jiného důvodu, nemusí se klientovi vrátit jako chyba.</span><span class="sxs-lookup"><span data-stu-id="a6164-115">If an error occurs during serialization of an outgoing reply on the server or for some other reason, it may not get returned to the client as a fault.</span></span>

1. <span data-ttu-id="a6164-116">Vytvoří instanci typu `Person`.</span><span class="sxs-lookup"><span data-stu-id="a6164-116">Create an instance of the `Person` type.</span></span>

    ```csharp
    var p = new Person();
    p.name = "John";
    p.age = 42;
    ```

2. <span data-ttu-id="a6164-117">Serializace objektu `Person` do paměťového proudu pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="a6164-117">Serialize the `Person` object to a memory stream by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

    ```csharp
    var stream1 = new MemoryStream();
    var ser = new DataContractJsonSerializer(typeof(Person));
    ```

3. <span data-ttu-id="a6164-118">Použijte metodu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> k zápisu dat JSON do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="a6164-118">Use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> method to write JSON data to the stream.</span></span>

    ```csharp
    ser.WriteObject(stream1, p);
    ```

4. <span data-ttu-id="a6164-119">Zobrazit výstup JSON.</span><span class="sxs-lookup"><span data-stu-id="a6164-119">Show the JSON output.</span></span>

    ```csharp
    stream1.Position = 0;
    var sr = new StreamReader(stream1);
    Console.Write("JSON form of Person object: ");
    Console.WriteLine(sr.ReadToEnd());
    ```

## <a name="to-deserialize-an-instance-of-type-person-from-json"></a><span data-ttu-id="a6164-120">Deserializace instance typu person z formátu JSON</span><span class="sxs-lookup"><span data-stu-id="a6164-120">To deserialize an instance of type Person from JSON</span></span>

1. <span data-ttu-id="a6164-121">Deserializace dat zakódovaných ve formátu JSON do nové instance `Person` pomocí metody <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="a6164-121">Deserialize the JSON-encoded data into a new instance of `Person` by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> method of the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

    ```csharp
    stream1.Position = 0;
    var p2 = (Person)ser.ReadObject(stream1);
    ```

2. <span data-ttu-id="a6164-122">Zobrazit výsledky.</span><span class="sxs-lookup"><span data-stu-id="a6164-122">Show the results.</span></span>

    ```csharp
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");
    ```

## <a name="example"></a><span data-ttu-id="a6164-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="a6164-123">Example</span></span>

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
> <span data-ttu-id="a6164-124">Serializátor JSON vyvolá výjimku serializace pro kontrakty dat, které mají více členů se stejným názvem, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="a6164-124">The JSON serializer throws a serialization exception for data contracts that have multiple members with the same name, as shown in the following sample code.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a6164-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6164-125">See also</span></span>

- [<span data-ttu-id="a6164-126">Serializace JSON v .NET</span><span class="sxs-lookup"><span data-stu-id="a6164-126">JSON serialization in .NET</span></span>](../../../standard/serialization/system-text-json-overview.md)
