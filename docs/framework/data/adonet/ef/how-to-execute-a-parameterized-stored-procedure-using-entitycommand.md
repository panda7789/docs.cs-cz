---
title: 'Postupy: Spuštění parametrizované uložené procedury pomocí EntityCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
ms.openlocfilehash: 27e756d8e44580d9205cc075367bce5a45536c69
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854679"
---
# <a name="how-to-execute-a-parameterized-stored-procedure-using-entitycommand"></a><span data-ttu-id="9e422-102">Postupy: Spuštění parametrizované uložené procedury pomocí EntityCommand</span><span class="sxs-lookup"><span data-stu-id="9e422-102">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>
<span data-ttu-id="9e422-103">Toto téma ukazuje, jak spustit parametrizovanou uloženou proceduru pomocí <xref:System.Data.EntityClient.EntityCommand> třídy.</span><span class="sxs-lookup"><span data-stu-id="9e422-103">This topic shows how to execute a parameterized stored procedure by using the <xref:System.Data.EntityClient.EntityCommand> class.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="9e422-104">Spuštění kódu v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="9e422-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="9e422-105">Přidejte do svého projektu [školní model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) a nakonfigurujte projekt tak, aby používal Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="9e422-105">Add the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="9e422-106">Další informace najdete v tématu [jak: Použijte průvodce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))model EDM (Entity Data Model).</span><span class="sxs-lookup"><span data-stu-id="9e422-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="9e422-107">Na kódové stránce vaší aplikace přidejte následující `using` příkazy (`Imports` v Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="9e422-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. <span data-ttu-id="9e422-108">Importujte uloženou proceduru a `CourseGrade` zadejte entity jako návratový typ. `GetStudentGrades`</span><span class="sxs-lookup"><span data-stu-id="9e422-108">Import the `GetStudentGrades` stored procedure and specify `CourseGrade` entities as a return type.</span></span> <span data-ttu-id="9e422-109">Informace o tom, jak importovat uloženou proceduru, [najdete v tématu How to: Importujte uloženou proceduru](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9e422-109">For information on how to import a stored procedure, see [How to: Import a Stored Procedure](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e422-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="9e422-110">Example</span></span>  
 <span data-ttu-id="9e422-111">Následující kód provede `GetStudentGrades` uloženou proceduru, `StudentId` kde je povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="9e422-111">The following code executes the `GetStudentGrades` stored procedure where `StudentId` is a required parameter.</span></span> <span data-ttu-id="9e422-112">Výsledky jsou pak čteny pomocí <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="9e422-112">The results are then read by an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="9e422-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9e422-113">See also</span></span>

- [<span data-ttu-id="9e422-114">Zprostředkovatel EntityClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="9e422-114">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
