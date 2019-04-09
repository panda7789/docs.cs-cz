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
ms.openlocfilehash: da13f9989b427da047c4a94f77907847ed2ae4d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124628"
---
# <a name="version-tolerant-serialization-callbacks"></a><span data-ttu-id="cc3cf-102">Zpětná volání serializace tolerantní k verzím</span><span class="sxs-lookup"><span data-stu-id="cc3cf-102">Version-Tolerant Serialization Callbacks</span></span>
<span data-ttu-id="cc3cf-103">Programovací model kontraktu dat plně podporuje metody zpětného volání serializace tolerantní, který <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> třídy podporu.</span><span class="sxs-lookup"><span data-stu-id="cc3cf-103">The data contract programming model fully supports the version-tolerant serialization callback methods that the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes support.</span></span>  
  
## <a name="version-tolerant-attributes"></a><span data-ttu-id="cc3cf-104">Verze chybám atributy</span><span class="sxs-lookup"><span data-stu-id="cc3cf-104">Version-Tolerant Attributes</span></span>  
 <span data-ttu-id="cc3cf-105">Existují čtyři atributy zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="cc3cf-105">There are four callback attributes.</span></span> <span data-ttu-id="cc3cf-106">Každý atribut lze použít pro metodu, která volá modul pro serializaci nebo deserializaci v různých časech.</span><span class="sxs-lookup"><span data-stu-id="cc3cf-106">Each attribute can be applied to a method that the serialization/deserialization engine calls at various times.</span></span> <span data-ttu-id="cc3cf-107">Následující tabulka vysvětluje, kdy používat jednotlivé atributy.</span><span class="sxs-lookup"><span data-stu-id="cc3cf-107">The table below explains when to use each attribute.</span></span>  
  
|<span data-ttu-id="cc3cf-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="cc3cf-108">Attribute</span></span>|<span data-ttu-id="cc3cf-109">Když je volána odpovídající – metoda</span><span class="sxs-lookup"><span data-stu-id="cc3cf-109">When the corresponding method is called</span></span>|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="cc3cf-110">Volá se před serializací typu.</span><span class="sxs-lookup"><span data-stu-id="cc3cf-110">Called before serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="cc3cf-111">Volá se po serializaci typu.</span><span class="sxs-lookup"><span data-stu-id="cc3cf-111">Called after serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="cc3cf-112">Volá se před deserializace typu.</span><span class="sxs-lookup"><span data-stu-id="cc3cf-112">Called before deserializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="cc3cf-113">Volá se po deserializace typu.</span><span class="sxs-lookup"><span data-stu-id="cc3cf-113">Called after deserializing the type.</span></span>|  
  
 <span data-ttu-id="cc3cf-114">Metody, musíte přijmout <xref:System.Runtime.Serialization.StreamingContext> parametru.</span><span class="sxs-lookup"><span data-stu-id="cc3cf-114">The methods must accept a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span>  
  
 <span data-ttu-id="cc3cf-115">Tyto metody jsou primárně určeny pro použití se službou správy verzí nebo inicializace.</span><span class="sxs-lookup"><span data-stu-id="cc3cf-115">These methods are primarily intended for use with versioning or initialization.</span></span> <span data-ttu-id="cc3cf-116">Během deserializace nejsou volány žádné konstruktory.</span><span class="sxs-lookup"><span data-stu-id="cc3cf-116">During deserialization, no constructors are called.</span></span> <span data-ttu-id="cc3cf-117">Proto se datové členy nemusí být správně inicializován (na určený výchozí hodnoty) Pokud jsou data pro tyto členy, chybí v příchozím datovém proudu, například pokud data pocházejí z předchozí verze typu, který chybí některé datové členy.</span><span class="sxs-lookup"><span data-stu-id="cc3cf-117">Therefore, data members may not be correctly initialized (to intended default values) if the data for these members is missing in the incoming stream, for example, if the data comes from a previous version of a type that is missing some data members.</span></span> <span data-ttu-id="cc3cf-118">Když to pokud chcete opravit, použijte metodu zpětného volání označenou pomocí <xref:System.Runtime.Serialization.OnDeserializingAttribute>, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="cc3cf-118">To correct this, use the callback method marked with the <xref:System.Runtime.Serialization.OnDeserializingAttribute>, as shown in the following example.</span></span>  
  
 <span data-ttu-id="cc3cf-119">Můžete označit jenom jednu metodu na typ s každým z předchozí atributy zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="cc3cf-119">You can mark only one method per type with each of the preceding callback attributes.</span></span>  
  
### <a name="example"></a><span data-ttu-id="cc3cf-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="cc3cf-120">Example</span></span>  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="cc3cf-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc3cf-121">See also</span></span>

- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- [<span data-ttu-id="cc3cf-122">Serializace tolerantní vůči verzím</span><span class="sxs-lookup"><span data-stu-id="cc3cf-122">Version Tolerant Serialization</span></span>](../../../../docs/standard/serialization/version-tolerant-serialization.md)
