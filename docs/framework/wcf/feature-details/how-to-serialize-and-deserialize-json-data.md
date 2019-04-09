---
title: 'Postupy: Serializace a deserializace dat protokolu JSON'
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 6363a8e161969c188c5dd18c425ffd42969e9adc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106155"
---
# <a name="how-to-serialize-and-deserialize-json-data"></a>Postupy: Serializace a deserializace dat protokolu JSON
JSON (JavaScript Object Notation) je formát kódování efektivní data, která umožňuje rychlé výměny malé množství dat mezi prohlížeče klienta a s povoleným AJAX webové služby.  
  
 Tento článek ukazuje, jak serializovat objekty typu .NET na data zakódovaná ve formátu JSON a potom deserializovat data ve formátu JSON zpět do instance typů .NET. Tento příklad používá kontrakt dat k předvedení serializace a deserializace uživatelem definované `Person` typu a používá <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
 Za normálních okolností JSON serializace a deserializace provádí automaticky pomocí Windows Communication Foundation (WCF) při použití typy kontraktů dat v servisní operace, které jsou zveřejněné prostřednictvím koncových bodů s povoleným AJAX. Nicméně v některých případech budete muset pracovat s daty JSON přímo.   
  
> [!NOTE]
>  Pokud dojde k chybě při serializaci odpovědi na odchozí na serveru nebo z nějakého důvodu, se nesmí získat vrácen do klienta jako chyba.  
  
 Tento článek je založen na [serializace JSON](../samples/json-serialization.md) vzorku.  
  
## <a name="to-define-the-data-contract-for-a-person-type"></a>Definování kontraktu dat pro typ osoby 
  
1.  Definování kontraktu dat pro `Person` připojením <xref:System.Runtime.Serialization.DataContractAttribute> do třídy a <xref:System.Runtime.Serialization.DataMemberAttribute> atribut členům chcete serializovat. Další informace o kontraktech dat najdete v tématu [navrhování kontraktů služby](../designing-service-contracts.md).  
  
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
  
## <a name="to-serialize-an-instance-of-type-person-to-json"></a>K serializaci instancí typu osoba do formátu JSON  
  
1.  Vytvoření instance `Person` typu.  
  
    ```csharp  
    Person p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2.  Serializace `Person` objektu do datový proud paměti pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
    ```csharp  
    MemoryStream stream1 = new MemoryStream();  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3.  Použití <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> metody zapsat JSON data do datového proudu.  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4.  Zobrazit výstup JSON.  
  
    ```csharp  
    stream1.Position = 0;  
    StreamReader sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
## <a name="to-deserialize-an-instance-of-type-person-from-json"></a>K deserializaci instance typu osoby z formátu JSON  
  
1.  Deserializuje data zakódovaná ve formátu JSON do nové instance `Person` pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> metodu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
    ```csharp  
    stream1.Position = 0;  
    Person p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2.  Zobrazte výsledky.  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a>Příklad  
  
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
>  Serializátor JSON výjimku serializaci dat smlouvy, které mají víc členů se stejným názvem, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Samostatná serializace JSON](stand-alone-json-serialization.md)
- [Podpora JSON a dalších přenosu dat formátů](support-for-json-and-other-data-transfer-formats.md)
