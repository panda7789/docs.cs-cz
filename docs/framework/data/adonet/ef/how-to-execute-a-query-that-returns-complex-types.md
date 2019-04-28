---
title: 'Postupy: Provedení dotazu, který vrátí komplexní typy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: a428f54c3834ccdf6a0c7a5bfce8307172724524
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607203"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a>Postupy: Provedení dotazu, který vrátí komplexní typy
Toto téma ukazuje, jak spustit [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotaz, který vrátí typ objektů, které obsahují vlastnost složitého typu entity.  
  
### <a name="to-run-the-code-in-this-example"></a>Chcete-li spustit kód v tomto příkladu  
  
1. Přidat [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) do vašeho projektu a konfigurace projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Další informace najdete v tématu [jak: Použijte Průvodce datovým modelem Entity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
2. V kódové stránce pro vaši aplikaci, přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. Poklikejte na soubor .edmx pro model v zobrazení [okno Prohlížeč modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) návrháře entit. Na povrchu návrháře entit vyberte `Email` a `Phone` vlastnosti `Contact` typ entity, pak klikněte pravým tlačítkem a vyberte **Refaktorovat do nový komplexní typ**.  
  
4. Nový komplexní typ se zvoleným `Email` a `Phone` vlastnosti se přidá do **prohlížeč modelu**. Komplexní typ je přiřazen výchozí název: přejmenujte typ na `EmailPhone` v **vlastnosti** okna. Kromě toho nový `ComplexProperty` je přidána vlastnost `Contact` typu entity. Přejmenovat vlastnost `EmailPhoneComplexType.`  
  
     Informace o vytváření a úpravách komplexní typy s použitím Průvodce entitního modelu dat najdete v tématu [jak: Refaktorujte již existující vlastnosti do komplexní vlastnosti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) a [jak: Vytvoření a úprava komplexní typy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).  
  
## <a name="example"></a>Příklad  
 Následující příklad spustí dotaz, který vrátí kolekci `Contact` objekty a zobrazí dvě vlastnosti `Contact` objekty: `ContactID` a hodnoty `EmailPhoneComplexType` komplexního typu.  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
