---
title: 'Postup: provedení dotazu, který vrací komplexní typy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: b999033046eb251400f033314ae7eb197a8f110a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760528"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a><span data-ttu-id="de6db-102">Postup: provedení dotazu, který vrací komplexní typy</span><span class="sxs-lookup"><span data-stu-id="de6db-102">How to: Execute a Query that Returns Complex Types</span></span>
<span data-ttu-id="de6db-103">Toto téma ukazuje, jak provést [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotaz, který vrátí typ objektů, které obsahují vlastnost komplexního typu entity.</span><span class="sxs-lookup"><span data-stu-id="de6db-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that returns entity type objects that contain a property of a complex type.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="de6db-104">Spustí kód v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="de6db-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="de6db-105">Přidat [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) do projektu a konfigurace projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="de6db-105">Add the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="de6db-106">Další informace najdete v tématu [postupy: použití průvodce Entity Data Model](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="de6db-106">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="de6db-107">Na stránce kódu pro aplikace, přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="de6db-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  <span data-ttu-id="de6db-108">Poklikejte na soubor EDMX zobrazíte model [okno prohlížeče modelu](http://msdn.microsoft.com/library/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) z Entity Designer.</span><span class="sxs-lookup"><span data-stu-id="de6db-108">Double click the .edmx file to display the model in the [Model Browser window](http://msdn.microsoft.com/library/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) of the Entity Designer.</span></span> <span data-ttu-id="de6db-109">Na ploše Entity Designer, vyberte `Email` a `Phone` vlastnosti `Contact` typ entity, pak klikněte pravým tlačítkem a vyberte **Refaktorovat do nový komplexní typ**.</span><span class="sxs-lookup"><span data-stu-id="de6db-109">On the Entity Designer surface, select the `Email` and `Phone` properties of the `Contact` entity type, then right-click and select **Refactor into New Complex Type**.</span></span>  
  
4.  <span data-ttu-id="de6db-110">Nový komplexní typ s vybranou `Email` a `Phone` vlastnosti je přidat do **prohlížeče modelu**.</span><span class="sxs-lookup"><span data-stu-id="de6db-110">A new complex type with the selected `Email` and `Phone` properties is added to the **Model Browser**.</span></span> <span data-ttu-id="de6db-111">Komplexní typ je zadána výchozí název: Přejmenovat typ, který má `EmailPhone` v **vlastnosti** okno.</span><span class="sxs-lookup"><span data-stu-id="de6db-111">The complex type is given a default name: rename the type to `EmailPhone` in the **Properties** window.</span></span> <span data-ttu-id="de6db-112">Navíc nový `ComplexProperty` vlastnost je přidán do `Contact` typ entity.</span><span class="sxs-lookup"><span data-stu-id="de6db-112">Also, a new `ComplexProperty` property is added to the `Contact` entity type.</span></span> <span data-ttu-id="de6db-113">Přejmenovat vlastnosti `EmailPhoneComplexType.`</span><span class="sxs-lookup"><span data-stu-id="de6db-113">Rename the property to `EmailPhoneComplexType.`</span></span>  
  
     <span data-ttu-id="de6db-114">Informace o vytvoření a úprava komplexní typy s použitím průvodce Entity Data Model najdete v tématu [postup: Refaktorovat existující vlastnosti do komplexní vlastnost typu](http://msdn.microsoft.com/library/5b2eb3b3-693d-42cb-b43a-405812d677eb) a [postupy: vytvoření a upravit komplexní typy](http://msdn.microsoft.com/library/afb8e206-0ffe-4597-b6d4-6ab566897e1d).</span><span class="sxs-lookup"><span data-stu-id="de6db-114">For information about creating and modifying complex types by using the Entity Data Model Wizard, see [How to: Refactor Existing Properties into a Complex Type Property](http://msdn.microsoft.com/library/5b2eb3b3-693d-42cb-b43a-405812d677eb) and [How to: Create and Modify Complex Types](http://msdn.microsoft.com/library/afb8e206-0ffe-4597-b6d4-6ab566897e1d).</span></span>  
  
## <a name="example"></a><span data-ttu-id="de6db-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="de6db-115">Example</span></span>  
 <span data-ttu-id="de6db-116">Následující příklad spustí dotaz, který vrátí kolekce `Contact` objekty a zobrazí dvě vlastnosti `Contact` objekty: `ContactID` a hodnoty `EmailPhoneComplexType` komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="de6db-116">The following example executes a query that returns a collection of `Contact` objects and displays two properties of the `Contact` objects: `ContactID` and the values of the `EmailPhoneComplexType` complex type.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
