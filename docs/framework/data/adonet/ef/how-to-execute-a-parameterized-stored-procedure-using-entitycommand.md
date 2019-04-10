---
title: 'Postupy: Spuštění parametrizované uložené procedury pomocí EntityCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
ms.openlocfilehash: deb1877397053ceab8c284a537a861ba56ffb729
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326655"
---
# <a name="how-to-execute-a-parameterized-stored-procedure-using-entitycommand"></a>Postupy: Spuštění parametrizované uložené procedury pomocí EntityCommand
Toto téma ukazuje, jak spustit uloženou proceduru s parametry s využitím <xref:System.Data.EntityClient.EntityCommand> třídy.  
  
### <a name="to-run-the-code-in-this-example"></a>Chcete-li spustit kód v tomto příkladu  
  
1. Přidat [školní modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) do vašeho projektu a konfigurace projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Další informace najdete v tématu [jak: Použijte Průvodce datovým modelem Entity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
2. V kódové stránce pro vaši aplikaci, přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. Import `GetStudentGrades` uložené procedury a zadejte `CourseGrade` jako návratový typ entity. Informace o tom, jak importovat uložené procedury, naleznete v tématu [jak: Importovat uloženou proceduru](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100)).  
  
## <a name="example"></a>Příklad  
 Následující kód se provádí `GetStudentGrades` uložené procedury, kde `StudentId` je povinný parametr. Výsledky se pak přečte <xref:System.Data.EntityClient.EntityDataReader>.  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## <a name="see-also"></a>Viz také:

- [Zprostředkovatel EntityClient pro Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
