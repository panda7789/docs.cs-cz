---
title: 'Postupy: Vytvoření základního kontraktu dat pro třídu nebo strukturu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
ms.openlocfilehash: 15c59f3ee7cbefafef7a304cfd1477685fff68f2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968452"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="a74d5-102">Postupy: Vytvoření základního kontraktu dat pro třídu nebo strukturu</span><span class="sxs-lookup"><span data-stu-id="a74d5-102">How to: Create a Basic Data Contract for a Class or Structure</span></span>
<span data-ttu-id="a74d5-103">V tomto tématu se dozvíte o základních krocích k vytvoření kontraktu dat pomocí třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="a74d5-103">This topic shows the basic steps to create a data contract using a class or structure.</span></span> <span data-ttu-id="a74d5-104">Další informace o kontraktech dat a způsobu jejich použití najdete v tématu [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="a74d5-104">For more information about data contracts and how they are used, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="a74d5-105">Kurz, který vás provede kroky pro vytvoření služby a klienta základní Windows Communication Foundation (WCF), najdete v [kurzu Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="a74d5-105">For a tutorial that walks through the steps of creating a basic Windows Communication Foundation (WCF) service and client, see the [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="a74d5-106">Pracovní ukázkovou aplikaci, která se skládá ze základní služby a klienta, najdete v tématu [Základní kontrakt dat](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span><span class="sxs-lookup"><span data-stu-id="a74d5-106">For a working sample application that consists of a basic service and client, see [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span></span>  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="a74d5-107">Vytvoření základního kontraktu dat pro třídu nebo strukturu</span><span class="sxs-lookup"><span data-stu-id="a74d5-107">To create a basic data contract for a class or structure</span></span>  
  
1. <span data-ttu-id="a74d5-108">Deklaruje, že typ obsahuje kontrakt dat použitím <xref:System.Runtime.Serialization.DataContractAttribute> atributu na třídu.</span><span class="sxs-lookup"><span data-stu-id="a74d5-108">Declare that the type has a data contract by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class.</span></span> <span data-ttu-id="a74d5-109">Všimněte si, že všechny veřejné typy, včetně těch, které jsou bez atributů, jsou serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="a74d5-109">Note that all public types, including those without attributes, are serializable.</span></span> <span data-ttu-id="a74d5-110">Odvodí kontrakt dat, <xref:System.Runtime.Serialization.DataContractAttribute> Pokud chybí atribut. <xref:System.Runtime.Serialization.DataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="a74d5-110">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract if the <xref:System.Runtime.Serialization.DataContractAttribute> attribute is absent.</span></span> <span data-ttu-id="a74d5-111">Další informace naleznete v tématu [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="a74d5-111">For more information, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
2. <span data-ttu-id="a74d5-112">Definujte členy (vlastnosti, pole nebo události), které jsou serializovány <xref:System.Runtime.Serialization.DataMemberAttribute> použitím atributu pro každý člen.</span><span class="sxs-lookup"><span data-stu-id="a74d5-112">Define the members (properties, fields, or events) that are serialized by applying the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each member.</span></span> <span data-ttu-id="a74d5-113">Tito členové se nazývají datové členy.</span><span class="sxs-lookup"><span data-stu-id="a74d5-113">These members are called data members.</span></span> <span data-ttu-id="a74d5-114">Ve výchozím nastavení jsou všechny veřejné typy serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="a74d5-114">By default, all public types are serializable.</span></span> <span data-ttu-id="a74d5-115">Další informace naleznete v tématu [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="a74d5-115">For more information, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a74d5-116">Můžete použít <xref:System.Runtime.Serialization.DataMemberAttribute> atribut na soukromá pole, což způsobí, že budou data zveřejněna ostatním.</span><span class="sxs-lookup"><span data-stu-id="a74d5-116">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to private fields, causing the data to be exposed to others.</span></span> <span data-ttu-id="a74d5-117">Ujistěte se, že člen neobsahuje citlivá data.</span><span class="sxs-lookup"><span data-stu-id="a74d5-117">Be sure that the member does not contain sensitive data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a74d5-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="a74d5-118">Example</span></span>  
 <span data-ttu-id="a74d5-119">Následující příklad ukazuje, jak vytvořit kontrakt dat pro `Person` typ <xref:System.Runtime.Serialization.DataContractAttribute> použitím atributů a <xref:System.Runtime.Serialization.DataMemberAttribute> pro třídu a její členy.</span><span class="sxs-lookup"><span data-stu-id="a74d5-119">The following example shows how to create a data contract for the `Person` type by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a74d5-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a74d5-120">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="a74d5-121">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="a74d5-121">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="a74d5-122">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="a74d5-122">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)
- [<span data-ttu-id="a74d5-123">Začínáme</span><span class="sxs-lookup"><span data-stu-id="a74d5-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
