---
title: Serializace JSON
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: c44dd71c3903e5c4d3d37b89881896c65c664262
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591864"
---
# <a name="json-serialization"></a>Serializace JSON
Tato ukázka předvádí, jak používat <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> k serializaci a deserializaci data ve formátu JavaScript Object Notation (JSON). Tato serializační stroj převádí JSON data do instance typů rozhraní .NET Framework a zpět do JSON data. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> podporuje stejné typy jako <xref:System.Runtime.Serialization.DataContractSerializer>. Formát dat JSON je obzvláště užitečná při psaní asynchronního JavaScript a XML (AJAX)-stylu webové aplikace. Podpora pro AJAX ve Windows Communication Foundation (WCF) je optimalizovaná pro použití s technologií ASP.NET AJAX prostřednictvím ovládacího prvku ScriptManager. Příklady, jak používat Windows Communication Foundation (WCF) s technologií ASP.NET AJAX, najdete v článku [AJAX ukázky](ajax.md).  
  
> [!NOTE]
>  Postupu a sestavení pokyny k instalaci pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Ukázka používá `Person` kontraktů dat k předvedení serializace a deserializace.  

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

 K serializaci instancí `Person` zadejte do formátu JSON, vytvořte <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> první a použít `WriteObject` metody zapsat JSON data na datový proud.  

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
  
 Ukázce deserializaci z dat JSON na objekt. Potom rewind datového proudu a volání `ReadObject`.  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 Zkoumání `p2` objekt odhalí správně deserializovat JSON data.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Sestavte řešení JsonSerialization.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Spuštění výsledné aplikace konzoly.  
