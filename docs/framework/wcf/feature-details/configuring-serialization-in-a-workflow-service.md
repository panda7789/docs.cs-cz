---
title: Konfigurace serializace ve službě pracovních postupů
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 0e0f03a30aa8e8679cf849aa75948e0bc2314fe5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857476"
---
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="08eea-102">Konfigurace serializace ve službě pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="08eea-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="08eea-103">Služby pracovních postupů jsou služby Windows Communication Foundation (WCF) a tak mají možnost používat buď <xref:System.Runtime.Serialization.DataContractSerializer> (výchozí) nebo <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="08eea-103">Workflow services are Windows Communication Foundation (WCF) services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="08eea-104">Při psaní mimo pracovní postup služby typu serializátoru je zadán u kontraktu služby nebo operace.</span><span class="sxs-lookup"><span data-stu-id="08eea-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="08eea-105">Při vytváření služby pracovního postupu WCF nezadáte těchto smluv v kódu, ale místo toho jsou generovány v době běhu podle odvození kontraktu.</span><span class="sxs-lookup"><span data-stu-id="08eea-105">When creating WCF workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> <span data-ttu-id="08eea-106">Další informace o odvození smlouvy najdete v tématu [použití kontraktů v pracovním postupu](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="08eea-106">For more information about contract inference, see  [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="08eea-107">Serializátoru, který je určen pomocí <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="08eea-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="08eea-108">To může být nastavit v návrháři, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="08eea-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 ![Nastavení vlastnosti SerializerOption v okně Vlastnosti.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 <span data-ttu-id="08eea-110">Serializátor můžete nastavit také v kódu, jak je znázorněno v následujícím příkladu</span><span class="sxs-lookup"><span data-stu-id="08eea-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
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
  
  <span data-ttu-id="08eea-111">Známé typy se dá nastavit na také služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="08eea-111">Known types can be specified on Workflow services as well.</span></span> <span data-ttu-id="08eea-112">Další informace o známé typy najdete v tématu [známé typy kontraktů dat](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="08eea-112">For more information about Known Types, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="08eea-113">Známé typy se dá nastavit v Návrháři nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="08eea-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="08eea-114">K určení známých typů v návrháři, klikněte na tlačítko se třemi tečkami vedle vlastnosti KnownTypes v **okno vlastností** pro <xref:System.ServiceModel.Activities.Receive> aktivity, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="08eea-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the **Properties Window** for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>   
  
 ![Snímek obrazovky dialogového okna Vlastnosti KnownTypes.](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 <span data-ttu-id="08eea-116">Zobrazí se Editor typu kolekce, která umožňuje hledat a zadejte známých typů.</span><span class="sxs-lookup"><span data-stu-id="08eea-116">This displays the Type Collections Editor that allows you to search for and specify known types.</span></span>  
  
 ![Snímek obrazovky Editor typu kolekce.](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 <span data-ttu-id="08eea-118">Klikněte na tlačítko **přidat nový typ** propojit a pomocí rozevíracího seznamu ji můžete vybrat nebo vyhledejte typ můžete přidat do kolekce známých typů.</span><span class="sxs-lookup"><span data-stu-id="08eea-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="08eea-119">K určení známé typy kódu používá <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> vlastnost, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="08eea-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
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
