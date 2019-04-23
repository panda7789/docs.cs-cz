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
ms.openlocfilehash: 4e5e6b77cdb13c17557f176a37fbb9e7d42ab667
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345999"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="64589-102">Postupy: Vytvoření základního kontraktu dat pro třídu nebo strukturu</span><span class="sxs-lookup"><span data-stu-id="64589-102">How to: Create a Basic Data Contract for a Class or Structure</span></span>
<span data-ttu-id="64589-103">Toto téma popisuje základní kroky k vytvoření kontraktu dat pomocí třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="64589-103">This topic shows the basic steps to create a data contract using a class or structure.</span></span> <span data-ttu-id="64589-104">Další informace o kontraktech dat a způsob jejich použití naleznete v tématu [kontraktů dat pomocí](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="64589-104">For more information about data contracts and how they are used, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="64589-105">Kurz vás provede kroky k vytvoření základní služby Windows Communication Foundation (WCF) a klienta, najdete v tématu [kurz Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="64589-105">For a tutorial that walks through the steps of creating a basic Windows Communication Foundation (WCF) service and client, see the [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="64589-106">Ukázkové aplikace práci, která se skládá klienta a služby na úrovni basic, naleznete v tématu [základní kontrakt dat](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span><span class="sxs-lookup"><span data-stu-id="64589-106">For a working sample application that consists of a basic service and client, see [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span></span>  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="64589-107">Vytvoření základního kontraktu dat pro třídu nebo strukturu</span><span class="sxs-lookup"><span data-stu-id="64589-107">To create a basic data contract for a class or structure</span></span>  
  
1. <span data-ttu-id="64589-108">Deklarujte, že má typ kontraktu dat použitím <xref:System.Runtime.Serialization.DataContractAttribute> atribut třídy.</span><span class="sxs-lookup"><span data-stu-id="64589-108">Declare that the type has a data contract by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class.</span></span> <span data-ttu-id="64589-109">Všimněte si, že všechny veřejné typy, včetně těch bez atributy, jsou serializovatelné.</span><span class="sxs-lookup"><span data-stu-id="64589-109">Note that all public types, including those without attributes, are serializable.</span></span> <span data-ttu-id="64589-110"><xref:System.Runtime.Serialization.DataContractSerializer> Odvodí kontraktu dat, pokud <xref:System.Runtime.Serialization.DataContractAttribute> atribut chybí.</span><span class="sxs-lookup"><span data-stu-id="64589-110">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract if the <xref:System.Runtime.Serialization.DataContractAttribute> attribute is absent.</span></span> <span data-ttu-id="64589-111">Další informace najdete v tématu [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="64589-111">For more information, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
2. <span data-ttu-id="64589-112">Definování členů (vlastnosti, pole nebo události), které jsou serializovány použitím <xref:System.Runtime.Serialization.DataMemberAttribute> atribut pro každého člena.</span><span class="sxs-lookup"><span data-stu-id="64589-112">Define the members (properties, fields, or events) that are serialized by applying the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each member.</span></span> <span data-ttu-id="64589-113">Tyto členy, se nazývají datové členy.</span><span class="sxs-lookup"><span data-stu-id="64589-113">These members are called data members.</span></span> <span data-ttu-id="64589-114">Standardně jsou všechny veřejné typy serializovatelné.</span><span class="sxs-lookup"><span data-stu-id="64589-114">By default, all public types are serializable.</span></span> <span data-ttu-id="64589-115">Další informace najdete v tématu [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="64589-115">For more information, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="64589-116">Můžete použít <xref:System.Runtime.Serialization.DataMemberAttribute> atribut k privátním položkám, způsobí data, která mají být vystaveny ostatním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="64589-116">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to private fields, causing the data to be exposed to others.</span></span> <span data-ttu-id="64589-117">Ujistěte se, že člen neobsahuje citlivá data.</span><span class="sxs-lookup"><span data-stu-id="64589-117">Be sure that the member does not contain sensitive data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64589-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="64589-118">Example</span></span>  
 <span data-ttu-id="64589-119">Následující příklad ukazuje způsob vytvoření kontraktu dat pro `Person` typ použitím <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> atributy třídy a jejích členů.</span><span class="sxs-lookup"><span data-stu-id="64589-119">The following example shows how to create a data contract for the `Person` type by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="64589-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64589-120">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="64589-121">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="64589-121">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="64589-122">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="64589-122">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)
- [<span data-ttu-id="64589-123">Začínáme</span><span class="sxs-lookup"><span data-stu-id="64589-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
