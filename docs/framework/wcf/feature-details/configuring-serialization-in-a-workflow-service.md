---
title: Konfigurace serializace ve službě pracovních postupů
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 5076f3d377a656cb96909cf8df01591dc6ab72b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597537"
---
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="5b0f7-102">Konfigurace serializace ve službě pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="5b0f7-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="5b0f7-103">Služby pracovních postupů jsou služby Windows Communication Foundation (WCF), které mají možnost použít buď <xref:System.Runtime.Serialization.DataContractSerializer> (výchozí), nebo <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="5b0f7-103">Workflow services are Windows Communication Foundation (WCF) services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="5b0f7-104">Při psaní služeb nesouvisejících s pracovními postupy je typ serializátoru, který se má použít, specifikovaný v kontraktu služby nebo operace.</span><span class="sxs-lookup"><span data-stu-id="5b0f7-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="5b0f7-105">Při vytváření služeb pracovních postupů WCF neurčíte tyto smlouvy v kódu, ale místo toho jsou generovány za běhu odvozenou od smlouvy.</span><span class="sxs-lookup"><span data-stu-id="5b0f7-105">When creating WCF workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> <span data-ttu-id="5b0f7-106">Další informace o odvození smlouvy najdete v tématu [Použití kontraktů v pracovním postupu](using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="5b0f7-106">For more information about contract inference, see  [Using Contracts in Workflow](using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="5b0f7-107">Serializátor je určen pomocí <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5b0f7-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="5b0f7-108">To lze nastavit v návrháři, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="5b0f7-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 ![Nastavení vlastnosti SerializerOption v okně Vlastnosti.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 <span data-ttu-id="5b0f7-110">Serializátor lze také nastavit v kódu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="5b0f7-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
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
  
  <span data-ttu-id="5b0f7-111">Známé typy lze také zadat ve službě pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5b0f7-111">Known types can be specified on Workflow services as well.</span></span> <span data-ttu-id="5b0f7-112">Další informace o známých typech najdete v tématu [známé typy kontraktu dat](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="5b0f7-112">For more information about Known Types, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="5b0f7-113">Známé typy lze zadat v Návrháři nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="5b0f7-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="5b0f7-114">Chcete-li v Návrháři zadat známé typy, klikněte na tlačítko se třemi tečkami vedle vlastnosti KnownTypes v **okně Vlastnosti** <xref:System.ServiceModel.Activities.Receive> aktivity, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="5b0f7-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the **Properties Window** for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>
  
 ![Snímek obrazovky dialogového okna vlastnosti KnownTypes](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 <span data-ttu-id="5b0f7-116">Tím se zobrazí Editor kolekce typů, který umožňuje vyhledat a zadat známé typy.</span><span class="sxs-lookup"><span data-stu-id="5b0f7-116">This displays the Type Collections Editor that allows you to search for and specify known types.</span></span>  
  
 ![Snímek obrazovky editoru kolekcí typů](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 <span data-ttu-id="5b0f7-118">Klikněte na odkaz **Přidat nový typ** a pomocí rozevírací nabídky vyberte nebo vyhledejte typ, který chcete přidat do kolekce známých typů.</span><span class="sxs-lookup"><span data-stu-id="5b0f7-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="5b0f7-119">Chcete-li zadat známé typy v kódu, použijte <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> vlastnost, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="5b0f7-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
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
