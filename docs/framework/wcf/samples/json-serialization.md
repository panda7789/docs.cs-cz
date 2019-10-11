---
title: Ukázka DataContractJsonSerializer
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 1711c826397dfb8b54ecedee08e88e67cb58d2a4
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180232"
---
# <a name="datacontractjsonserializer-sample"></a>Ukázka DataContractJsonSerializer
Tato ukázka předvádí, jak použít <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> k serializaci a deserializaci dat ve formátu JavaScript Object Notation (JSON). Tento modul serializace převede data JSON na instance .NET Frameworkch typů a vrátí se zpět do dat JSON. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> podporuje stejné typy jako <xref:System.Runtime.Serialization.DataContractSerializer>. Formát dat JSON je zvláště užitečný při psaní asynchronních webových aplikací ve stylu JavaScript a XML (AJAX). Podpora AJAX v Windows Communication Foundation (WCF) je optimalizována pro použití s ASP.NET AJAX prostřednictvím ovládacího prvku ScriptManager. Příklady použití Windows Communication Foundation (WCF) s ASP.NET AJAX naleznete v [ukázkách AJAX](ajax.md).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Ukázka používá ke znázornění serializace a deserializace kontrakt dat `Person`.  

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

 Chcete-li serializovat instanci typu `Person` na JSON, nejprve vytvořte <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> a použijte metodu `WriteObject` pro zápis dat JSON do datového proudu.  

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
  
 Ukázka demonstruje deserializaci z dat JSON do objektu. Potom datový proud převinete a zavoláte `ReadObject`.  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 Prozkoumání objektu `p2` odhalí, že data JSON byla správně deserializována.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pro stažení ukázek Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Sestavte řešení JsonSerialization. sln, jak je popsáno v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Spusťte výslednou konzolovou aplikaci.  
