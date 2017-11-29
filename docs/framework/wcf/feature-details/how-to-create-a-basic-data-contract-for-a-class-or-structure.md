---
title: "Postupy: vytvoření kontraktu základní Data pro třídu nebo strukturu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
caps.latest.revision: "25"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6c5f82e2445e816c4e577e6ce5b0c8c4e2359221
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="7c59a-102">Postupy: vytvoření kontraktu základní Data pro třídu nebo strukturu</span><span class="sxs-lookup"><span data-stu-id="7c59a-102">How to: Create a Basic Data Contract for a Class or Structure</span></span>
<span data-ttu-id="7c59a-103">Toto téma ukazuje základní kroky pro vytvoření kontraktu dat pomocí třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="7c59a-103">This topic shows the basic steps to create a data contract using a class or structure.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="7c59a-104">měnící data a jak se používají, najdete v části [pomocí kontrakty dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="7c59a-104"> data contracts and how they are used, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="7c59a-105">Kurz, který vás provede kroky k vytvoření základního [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby a klienta, najdete v článku [kurzu Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="7c59a-105">For a tutorial that walks through the steps of creating a basic [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service and client, see the [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="7c59a-106">Pracovní ukázkovou aplikaci, která se skládá z klienta a služby na úrovni basic, najdete v části [základní kontrakt dat](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span><span class="sxs-lookup"><span data-stu-id="7c59a-106">For a working sample application that consists of a basic service and client, see [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span></span>  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="7c59a-107">K vytvoření kontraktu základní data pro třídu nebo strukturu</span><span class="sxs-lookup"><span data-stu-id="7c59a-107">To create a basic data contract for a class or structure</span></span>  
  
1.  <span data-ttu-id="7c59a-108">Deklarovat, zda má tento typ kontraktu dat s použitím <xref:System.Runtime.Serialization.DataContractAttribute> atribut třídy.</span><span class="sxs-lookup"><span data-stu-id="7c59a-108">Declare that the type has a data contract by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class.</span></span> <span data-ttu-id="7c59a-109">Upozorňujeme, že jsou všechny veřejné typy, včetně těch bez atributy, serializable.</span><span class="sxs-lookup"><span data-stu-id="7c59a-109">Note that all public types, including those without attributes, are serializable.</span></span> <span data-ttu-id="7c59a-110"><xref:System.Runtime.Serialization.DataContractSerializer> Odvodí kontraktu dat, pokud <xref:System.Runtime.Serialization.DataContractAttribute> chybí atribut.</span><span class="sxs-lookup"><span data-stu-id="7c59a-110">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract if the <xref:System.Runtime.Serialization.DataContractAttribute> attribute is absent.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="7c59a-111">[Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="7c59a-111"> [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
2.  <span data-ttu-id="7c59a-112">Definování členů (vlastnosti, pole nebo události), které jsou serializovány použitím <xref:System.Runtime.Serialization.DataMemberAttribute> atribut pro každého člena.</span><span class="sxs-lookup"><span data-stu-id="7c59a-112">Define the members (properties, fields, or events) that are serialized by applying the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each member.</span></span> <span data-ttu-id="7c59a-113">Tito členové se nazývají datových členů.</span><span class="sxs-lookup"><span data-stu-id="7c59a-113">These members are called data members.</span></span> <span data-ttu-id="7c59a-114">Všechny veřejné typy jsou ve výchozím nastavení, serializable.</span><span class="sxs-lookup"><span data-stu-id="7c59a-114">By default, all public types are serializable.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="7c59a-115">[Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="7c59a-115"> [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7c59a-116">Můžete použít <xref:System.Runtime.Serialization.DataMemberAttribute> atribut privátním polím, způsobuje data, která mají být zpřístupněny ostatním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="7c59a-116">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to private fields, causing the data to be exposed to others.</span></span> <span data-ttu-id="7c59a-117">Ujistěte se, zda člen neobsahuje citlivá data.</span><span class="sxs-lookup"><span data-stu-id="7c59a-117">Be sure that the member does not contain sensitive data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c59a-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c59a-118">Example</span></span>  
 <span data-ttu-id="7c59a-119">Následující příklad ukazuje postup vytvoření kontraktu dat pro `Person` typ použitím <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> atributy třídy a její členy.</span><span class="sxs-lookup"><span data-stu-id="7c59a-119">The following example shows how to create a data contract for the `Person` type by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7c59a-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c59a-120">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [<span data-ttu-id="7c59a-121">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="7c59a-121">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="7c59a-122">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="7c59a-122">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [<span data-ttu-id="7c59a-123">Začínáme</span><span class="sxs-lookup"><span data-stu-id="7c59a-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
