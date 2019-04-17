---
title: Interoperabilní odkazy na objekty
ms.date: 04/15/2019
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: ada9084f6ac3c97dc641571c0cb8379a2fac68a8
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59610636"
---
# <a name="interoperable-object-references"></a>Interoperabilní odkazy na objekty
Ve výchozím nastavení <xref:System.Runtime.Serialization.DataContractSerializer> serializuje objekty podle hodnoty. Můžete použít <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> vlastnost dáte pokyn, aby serializátor kontraktu dat pro zachování odkazy na objekty při serializaci objektů.  
  
## <a name="generated-xml"></a>Vygenerovaný kód XML  
 Jako příklad vezměte v úvahu následující objekt:  
  
```csharp  
[DataContract]  
public class X  
{  
    SomeClass someInstance = new SomeClass();  
    [DataMember]  
    public SomeClass A = someInstance;  
    [DataMember]  
    public SomeClass B = someInstance;  
}  
  
public class SomeClass   
{  
}  
```  
  
 S <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> nastavena na `false` (výchozí), je vygenerována následující kód XML:  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 S <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> nastavena na `true`, je vygenerována následující kód XML:  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 Však <xref:System.Runtime.Serialization.XsdDataContractExporter> nepopisuje `id` a `ref` atributů v jeho schématu, i když `preserveObjectReferences` je nastavena na `true`.  
  
## <a name="using-isreference"></a>Pomocí IsReference  
 Chcete-li vygenerovat odkaz na informace o objektu, který je platný podle schématu, které aplikaci popisuje, použijte <xref:System.Runtime.Serialization.DataContractAttribute> atribut na typ a nastavte <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> příznak `true`. Následující příklad upravuje třída `X` v předchozím příkladu tak, že přidáte `IsReference`:  
  
```csharp
[DataContract(IsReference=true)]
public class X   
{  
     SomeClass someInstance = new SomeClass(); 
     [DataMember]
     public SomeClass A = someInstance;
     [DataMember] 
     public SomeClass B = someInstance;
}
  
public class SomeClass 
{   
}  
````

 Vygenerovaný kód XML je následující:  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A> 
    <B ref="1"></B>  
</X>
```  
  
 Pomocí `IsReference` zajišťuje dodržování předpisů na zprávu verzemi. Bez toho při generování typ ze schématu, XML výstupu, není nutně kompatibilní se schématem původně předpokládá, že typ. Jinými slovy i když `id` a `ref` atributy byly serializován, původní schématu může mít zavřené tyto atributy (nebo všechny) ze které se vyskytují v kódu XML. S `IsReference` použít na datový člen, člen nadále získat renomé jako *označím* při odbavovaná.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
