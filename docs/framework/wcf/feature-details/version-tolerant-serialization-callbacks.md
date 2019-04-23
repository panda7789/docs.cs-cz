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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124628"
---
# <a name="version-tolerant-serialization-callbacks"></a><span data-ttu-id="6c509-102">Zpětná volání serializace tolerantní k verzím</span><span class="sxs-lookup"><span data-stu-id="6c509-102">Version-Tolerant Serialization Callbacks</span></span>
<span data-ttu-id="6c509-103">Programovací model kontraktu dat plně podporuje metody zpětného volání serializace tolerantní, který <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> třídy podporu.</span><span class="sxs-lookup"><span data-stu-id="6c509-103">The data contract programming model fully supports the version-tolerant serialization callback methods that the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes support.</span></span>  
  
## <a name="version-tolerant-attributes"></a><span data-ttu-id="6c509-104">Verze chybám atributy</span><span class="sxs-lookup"><span data-stu-id="6c509-104">Version-Tolerant Attributes</span></span>  
 <span data-ttu-id="6c509-105">Existují čtyři atributy zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="6c509-105">There are four callback attributes.</span></span> <span data-ttu-id="6c509-106">Každý atribut lze použít pro metodu, která volá modul pro serializaci nebo deserializaci v různých časech.</span><span class="sxs-lookup"><span data-stu-id="6c509-106">Each attribute can be applied to a method that the serialization/deserialization engine calls at various times.</span></span> <span data-ttu-id="6c509-107">Následující tabulka vysvětluje, kdy používat jednotlivé atributy.</span><span class="sxs-lookup"><span data-stu-id="6c509-107">The table below explains when to use each attribute.</span></span>  
  
|<span data-ttu-id="6c509-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="6c509-108">Attribute</span></span>|<span data-ttu-id="6c509-109">Když je volána odpovídající – metoda</span><span class="sxs-lookup"><span data-stu-id="6c509-109">When the corresponding method is called</span></span>|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="6c509-110">Volá se před serializací typu.</span><span class="sxs-lookup"><span data-stu-id="6c509-110">Called before serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="6c509-111">Volá se po serializaci typu.</span><span class="sxs-lookup"><span data-stu-id="6c509-111">Called after serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="6c509-112">Volá se před deserializace typu.</span><span class="sxs-lookup"><span data-stu-id="6c509-112">Called before deserializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="6c509-113">Volá se po deserializace typu.</span><span class="sxs-lookup"><span data-stu-id="6c509-113">Called after deserializing the type.</span></span>|  
  
 <span data-ttu-id="6c509-114">Metody, musíte přijmout <xref:System.Runtime.Serialization.StreamingContext> parametru.</span><span class="sxs-lookup"><span data-stu-id="6c509-114">The methods must accept a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span>  
  
 <span data-ttu-id="6c509-115">Tyto metody jsou primárně určeny pro použití se službou správy verzí nebo inicializace.</span><span class="sxs-lookup"><span data-stu-id="6c509-115">These methods are primarily intended for use with versioning or initialization.</span></span> <span data-ttu-id="6c509-116">Během deserializace nejsou volány žádné konstruktory.</span><span class="sxs-lookup"><span data-stu-id="6c509-116">During deserialization, no constructors are called.</span></span> <span data-ttu-id="6c509-117">Proto se datové členy nemusí být správně inicializován (na určený výchozí hodnoty) Pokud jsou data pro tyto členy, chybí v příchozím datovém proudu, například pokud data pocházejí z předchozí verze typu, který chybí některé datové členy.</span><span class="sxs-lookup"><span data-stu-id="6c509-117">Therefore, data members may not be correctly initialized (to intended default values) if the data for these members is missing in the incoming stream, for example, if the data comes from a previous version of a type that is missing some data members.</span></span> <span data-ttu-id="6c509-118">Když to pokud chcete opravit, použijte metodu zpětného volání označenou pomocí <xref:System.Runtime.Serialization.OnDeserializingAttribute>, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6c509-118">To correct this, use the callback method marked with the <xref:System.Runtime.Serialization.OnDeserializingAttribute>, as shown in the following example.</span></span>  
  
 <span data-ttu-id="6c509-119">Můžete označit jenom jednu metodu na typ s každým z předchozí atributy zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="6c509-119">You can mark only one method per type with each of the preceding callback attributes.</span></span>  
  
### <a name="example"></a><span data-ttu-id="6c509-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c509-120">Example</span></span>  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="6c509-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c509-121">See also</span></span>

- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- [<span data-ttu-id="6c509-122">Serializace tolerantní vůči verzím (VTS)</span><span class="sxs-lookup"><span data-stu-id="6c509-122">Version Tolerant Serialization</span></span>](../../../../docs/standard/serialization/version-tolerant-serialization.md)
