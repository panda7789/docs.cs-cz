---
title: 'Postupy: Provedení dotazu, který vrátí komplexní typy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: b08b220e969ad1c400413978c85b2f107d64a688
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854639"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a><span data-ttu-id="ffcbf-102">Postupy: Provedení dotazu, který vrátí komplexní typy</span><span class="sxs-lookup"><span data-stu-id="ffcbf-102">How to: Execute a Query that Returns Complex Types</span></span>
<span data-ttu-id="ffcbf-103">Toto téma ukazuje, jak spustit [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotaz, který vrací objekty typu entity, které obsahují vlastnost komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="ffcbf-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that returns entity type objects that contain a property of a complex type.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="ffcbf-104">Spuštění kódu v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="ffcbf-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="ffcbf-105">Přidejte do svého projektu [model AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) a nakonfigurujte projekt tak, aby používal Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="ffcbf-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="ffcbf-106">Další informace najdete v tématu [jak: Použijte průvodce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))model EDM (Entity Data Model).</span><span class="sxs-lookup"><span data-stu-id="ffcbf-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="ffcbf-107">Na kódové stránce vaší aplikace přidejte následující `using` příkazy (`Imports` v Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="ffcbf-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. <span data-ttu-id="ffcbf-108">Dvojím kliknutím na soubor. edmx zobrazte model v [okně prohlížeče modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) Entity Designer.</span><span class="sxs-lookup"><span data-stu-id="ffcbf-108">Double click the .edmx file to display the model in the [Model Browser window](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) of the Entity Designer.</span></span> <span data-ttu-id="ffcbf-109">Na Entity Designer ploše vyberte `Email` vlastnosti `Contact` a `Phone` pro typ entity, potom klikněte pravým tlačítkem a vyberte **refaktoring do nového komplexního typu**.</span><span class="sxs-lookup"><span data-stu-id="ffcbf-109">On the Entity Designer surface, select the `Email` and `Phone` properties of the `Contact` entity type, then right-click and select **Refactor into New Complex Type**.</span></span>  
  
4. <span data-ttu-id="ffcbf-110">Do **prohlížeče modelu**se přidá nový komplexní `Email` typ `Phone` s vybranými vlastnostmi a.</span><span class="sxs-lookup"><span data-stu-id="ffcbf-110">A new complex type with the selected `Email` and `Phone` properties is added to the **Model Browser**.</span></span> <span data-ttu-id="ffcbf-111">Komplexní typ má předaný výchozí název: Přejmenujte typ na `EmailPhone` v okně **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="ffcbf-111">The complex type is given a default name: rename the type to `EmailPhone` in the **Properties** window.</span></span> <span data-ttu-id="ffcbf-112">Do typu `ComplexProperty`entityjetaképřidána Novávlastnost.`Contact`</span><span class="sxs-lookup"><span data-stu-id="ffcbf-112">Also, a new `ComplexProperty` property is added to the `Contact` entity type.</span></span> <span data-ttu-id="ffcbf-113">Přejmenujte vlastnost na`EmailPhoneComplexType.`</span><span class="sxs-lookup"><span data-stu-id="ffcbf-113">Rename the property to `EmailPhoneComplexType.`</span></span>  
  
     <span data-ttu-id="ffcbf-114">Informace o vytváření a úpravách komplexních typů pomocí Průvodce model EDM (Entity Data Model) naleznete v tématu [How to: Refaktorujte existující vlastnosti do vlastnosti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) komplexního typu a [postupujte takto: Vytvářejte a upravujte komplexní typy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ffcbf-114">For information about creating and modifying complex types by using the Entity Data Model Wizard, see [How to: Refactor Existing Properties into a Complex Type Property](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) and [How to: Create and Modify Complex Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffcbf-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="ffcbf-115">Example</span></span>  
 <span data-ttu-id="ffcbf-116">Následující příklad spustí dotaz, `Contact` který vrátí kolekci objektů a zobrazí dvě vlastnosti `Contact` objektů: `ContactID` a hodnoty `EmailPhoneComplexType` komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="ffcbf-116">The following example executes a query that returns a collection of `Contact` objects and displays two properties of the `Contact` objects: `ContactID` and the values of the `EmailPhoneComplexType` complex type.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
