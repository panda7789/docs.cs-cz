---
title: Ukázka DataContractJsonSerializer
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 509f80812bb815e4fa56fa3ebdc9236ac0622ace
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141831"
---
# <a name="datacontractjsonserializer-sample"></a>Ukázka DataContractJsonSerializer

> [!NOTE]
> Tato ukázka je určena pro <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. Pro většinu scénářů, které zahrnují serializaci a deserializaci JSON, doporučujeme použít nástroje v [oboru názvů System. text. JSON](../../../standard/serialization/system-text-json-overview.md). 

<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> podporuje stejné typy jako <xref:System.Runtime.Serialization.DataContractSerializer>. Formát dat JSON je zvláště užitečný při psaní asynchronních webových aplikací ve stylu JavaScript a XML (AJAX). Podpora AJAX v Windows Communication Foundation (WCF) je optimalizována pro použití s ASP.NET AJAX prostřednictvím ovládacího prvku ScriptManager. Příklady použití Windows Communication Foundation (WCF) s ASP.NET AJAX naleznete v [ukázkách AJAX](ajax.md).  
  
Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
Ukázka používá kontrakt dat `Person` k demonstraci serializace a deserializace.  

```csharp
[DataContract]
class Person
{
    [DataMember]
    internal string name;

    [DataMember]
    internal int age;
}
```

 Chcete-li serializovat instanci typu `Person` do formátu JSON, nejprve vytvořte <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> a pomocí metody `WriteObject` Zapište data JSON do datového proudu.  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 Proud paměti obsahuje platná data JSON.
  
```json  
{"age":42,"name":"John"}  
```  
  
 Ukázka demonstruje deserializaci z dat JSON do objektu. Pak můžete datový proud převinout zpět a volat `ReadObject`.  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 Prozkoumání `p2`ho objektu odhalí, že data JSON byla deserializována správně.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Sestavte řešení JsonSerialization. sln, jak je popsáno v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Spusťte výslednou konzolovou aplikaci.  
