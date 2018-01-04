---
title: "Postupy: volání modelu definované funkce v dotazech."
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
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d639297764333b99675cb9e076e816314f3567c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-call-model-defined-functions-in-queries"></a>Postupy: volání modelu definované funkce v dotazech.
Toto téma popisuje, jak volat funkce, které jsou definované v konceptuálním modelu uvnitř [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy.  
  
 Následující postup obsahovala hrubý nástin pro volání funkce modelu definované v nástroji [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazu. Příklad, který následuje obsahuje více podrobností o kroků v postupu. Postupu se předpokládá, že jste definovali funkci v konceptuálním modelu. Další informace najdete v tématu [postupy: definování vlastní funkce v konceptuálním modelu](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a>Volat funkci definovanou v konceptuálním modelu  
  
1.  Přidejte běžnou metodu language runtime (CLR) do vaší aplikace, která se mapuje na funkci definovanou v konceptuálním modelu. Chcete-li mapovat metodu, je nutné použít <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> metodě. Všimněte si, že <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametry atributu jsou název oboru názvů konceptuálního modelu a název funkce v konceptuálním modelu v uvedeném pořadí. Funkce překladu názvů u LINQ je malá a velká písmena.  
  
2.  Volání funkce v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zavolat funkci, která je definována v konceptuálním modelu uvnitř [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazu. V příkladu školní modelu. Informace o modelu školní najdete v tématu [vytváření ukázkovou databázi školy](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) a [generování školní .edmx souboru](http://msdn.microsoft.com/en-us/c48b3907-a8be-4fe6-884c-e95af1852758).  
  
 Následující funkce konceptuálního modelu vrátí počet roků, vzhledem k tomu, že lektorem byl přijat. Informace o přidání funkce do konceptuálního modelu najdete v tématu [postupy: definování vlastní funkce v konceptuálním modelu](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).)  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a>Příklad  
 V dalším kroku přidejte následující metodu pro vaše aplikace a použít <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> k mapování na funkci konceptuálního modelu:  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a>Příklad  
 Teď můžete volat funkci konceptuálního modelu z uvnitř [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazu. Následující kód zavolá metodu pro zobrazení všech vyučující, které byly přijaty před více než deset let:  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled souboru EDMX](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Dotazy v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [Volání funkcí v dotazech LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [Postupy: Volání modelově definovaných funkcí jako objektových metod](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)
