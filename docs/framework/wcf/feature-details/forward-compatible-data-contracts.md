---
title: "Kontrakty dat s dopřednou kompatibilitou"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], forward compatibility
ms.assetid: 413c9044-26f8-4ecb-968c-18495ea52cd9
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5ffd4a09de508a2353af356863f9e4f41fc253e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="forward-compatible-data-contracts"></a><span data-ttu-id="9a8b0-102">Kontrakty dat s dopřednou kompatibilitou</span><span class="sxs-lookup"><span data-stu-id="9a8b0-102">Forward-Compatible Data Contracts</span></span>
<span data-ttu-id="9a8b0-103">Funkce [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] systém kontraktu dat je, že kontrakty můžete vyvíjet pevných způsoby se v čase.</span><span class="sxs-lookup"><span data-stu-id="9a8b0-103">A feature of the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] data contract system is that contracts can evolve over time in nonbreaking ways.</span></span> <span data-ttu-id="9a8b0-104">To znamená klient se starší verzí systému kontraktu dat může komunikovat se službou novější verzi stejné kontrakt dat nebo klient novější verzi kontraktu dat může komunikovat s starší verze stejné kontrakt dat.</span><span class="sxs-lookup"><span data-stu-id="9a8b0-104">That is, a client with an older version of a data contract can communicate with a service with a newer version of the same data contract, or a client with a newer version of a data contract can communicate with an older version of the same data contract.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="9a8b0-105">[Osvědčené postupy: Správa verzí kontraktů dat](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="9a8b0-105"> [Best Practices: Data Contract Versioning](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md).</span></span>  
  
 <span data-ttu-id="9a8b0-106">Většina funkcí správy verzí na podle potřeby můžete použít při vytváření nové verze existující smlouvy data.</span><span class="sxs-lookup"><span data-stu-id="9a8b0-106">You can apply most of the versioning features on an as-needed basis when new versions of an existing data contract are created.</span></span> <span data-ttu-id="9a8b0-107">Ale jedna z funkcí správy verzí, *odezvy*, musí být typu z první verze součástí správné fungování.</span><span class="sxs-lookup"><span data-stu-id="9a8b0-107">However, one versioning feature, *round-tripping*, must be built into the type from the first version in order to work properly.</span></span>  
  
## <a name="round-tripping"></a><span data-ttu-id="9a8b0-108">Odezvy</span><span class="sxs-lookup"><span data-stu-id="9a8b0-108">Round-Tripping</span></span>  
 <span data-ttu-id="9a8b0-109">Odezvy nastane, když data předává z novou verzi na předchozí verzi a zpět na novou verzi sady kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="9a8b0-109">Round-tripping occurs when data passes from a new version to an old version and back to the new version of a data contract.</span></span> <span data-ttu-id="9a8b0-110">Odezvy zaručuje, že je ztracena žádná data.</span><span class="sxs-lookup"><span data-stu-id="9a8b0-110">Round-tripping guarantees that no data is lost.</span></span> <span data-ttu-id="9a8b0-111">Povolení odezvy díky typ dopřednou s všechny budoucí změny nepodporuje kontrakt datový model správy verzí.</span><span class="sxs-lookup"><span data-stu-id="9a8b0-111">Enabling round-tripping makes the type forward-compatible with any future changes supported by the data contract versioning model.</span></span>  
  
 <span data-ttu-id="9a8b0-112">Pokud chcete povolit odezvy pro určitý typ, musí typ implementovat <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9a8b0-112">To enable round-tripping for a particular type, the type must implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface.</span></span> <span data-ttu-id="9a8b0-113">Rozhraní obsahuje jednu vlastnost <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> (vrácení <xref:System.Runtime.Serialization.ExtensionDataObject> typ).</span><span class="sxs-lookup"><span data-stu-id="9a8b0-113">The interface contains one property, <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> (returning the <xref:System.Runtime.Serialization.ExtensionDataObject> type).</span></span> <span data-ttu-id="9a8b0-114">Vlastnost ukládá všechna data v budoucích verzích kontrakt dat, který neznámý na aktuální verzi.</span><span class="sxs-lookup"><span data-stu-id="9a8b0-114">The property stores any data from future versions of the data contract that is unknown to the current version.</span></span>  
  
### <a name="example"></a><span data-ttu-id="9a8b0-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="9a8b0-115">Example</span></span>  
 <span data-ttu-id="9a8b0-116">Následující kontrakt dat není dopřednou budoucí změny.</span><span class="sxs-lookup"><span data-stu-id="9a8b0-116">The following data contract is not forward-compatible with future changes.</span></span>  
  
 [!code-csharp[C_DataContract#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#7)]
 [!code-vb[C_DataContract#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#7)]  
  
 <span data-ttu-id="9a8b0-117">Chcete-li typ kompatibilní s budoucí změny (jako je například přidávání nového člena dat s názvem "phoneNumber"), implementovat <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9a8b0-117">To make the type compatible with future changes (such as adding a new data member named "phoneNumber"), implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface.</span></span>  
  
 [!code-csharp[C_DataContract#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#8)]
 [!code-vb[C_DataContract#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#8)]  
  
 <span data-ttu-id="9a8b0-118">Když [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury zaznamená data, která není součástí původní kontrakt dat, data jsou uložené v určité vlastnosti a zachovají.</span><span class="sxs-lookup"><span data-stu-id="9a8b0-118">When the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure encounters data that is not part of the original data contract, the data is stored in the property and preserved.</span></span> <span data-ttu-id="9a8b0-119">Jiným způsobem s výjimkou dočasné úložiště není zpracován.</span><span class="sxs-lookup"><span data-stu-id="9a8b0-119">It is not processed in any other way except for temporary storage.</span></span> <span data-ttu-id="9a8b0-120">Pokud objekt se vrátí zpět na místo původu, vrátí se také původní data (neznámé).</span><span class="sxs-lookup"><span data-stu-id="9a8b0-120">If the object is returned back to where it originated, the original (unknown) data is also returned.</span></span> <span data-ttu-id="9a8b0-121">Proto data udělal dobu odezvy na a z původní koncového bodu bez ztráty.</span><span class="sxs-lookup"><span data-stu-id="9a8b0-121">Therefore, the data has made a round trip to and from the originating endpoint without loss.</span></span> <span data-ttu-id="9a8b0-122">Upozorňujeme však, že v případě potřeby data ke zpracování výchozí koncový bod této očekávání je unmet, a koncový bod musí nějakým způsobem zjistit a uložení změn.</span><span class="sxs-lookup"><span data-stu-id="9a8b0-122">Note, however, that if the originating endpoint required the data to be processed, that expectation is unmet, and the endpoint must somehow detect and accommodate the change.</span></span>  
  
 <span data-ttu-id="9a8b0-123"><xref:System.Runtime.Serialization.ExtensionDataObject> Typ obsahuje žádné veřejné metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9a8b0-123">The <xref:System.Runtime.Serialization.ExtensionDataObject> type contains no public methods or properties.</span></span> <span data-ttu-id="9a8b0-124">Proto není možné získat přímý přístup k datům uloženým v <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9a8b0-124">Thus, it is impossible to get direct access to the data stored inside the <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> property.</span></span>  
  
 <span data-ttu-id="9a8b0-125">Funkci odezvy může být vypnutý, buď nastavením `ignoreExtensionDataObject` k `true` v <xref:System.Runtime.Serialization.DataContractSerializer> konstruktor nebo nastavením <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> vlastnost `true` na <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9a8b0-125">The round-tripping feature may be turned off, either by setting `ignoreExtensionDataObject` to `true` in the <xref:System.Runtime.Serialization.DataContractSerializer> constructor or by setting the <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> property to `true` on the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="9a8b0-126">Když tato funkce je vypnutá, nebudou naplnit deserializátor <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> vlastnost a serializátor, nebude emitování obsah vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9a8b0-126">When this feature is off, the deserializer will not populate the <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> property, and the serializer will not emit the contents of the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a8b0-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a8b0-127">See Also</span></span>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 <xref:System.Runtime.Serialization.ExtensionDataObject>  
 [<span data-ttu-id="9a8b0-128">Správa verzí kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="9a8b0-128">Data Contract Versioning</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)  
 [<span data-ttu-id="9a8b0-129">Osvědčené postupy: Správa verzí kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="9a8b0-129">Best Practices: Data Contract Versioning</span></span>](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)
