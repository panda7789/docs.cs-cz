---
title: Zpětná volání serializace tolerantní k verzím
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OnDeserializedAttribute [WCF]
- OnDeserializingAttribute [WCF]
- OnSerializingAttribute [WCF]
- serialization [WCF], setting default values
- OnSerializedAttribute [WCF]
ms.assetid: aa4a3a6f-05ec-4efd-bdbf-2181e13e6468
ms.openlocfilehash: 0736f94b1fe1a91b20ee76da673e0bc139aa802a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959558"
---
# <a name="version-tolerant-serialization-callbacks"></a><span data-ttu-id="3a2d3-102">Zpětná volání serializace tolerantní k verzím</span><span class="sxs-lookup"><span data-stu-id="3a2d3-102">Version-Tolerant Serialization Callbacks</span></span>
<span data-ttu-id="3a2d3-103">Model programování kontraktů dat plně podporuje metody zpětného volání serializace odolné proti <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> verzí <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> , které třídy a podporují.</span><span class="sxs-lookup"><span data-stu-id="3a2d3-103">The data contract programming model fully supports the version-tolerant serialization callback methods that the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes support.</span></span>  
  
## <a name="version-tolerant-attributes"></a><span data-ttu-id="3a2d3-104">Atributy odolné vůči verzím</span><span class="sxs-lookup"><span data-stu-id="3a2d3-104">Version-Tolerant Attributes</span></span>  
 <span data-ttu-id="3a2d3-105">Existují čtyři atributy zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="3a2d3-105">There are four callback attributes.</span></span> <span data-ttu-id="3a2d3-106">Každý atribut lze použít na metodu, kterou modul serializace/deserializace volá v různých časech.</span><span class="sxs-lookup"><span data-stu-id="3a2d3-106">Each attribute can be applied to a method that the serialization/deserialization engine calls at various times.</span></span> <span data-ttu-id="3a2d3-107">Následující tabulka vysvětluje, kdy použít jednotlivé atributy.</span><span class="sxs-lookup"><span data-stu-id="3a2d3-107">The table below explains when to use each attribute.</span></span>  
  
|<span data-ttu-id="3a2d3-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="3a2d3-108">Attribute</span></span>|<span data-ttu-id="3a2d3-109">Při volání odpovídající metody</span><span class="sxs-lookup"><span data-stu-id="3a2d3-109">When the corresponding method is called</span></span>|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="3a2d3-110">Volá se před serializací typu.</span><span class="sxs-lookup"><span data-stu-id="3a2d3-110">Called before serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="3a2d3-111">Volá se po serializaci typu.</span><span class="sxs-lookup"><span data-stu-id="3a2d3-111">Called after serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="3a2d3-112">Volá se před deserializací typu.</span><span class="sxs-lookup"><span data-stu-id="3a2d3-112">Called before deserializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="3a2d3-113">Volá se po deserializaci typu.</span><span class="sxs-lookup"><span data-stu-id="3a2d3-113">Called after deserializing the type.</span></span>|  
  
 <span data-ttu-id="3a2d3-114">Metody musí přijmout <xref:System.Runtime.Serialization.StreamingContext> parametr.</span><span class="sxs-lookup"><span data-stu-id="3a2d3-114">The methods must accept a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span>  
  
 <span data-ttu-id="3a2d3-115">Tyto metody jsou primárně určeny pro použití se správou verzí nebo inicializací.</span><span class="sxs-lookup"><span data-stu-id="3a2d3-115">These methods are primarily intended for use with versioning or initialization.</span></span> <span data-ttu-id="3a2d3-116">Během deserializace nejsou volány žádné konstruktory.</span><span class="sxs-lookup"><span data-stu-id="3a2d3-116">During deserialization, no constructors are called.</span></span> <span data-ttu-id="3a2d3-117">Datové členy proto nemusí být správně inicializovány (na zamýšlené výchozí hodnoty), pokud data pro tyto členy chybějí v příchozím datovém proudu, například pokud data pocházejí z předchozí verze typu, ve kterém chybí některé datové členy.</span><span class="sxs-lookup"><span data-stu-id="3a2d3-117">Therefore, data members may not be correctly initialized (to intended default values) if the data for these members is missing in the incoming stream, for example, if the data comes from a previous version of a type that is missing some data members.</span></span> <span data-ttu-id="3a2d3-118">Chcete-li tento problém vyřešit, použijte metodu zpětného <xref:System.Runtime.Serialization.OnDeserializingAttribute>volání označenou, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3a2d3-118">To correct this, use the callback method marked with the <xref:System.Runtime.Serialization.OnDeserializingAttribute>, as shown in the following example.</span></span>  
  
 <span data-ttu-id="3a2d3-119">U každého z předchozích atributů zpětného volání můžete označit jenom jednu metodu na typ.</span><span class="sxs-lookup"><span data-stu-id="3a2d3-119">You can mark only one method per type with each of the preceding callback attributes.</span></span>  
  
### <a name="example"></a><span data-ttu-id="3a2d3-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="3a2d3-120">Example</span></span>  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="3a2d3-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3a2d3-121">See also</span></span>

- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- [<span data-ttu-id="3a2d3-122">Serializace tolerantní vůči verzím (VTS)</span><span class="sxs-lookup"><span data-stu-id="3a2d3-122">Version Tolerant Serialization</span></span>](../../../standard/serialization/version-tolerant-serialization.md)
