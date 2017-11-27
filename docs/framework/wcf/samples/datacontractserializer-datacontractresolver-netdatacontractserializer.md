---
title: "Použití DataContractSerializer a DataContractResolver pro zajištění funkcí NetDataContractSerializer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d189b68cc8321dace0418a3c1e4b1b3c21cfd3ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a>Použití DataContractSerializer a DataContractResolver pro zajištění funkcí NetDataContractSerializer
Tento příklad znázorňuje způsob použití <xref:System.Runtime.Serialization.DataContractSerializer> odpovídajícími <xref:System.Runtime.Serialization.DataContractResolver> poskytuje stejné funkce jako <xref:System.Runtime.Serialization.NetDataContractSerializer>. Tento příklad ukazuje postup vytvoření odpovídající <xref:System.Runtime.Serialization.DataContractResolver> a jak ho přidat do <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 <xref:System.Runtime.Serialization.NetDataContractSerializer>se liší od <xref:System.Runtime.Serialization.DataContractSerializer> jedním způsobem důležité: <xref:System.Runtime.Serialization.NetDataContractSerializer> obsahuje informace o typu CLR v serializovaných XML, zatímco <xref:System.Runtime.Serialization.DataContractSerializer> neexistuje. Proto <xref:System.Runtime.Serialization.NetDataContractSerializer> lze použít pouze v případě, že jak serializaci a deserializaci končí sdílet stejné typy CLR. Doporučujeme však používat <xref:System.Runtime.Serialization.DataContractSerializer> vzhledem k tomu, že je lepší, než jeho výkon <xref:System.Runtime.Serialization.NetDataContractSerializer>. Můžete změnit informace, které je serializována v <xref:System.Runtime.Serialization.DataContractSerializer> přidáním <xref:System.Runtime.Serialization.DataContractResolver> k němu.  
  
 Tato ukázka se skládá ze dvou projektů. První projekt používá <xref:System.Runtime.Serialization.NetDataContractSerializer> o serializaci objektu. Druhý projektu používá <xref:System.Runtime.Serialization.DataContractSerializer> s <xref:System.Runtime.Serialization.DataContractResolver> nabízí stejné funkce jako první projekt.  
  
 Následující příklad kódu ukazuje implementaci vlastní <xref:System.Runtime.Serialization.DataContractResolver> s názvem `MyDataContractResolver` který je přidán do <xref:System.Runtime.Serialization.DataContractSerializer> v DCSwithDCR projektu.  
  
```  
class MyDataContractResolver : DataContractResolver  
{  
    private XmlDictionary dictionary = new XmlDictionary();  
  
    public MyDataContractResolver()  
    {  
    }  
  
    // Used at deserialization  
    // Allows users to map xsi:type name to any Type   
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)  
    {  
        Type type = knownTypeResolver.ResolveName(typeName, typeNamespace, null);  
        if (type == null)  
        {  
            type = Type.GetType(typeName + ", " + typeNamespace);  
        }  
        return type;  
    }  
  
    // Used at serialization  
    // Maps any Type to a new xsi:type representation  
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)  
    {  
        knownTypeResolver.ResolveType(dataContractType, null, out typeName, out typeNamespace);  
        if (typeName == null || typeNamespace == null)  
        {  
            XmlDictionary dictionary = new XmlDictionary();  
            typeName = dictionary.Add(dataContractType.FullName);  
            typeNamespace = dictionary.Add(dataContractType.Assembly.FullName);  
        }  
    }  
}  
```  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor řešení DCRSample.sln.  
  
2.  Klikněte pravým tlačítkem na soubor řešení a zvolte **vlastnosti**.  
  
3.  V **stránky vlastností řešení** dialogové okno, v části **společných vlastností**, **spouštěný projekt**, vyberte **více projektů po spuštění:**.  
  
4.  Vedle položky **DCSwithDCR** projekt, vyberte **spustit** z **akce** rozevíracího seznamu.  
  
5.  Vedle položky **NetDCS** projekt, vyberte **spustit** z **akce** rozevíracího seznamu.  
  
6.  Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
7.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
8.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
  
## <a name="see-also"></a>Viz také
