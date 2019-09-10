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
# <a name="how-to-execute-a-parameterized-stored-procedure-using-entitycommand"></a>Postupy: Spuštění parametrizované uložené procedury pomocí EntityCommand
Toto téma ukazuje, jak spustit parametrizovanou uloženou proceduru pomocí <xref:System.Data.EntityClient.EntityCommand> třídy.  
  
### <a name="to-run-the-code-in-this-example"></a>Spuštění kódu v tomto příkladu  
  
1. Přidejte do svého projektu [školní model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) a nakonfigurujte projekt tak, aby používal Entity Framework. Další informace najdete v tématu [jak: Použijte průvodce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))model EDM (Entity Data Model).  
  
2. Na kódové stránce vaší aplikace přidejte následující `using` příkazy (`Imports` v Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. Importujte uloženou proceduru a `CourseGrade` zadejte entity jako návratový typ. `GetStudentGrades` Informace o tom, jak importovat uloženou proceduru, [najdete v tématu How to: Importujte uloženou proceduru](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100)).  
  
## <a name="example"></a>Příklad  
 Následující kód provede `GetStudentGrades` uloženou proceduru, `StudentId` kde je povinný parametr. Výsledky jsou pak čteny pomocí <xref:System.Data.EntityClient.EntityDataReader>.  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## <a name="see-also"></a>Viz také:

- [Zprostředkovatel EntityClient pro Entity Framework](entityclient-provider-for-the-entity-framework.md)
