---
title: Použití DataContractSerializer a DataContractResolver pro zajištění funkcí NetDataContractSerializer
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: e7a4f0d754b444d8558b03e07d98788a2eee5971
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144979"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a>Použití DataContractSerializer a DataContractResolver pro zajištění funkcí NetDataContractSerializer
Tato ukázka ukazuje, <xref:System.Runtime.Serialization.DataContractSerializer> jak použití <xref:System.Runtime.Serialization.DataContractResolver> s vhodné poskytuje <xref:System.Runtime.Serialization.NetDataContractSerializer>stejné funkce jako . Tato ukázka ukazuje, <xref:System.Runtime.Serialization.DataContractResolver> jak vytvořit vhodné a <xref:System.Runtime.Serialization.DataContractSerializer>jak ji přidat do .

## <a name="sample-details"></a>Podrobnosti ukázky
 <xref:System.Runtime.Serialization.NetDataContractSerializer>se liší <xref:System.Runtime.Serialization.DataContractSerializer> jedním důležitým <xref:System.Runtime.Serialization.NetDataContractSerializer> způsobem: zahrnuje informace o typu CLR <xref:System.Runtime.Serialization.DataContractSerializer> v serializovaném XML, zatímco není. Proto <xref:System.Runtime.Serialization.NetDataContractSerializer> lze použít pouze v případě, že serializace a deserializace končí sdílet stejné typy CLR. Doporučuje se však <xref:System.Runtime.Serialization.DataContractSerializer> používat, protože jeho <xref:System.Runtime.Serialization.NetDataContractSerializer>výkon je lepší než . Informace, které jsou serializovány <xref:System.Runtime.Serialization.DataContractSerializer> v <xref:System.Runtime.Serialization.DataContractResolver> souboru přidáním a k němu.

 Tato ukázka se skládá ze dvou projektů. První projekt <xref:System.Runtime.Serialization.NetDataContractSerializer> používá serializovat objekt. Druhý projekt <xref:System.Runtime.Serialization.DataContractSerializer> používá <xref:System.Runtime.Serialization.DataContractResolver> s poskytnout stejné funkce jako první projekt.

 Následující příklad kódu ukazuje implementaci <xref:System.Runtime.Serialization.DataContractResolver> vlastního `MyDataContractResolver` s názvem, <xref:System.Runtime.Serialization.DataContractSerializer> který je přidán do projektu DCSwithDCR.

```csharp
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
        type ??= Type.GetType(typeName + ", " + typeNamespace);
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

#### <a name="to-use-this-sample"></a>Chcete-li použít tento vzorek

1. Pomocí Visual Studia 2012 otevřete soubor řešení DCRSample.sln.

2. Klepněte pravým tlačítkem myši na soubor řešení a zvolte **Vlastnosti**.

3. V dialogovém okně **Stránky vlastností řešení** vyberte v části **Společné vlastnosti** **projekt po spuštění** **položku Více projektů při spuštění:**.

4. Vedle projektu **DCSwithDCR** vyberte v rozevíracím seznamu **Akce** možnost **Začít.**

5. Vedle projektu **NetDCS** vyberte v rozevíracím souboru **Akce** možnost **Zahájit.**

6. Klepnutím na **tlačítko OK** zavřete dialogové okno.

7. Chcete-li vytvořit řešení, stiskněte kombinaci kláves CTRL+SHIFT+B.

8. Chcete-li řešení spustit, stiskněte kombinaci kláves CTRL+F5.

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
