---
title: Konfigurace serializace ve službě pracovních postupů
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: f894f2e044e35bb278f975ef2385a6b22a8bea49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185337"
---
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="619f1-102">Konfigurace serializace ve službě pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="619f1-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="619f1-103">Pracovní postupy služby jsou Windows Communication Foundation (WCF) <xref:System.Runtime.Serialization.DataContractSerializer> služby a tak <xref:System.Xml.Serialization.XmlSerializer>mají možnost použít (výchozí) nebo .</span><span class="sxs-lookup"><span data-stu-id="619f1-103">Workflow services are Windows Communication Foundation (WCF) services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="619f1-104">Při zápisu služeb bez pracovního postupu je typ serializátoru, který chcete použít, určen ve smlouvě o službě nebo operaci.</span><span class="sxs-lookup"><span data-stu-id="619f1-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="619f1-105">Při vytváření služeb pracovního postupu WCF nezadáte tyto smlouvy v kódu, ale spíše jsou generovány za běhu podle odvození smlouvy.</span><span class="sxs-lookup"><span data-stu-id="619f1-105">When creating WCF workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> <span data-ttu-id="619f1-106">Další informace o odvození smlouvy naleznete v [tématu Použití smluv v pracovním postupu](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="619f1-106">For more information about contract inference, see  [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="619f1-107">Serializátor je <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> určen pomocí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="619f1-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="619f1-108">To lze nastavit v návrháři, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="619f1-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 ![Nastavení vlastnosti SerializerOption v okně Vlastnosti.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 <span data-ttu-id="619f1-110">Serializátor lze také nastavit v kódu, jak je znázorněno v následujícím příkladu,</span><span class="sxs-lookup"><span data-stu-id="619f1-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
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
  
  <span data-ttu-id="619f1-111">Známé typy lze zadat také ve službách pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="619f1-111">Known types can be specified on Workflow services as well.</span></span> <span data-ttu-id="619f1-112">Další informace o známých typech naleznete v [tématu Data Contract Known Types](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="619f1-112">For more information about Known Types, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="619f1-113">Známé typy lze zadat v návrháři nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="619f1-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="619f1-114">Chcete-li určit známé typy v návrháři, klepněte na tlačítko se třemi tečkami vedle vlastnosti KnownTypes v **okně Vlastnosti** pro aktivitu, <xref:System.ServiceModel.Activities.Receive> jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="619f1-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the **Properties Window** for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>
  
 ![Snímek obrazovky s dialogovým oknem vlastnosti KnownTypes](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 <span data-ttu-id="619f1-116">Zobrazí se Editor kolekcí typů, který umožňuje vyhledávat a zadávat známé typy.</span><span class="sxs-lookup"><span data-stu-id="619f1-116">This displays the Type Collections Editor that allows you to search for and specify known types.</span></span>  
  
 ![Snímek obrazovky editoru kolekcí typů](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 <span data-ttu-id="619f1-118">Klikněte na odkaz **Přidat nový typ** a pomocí rozevíracího pole vyberte nebo vyhledejte typ, který chcete přidat do kolekce známých typů.</span><span class="sxs-lookup"><span data-stu-id="619f1-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="619f1-119">Chcete-li určit známé <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> typy v kódu, použijte vlastnost, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="619f1-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
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
