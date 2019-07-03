---
title: 'Postupy: Volání modelově definovaných funkcí v dotazech'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
ms.openlocfilehash: 32cdb5b0f27817856ab586eb38f89df63c1c4d3b
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539862"
---
# <a name="how-to-call-model-defined-functions-in-queries"></a>Postupy: Volání modelově definovaných funkcí v dotazech
Toto téma popisuje, jak volat funkce, které jsou definované v konceptuálním modelu z v rámci LINQ na dotazy na entity.  
  
 Následující postup obsahovala hrubý nástin pro volání modelově definovaných funkce z v rámci LINQ dotazu entity. Následující příklad obsahuje více podrobností o kroků v postupu. V postupu se předpokládá, že jste definovali funkce v konceptuálním modelu. Další informace najdete v tématu [jak: Definování vlastních funkcí v konceptuálním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a>Pro volání funkce definované v konceptuálním modelu  
  
1. Běžnou metodou language runtime (CLR) přidáte do vaší aplikace, který se mapuje na funkce definované v konceptuálním modelu. Pokud chcete namapovat metodu, musíte použít <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> metody. Všimněte si, <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametry atributu se názvu oboru názvů Koncepční model a název funkce v konceptuálním modelu v uvedeném pořadí. Funkce překlad názvů pro funkci LINQ je velká a malá písmena.  
  
2. Volání funkce v technologii LINQ to Entities dotazu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak volat funkci, která je definována v konceptuálním modelu z v rámci LINQ dotazu entity. V příkladu používá model školy. Informace o School modelu najdete v tématu [vytvoření ukázkové databáze školy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) a [generování školní edmx soubor](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).  
  
 Následující Koncepční model funkce vrátí počet roků, protože byl přijat instruktorem. Informace o přidání funkce do koncepčního modelu najdete v tématu [jak: Definování vlastních funkcí v konceptuálním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a>Příklad  
 V dalším kroku přidejte následující metodu do vaší aplikace a použití <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> mapovat funkci koncepčního modelu:  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a>Příklad  
 Nyní můžete volat funkce konceptuální model v rámci LINQ dotazu entity. Následující kód volá metodu pro zobrazení všech školitelů, které byly přijaty před více než deset let:  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled souboru EDMX](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Dotazy v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
- [Volání funkcí v dotazech LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [Postupy: Volání modelově definovaných funkcí jako objektových metod](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)
