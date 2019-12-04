---
title: DataContractResolver
ms.date: 03/30/2017
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
ms.openlocfilehash: 101c33ca197be9dff52a73c844dd0b006e62b2ac
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716596"
---
# <a name="datacontractresolver"></a>DataContractResolver
Tato ukázka předvádí, jak lze upravit procesy serializace a deserializace pomocí třídy <xref:System.Runtime.Serialization.DataContractResolver>. Tento příklad ukazuje, jak použít DataContractResolver k namapování typů CLR do a z reprezentace xsi: Type během serializace a deserializace.

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

 Ukázka načte sestavení, extrahuje každý z těchto typů a pak je serializace a deserializace. <xref:System.Runtime.Serialization.DataContractResolver> je zapojen do procesu serializace předáním instance <xref:System.Runtime.Serialization.DataContractResolver>odvozené třídy do konstruktoru <xref:System.Runtime.Serialization.DataContractSerializer>, jak je znázorněno v následujícím příkladu.

```csharp
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));
```

 Ukázka pak serializace typy CLR, jak je znázorněno v následujícím příkladu kódu.

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

 Ukázka pak deserializace xsi: Types, jak je znázorněno v následujícím příkladu kódu.

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

 Vzhledem k tomu, že vlastní <xref:System.Runtime.Serialization.DataContractResolver> jsou předány do konstruktoru <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> je volána během serializace pro mapování typu CLR na ekvivalentní `xsi:type`. Podobně <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> je volána během deserializace pro mapování `xsi:type` na ekvivalentní typ CLR. V této ukázce je <xref:System.Runtime.Serialization.DataContractResolver> definován tak, jak je znázorněno v následujícím příkladu.

 Následující příklad kódu je třída odvozená od <xref:System.Runtime.Serialization.DataContractResolver>.

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

 V rámci ukázky vytvoří projekt typy sestavení se všemi typy, které jsou použity v této ukázce. Tento projekt použijte k přidání, odebrání nebo úpravě typů, které budou serializovány.

#### <a name="to-use-this-sample"></a>Použití této ukázky

1. Pomocí sady Visual Studio 2012 otevřete soubor řešení DCRSample. sln.

2. Pokud chcete řešení spustit, stiskněte klávesu F5.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a>Viz také:

- [Použití překladače kontraktů dat](../../../../docs/framework/wcf/feature-details/using-a-data-contract-resolver.md)
