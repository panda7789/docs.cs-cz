---
title: Serializace JSON
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: bb38005c02e9b3e850282d2a81c2e17143657025
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305283"
---
# <a name="json-serialization"></a>Serializace JSON
Tato ukázka předvádí, jak používat <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> k serializaci a deserializaci data ve formátu JavaScript Object Notation (JSON). Tato serializační stroj převádí JSON data do instance [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typů a zpět do JSON data. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> podporuje stejné typy jako <xref:System.Runtime.Serialization.DataContractSerializer>. Formát dat JSON je obzvláště užitečná při psaní asynchronního JavaScript a XML (AJAX)-stylu webové aplikace. Podpora pro AJAX ve Windows Communication Foundation (WCF) je optimalizovaná pro použití s technologií ASP.NET AJAX prostřednictvím ovládacího prvku ScriptManager. Příklady, jak používat Windows Communication Foundation (WCF) s technologií ASP.NET AJAX, najdete v článku [AJAX ukázky](ajax.md).  
  
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
