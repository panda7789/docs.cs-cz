---
title: 'Postupy: provedení dotazu, který vrátí komplexní typy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: 013f1980d2ea13927871719aeea293cfce38b4d5
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861891"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a><span data-ttu-id="d8cc0-102">Postupy: provedení dotazu, který vrátí komplexní typy</span><span class="sxs-lookup"><span data-stu-id="d8cc0-102">How to: Execute a Query that Returns Complex Types</span></span>
<span data-ttu-id="d8cc0-103">Toto téma ukazuje, jak spustit [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotaz, který vrátí typ objektů, které obsahují vlastnost složitého typu entity.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that returns entity type objects that contain a property of a complex type.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="d8cc0-104">Chcete-li spustit kód v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="d8cc0-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="d8cc0-105">Přidat [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) do vašeho projektu a konfigurace projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d8cc0-105">Add the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="d8cc0-106">Další informace najdete v tématu [postupy: použití Průvodce datovým modelem Entity](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="d8cc0-106">For more information, see [How to: Use the Entity Data Model Wizard](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="d8cc0-107">V kódové stránce pro vaši aplikaci, přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="d8cc0-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  <span data-ttu-id="d8cc0-108">Poklikejte na soubor .edmx pro model v zobrazení [okno Prohlížeč modelu](https://msdn.microsoft.com/library/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) návrháře entit.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-108">Double click the .edmx file to display the model in the [Model Browser window](https://msdn.microsoft.com/library/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) of the Entity Designer.</span></span> <span data-ttu-id="d8cc0-109">Na povrchu návrháře entit vyberte `Email` a `Phone` vlastnosti `Contact` typ entity, pak klikněte pravým tlačítkem a vyberte **Refaktorovat do nový komplexní typ**.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-109">On the Entity Designer surface, select the `Email` and `Phone` properties of the `Contact` entity type, then right-click and select **Refactor into New Complex Type**.</span></span>  
  
4.  <span data-ttu-id="d8cc0-110">Nový komplexní typ se zvoleným `Email` a `Phone` vlastnosti se přidá do **prohlížeč modelu**.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-110">A new complex type with the selected `Email` and `Phone` properties is added to the **Model Browser**.</span></span> <span data-ttu-id="d8cc0-111">Komplexní typ je přiřazen výchozí název: přejmenujte typ na `EmailPhone` v **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-111">The complex type is given a default name: rename the type to `EmailPhone` in the **Properties** window.</span></span> <span data-ttu-id="d8cc0-112">Kromě toho nový `ComplexProperty` je přidána vlastnost `Contact` typu entity.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-112">Also, a new `ComplexProperty` property is added to the `Contact` entity type.</span></span> <span data-ttu-id="d8cc0-113">Přejmenovat vlastnost `EmailPhoneComplexType.`</span><span class="sxs-lookup"><span data-stu-id="d8cc0-113">Rename the property to `EmailPhoneComplexType.`</span></span>  
  
     <span data-ttu-id="d8cc0-114">Informace o vytváření a úpravách komplexní typy s použitím Průvodce entitního modelu dat najdete v tématu [jak: Refaktorujte již existující vlastnosti do komplexní vlastnosti typu](https://msdn.microsoft.com/library/5b2eb3b3-693d-42cb-b43a-405812d677eb) a [postupy: vytvoření a úprava komplexní typy](https://msdn.microsoft.com/library/afb8e206-0ffe-4597-b6d4-6ab566897e1d).</span><span class="sxs-lookup"><span data-stu-id="d8cc0-114">For information about creating and modifying complex types by using the Entity Data Model Wizard, see [How to: Refactor Existing Properties into a Complex Type Property](https://msdn.microsoft.com/library/5b2eb3b3-693d-42cb-b43a-405812d677eb) and [How to: Create and Modify Complex Types](https://msdn.microsoft.com/library/afb8e206-0ffe-4597-b6d4-6ab566897e1d).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8cc0-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="d8cc0-115">Example</span></span>  
 <span data-ttu-id="d8cc0-116">Následující příklad spustí dotaz, který vrátí kolekci `Contact` objekty a zobrazí dvě vlastnosti `Contact` objekty: `ContactID` a hodnoty `EmailPhoneComplexType` komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-116">The following example executes a query that returns a collection of `Contact` objects and displays two properties of the `Contact` objects: `ContactID` and the values of the `EmailPhoneComplexType` complex type.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
