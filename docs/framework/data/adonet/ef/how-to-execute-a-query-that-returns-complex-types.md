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
# <a name="how-to-execute-a-query-that-returns-complex-types"></a>Postupy: provedení dotazu, který vrátí komplexní typy
Toto téma ukazuje, jak spustit [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotaz, který vrátí typ objektů, které obsahují vlastnost složitého typu entity.  
  
### <a name="to-run-the-code-in-this-example"></a>Chcete-li spustit kód v tomto příkladu  
  
1.  Přidat [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) do vašeho projektu a konfigurace projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Další informace najdete v tématu [postupy: použití Průvodce datovým modelem Entity](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  V kódové stránce pro vaši aplikaci, přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  Poklikejte na soubor .edmx pro model v zobrazení [okno Prohlížeč modelu](https://msdn.microsoft.com/library/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) návrháře entit. Na povrchu návrháře entit vyberte `Email` a `Phone` vlastnosti `Contact` typ entity, pak klikněte pravým tlačítkem a vyberte **Refaktorovat do nový komplexní typ**.  
  
4.  Nový komplexní typ se zvoleným `Email` a `Phone` vlastnosti se přidá do **prohlížeč modelu**. Komplexní typ je přiřazen výchozí název: přejmenujte typ na `EmailPhone` v **vlastnosti** okna. Kromě toho nový `ComplexProperty` je přidána vlastnost `Contact` typu entity. Přejmenovat vlastnost `EmailPhoneComplexType.`  
  
     Informace o vytváření a úpravách komplexní typy s použitím Průvodce entitního modelu dat najdete v tématu [jak: Refaktorujte již existující vlastnosti do komplexní vlastnosti typu](https://msdn.microsoft.com/library/5b2eb3b3-693d-42cb-b43a-405812d677eb) a [postupy: vytvoření a úprava komplexní typy](https://msdn.microsoft.com/library/afb8e206-0ffe-4597-b6d4-6ab566897e1d).  
  
## <a name="example"></a>Příklad  
 Následující příklad spustí dotaz, který vrátí kolekci `Contact` objekty a zobrazí dvě vlastnosti `Contact` objekty: `ContactID` a hodnoty `EmailPhoneComplexType` komplexního typu.  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
