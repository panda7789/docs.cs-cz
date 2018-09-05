---
title: 'Postupy: volání modelově definovaných funkcí jako objektových metod'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33bae8a8-4ed8-4a1f-85d1-c62ff288cc61
ms.openlocfilehash: 290c2f58d0259d5a0df52711f63c48521891ae12
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502078"
---
# <a name="how-to-call-model-defined-functions-as-object-methods"></a>Postupy: volání modelově definovaných funkcí jako objektových metod
Toto téma popisuje, jak volat funkci modelově definovaných jako metody na <xref:System.Data.Objects.ObjectContext> objektu nebo jako statickou metodu pro vlastní třídu. A *modelově definovaných funkcí* je funkce, která je definována v konceptuálním modelu. Postupy v tomto tématu popisují, jak volat tyto funkce přímo, bez volání je z LINQ na dotazy na entity. Informace o volání modelově definovaných funkcí v jazyce LINQ dotazy entit najdete v tématu [jak: Call Model-Defined funkcí v dotazech](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md).  
  
 Zda volání modelově definovaných funkci tak, aby <xref:System.Data.Objects.ObjectContext> metody nebo jako statickou metodu pro vlastní třídu, je nutné nejprve mapovat metodu do modelově definovaných funkcí s <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>. Když však definujete metodu na <xref:System.Data.Objects.ObjectContext> třídy, je nutné použít <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> vlastnost k vystavení zprostředkovatele LINQ, že když definujete statickou metodu pro vlastní třídu, je nutné použít <xref:System.Linq.IQueryable.Provider%2A> vlastnost vystavení zprostředkovatele LINQ. Další informace najdete v tématu příklady, které postupujte podle níže uvedených postupech.  
  
 Následující postupy obsahují vysoké úrovně jsou podrobněji popsány dále pro volání modelově definovaných funkce jako metoda u <xref:System.Data.Objects.ObjectContext> objektu a jako statickou metodu pro vlastní třídu. Následující příklady poskytují podrobnější informace o postupu v postupech. V postupech se předpokládá, že jste definovali funkce v konceptuálním modelu. Další informace najdete v tématu [postupy: definování vlastní funkce v konceptuálním modelu](https://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).  
  
### <a name="to-call-a-model-defined-function-as-a-method-on-an-objectcontext-object"></a>Pro volání modelově definovaných funkce jako metoda pro objekt ObjectContext  
  
1.  Přidání zdrojového souboru částečné třídy odvozené od rozšířit <xref:System.Data.Objects.ObjectContext> třídy automaticky vygenerován pomocí nástroje Entity Framework. Definování zástupné procedury CLR v samostatném zdrojovém souboru zabrání změně ke ztrátě, když se znovu vygeneroval soubor.  
  
2.  Přidejte metodu běžné jazyka runtime (CLR) pro vaše <xref:System.Data.Objects.ObjectContext> třídu, která provede následující akce:  
  
    -   Mapuje se na funkci definované v konceptuálním modelu. Pokud chcete namapovat metodu, musíte použít <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> metody. Všimněte si, <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> jsou parametry atributu název oboru názvů konceptuálního modelu a název funkce v konceptuálním modelu, v uvedeném pořadí. Funkce překlad názvů pro funkci LINQ je velká a malá písmena.  
  
    -   Vrátí výsledky <xref:System.Linq.IQueryProvider.Execute%2A> metodu, která je vrácena <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> vlastnost.  
  
3.  Jako člen instance volejte metodu <xref:System.Data.Objects.ObjectContext> třídy.  
  
### <a name="to-call-a-model-defined-function-as-static-method-on-a-custom-class"></a>Volat funkci modelu definovány jako statické metody na vlastní třídy  
  
1.  Přidání třídy do vaší aplikace s statická metoda, která provede následující akce:  
  
    -   Mapuje se na funkci definované v konceptuálním modelu. Pokud chcete namapovat metodu, musíte použít <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> metody. Všimněte si, <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> jsou parametry atributu název oboru názvů konceptuálního modelu a název funkce v konceptuálním modelu, v uvedeném pořadí.  
  
    -   Přijímá <xref:System.Linq.IQueryable> argument.  
  
    -   Vrátí výsledky <xref:System.Linq.IQueryProvider.Execute%2A> metodu, která je vrácena <xref:System.Linq.IQueryable.Provider%2A> vlastnost.  
  
2.  Volat metodu jako člen statickou metodu ve vlastní třídy  
  
## <a name="example"></a>Příklad  
 **Volání modelově definovaných funkce jako metoda pro objekt ObjectContext**  
  
 Následující příklad ukazuje, jak volat funkci modelově definovaných jako metodu <xref:System.Data.Objects.ObjectContext> objektu. V příkladu se používá [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).  
  
 Zvažte koncepčního modelu níže, který vrátí výnosy produktu pro konkrétní produkt. (Informace o přidání funkce do koncepčního modelu najdete v tématu [postupy: definování vlastní funkce v konceptuálním modelu](https://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).)  
  
 [!code-xml[DP L2E Methods on ObjectContext#4](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#4)]  

## <a name="example"></a>Příklad  
 Následující kód přidá metodu `AdventureWorksEntities` třídu, která se mapuje na výše uvedené funkce koncepčního modelu.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#2)]
 [!code-vb[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#2)]  
  
## <a name="example"></a>Příklad  
 Následující kód volá metodu výše a zobrazte výnosy produktu pro konkrétní produkt:  
  
 [!code-csharp[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#3)]
 [!code-vb[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob volání modelově definovaných funkci, která vrátí kolekci (jako <xref:System.Linq.IQueryable%601> objekt). Vezměte v úvahu následující Koncepční model funkce, která vrátí všechny `SalesOrderDetails` pro ID daného produktu.  
  
 [!code-xml[DP L2E Methods on ObjectContext#7](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#7)]  
  
## <a name="example"></a>Příklad  
 Následující kód přidá metodu `AdventureWorksEntities` třídu, která se mapuje na výše uvedené funkce koncepčního modelu.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#8)]
 [!code-vb[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#8)]  
  
## <a name="example"></a>Příklad  
 Následující kód volá metodu. Všimněte si, že vrácené <xref:System.Linq.IQueryable%601> dotazu je dále vylepšili o vrátí řádek součtů pro každý `SalesOrderDetail`.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#9)]
 [!code-vb[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#9)]  
  
## <a name="example"></a>Příklad  
 **Volání funkce modelu definovány jako statické metody na vlastní třídy**  
  
 Následující příklad ukazuje, jak volat funkci modelu definovány jako statické metody na vlastní třídu. V příkladu se používá [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).  
  
> [!NOTE]
>  Při volání funkce modelově definovaných jako statickou metodu pro vlastní třídu modelově definovaných funkcí musí přijmout kolekce a vracet agregace hodnot v kolekci.  
  
 Vezměte v úvahu, že funkce koncepčního modelu níže, která vrací výnosy produktu pro kolekci podrobnosti prodejní objednávky. (Informace o přidání funkce do koncepčního modelu najdete v tématu [postupy: definování vlastní funkce v konceptuálním modelu](https://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).).  
  
 [!code-xml[DP L2E Methods on ObjectContext#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#1)]
  
## <a name="example"></a>Příklad  
 Následující kód přidá třídu do aplikace, který obsahuje statickou metodu, která se mapuje na výše uvedené funkce koncepčního modelu.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#5)]
 [!code-vb[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#5)]  
  
## <a name="example"></a>Příklad  
 Následující kód volá metodu výše a zobrazte výnosy produktu pro kolekci podrobnosti prodejní objednávky:  
  
 [!code-csharp[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#6)]
 [!code-vb[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#6)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled souboru EDMX](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Dotazy v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [Volání funkcí v dotazech LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
