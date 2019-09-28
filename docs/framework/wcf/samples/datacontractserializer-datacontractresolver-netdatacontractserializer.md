---
title: Použití DataContractSerializer a DataContractResolver pro zajištění funkcí NetDataContractSerializer
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: e52b6da80100cbffb7dc8725d16c31a67bc19445
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351663"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a>Použití DataContractSerializer a DataContractResolver pro zajištění funkcí NetDataContractSerializer
Tato ukázka předvádí, jak použití <xref:System.Runtime.Serialization.DataContractSerializer> s příslušným <xref:System.Runtime.Serialization.DataContractResolver> poskytuje stejné funkce jako <xref:System.Runtime.Serialization.NetDataContractSerializer>. V této ukázce se dozvíte, jak vytvořit odpovídající <xref:System.Runtime.Serialization.DataContractResolver> a jak ho přidat do <xref:System.Runtime.Serialization.DataContractSerializer>.

## <a name="sample-details"></a>Podrobnosti ukázky
 <xref:System.Runtime.Serialization.NetDataContractSerializer> se liší od <xref:System.Runtime.Serialization.DataContractSerializer> v jednom důležitém způsobu: <xref:System.Runtime.Serialization.NetDataContractSerializer> zahrnuje informace o typu CLR v serializovaném kódu XML, zatímco <xref:System.Runtime.Serialization.DataContractSerializer> ne. Proto lze použít <xref:System.Runtime.Serialization.NetDataContractSerializer> pouze v případě, že serializace a deserializace končí sdílení stejných typů CLR. Doporučuje se ale použít <xref:System.Runtime.Serialization.DataContractSerializer>, protože jeho výkon je lepší než <xref:System.Runtime.Serialization.NetDataContractSerializer>. Informace, které jsou serializovány v <xref:System.Runtime.Serialization.DataContractSerializer>, lze změnit přidáním <xref:System.Runtime.Serialization.DataContractResolver> do něj.

 Tato ukázka se skládá ze dvou projektů. První projekt používá <xref:System.Runtime.Serialization.NetDataContractSerializer> k serializaci objektu. Druhý projekt používá <xref:System.Runtime.Serialization.DataContractSerializer> s <xref:System.Runtime.Serialization.DataContractResolver> k poskytnutí stejné funkce jako první projekt.

 Následující příklad kódu ukazuje implementaci vlastního <xref:System.Runtime.Serialization.DataContractResolver> s názvem `MyDataContractResolver`, která je přidána do <xref:System.Runtime.Serialization.DataContractSerializer> v projektu DCSwithDCR.

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

#### <a name="to-use-this-sample"></a>Použití této ukázky

1. Pomocí sady Visual Studio 2012 otevřete soubor řešení DCRSample. sln.

2. Klikněte pravým tlačítkem na soubor řešení a vyberte **vlastnosti**.

3. V dialogovém okně **stránky vlastností řešení** v části **společné vlastnosti**, **spouštěný projekt**vyberte **více projektů po spuštění:** .

4. Vedle projektu **DCSwithDCR** vyberte v rozevíracím seznamu **Akce** možnost **Spustit** .

5. Vedle projektu **NetDCS** vyberte v rozevíracím seznamu **Akce** možnost **Spustit** .

6. Kliknutím na tlačítko **OK** zavřete dialogové okno.

7. Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.

8. Pokud chcete řešení spustit, stiskněte klávesy CTRL + F5.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
