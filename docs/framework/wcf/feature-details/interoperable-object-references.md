---
title: Interoperabilní odkazy na objekty
ms.date: 03/30/2017
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: 9cbbd5a34269a7c4a5c33d72487a02df21f2f0fb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222702"
---
# <a name="interoperable-object-references"></a>Interoperabilní odkazy na objekty
Ve výchozím nastavení <xref:System.Runtime.Serialization.DataContractSerializer> serializuje objekty podle hodnoty. Můžete použít <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> vlastnost dáte pokyn, aby serializátor kontraktu dat pro zachování odkazy na objekty při serializaci objektů typu.  
  
## <a name="generated-xml"></a>Vygenerovaný kód XML  
 Jako příklad vezměte v úvahu následující objekt:  
  
```  
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
   <B ref="1" />  
</X>  
```  
  
 Však <xref:System.Runtime.Serialization.XsdDataContractExporter> nepopisuje `id` a `ref` atributů v jeho schématu, i v případě `preserveObjectReferences` je nastavena na `true`.  
  
## <a name="using-isreference"></a>Pomocí IsReference  
 Chcete-li vygenerovat odkaz na informace o objektu, který je platný podle schématu, které aplikaci popisuje, použijte <xref:System.Runtime.Serialization.DataContractAttribute> atribut na typ a nastavte <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> příznak `true`. Pomocí `IsReference` v předchozím příkladu třída `X`:  
  
 `[DataContract(IsReference=true)] public class X`  
  
 `{`  
  
 `SomeClass someInstance = new SomeClass();`  
  
 `[DataMember]`  
  
 `public SomeClass A = someInstance;`  
  
 `[DataMember]`  
  
 `public SomeClass B = someInstance;`  
  
 `}`  
  
 `public class SomeClass`  
  
 `{`  
  
 `}`  
  
 Vygenerovaný kód XML je následující:  
  
 `<X>`  
  
 `<A id="1">`  
  
 `<Value>contents of A</Value>`  
  
 `</A>`  
  
 `<B ref="1">`  
  
 `</B>`  
  
 `</X>`  
  
 Pomocí `IsReference` zajišťuje dodržování předpisů na zprávu verzemi. Bez něj při generování typ ze schématu, co se odesílá zpět jako XML pro, že typ není nutně kompatibilní s původně předpokládá, že schéma. Jinými slovy i když `id` a `ref` atributy byly serializován, původní schématu může mít zavřené tyto atributy (nebo všechny) ze které se vyskytují v kódu XML. S `IsReference` použít na datový člen, člen nadále získat renomé jako "kde" v případě roundtripped.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference%2A>
