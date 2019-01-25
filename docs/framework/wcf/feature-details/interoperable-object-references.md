---
title: Interoperabilní odkazy na objekty
ms.date: 03/30/2017
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: 5d2f7d93544cafab7cfe5d8dcbb8a4c5d5c5b576
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582418"
---
# <a name="interoperable-object-references"></a><span data-ttu-id="ac2c1-102">Interoperabilní odkazy na objekty</span><span class="sxs-lookup"><span data-stu-id="ac2c1-102">Interoperable Object References</span></span>
<span data-ttu-id="ac2c1-103">Ve výchozím nastavení <xref:System.Runtime.Serialization.DataContractSerializer> serializuje objekty podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ac2c1-103">By default the <xref:System.Runtime.Serialization.DataContractSerializer> serializes objects by value.</span></span> <span data-ttu-id="ac2c1-104">Můžete použít <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> vlastnost dáte pokyn, aby serializátor kontraktu dat pro zachování odkazy na objekty při serializaci objektů typu.</span><span class="sxs-lookup"><span data-stu-id="ac2c1-104">You can use the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> property to instruct the Data Contract Serializer to preserve object references when serializing objects of the type.</span></span>  
  
## <a name="generated-xml"></a><span data-ttu-id="ac2c1-105">Vygenerovaný kód XML</span><span class="sxs-lookup"><span data-stu-id="ac2c1-105">Generated XML</span></span>  
 <span data-ttu-id="ac2c1-106">Jako příklad vezměte v úvahu následující objekt:</span><span class="sxs-lookup"><span data-stu-id="ac2c1-106">As an example, consider the following object:</span></span>  
  
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
  
 <span data-ttu-id="ac2c1-107">S <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> nastavena na `false` (výchozí), je vygenerována následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="ac2c1-107">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `false` (the default), the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <span data-ttu-id="ac2c1-108">S <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> nastavena na `true`, je vygenerována následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="ac2c1-108">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `true`, the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1" />  
</X>  
```  
  
 <span data-ttu-id="ac2c1-109">Však <xref:System.Runtime.Serialization.XsdDataContractExporter> nepopisuje `id` a `ref` atributů v jeho schématu, i v případě `preserveObjectReferences` je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="ac2c1-109">However, <xref:System.Runtime.Serialization.XsdDataContractExporter> does not describe the `id` and `ref` attributes in its schema, even when the `preserveObjectReferences` property is set to `true`.</span></span>  
  
## <a name="using-isreference"></a><span data-ttu-id="ac2c1-110">Pomocí IsReference</span><span class="sxs-lookup"><span data-stu-id="ac2c1-110">Using IsReference</span></span>  
 <span data-ttu-id="ac2c1-111">Chcete-li vygenerovat odkaz na informace o objektu, který je platný podle schématu, které aplikaci popisuje, použijte <xref:System.Runtime.Serialization.DataContractAttribute> atribut na typ a nastavte <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> příznak `true`.</span><span class="sxs-lookup"><span data-stu-id="ac2c1-111">To generate object reference information that is valid according to the schema that describes it, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a type, and set the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flag to `true`.</span></span> <span data-ttu-id="ac2c1-112">Pomocí `IsReference` v předchozím příkladu třída `X`:</span><span class="sxs-lookup"><span data-stu-id="ac2c1-112">Using `IsReference` in the previous example class `X`:</span></span>  
  
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
  
 <span data-ttu-id="ac2c1-113">Vygenerovaný kód XML je následující:</span><span class="sxs-lookup"><span data-stu-id="ac2c1-113">The generated XML is as follows:</span></span>  
  
 `<X>`  
  
 `<A id="1">`  
  
 `<Value>contents of A</Value>`  
  
 `</A>`  
  
 `<B ref="1">`  
  
 `</B>`  
  
 `</X>`  
  
 <span data-ttu-id="ac2c1-114">Pomocí `IsReference` zajišťuje dodržování předpisů na zprávu verzemi.</span><span class="sxs-lookup"><span data-stu-id="ac2c1-114">Using `IsReference` ensures compliance on message round-tripping.</span></span> <span data-ttu-id="ac2c1-115">Bez něj při generování typ ze schématu, co se odesílá zpět jako XML pro, že typ není nutně kompatibilní s původně předpokládá, že schéma.</span><span class="sxs-lookup"><span data-stu-id="ac2c1-115">Without it, when a type is generated from schema, what is sent back as XML for that type is not necessarily compatible with the schema originally assumed.</span></span> <span data-ttu-id="ac2c1-116">Jinými slovy i když `id` a `ref` atributy byly serializován, původní schématu může mít zavřené tyto atributy (nebo všechny) ze které se vyskytují v kódu XML.</span><span class="sxs-lookup"><span data-stu-id="ac2c1-116">In other words, although the `id` and `ref` attributes were serialized, the original schema could have barred these attributes (or all attributes) from occurring in the XML.</span></span> <span data-ttu-id="ac2c1-117">S `IsReference` použít na datový člen, člen nadále získat renomé jako "kde" v případě roundtripped.</span><span class="sxs-lookup"><span data-stu-id="ac2c1-117">With `IsReference` applied to a data member, the member continues to be recognized as "referenceable" when roundtripped.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac2c1-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac2c1-118">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference%2A>
