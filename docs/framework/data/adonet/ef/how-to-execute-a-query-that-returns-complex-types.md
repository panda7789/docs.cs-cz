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
# <a name="how-to-execute-a-query-that-returns-complex-types"></a>Postupy: Provedení dotazu, který vrátí komplexní typy
Toto téma ukazuje, jak spustit [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotaz, který vrací objekty typu entity, které obsahují vlastnost komplexního typu.  
  
### <a name="to-run-the-code-in-this-example"></a>Spuštění kódu v tomto příkladu  
  
1. Přidejte do svého projektu [model AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) a nakonfigurujte projekt tak, aby používal Entity Framework. Další informace najdete v tématu [jak: Použijte průvodce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))model EDM (Entity Data Model).  
  
2. Na kódové stránce vaší aplikace přidejte následující `using` příkazy (`Imports` v Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. Dvojím kliknutím na soubor. edmx zobrazte model v [okně prohlížeče modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) Entity Designer. Na Entity Designer ploše vyberte `Email` vlastnosti `Contact` a `Phone` pro typ entity, potom klikněte pravým tlačítkem a vyberte **refaktoring do nového komplexního typu**.  
  
4. Do **prohlížeče modelu**se přidá nový komplexní `Email` typ `Phone` s vybranými vlastnostmi a. Komplexní typ má předaný výchozí název: Přejmenujte typ na `EmailPhone` v okně **vlastnosti** . Do typu `ComplexProperty`entityjetaképřidána Novávlastnost.`Contact` Přejmenujte vlastnost na`EmailPhoneComplexType.`  
  
     Informace o vytváření a úpravách komplexních typů pomocí Průvodce model EDM (Entity Data Model) naleznete v tématu [How to: Refaktorujte existující vlastnosti do vlastnosti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) komplexního typu a [postupujte takto: Vytvářejte a upravujte komplexní typy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).  
  
## <a name="example"></a>Příklad  
 Následující příklad spustí dotaz, `Contact` který vrátí kolekci objektů a zobrazí dvě vlastnosti `Contact` objektů: `ContactID` a hodnoty `EmailPhoneComplexType` komplexního typu.  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
