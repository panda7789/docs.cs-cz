---
title: Ukázka dataContractJsonSerializer
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: d3456582d73640f1802c17d7f29f4931a6f920b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144627"
---
# <a name="datacontractjsonserializer-sample"></a>Ukázka dataContractJsonSerializer

> [!NOTE]
> Tento vzorek <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>je pro . Pro většinu scénářů, které zahrnují serializaci a rekonstrukci json, doporučujeme api v [oboru názvů System.Text.Json](../../../standard/serialization/system-text-json-overview.md).

<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>podporuje stejné typy <xref:System.Runtime.Serialization.DataContractSerializer>jako . Formát dat JSON je zvláště užitečný při psaní webových aplikací ve stylu JavaScriptu a XML (AJAX). Podpora AJAX v systému Windows Communication Foundation (WCF) je optimalizována pro použití s ASP.NET AJAX prostřednictvím ovládacího prvku ScriptManager. Příklady použití Windows Communication Foundation (WCF) s ASP.NET AJAX, naleznete [v ajax ukázky](ajax.md).  
  
Postup nastavení a sestavení pokyny pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
Ukázka používá `Person` kontrakt dat k předvedení serializace a deserializace.  

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

 Chcete-li serializovat instanci `Person` typu do JSON, vytvořte <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> první a použijte metodu `WriteObject` k zápisu dat JSON do datového proudu.  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 Datový proud paměti obsahuje platná data JSON.
  
```json  
{"age":42,"name":"John"}  
```  
  
 Ukázka ukazuje deserializaci z dat JSON do objektu. Potom přetoč proud `ReadObject`a volání .  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 Zkoumání objektu `p2` ukazuje, že data JSON byla správně zserializována.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavení a spuštění ukázky  
  
1. Vytvořte řešení JsonSerialization.sln, jak je popsáno v [sestavení ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Spusťte výslednou konzolovou aplikaci.  
