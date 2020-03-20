---
title: DataContractResolver
ms.date: 03/30/2017
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
ms.openlocfilehash: 716bcb2bb43656051beffb15da9c7a988942ecd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183787"
---
# <a name="datacontractresolver"></a>DataContractResolver
Tato ukázka ukazuje, jak serializace a deserializace procesy lze přizpůsobit pomocí třídy. <xref:System.Runtime.Serialization.DataContractResolver> Tato ukázka ukazuje, jak pomocí DataContractResolver mapovat typy CLR do a z xsi:typ reprezentace během serializace a deserializace.

## <a name="sample-details"></a>Podrobnosti ukázky
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

 Ukázka načte sestavu, extrahuje každý z těchto typů a potom je serializuje a reserializuje. Je <xref:System.Runtime.Serialization.DataContractResolver> zapojen do procesu serializace předáním <xref:System.Runtime.Serialization.DataContractResolver>instance -derived <xref:System.Runtime.Serialization.DataContractSerializer> třídy konstruktoru, jak je znázorněno v následujícím příkladu.

```csharp
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));
```

 Ukázka pak serializuje typy CLR, jak je znázorněno v následujícím příkladu kódu.

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

 Ukázka pak deserializuje xsi:typy, jak je znázorněno v následujícím příkladu kódu.

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

 Vzhledem <xref:System.Runtime.Serialization.DataContractResolver> k tomu, <xref:System.Runtime.Serialization.DataContractSerializer> že vlastní <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> je předán konstruktoru, je volána `xsi:type`během serializace mapovat typ CLR na ekvivalentní . Podobně <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> je volána během deserializace `xsi:type` mapovat na ekvivalentní typ CLR. V této ukázce <xref:System.Runtime.Serialization.DataContractResolver> je definována, jak je znázorněno v následujícím příkladu.

 Následující příklad kódu je třída odvozená <xref:System.Runtime.Serialization.DataContractResolver>z .

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

 Jako součást vzorku Typy projektu generuje sestavení se všemi typy, které se používají v této ukázce. Tento projekt slouží k přidání, odebrání nebo úpravě typů, které budou serializovány.

#### <a name="to-use-this-sample"></a>Chcete-li použít tento vzorek

1. Pomocí Visual Studia 2012 otevřete soubor řešení DCRSample.sln.

2. Chcete-li řešení spustit, stiskněte klávesu F5.

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a>Viz také

- [Použití překladače kontraktů dat](../../../../docs/framework/wcf/feature-details/using-a-data-contract-resolver.md)
