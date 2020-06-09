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
ms.openlocfilehash: 0fd7bbea4d6e8d315566aa798ed89a0fd2657f58
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599032"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="5093e-102">Postupy: Vytvoření základního kontraktu dat pro třídu nebo strukturu</span><span class="sxs-lookup"><span data-stu-id="5093e-102">How to: Create a Basic Data Contract for a Class or Structure</span></span>
<span data-ttu-id="5093e-103">V tomto tématu se dozvíte o základních krocích k vytvoření kontraktu dat pomocí třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="5093e-103">This topic shows the basic steps to create a data contract using a class or structure.</span></span> <span data-ttu-id="5093e-104">Další informace o kontraktech dat a způsobu jejich použití najdete v tématu [Použití kontraktů dat](using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="5093e-104">For more information about data contracts and how they are used, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="5093e-105">Kurz, který vás provede kroky pro vytvoření služby a klienta základní Windows Communication Foundation (WCF), najdete v [kurzu Začínáme](../getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="5093e-105">For a tutorial that walks through the steps of creating a basic Windows Communication Foundation (WCF) service and client, see the [Getting Started Tutorial](../getting-started-tutorial.md).</span></span> <span data-ttu-id="5093e-106">Pracovní ukázkovou aplikaci, která se skládá ze základní služby a klienta, najdete v tématu [Základní kontrakt dat](../samples/basic-data-contract.md).</span><span class="sxs-lookup"><span data-stu-id="5093e-106">For a working sample application that consists of a basic service and client, see [Basic Data Contract](../samples/basic-data-contract.md).</span></span>  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="5093e-107">Vytvoření základního kontraktu dat pro třídu nebo strukturu</span><span class="sxs-lookup"><span data-stu-id="5093e-107">To create a basic data contract for a class or structure</span></span>  
  
1. <span data-ttu-id="5093e-108">Deklaruje, že typ obsahuje kontrakt dat použitím <xref:System.Runtime.Serialization.DataContractAttribute> atributu na třídu.</span><span class="sxs-lookup"><span data-stu-id="5093e-108">Declare that the type has a data contract by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class.</span></span> <span data-ttu-id="5093e-109">Všimněte si, že všechny veřejné typy, včetně těch, které jsou bez atributů, jsou serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="5093e-109">Note that all public types, including those without attributes, are serializable.</span></span> <span data-ttu-id="5093e-110"><xref:System.Runtime.Serialization.DataContractSerializer>Odvodí kontrakt dat, pokud chybí <xref:System.Runtime.Serialization.DataContractAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="5093e-110">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract if the <xref:System.Runtime.Serialization.DataContractAttribute> attribute is absent.</span></span> <span data-ttu-id="5093e-111">Další informace naleznete v tématu [Serializovatelné typy](serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="5093e-111">For more information, see [Serializable Types](serializable-types.md).</span></span>  
  
2. <span data-ttu-id="5093e-112">Definujte členy (vlastnosti, pole nebo události), které jsou serializovány použitím <xref:System.Runtime.Serialization.DataMemberAttribute> atributu pro každý člen.</span><span class="sxs-lookup"><span data-stu-id="5093e-112">Define the members (properties, fields, or events) that are serialized by applying the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each member.</span></span> <span data-ttu-id="5093e-113">Tito členové se nazývají datové členy.</span><span class="sxs-lookup"><span data-stu-id="5093e-113">These members are called data members.</span></span> <span data-ttu-id="5093e-114">Ve výchozím nastavení jsou všechny veřejné typy serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="5093e-114">By default, all public types are serializable.</span></span> <span data-ttu-id="5093e-115">Další informace naleznete v tématu [Serializovatelné typy](serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="5093e-115">For more information, see [Serializable Types](serializable-types.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5093e-116">Můžete použít <xref:System.Runtime.Serialization.DataMemberAttribute> atribut na soukromá pole, což způsobí, že budou data zveřejněna ostatním.</span><span class="sxs-lookup"><span data-stu-id="5093e-116">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to private fields, causing the data to be exposed to others.</span></span> <span data-ttu-id="5093e-117">Ujistěte se, že člen neobsahuje citlivá data.</span><span class="sxs-lookup"><span data-stu-id="5093e-117">Be sure that the member does not contain sensitive data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5093e-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="5093e-118">Example</span></span>  
 <span data-ttu-id="5093e-119">Následující příklad ukazuje, jak vytvořit kontrakt dat pro `Person` typ použitím <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> atributů a pro třídu a její členy.</span><span class="sxs-lookup"><span data-stu-id="5093e-119">The following example shows how to create a data contract for the `Person` type by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="5093e-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="5093e-120">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="5093e-121">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="5093e-121">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="5093e-122">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="5093e-122">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)
- [<span data-ttu-id="5093e-123">Začínáme</span><span class="sxs-lookup"><span data-stu-id="5093e-123">Getting Started</span></span>](../samples/getting-started-sample.md)
