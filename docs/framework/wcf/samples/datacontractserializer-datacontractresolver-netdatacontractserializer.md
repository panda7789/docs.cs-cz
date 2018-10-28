---
title: Použití DataContractSerializer a DataContractResolver pro zajištění funkcí NetDataContractSerializer
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: a2efa9f66e4053b94dc85b3bbe73400630fa84d1
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184516"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a>Použití DataContractSerializer a DataContractResolver pro zajištění funkcí NetDataContractSerializer
Tato ukázka předvádí, jak používat <xref:System.Runtime.Serialization.DataContractSerializer> odpovídající <xref:System.Runtime.Serialization.DataContractResolver> poskytuje stejné funkce jako <xref:System.Runtime.Serialization.NetDataContractSerializer>. Tento příklad ukazuje, jak vytvořit odpovídající <xref:System.Runtime.Serialization.DataContractResolver> a jak ho přidat do <xref:System.Runtime.Serialization.DataContractSerializer>.

## <a name="sample-details"></a>Ukázka podrobnosti
 <xref:System.Runtime.Serialization.NetDataContractSerializer> se liší od <xref:System.Runtime.Serialization.DataContractSerializer> jedním způsobem důležité: <xref:System.Runtime.Serialization.NetDataContractSerializer> obsahuje informace o typu modulu CLR v serializovaném kódu XML, zatímco <xref:System.Runtime.Serialization.DataContractSerializer> tak není. Proto <xref:System.Runtime.Serialization.NetDataContractSerializer> lze použít pouze v případě, že i serializaci a deserializaci končí sdílet stejné typy CLR. Doporučujeme však použít <xref:System.Runtime.Serialization.DataContractSerializer> vzhledem k tomu, že jeho výkon je vhodnější než <xref:System.Runtime.Serialization.NetDataContractSerializer>. Můžete změnit informace, které je serializován ve <xref:System.Runtime.Serialization.DataContractSerializer> tak, že přidáte <xref:System.Runtime.Serialization.DataContractResolver> k němu.

 Tento příklad se skládá ze dvou projektů. První projekt používá <xref:System.Runtime.Serialization.NetDataContractSerializer> k serializaci objektu. Druhý projekt používá <xref:System.Runtime.Serialization.DataContractSerializer> s <xref:System.Runtime.Serialization.DataContractResolver> poskytnout stejné funkce jako první projekt.

 Následující příklad kódu ukazuje implementaci vlastního <xref:System.Runtime.Serialization.DataContractResolver> s názvem `MyDataContractResolver` , který je přidán do <xref:System.Runtime.Serialization.DataContractSerializer> DCSwithDCR projektu.

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

1.  Pomocí sady Visual Studio 2012, otevřete soubor řešení DCRSample.sln.

2.  Klikněte pravým tlačítkem na soubor řešení a zvolte **vlastnosti**.

3.  V **stránek vlastností řešení** dialogového okna, v části **společné vlastnosti**, **spouštěný projekt**vyberte **více projektů po spuštění:**.

4.  Vedle položky **DCSwithDCR** projekt, vyberte **Start** z **akce** rozevíracího seznamu.

5.  Vedle položky **NetDCS** projekt, vyberte **Start** z **akce** rozevíracího seznamu.

6.  Klikněte na tlačítko **OK** zavřete dialogové okno.

7.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.

8.  Abyste mohli spustit řešení, stiskněte CTRL + F5.

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
  
## <a name="see-also"></a>Viz také
