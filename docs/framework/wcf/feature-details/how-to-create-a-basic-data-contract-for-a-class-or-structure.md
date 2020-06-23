---
title: 'Postupy: Vytvoření základního kontraktu dat pro třídu nebo strukturu'
description: Podle tohoto příkladu se dozvíte, jak vytvořit kontrakt dat pomocí třídy nebo struktury v technologii WCF pomocí atributu DataContractAttribute.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
ms.openlocfilehash: a45fde58795947c3e46fa45750ae1a3faddd8849
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247166"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="00169-103">Postupy: Vytvoření základního kontraktu dat pro třídu nebo strukturu</span><span class="sxs-lookup"><span data-stu-id="00169-103">How to: Create a Basic Data Contract for a Class or Structure</span></span>
<span data-ttu-id="00169-104">V tomto tématu se dozvíte o základních krocích k vytvoření kontraktu dat pomocí třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="00169-104">This topic shows the basic steps to create a data contract using a class or structure.</span></span> <span data-ttu-id="00169-105">Další informace o kontraktech dat a způsobu jejich použití najdete v tématu [Použití kontraktů dat](using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="00169-105">For more information about data contracts and how they are used, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="00169-106">Kurz, který vás provede kroky pro vytvoření služby a klienta základní Windows Communication Foundation (WCF), najdete v [kurzu Začínáme](../getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="00169-106">For a tutorial that walks through the steps of creating a basic Windows Communication Foundation (WCF) service and client, see the [Getting Started Tutorial](../getting-started-tutorial.md).</span></span> <span data-ttu-id="00169-107">Pracovní ukázkovou aplikaci, která se skládá ze základní služby a klienta, najdete v tématu [Základní kontrakt dat](../samples/basic-data-contract.md).</span><span class="sxs-lookup"><span data-stu-id="00169-107">For a working sample application that consists of a basic service and client, see [Basic Data Contract](../samples/basic-data-contract.md).</span></span>  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="00169-108">Vytvoření základního kontraktu dat pro třídu nebo strukturu</span><span class="sxs-lookup"><span data-stu-id="00169-108">To create a basic data contract for a class or structure</span></span>  
  
1. <span data-ttu-id="00169-109">Deklaruje, že typ obsahuje kontrakt dat použitím <xref:System.Runtime.Serialization.DataContractAttribute> atributu na třídu.</span><span class="sxs-lookup"><span data-stu-id="00169-109">Declare that the type has a data contract by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class.</span></span> <span data-ttu-id="00169-110">Všimněte si, že všechny veřejné typy, včetně těch, které jsou bez atributů, jsou serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="00169-110">Note that all public types, including those without attributes, are serializable.</span></span> <span data-ttu-id="00169-111"><xref:System.Runtime.Serialization.DataContractSerializer>Odvodí kontrakt dat, pokud chybí <xref:System.Runtime.Serialization.DataContractAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="00169-111">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract if the <xref:System.Runtime.Serialization.DataContractAttribute> attribute is absent.</span></span> <span data-ttu-id="00169-112">Další informace naleznete v tématu [Serializovatelné typy](serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="00169-112">For more information, see [Serializable Types](serializable-types.md).</span></span>  
  
2. <span data-ttu-id="00169-113">Definujte členy (vlastnosti, pole nebo události), které jsou serializovány použitím <xref:System.Runtime.Serialization.DataMemberAttribute> atributu pro každý člen.</span><span class="sxs-lookup"><span data-stu-id="00169-113">Define the members (properties, fields, or events) that are serialized by applying the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each member.</span></span> <span data-ttu-id="00169-114">Tito členové se nazývají datové členy.</span><span class="sxs-lookup"><span data-stu-id="00169-114">These members are called data members.</span></span> <span data-ttu-id="00169-115">Ve výchozím nastavení jsou všechny veřejné typy serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="00169-115">By default, all public types are serializable.</span></span> <span data-ttu-id="00169-116">Další informace naleznete v tématu [Serializovatelné typy](serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="00169-116">For more information, see [Serializable Types](serializable-types.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="00169-117">Můžete použít <xref:System.Runtime.Serialization.DataMemberAttribute> atribut na soukromá pole, což způsobí, že budou data zveřejněna ostatním.</span><span class="sxs-lookup"><span data-stu-id="00169-117">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to private fields, causing the data to be exposed to others.</span></span> <span data-ttu-id="00169-118">Ujistěte se, že člen neobsahuje citlivá data.</span><span class="sxs-lookup"><span data-stu-id="00169-118">Be sure that the member does not contain sensitive data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00169-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="00169-119">Example</span></span>  
 <span data-ttu-id="00169-120">Následující příklad ukazuje, jak vytvořit kontrakt dat pro `Person` typ použitím <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> atributů a pro třídu a její členy.</span><span class="sxs-lookup"><span data-stu-id="00169-120">The following example shows how to create a data contract for the `Person` type by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="00169-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="00169-121">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="00169-122">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="00169-122">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="00169-123">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="00169-123">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)
- [<span data-ttu-id="00169-124">Začínáme</span><span class="sxs-lookup"><span data-stu-id="00169-124">Getting Started</span></span>](../samples/getting-started-sample.md)
