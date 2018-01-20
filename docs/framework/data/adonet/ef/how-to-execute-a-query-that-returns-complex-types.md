---
title: "Postup: provedení dotazu, který vrací komplexní typy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: cae0cc50b18641634fc8109fb29eeb30e9cf7cd8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a>Postup: provedení dotazu, který vrací komplexní typy
Toto téma ukazuje, jak provést [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotaz, který vrátí typ objektů, které obsahují vlastnost komplexního typu entity.  
  
### <a name="to-run-the-code-in-this-example"></a>Spustí kód v tomto příkladu  
  
1.  Přidat [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) do projektu a konfigurace projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Další informace najdete v tématu [postupy: použití průvodce Entity Data Model](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  Na stránce kódu pro aplikace, přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  Poklikejte na soubor EDMX zobrazíte model [okno prohlížeče modelu](http://msdn.microsoft.com/library/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) z Entity Designer. Na ploše Entity Designer, vyberte `Email` a `Phone` vlastnosti `Contact` typ entity, pak klikněte pravým tlačítkem a vyberte **Refaktorovat do nový komplexní typ**.  
  
4.  Nový komplexní typ s vybranou `Email` a `Phone` vlastnosti je přidat do **prohlížeče modelu**. Komplexní typ je zadána výchozí název: Přejmenovat typ, který má `EmailPhone` v **vlastnosti** okno. Navíc nový `ComplexProperty` vlastnost je přidán do `Contact` typ entity. Přejmenovat vlastnosti`EmailPhoneComplexType.`  
  
     Informace o vytvoření a úprava komplexní typy s použitím průvodce Entity Data Model najdete v tématu [postup: Refaktorovat existující vlastnosti do komplexní vlastnost typu](http://msdn.microsoft.com/library/5b2eb3b3-693d-42cb-b43a-405812d677eb) a [postupy: vytvoření a upravit komplexní typy](http://msdn.microsoft.com/library/afb8e206-0ffe-4597-b6d4-6ab566897e1d).  
  
## <a name="example"></a>Příklad  
 Následující příklad spustí dotaz, který vrátí kolekce `Contact` objekty a zobrazí dvě vlastnosti `Contact` objekty: `ContactID` a hodnoty `EmailPhoneComplexType` komplexního typu.  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
