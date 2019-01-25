---
title: DataContractResolver
ms.date: 03/30/2017
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
ms.openlocfilehash: ad5436a60b5cd82b44931713d863eaeed791e264
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723976"
---
# <a name="datacontractresolver"></a>DataContractResolver
Tato ukázka předvádí, jak lze přizpůsobit procesů serializace a deserializace pomocí <xref:System.Runtime.Serialization.DataContractResolver> třídy. Tento příklad ukazuje způsob použití modulu DataContractResolver Mapovat typy CLR do a z reprezentaci xsi: type během serializace a deserializace.

## <a name="sample-details"></a>Ukázka podrobnosti
 Ukázka definuje následující typy CLR.

```csharp
using System;
using System.Runtime.Serialization;

namespace Types
{
    [DataContract]
    public class Customer
    {
        [DataMember]
        public string Name { get; set; }
    }

    [DataContract]
    public class VIPCustomer : Customer
    {
        [DataMember]
        public string VipInfo { get; set; }
    }

    [DataContract]
    public class RegularCustomer : Customer
    {
    }

    [DataContract]
    public class PreferredVIPCustomer : VIPCustomer
    {
    }
}
```

 Ukázka načte sestavení, extrahuje každý z těchto typů a poté serializuje a deserializuje je. <xref:System.Runtime.Serialization.DataContractResolver> Zapojí se do procesu serializace předáním instance <xref:System.Runtime.Serialization.DataContractResolver>-odvozené třídy <xref:System.Runtime.Serialization.DataContractSerializer> konstruktoru, jak je znázorněno v následujícím příkladu.

```csharp
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));
```

 Ukázka pak Serializuje typy CLR, jak je znázorněno v následujícím příkladu kódu.

```csharp
Assembly assembly = Assembly.Load(new AssemblyName("Types"));

public void serialize(Type type)
{
    Object instance = Activator.CreateInstance(type);

    Console.WriteLine("----------------------------------------");
    Console.WriteLine();
    Console.WriteLine("Serializing type: {0}", type.Name);
    Console.WriteLine();
    this.buffer = new StringBuilder();
    using (XmlWriter xmlWriter = XmlWriter.Create(this.buffer))
    {
        try
        {
            this.serializer.WriteObject(xmlWriter, instance);
        }
        catch (SerializationException error)
        {
            Console.WriteLine(error.ToString());
        }
    }
    Console.WriteLine(this.buffer.ToString());
}
```

 Ukázka pak deserializuje xsi:types, jak je znázorněno v následujícím příkladu kódu.

```csharp
public void deserialize(Type type)
{
    Console.WriteLine();
    Console.WriteLine("Deserializing type: {0}", type.Name);
    Console.WriteLine();
    using (XmlReader xmlReader = XmlReader.Create(new StringReader(this.buffer.ToString())))
    {
        Object obj = this.serializer.ReadObject(xmlReader);
    }
}
```

 Od vlastní <xref:System.Runtime.Serialization.DataContractResolver> je předán <xref:System.Runtime.Serialization.DataContractSerializer> konstruktoru, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> je volaný během serializace pro mapování typu CLR na ekvivalentní `xsi:type`. Podobně jako <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> je volán během deserializaci k mapování `xsi:type` na ekvivalentní typ CLR. V této ukázce <xref:System.Runtime.Serialization.DataContractResolver> je definován, jak je znázorněno v následujícím příkladu.

 Následující příklad kódu je třídu odvozenou z <xref:System.Runtime.Serialization.DataContractResolver>.

```csharp
class MyDataContractResolver : DataContractResolver
{
    private Dictionary<string, XmlDictionaryString> dictionary = new Dictionary<string, XmlDictionaryString>();
    Assembly assembly;

    public MyDataContractResolver(Assembly assembly)
    {
        this.assembly = assembly;
    }

    // Used at deserialization
    // Allows users to map xsi:type name to any Type
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)
    {
        XmlDictionaryString tName;
        XmlDictionaryString tNamespace;
        if (dictionary.TryGetValue(typeName, out tName) && dictionary.TryGetValue(typeNamespace, out tNamespace))
        {
            return this.assembly.GetType(tNamespace.Value + "." + tName.Value);
        }
        else
        {
            return null;
        }
    }

    // Used at serialization
    // Maps any Type to a new xsi:type representation
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)
    {
        string name = dataContractType.Name;
        string namesp = dataContractType.Namespace;
        typeName = new XmlDictionaryString(XmlDictionary.Empty, name, 0);
        typeNamespace = new XmlDictionaryString(XmlDictionary.Empty, namesp, 0);
        if (!dictionary.ContainsKey(dataContractType.Name))
        {
            dictionary.Add(name, typeName);
        }
        if (!dictionary.ContainsKey(dataContractType.Namespace))
        {
            dictionary.Add(namesp, typeNamespace);
        }
    }
}
```

 Jako součást vzorku generuje typy projektu sestavení se všemi typy, které se používají v této ukázce. Pomocí tohoto projektu můžete přidat, odebrat nebo změnit typy, které bude serializována.

#### <a name="to-use-this-sample"></a>Pro fungování této ukázky

1.  Pomocí sady Visual Studio 2012, otevřete soubor řešení DCRSample.sln.

2.  Abyste mohli spustit řešení, stisknutím klávesy F5

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a>Viz také:
- [Použití překladače kontraktů dat](../../../../docs/framework/wcf/feature-details/using-a-data-contract-resolver.md)
