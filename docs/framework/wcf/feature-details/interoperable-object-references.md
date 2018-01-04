---
title: "Interoperabilní odkazy na objekty"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3d74c54d29f7da085d9d87bf37cc93078726f308
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="interoperable-object-references"></a>Interoperabilní odkazy na objekty
Ve výchozím nastavení <xref:System.Runtime.Serialization.DataContractSerializer> serializuje objekty podle hodnoty. Můžete použít <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> vlastnost dáte pokyn, aby serializátor kontraktu dat pro zachování odkazy na objekty při serializaci objektů typu.  
  
## <a name="generated-xml"></a>Vygenerovaný XML  
 Jako příklad zvažte následující objekt:  
  
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
  
 S <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> nastavena na `false` (výchozí), je generována následující kód XML:  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 S <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> nastavena na `true`, je generována následující kód XML:  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1" />  
</X>  
```  
  
 Ale <xref:System.Runtime.Serialization.XsdDataContractExporter> nepopisuje `id` a `ref` atributů v jeho schématu i v případě `preserveObjectReferences` je nastavena na `true`.  
  
## <a name="using-isreference"></a>Pomocí IsReference  
 Generovat objekt referenční informace, který je platný podle schématu s popisem, použít <xref:System.Runtime.Serialization.DataContractAttribute> atribut na typ a nastavte <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> příznak, který `true`. Pomocí `IsReference` v předchozím příkladu třída `X`:  
  
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
  
 Vygenerovaný soubor XML je následující:  
  
 `<X>`  
  
 `<A id="1">`  
  
 `<Value>contents of A</Value>`  
  
 `</A>`  
  
 `<B ref="1">`  
  
 `</B>`  
  
 `</X>`  
  
 Pomocí `IsReference` zajišťuje dodržování předpisů na zprávu odezvy. Bez toho při vygenerování typu ze schématu, co je odeslána zpět jako XML pro, typ není nutně kompatibilní s původně předpokládá, že schéma. Jinými slovy i když `id` a `ref` byly serializovat atributy, původní schéma může mít zavřené tyto atributy (nebo všechny) z ke kterým dochází v souboru XML. S `IsReference` použité na člena, člen nadále rozpoznat jako "kde" Pokud roundtripped.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference%2A>
