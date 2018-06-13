---
title: Konfigurace serializace ve službě pracovních postupů
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 74d9a812b9e0cd51a401fa3526c947d52413807a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488869"
---
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="fb38e-102">Konfigurace serializace ve službě pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="fb38e-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="fb38e-103">Služby pracovních postupů jsou služby Windows Communication Foundation (WCF), a tak mít možnost buď pomocí <xref:System.Runtime.Serialization.DataContractSerializer> (výchozí) nebo <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="fb38e-103">Workflow services are Windows Communication Foundation (WCF) services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="fb38e-104">Při zápisu mimo pracovní postup služby typu serializátoru je zadán pro kontrakt služby nebo operace.</span><span class="sxs-lookup"><span data-stu-id="fb38e-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="fb38e-105">Při vytváření pracovního postupu služby WCF v kódu nezadáte tyto smlouvy, ale místo jsou generovány při běhu pomocí odvození kontrakt.</span><span class="sxs-lookup"><span data-stu-id="fb38e-105">When creating WCF workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> <span data-ttu-id="fb38e-106">Další informace o odvození kontrakt najdete v tématu [použití kontraktů v pracovním postupu](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="fb38e-106">For more information about contract inference, see  [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="fb38e-107">Serializátor je zadán pomocí <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fb38e-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="fb38e-108">To je možné nastavit v návrháři, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="fb38e-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="fb38e-109">![Nastavení serializátoru](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span><span class="sxs-lookup"><span data-stu-id="fb38e-109">![Setting the serializer](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span></span>  
  
 <span data-ttu-id="fb38e-110">Serializátor lze nastavit i v kódu, jak je znázorněno v následujícím příkladu</span><span class="sxs-lookup"><span data-stu-id="fb38e-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
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
  
 <span data-ttu-id="fb38e-111">Známé typy lze na i služeb pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="fb38e-111">Known types can be specified on Workflow services as well.</span></span> <span data-ttu-id="fb38e-112">Další informace o známé typy najdete v části [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="fb38e-112">For more information about Known Types see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="fb38e-113">Známé typy mohou být zadané v Návrháři nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="fb38e-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="fb38e-114">Chcete-li zadat známé typy v návrháři, klikněte na tlačítko se třemi tečkami vedle vlastnosti KnownTypes v okně Vlastnosti pro <xref:System.ServiceModel.Activities.Receive> aktivity, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="fb38e-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the properties window for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="fb38e-115">![Vlastnost KnownTypes](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")</span><span class="sxs-lookup"><span data-stu-id="fb38e-115">![KnownTypes property](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")</span></span>  
  
 <span data-ttu-id="fb38e-116">Tato akce zobrazí Editor kolekcí typ, který vám umožní vyhledat a zadejte známé typy.</span><span class="sxs-lookup"><span data-stu-id="fb38e-116">This will display the Type Collections Editor that will allow you to search for and specify known types.</span></span>  
  
 <span data-ttu-id="fb38e-117">![Přidání známé typy](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span><span class="sxs-lookup"><span data-stu-id="fb38e-117">![Adding Known Types](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span></span>  
  
 <span data-ttu-id="fb38e-118">Klikněte **přidat nový typ** propojit a pomocí rozevíracího dolů vyberte nebo vyhledejte typu můžete přidat do kolekce známé typy.</span><span class="sxs-lookup"><span data-stu-id="fb38e-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="fb38e-119">Určete známé typy v kódu pomocí <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> vlastnost, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="fb38e-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="fb38e-120">Chcete-li zobrazit kompletní příklad znázorňující postup konfigurace serializace pro služby pracovního postupu najdete v části [formátování zprávy v služeb pracovních postupů](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="fb38e-120">To see a complete code example showing how to configure serialization for a workflow service see [Formatting messages in Workflow Services](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md).</span></span>
