---
title: 'Postupy: Volání modelově definovaných funkcí v dotazech'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
ms.openlocfilehash: 33f26896dd0d4ff08beb4a011fa6bd468cba7207
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250759"
---
# <a name="how-to-call-model-defined-functions-in-queries"></a>Postupy: Volání modelově definovaných funkcí v dotazech
Toto téma popisuje, jak volat funkce, které jsou definovány v koncepčním modelu v rámci LINQ to Entities dotazů.  
  
 Následující postup poskytuje osnovu vysoké úrovně pro volání funkce definované modelem v rámci dotazu LINQ to Entities. Následující příklad poskytuje další podrobnosti o krocích v postupu. Procedura předpokládá, že jste definovali funkci v koncepčním modelu. Další informace najdete v tématu [jak: Definujte vlastní funkce v koncepčním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a>Volání funkce definované v koncepčním modelu  
  
1. Přidejte do aplikace metodu modulu CLR (Common Language Runtime), která se mapuje na funkci definovanou v koncepčním modelu. Chcete-li namapovat metodu, musíte použít <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> na metodu. Všimněte si, <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> že <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametry a atributu jsou název oboru názvů koncepčního modelu a název funkce v uvedeném koncepčním modelu. Rozlišení názvu funkce pro LINQ rozlišuje velká a malá písmena.  
  
2. Volání funkce v dotazu LINQ to Entities.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak volat funkci, která je definována v koncepčním modelu v rámci LINQ to Entitiesho dotazu. V příkladu se používá školní model. Informace o školním modelu najdete v tématu [vytvoření ukázkové školní databáze](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) a [Vytvoření souboru School. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).  
  
 Následující funkce koncepčního modelu vrátí počet roků od přijetí instruktora. Informace o přidání funkce do koncepčního modelu naleznete v tématu [How to: Definujte vlastní funkce v koncepčním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a>Příklad  
 Dále do aplikace přidejte následující metodu a použijte <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> ji k namapování na funkci koncepčního modelu:  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a>Příklad  
 Nyní můžete volat funkci koncepčního modelu v rámci LINQ to Entitiesho dotazu. Následující kód volá metodu pro zobrazení všech instruktorů, které byly přijaty před více než deseti lety:  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Soubor. edmx – přehled](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Dotazy v technologii LINQ to Entities](queries-in-linq-to-entities.md)
- [Volání funkcí v dotazech LINQ to Entities](calling-functions-in-linq-to-entities-queries.md)
- [Postupy: Volání funkcí definovaných modelem jako metod objektů](how-to-call-model-defined-functions-as-object-methods.md)
