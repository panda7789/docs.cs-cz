---
title: 'Postupy: Použití DataContractJsonSerializer'
description: Naučte se serializovat objekty typu .NET do dat zakódovaných ve formátu JSON a pak tato data deserializovat zpátky do instancí typů .NET.
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 4ffa0e9dec0a677a38d244b4a0da476d91852da5
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246802"
---
# <a name="how-to-use-datacontractjsonserializer"></a>Jak používat DataContractJsonSerializer

> [!NOTE]
> Tento článek se týká <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> . Pro většinu scénářů, které zahrnují serializaci a deserializaci JSON, doporučujeme rozhraní API v [System.Text.Jsv oboru názvů](../../../standard/serialization/system-text-json-overview.md).

JSON (JavaScript Object Notation) je efektivní formát kódování dat, který umožňuje rychlé výměny malých objemů dat mezi klientskými prohlížeči a webovými službami s podporou AJAX.

Tento článek ukazuje, jak serializovat objekty typu .NET do dat zakódovaných ve formátu JSON a potom deserializovat data ve formátu JSON zpátky do instancí typů .NET. V tomto příkladu se používá kontrakt dat k předvedení serializace a deserializace uživatelsky definovaného `Person` typu a použití <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .

V normálním případě je serializace a deserializace JSON zpracovávána automaticky Windows Communication Foundation (WCF) při použití typů kontraktů dat v operacích služby, které jsou zpřístupněny přes koncové body s povoleným AJAX. V některých případech ale možná budete potřebovat přímo pracovat s daty JSON.

Tento článek je založený na [ukázce DataContractJsonSerializer](../samples/json-serialization.md).

## <a name="to-define-the-data-contract-for-a-person-type"></a>Definování kontraktu dat pro typ osoby

1. Definujte kontrakt dat pro tím, že `Person` připojíte <xref:System.Runtime.Serialization.DataContractAttribute> třídu a k <xref:System.Runtime.Serialization.DataMemberAttribute> atributu členům, které chcete serializovat. Další informace o kontraktech dat najdete v tématu [Navrhování kontraktů služeb](../designing-service-contracts.md).

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

## <a name="to-serialize-an-instance-of-type-person-to-json"></a>Serializace instance typu Person do formátu JSON

> [!NOTE]
> Pokud dojde k chybě během serializace odchozí odpovědi na serveru nebo z jiného důvodu, nemusí se klientovi vrátit jako chyba.

1. Vytvořte instanci `Person` typu.

    ```csharp
    var p = new Person();
    p.name = "John";
    p.age = 42;
    ```

2. Serializace `Person` objektu do paměťového proudu pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .

    ```csharp
    var stream1 = new MemoryStream();
    var ser = new DataContractJsonSerializer(typeof(Person));
    ```

3. Použijte <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> metodu pro zápis dat JSON do datového proudu.

    ```csharp
    ser.WriteObject(stream1, p);
    ```

4. Zobrazit výstup JSON.

    ```csharp
    stream1.Position = 0;
    var sr = new StreamReader(stream1);
    Console.Write("JSON form of Person object: ");
    Console.WriteLine(sr.ReadToEnd());
    ```

## <a name="to-deserialize-an-instance-of-type-person-from-json"></a>Deserializace instance typu person z formátu JSON

1. Deserializace dat zakódovaných ve formátu JSON do nové instance `Person` pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> metody <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .

    ```csharp
    stream1.Position = 0;
    var p2 = (Person)ser.ReadObject(stream1);
    ```

2. Zobrazit výsledky.

    ```csharp
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");
    ```

## <a name="example"></a>Příklad

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
> Serializátor JSON vyvolá výjimku serializace pro kontrakty dat, které mají více členů se stejným názvem, jak je znázorněno v následujícím ukázkovém kódu.

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

## <a name="see-also"></a>Viz také

- [Serializace JSON v .NET](../../../standard/serialization/system-text-json-overview.md)
