---
title: 'Postupy: Serializace a deserializace dat protokolu JSON'
ms.date: 03/30/2017
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 797b29fd7ddecd3e3ed85f8cb3a6df93044942ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704339"
---
# <a name="how-to-serialize-and-deserialize-json-data"></a>Postupy: Serializace a deserializace dat protokolu JSON
JSON (JavaScript Object Notation) je formát kódování efektivní data, která umožňuje rychlé výměny malé množství dat mezi prohlížeče klienta a s povoleným AJAX webové služby.  
  
 Toto téma ukazuje, jak serializovat objekty typu .NET na data zakódovaná ve formátu JSON a potom deserializovat data ve formátu JSON zpět do instance typů .NET pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. Tento příklad používá kontrakt dat k předvedení serializace a deserializace uživatelem definované `Person` typu.  
  
 Za normálních okolností JSON serializace a deserializace je automaticky zpracována Windows Communication Foundation (WCF) při použití typy kontraktů dat v servisní operace, které jsou zveřejněné prostřednictvím koncových bodů s povoleným AJAX. V některých případech možná bude nutné pracovat s daty JSON přímo – je to ale toto téma popisuje následující scénář.  
  
> [!NOTE]
>  Pokud dojde k chybě během serializace za odchozí odpovědi na serveru nebo operace odpovědi z nějakého důvodu dojde k výjimce, se nesmí získat vrácen do klienta jako chyba.  
  
 Toto téma vychází [serializace JSON](../../../../docs/framework/wcf/samples/json-serialization.md) vzorku.  
  
### <a name="to-define-the-data-contract-for-a-person"></a>Definování kontraktu dat pro osobu  
  
1.  Definování kontraktu dat pro `Person` připojením <xref:System.Runtime.Serialization.DataContractAttribute> do třídy a <xref:System.Runtime.Serialization.DataMemberAttribute> atribut členům chcete serializovat. Další informace o kontraktech dat najdete v tématu [navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
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
  
### <a name="to-serialize-an-instance-of-type-person-to-json"></a>K serializaci instancí typu osoba do formátu JSON  
  
1.  Vytvoření instance `Person` typu.  
  
    ```csharp  
    Person p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2.  Serializace `Person` objektu pomocí datového proudu paměti <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
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
  
### <a name="to-deserialize-an-instance-of-type-person-from-json"></a>K deserializaci instance typu osoby z formátu JSON  
  
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
- [Samostatná serializace JSON](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)
- [Podpora JSON a dalších formátů přenosu dat](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
