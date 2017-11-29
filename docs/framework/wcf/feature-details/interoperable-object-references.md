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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6d55ffb6ed08b4642bc72c1eabb60164b6c744c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="interoperable-object-references"></a><span data-ttu-id="ca02f-102">Interoperabilní odkazy na objekty</span><span class="sxs-lookup"><span data-stu-id="ca02f-102">Interoperable Object References</span></span>
<span data-ttu-id="ca02f-103">Ve výchozím nastavení <xref:System.Runtime.Serialization.DataContractSerializer> serializuje objekty podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ca02f-103">By default the <xref:System.Runtime.Serialization.DataContractSerializer> serializes objects by value.</span></span> <span data-ttu-id="ca02f-104">Můžete použít <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> vlastnost dáte pokyn, aby serializátor kontraktu dat pro zachování odkazy na objekty při serializaci objektů typu.</span><span class="sxs-lookup"><span data-stu-id="ca02f-104">You can use the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> property to instruct the Data Contract Serializer to preserve object references when serializing objects of the type.</span></span>  
  
## <a name="generated-xml"></a><span data-ttu-id="ca02f-105">Vygenerovaný XML</span><span class="sxs-lookup"><span data-stu-id="ca02f-105">Generated XML</span></span>  
 <span data-ttu-id="ca02f-106">Jako příklad zvažte následující objekt:</span><span class="sxs-lookup"><span data-stu-id="ca02f-106">As an example, consider the following object:</span></span>  
  
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
  
 <span data-ttu-id="ca02f-107">S <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> nastavena na `false` (výchozí), je generována následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="ca02f-107">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `false` (the default), the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <span data-ttu-id="ca02f-108">S <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> nastavena na `true`, je generována následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="ca02f-108">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `true`, the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1" />  
</X>  
```  
  
 <span data-ttu-id="ca02f-109">Ale <xref:System.Runtime.Serialization.XsdDataContractExporter> nepopisuje `id` a `ref` atributů v jeho schématu i v případě `preserveObjectReferences` je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="ca02f-109">However, <xref:System.Runtime.Serialization.XsdDataContractExporter> does not describe the `id` and `ref` attributes in its schema, even when the `preserveObjectReferences` property is set to `true`.</span></span>  
  
## <a name="using-isreference"></a><span data-ttu-id="ca02f-110">Pomocí IsReference</span><span class="sxs-lookup"><span data-stu-id="ca02f-110">Using IsReference</span></span>  
 <span data-ttu-id="ca02f-111">Generovat objekt referenční informace, který je platný podle schématu s popisem, použít <xref:System.Runtime.Serialization.DataContractAttribute> atribut na typ a nastavte <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> příznak, který `true`.</span><span class="sxs-lookup"><span data-stu-id="ca02f-111">To generate object reference information that is valid according to the schema that describes it, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a type, and set the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flag to `true`.</span></span> <span data-ttu-id="ca02f-112">Pomocí `IsReference` v předchozím příkladu třída `X`:</span><span class="sxs-lookup"><span data-stu-id="ca02f-112">Using `IsReference` in the previous example class `X`:</span></span>  
  
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
  
 <span data-ttu-id="ca02f-113">Vygenerovaný soubor XML je následující:</span><span class="sxs-lookup"><span data-stu-id="ca02f-113">The generated XML is as follows:</span></span>  
  
 `<X>`  
  
 `<A id="1">`  
  
 `<Value>contents of A</Value>`  
  
 `</A>`  
  
 `<B ref="1">`  
  
 `</B>`  
  
 `</X>`  
  
 <span data-ttu-id="ca02f-114">Pomocí `IsReference` zajišťuje dodržování předpisů na zprávu odezvy.</span><span class="sxs-lookup"><span data-stu-id="ca02f-114">Using `IsReference` ensures compliance on message round-tripping.</span></span> <span data-ttu-id="ca02f-115">Bez toho při vygenerování typu ze schématu, co je odeslána zpět jako XML pro, typ není nutně kompatibilní s původně předpokládá, že schéma.</span><span class="sxs-lookup"><span data-stu-id="ca02f-115">Without it, when a type is generated from schema, what is sent back as XML for that type is not necessarily compatible with the schema originally assumed.</span></span> <span data-ttu-id="ca02f-116">Jinými slovy i když `id` a `ref` byly serializovat atributy, původní schéma může mít zavřené tyto atributy (nebo všechny) z ke kterým dochází v souboru XML.</span><span class="sxs-lookup"><span data-stu-id="ca02f-116">In other words, although the `id` and `ref` attributes were serialized, the original schema could have barred these attributes (or all attributes) from occurring in the XML.</span></span> <span data-ttu-id="ca02f-117">S `IsReference` použité na člena, člen nadále rozpoznat jako "kde" Pokud roundtripped.</span><span class="sxs-lookup"><span data-stu-id="ca02f-117">With `IsReference` applied to a data member, the member continues to be recognized as "referenceable" when roundtripped.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca02f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca02f-118">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference%2A>
