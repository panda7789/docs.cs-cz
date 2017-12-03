---
title: Serializace JSON
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 706cea8ed07fae680987e58b118b0a87951a059b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="json-serialization"></a>Serializace JSON
Tento příklad znázorňuje způsob použití <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> k serializaci a deserializaci data ve formátu JavaScript Object Notation (JSON). Tento modul serializace převádí JSON data do instance [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy a zpět do JSON data. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>podporuje stejné typy jako <xref:System.Runtime.Serialization.DataContractSerializer>. Formát dat JSON je obzvláště užitečná při psaní asynchronní JavaScript a XML (AJAX)-styl webové aplikace. Podpora jazyka AJAX v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] je optimalizovaný pro použití s prvku ASP.NET AJAX prostřednictvím ovládací prvek ScriptManager. Příklady, jak používat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pomocí prvku ASP.NET AJAX, najdete v článku [AJAX ukázky](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  Nastavení postupu a sestavení pokyny k této ukázce jsou umístěné na konci tohoto tématu.  
  
 Ukázce se používá `Person` kontraktů dat k předvedení serializace a deserializace.  
  
```  
[DataContract]  
    class Person  
    {  
        [DataMember]  
        internal string name;  
  
        [DataMember]  
        internal int age;  
    }  
```  
  
 K serializaci instanci `Person` zadejte do formátu JSON, vytvořte <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> první a použít `WriteObject` metoda při zápisu dat JSON na datový proud.  
  
```  
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
  
 Ukázka ukazuje deserializaci z dat JSON na objekt. Potom rewind datového proudu a volání `ReadObject`.  
  
```  
Person p2 = (Person)ser.ReadObject(stream1);  
```  
  
 Zkoumání `p2` objekt zjistí, zda byl správně deserializovat JSON data.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Sestavte řešení JsonSerialization.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Spusťte výsledné konzolovou aplikaci.  
  
## <a name="see-also"></a>Viz také
