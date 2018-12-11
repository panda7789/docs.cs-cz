---
title: Konfigurace serializace ve službě pracovních postupů
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 63a5860bd428fd4ce7fe01d7901427c85b2d5609
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154109"
---
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="24bfd-102">Konfigurace serializace ve službě pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="24bfd-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="24bfd-103">Služby pracovních postupů jsou služby Windows Communication Foundation (WCF) a tak mají možnost používat buď <xref:System.Runtime.Serialization.DataContractSerializer> (výchozí) nebo <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="24bfd-103">Workflow services are Windows Communication Foundation (WCF) services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="24bfd-104">Při psaní mimo pracovní postup služby typu serializátoru je zadán u kontraktu služby nebo operace.</span><span class="sxs-lookup"><span data-stu-id="24bfd-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="24bfd-105">Při vytváření služby pracovního postupu WCF nezadáte těchto smluv v kódu, ale místo toho jsou generovány v době běhu podle odvození kontraktu.</span><span class="sxs-lookup"><span data-stu-id="24bfd-105">When creating WCF workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> <span data-ttu-id="24bfd-106">Další informace o odvození smlouvy najdete v tématu [použití kontraktů v pracovním postupu](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="24bfd-106">For more information about contract inference, see  [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="24bfd-107">Serializátoru, který je určen pomocí <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="24bfd-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="24bfd-108">To může být nastavit v návrháři, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="24bfd-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="24bfd-109">![Nastavení serializátoru](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span><span class="sxs-lookup"><span data-stu-id="24bfd-109">![Setting the serializer](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span></span>  
  
 <span data-ttu-id="24bfd-110">Serializátor můžete nastavit také v kódu, jak je znázorněno v následujícím příkladu</span><span class="sxs-lookup"><span data-stu-id="24bfd-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
```csharp  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
```  
  
 <span data-ttu-id="24bfd-111">Známé typy se dá nastavit na také služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="24bfd-111">Known types can be specified on Workflow services as well.</span></span> <span data-ttu-id="24bfd-112">Další informace o známé typy najdete v části [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="24bfd-112">For more information about Known Types see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="24bfd-113">Známé typy se dá nastavit v Návrháři nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="24bfd-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="24bfd-114">K určení známých typů v návrháři, klikněte na tlačítko se třemi tečkami vedle vlastnosti KnownTypes v okně Vlastnosti <xref:System.ServiceModel.Activities.Receive> aktivity, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="24bfd-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the properties window for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="24bfd-115">![Vlastnost KnownTypes](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")</span><span class="sxs-lookup"><span data-stu-id="24bfd-115">![KnownTypes property](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")</span></span>  
  
 <span data-ttu-id="24bfd-116">Zobrazí se Editor typu kolekce, které vám umožní vyhledat a zadejte známých typů.</span><span class="sxs-lookup"><span data-stu-id="24bfd-116">This will display the Type Collections Editor that will allow you to search for and specify known types.</span></span>  
  
 <span data-ttu-id="24bfd-117">![Přidání známé typy](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span><span class="sxs-lookup"><span data-stu-id="24bfd-117">![Adding Known Types](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span></span>  
  
 <span data-ttu-id="24bfd-118">Klikněte na tlačítko **přidat nový typ** propojit a pomocí rozevíracího seznamu ji můžete vybrat nebo vyhledejte typ můžete přidat do kolekce známých typů.</span><span class="sxs-lookup"><span data-stu-id="24bfd-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="24bfd-119">K určení známé typy kódu používá <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> vlastnost, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="24bfd-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
```csharp
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
