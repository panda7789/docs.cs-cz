---
title: "Konfigurace serializace ve službě pracovních postupů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9aa50b8e9f29e5dd14f0ff18d253943a73ef3a0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="fc3c6-102">Konfigurace serializace ve službě pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="fc3c6-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="fc3c6-103">Služby pracovních postupů jsou [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služeb a tak mít možnost buď pomocí <xref:System.Runtime.Serialization.DataContractSerializer> (výchozí) nebo <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="fc3c6-103">Workflow services are [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="fc3c6-104">Při zápisu mimo pracovní postup služby typu serializátoru je zadán pro kontrakt služby nebo operace.</span><span class="sxs-lookup"><span data-stu-id="fc3c6-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="fc3c6-105">Při vytváření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] měnící nezadáte tyto služby pracovních postupů v kódu, ale místo jsou generovány při běhu pomocí odvození kontrakt.</span><span class="sxs-lookup"><span data-stu-id="fc3c6-105">When creating [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="fc3c6-106">Sbalit odvození najdete v tématu [použití kontraktů v pracovním postupu](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="fc3c6-106"> contract inference, see  [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="fc3c6-107">Serializátor je zadán pomocí <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fc3c6-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="fc3c6-108">To je možné nastavit v návrháři, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="fc3c6-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="fc3c6-109">![Nastavení serializátoru](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span><span class="sxs-lookup"><span data-stu-id="fc3c6-109">![Setting the serializer](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span></span>  
  
 <span data-ttu-id="fc3c6-110">Serializátor lze nastavit i v kódu, jak je znázorněno v následujícím příkladu</span><span class="sxs-lookup"><span data-stu-id="fc3c6-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
```  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
```  
  
 <span data-ttu-id="fc3c6-111">Známé typy lze na i služeb pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="fc3c6-111">Known types can be specified on Workflow services as well.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="fc3c6-112">Známé typy najdete v části [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="fc3c6-112"> Known Types see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="fc3c6-113">Známé typy mohou být zadané v Návrháři nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="fc3c6-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="fc3c6-114">Chcete-li zadat známé typy v návrháři, klikněte na tlačítko se třemi tečkami vedle vlastnosti KnownTypes v okně Vlastnosti pro <xref:System.ServiceModel.Activities.Receive> aktivity, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="fc3c6-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the properties window for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="fc3c6-115">![Vlastnost KnownTypes](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")</span><span class="sxs-lookup"><span data-stu-id="fc3c6-115">![KnownTypes property](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")</span></span>  
  
 <span data-ttu-id="fc3c6-116">Tato akce zobrazí Editor kolekcí typ, který vám umožní vyhledat a zadejte známé typy.</span><span class="sxs-lookup"><span data-stu-id="fc3c6-116">This will display the Type Collections Editor that will allow you to search for and specify known types.</span></span>  
  
 <span data-ttu-id="fc3c6-117">![Přidání známé typy](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span><span class="sxs-lookup"><span data-stu-id="fc3c6-117">![Adding Known Types](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span></span>  
  
 <span data-ttu-id="fc3c6-118">Klikněte **přidat nový typ** propojit a pomocí rozevíracího dolů vyberte nebo vyhledejte typu můžete přidat do kolekce známé typy.</span><span class="sxs-lookup"><span data-stu-id="fc3c6-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="fc3c6-119">Určete známé typy v kódu pomocí <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> vlastnost, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="fc3c6-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
```  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
            approveExpense.KnownTypes.Add(typeof(Travel));  
            approveExpense.KnownTypes.Add(typeof(Meal));  
```  
  
 <span data-ttu-id="fc3c6-120">Chcete-li zobrazit kompletní příklad znázorňující postup konfigurace serializace pro služby pracovního postupu najdete v části [formátování zprávy v služeb pracovních postupů](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="fc3c6-120">To see a complete code example showing how to configure serialization for a workflow service see [Formatting messages in Workflow Services](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md).</span></span>
