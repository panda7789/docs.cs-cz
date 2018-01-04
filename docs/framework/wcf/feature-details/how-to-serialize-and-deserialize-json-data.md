---
title: 'Postupy: Serializace a deserializace dat protokolu JSON'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: deb02217b5d2a79cdf90d511658657f642ca1fc9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-serialize-and-deserialize-json-data"></a>Postupy: Serializace a deserializace dat protokolu JSON
JSON (JavaScript Object Notation) je formát kódování efektivní dat, který umožňuje rychlé výměnu malé množství dat mezi prohlížeče klienta a podporou AJAXU webové služby.  
  
 Toto téma ukazuje, jak serializovat objekty typu .NET do data zakódovaná ve formátu JSON a jeho následné deserializaci data ve formátu JSON zpět do instance typy .NET pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. Tento příklad používá kontrakt dat k předvedení serializace a deserializace uživatelem definované `Person` typu.  
  
 Za normálních okolností JSON serializace a deserializace zpracovává automaticky [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] při použití typy kontraktů dat v operace služby, které jsou přístupné přes podporou AJAXU koncové body. V některých případech, které budete potřebovat k práci s daty JSON přímo – je to ale scénář, který toto téma popisuje.  
  
> [!NOTE]
>  Pokud dojde k chybě během serializace odchozí odpovědi na serveru nebo odpověď operace vyvolá výjimku z jiného důvodu, se nemusí získat vrácen do klienta jako chybu.  
  
 Toto téma je založena na [serializace JSON](../../../../docs/framework/wcf/samples/json-serialization.md) ukázka.  
  
### <a name="to-define-the-data-contract-for-a-person"></a>Chcete-li definovat kontrakt dat osoby  
  
1.  Definovat kontrakt dat pro `Person` připojením <xref:System.Runtime.Serialization.DataContractAttribute> k třídě a <xref:System.Runtime.Serialization.DataMemberAttribute> atribut u členů chcete serializovat. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]kontrakty dat najdete v části [navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
    ```  
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
  
    ```  
    Person p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2.  Serializovat `Person` objekt, který má datový proud paměti pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
    ```  
    MemoryStream stream1 = new MemoryStream();  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3.  Použití <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> metoda při zápisu dat JSON do datového proudu.  
  
    ```  
    ser.WriteObject(stream1, p);  
    ```  
  
4.  Zobrazit výstup JSON.  
  
    ```  
    stream1.Position = 0;  
    StreamReader sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
### <a name="to-deserialize-an-instance-of-type-person-from-json"></a>K deserializaci instance typu osoby z formátu JSON  
  
1.  Deserializuje data zakódovaná ve formátu JSON do novou instanci třídy `Person` pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> metodu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
    ```  
    stream1.Position = 0;  
    Person p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2.  Zobrazit výsledky.  
  
    ```  
    Console.Write("Deserialized back, got name=");  
    Console.Write(p2.name);  
    Console.Write(", age=");  
    Console.WriteLine(p2.age);  
    ```  
  
## <a name="example"></a>Příklad  
  
```  
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
>  Serializátor JSON, vyvolá výjimku serializace pro kontrakty dat, které mají více členy se stejným názvem, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
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
 [Samostatná serializace JSON](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)  
 [Podpora JSON a dalších formátů přenosu dat](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
