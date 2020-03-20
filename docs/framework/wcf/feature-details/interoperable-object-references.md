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
# <a name="interoperable-object-references"></a><span data-ttu-id="86308-102">Interoperabilní odkazy na objekty</span><span class="sxs-lookup"><span data-stu-id="86308-102">Interoperable object references</span></span>
<span data-ttu-id="86308-103">Ve výchozím <xref:System.Runtime.Serialization.DataContractSerializer> nastavení serializuje objekty podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="86308-103">By default, <xref:System.Runtime.Serialization.DataContractSerializer> serializes objects by value.</span></span> <span data-ttu-id="86308-104"><xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> Vlastnost můžete použít k pokynu serializátoru kontraktu dat k zachování odkazů na objekty při serializaci objektů.</span><span class="sxs-lookup"><span data-stu-id="86308-104">You can use the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> property to instruct the data contract serializer to preserve object references when serializing objects.</span></span>  
  
## <a name="generated-xml"></a><span data-ttu-id="86308-105">Vygenerovaný kód XML</span><span class="sxs-lookup"><span data-stu-id="86308-105">Generated XML</span></span>  
 <span data-ttu-id="86308-106">Jako příklad zvažte následující objekt:</span><span class="sxs-lookup"><span data-stu-id="86308-106">As an example, consider the following object:</span></span>  
  
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
  
 <span data-ttu-id="86308-107">S <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> nastavenou na `false` (výchozí) se vygeneruje následující XML:</span><span class="sxs-lookup"><span data-stu-id="86308-107">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `false` (the default), the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <span data-ttu-id="86308-108">S <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> nastavenou na `true`, je generován následující XML:</span><span class="sxs-lookup"><span data-stu-id="86308-108">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `true`, the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 <span data-ttu-id="86308-109">Však <xref:System.Runtime.Serialization.XsdDataContractExporter> `id` nepopisuje atributy `ref` a v jeho schématu, `preserveObjectReferences` i když je `true`vlastnost nastavena na .</span><span class="sxs-lookup"><span data-stu-id="86308-109">However, <xref:System.Runtime.Serialization.XsdDataContractExporter> doesn't describe the `id` and `ref` attributes in its schema, even when the `preserveObjectReferences` property is set to `true`.</span></span>  
  
## <a name="using-isreference"></a><span data-ttu-id="86308-110">Použití odkazu IsReference</span><span class="sxs-lookup"><span data-stu-id="86308-110">Using IsReference</span></span>  
 <span data-ttu-id="86308-111">Chcete-li generovat informace o odkazu na objekt, které jsou platné <xref:System.Runtime.Serialization.DataContractAttribute> podle schématu, které <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> jej `true`popisuje, použijte atribut pro typ a nastavte příznak na .</span><span class="sxs-lookup"><span data-stu-id="86308-111">To generate object reference information that's valid according to the schema that describes it, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a type, and set the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flag to `true`.</span></span> <span data-ttu-id="86308-112">Následující příklad upravuje třídu `X` v předchozím příkladu přidáním `IsReference`:</span><span class="sxs-lookup"><span data-stu-id="86308-112">The following example modifies class `X` in the previous example by adding `IsReference`:</span></span>  
  
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

 <span data-ttu-id="86308-113">Vygenerovaný xml je následující:</span><span class="sxs-lookup"><span data-stu-id="86308-113">The generated XML is as follows:</span></span>  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A>
    <B ref="1"></B>  
</X>
```  
  
 <span data-ttu-id="86308-114">Použití `IsReference` zajišťuje dodržování předpisů při zakopnutí zpráv.</span><span class="sxs-lookup"><span data-stu-id="86308-114">Using `IsReference` ensures compliance on message round-tripping.</span></span> <span data-ttu-id="86308-115">Bez něj, když je typ generován ze schématu, výstup XML pro tento typ není nutně kompatibilní se schématem původně předpokládal.</span><span class="sxs-lookup"><span data-stu-id="86308-115">Without it, when a type is generated from schema, the XML output for that type isn't necessarily compatible with the schema originally assumed.</span></span> <span data-ttu-id="86308-116">Jinými slovy, `id` i `ref` když atributy a byly serializovány, původní schéma mohlo zabránit výskytu těchto atributů (nebo všech atributů) v XML.</span><span class="sxs-lookup"><span data-stu-id="86308-116">In other words, although the `id` and `ref` attributes were serialized, the original schema could have barred these attributes (or all attributes) from occurring in the XML.</span></span> <span data-ttu-id="86308-117">Při `IsReference` použití na datový člen člen i nadále rozpoznán jako *odkazovatelný* při zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="86308-117">With `IsReference` applied to a data member, the member continues to be recognized as *referenceable* when round-tripped.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86308-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="86308-118">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
