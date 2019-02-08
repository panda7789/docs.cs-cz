---
title: 'Postupy: Provedení dotazu, který vrátí komplexní typy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: 6c063c9ef6bfde868c773d941ba2107dbaa9ee73
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827120"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a><span data-ttu-id="cf784-102">Postupy: Provedení dotazu, který vrátí komplexní typy</span><span class="sxs-lookup"><span data-stu-id="cf784-102">How to: Execute a Query that Returns Complex Types</span></span>
<span data-ttu-id="cf784-103">Toto téma ukazuje, jak spustit [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotaz, který vrátí typ objektů, které obsahují vlastnost složitého typu entity.</span><span class="sxs-lookup"><span data-stu-id="cf784-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that returns entity type objects that contain a property of a complex type.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="cf784-104">Chcete-li spustit kód v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="cf784-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="cf784-105">Přidat [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) do vašeho projektu a konfigurace projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cf784-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="cf784-106">Další informace najdete v tématu [jak: Použijte Průvodce datovým modelem Entity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="cf784-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="cf784-107">V kódové stránce pro vaši aplikaci, přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="cf784-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  <span data-ttu-id="cf784-108">Poklikejte na soubor .edmx pro model v zobrazení [okno Prohlížeč modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) návrháře entit.</span><span class="sxs-lookup"><span data-stu-id="cf784-108">Double click the .edmx file to display the model in the [Model Browser window](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) of the Entity Designer.</span></span> <span data-ttu-id="cf784-109">Na povrchu návrháře entit vyberte `Email` a `Phone` vlastnosti `Contact` typ entity, pak klikněte pravým tlačítkem a vyberte **Refaktorovat do nový komplexní typ**.</span><span class="sxs-lookup"><span data-stu-id="cf784-109">On the Entity Designer surface, select the `Email` and `Phone` properties of the `Contact` entity type, then right-click and select **Refactor into New Complex Type**.</span></span>  
  
4.  <span data-ttu-id="cf784-110">Nový komplexní typ se zvoleným `Email` a `Phone` vlastnosti se přidá do **prohlížeč modelu**.</span><span class="sxs-lookup"><span data-stu-id="cf784-110">A new complex type with the selected `Email` and `Phone` properties is added to the **Model Browser**.</span></span> <span data-ttu-id="cf784-111">Komplexní typ je přiřazen výchozí název: přejmenujte typ na `EmailPhone` v **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="cf784-111">The complex type is given a default name: rename the type to `EmailPhone` in the **Properties** window.</span></span> <span data-ttu-id="cf784-112">Kromě toho nový `ComplexProperty` je přidána vlastnost `Contact` typu entity.</span><span class="sxs-lookup"><span data-stu-id="cf784-112">Also, a new `ComplexProperty` property is added to the `Contact` entity type.</span></span> <span data-ttu-id="cf784-113">Přejmenovat vlastnost `EmailPhoneComplexType.`</span><span class="sxs-lookup"><span data-stu-id="cf784-113">Rename the property to `EmailPhoneComplexType.`</span></span>  
  
     <span data-ttu-id="cf784-114">Informace o vytváření a úpravách komplexní typy s použitím Průvodce entitního modelu dat najdete v tématu [jak: Refaktorujte již existující vlastnosti do komplexní vlastnosti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) a [jak: Vytvoření a úprava komplexní typy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="cf784-114">For information about creating and modifying complex types by using the Entity Data Model Wizard, see [How to: Refactor Existing Properties into a Complex Type Property](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) and [How to: Create and Modify Complex Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf784-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="cf784-115">Example</span></span>  
 <span data-ttu-id="cf784-116">Následující příklad spustí dotaz, který vrátí kolekci `Contact` objekty a zobrazí dvě vlastnosti `Contact` objekty: `ContactID` a hodnoty `EmailPhoneComplexType` komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="cf784-116">The following example executes a query that returns a collection of `Contact` objects and displays two properties of the `Contact` objects: `ContactID` and the values of the `EmailPhoneComplexType` complex type.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
