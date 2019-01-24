---
title: 'Postupy: Spuštění parametrizované uložené procedury pomocí EntityCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
ms.openlocfilehash: 11894decbb81192eb68c680149bbe9f7398f0203
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587805"
---
# <a name="how-to-execute-a-parameterized-stored-procedure-using-entitycommand"></a><span data-ttu-id="50dbd-102">Postupy: Spuštění parametrizované uložené procedury pomocí EntityCommand</span><span class="sxs-lookup"><span data-stu-id="50dbd-102">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>
<span data-ttu-id="50dbd-103">Toto téma ukazuje, jak spustit uloženou proceduru s parametry s využitím <xref:System.Data.EntityClient.EntityCommand> třídy.</span><span class="sxs-lookup"><span data-stu-id="50dbd-103">This topic shows how to execute a parameterized stored procedure by using the <xref:System.Data.EntityClient.EntityCommand> class.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="50dbd-104">Chcete-li spustit kód v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="50dbd-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="50dbd-105">Přidat [školní modelu](https://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) do vašeho projektu a konfigurace projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="50dbd-105">Add the [School Model](https://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="50dbd-106">Další informace najdete v tématu [jak: Použijte Průvodce datovým modelem Entity](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="50dbd-106">For more information, see [How to: Use the Entity Data Model Wizard](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="50dbd-107">V kódové stránce pro vaši aplikaci, přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="50dbd-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  <span data-ttu-id="50dbd-108">Import `GetStudentGrades` uložené procedury a zadejte `CourseGrade` jako návratový typ entity.</span><span class="sxs-lookup"><span data-stu-id="50dbd-108">Import the `GetStudentGrades` stored procedure and specify `CourseGrade` entities as a return type.</span></span> <span data-ttu-id="50dbd-109">Informace o tom, jak importovat uložené procedury, naleznete v tématu [jak: Importovat uloženou proceduru](https://msdn.microsoft.com/library/24e68bf4-bd6d-428d-bc35-92d7b8e3736d).</span><span class="sxs-lookup"><span data-stu-id="50dbd-109">For information on how to import a stored procedure, see [How to: Import a Stored Procedure](https://msdn.microsoft.com/library/24e68bf4-bd6d-428d-bc35-92d7b8e3736d).</span></span>  
  
## <a name="example"></a><span data-ttu-id="50dbd-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="50dbd-110">Example</span></span>  
 <span data-ttu-id="50dbd-111">Následující kód se provádí `GetStudentGrades` uložené procedury, kde `StudentId` je povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="50dbd-111">The following code executes the `GetStudentGrades` stored procedure where `StudentId` is a required parameter.</span></span> <span data-ttu-id="50dbd-112">Výsledky se pak přečte <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="50dbd-112">The results are then read by an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="50dbd-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50dbd-113">See also</span></span>
- [<span data-ttu-id="50dbd-114">Zprostředkovatel EntityClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="50dbd-114">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
