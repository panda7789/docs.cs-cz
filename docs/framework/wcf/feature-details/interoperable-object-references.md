---
title: Interoperabilní odkazy na objekty
ms.date: 04/15/2019
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: 0927f217a1666f8f27ca9c3e68f80a96b9c0f2b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184709"
---
# <a name="interoperable-object-references"></a>Interoperabilní odkazy na objekty
Ve výchozím <xref:System.Runtime.Serialization.DataContractSerializer> nastavení serializuje objekty podle hodnoty. <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> Vlastnost můžete použít k pokynu serializátoru kontraktu dat k zachování odkazů na objekty při serializaci objektů.  
  
## <a name="generated-xml"></a>Vygenerovaný kód XML  
 Jako příklad zvažte následující objekt:  
  
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
  
 S <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> nastavenou na `false` (výchozí) se vygeneruje následující XML:  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 S <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> nastavenou na `true`, je generován následující XML:  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 Však <xref:System.Runtime.Serialization.XsdDataContractExporter> `id` nepopisuje atributy `ref` a v jeho schématu, `preserveObjectReferences` i když je `true`vlastnost nastavena na .  
  
## <a name="using-isreference"></a>Použití odkazu IsReference  
 Chcete-li generovat informace o odkazu na objekt, které jsou platné <xref:System.Runtime.Serialization.DataContractAttribute> podle schématu, které <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> jej `true`popisuje, použijte atribut pro typ a nastavte příznak na . Následující příklad upravuje třídu `X` v předchozím příkladu přidáním `IsReference`:  
  
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

 Vygenerovaný xml je následující:  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A>
    <B ref="1"></B>  
</X>
```  
  
 Použití `IsReference` zajišťuje dodržování předpisů při zakopnutí zpráv. Bez něj, když je typ generován ze schématu, výstup XML pro tento typ není nutně kompatibilní se schématem původně předpokládal. Jinými slovy, `id` i `ref` když atributy a byly serializovány, původní schéma mohlo zabránit výskytu těchto atributů (nebo všech atributů) v XML. Při `IsReference` použití na datový člen člen i nadále rozpoznán jako *odkazovatelný* při zaokrouhlení.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
