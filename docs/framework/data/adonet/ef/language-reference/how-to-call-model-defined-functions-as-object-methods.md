---
title: 'Postupy: Volání modelově definovaných funkcí jako objektových metod'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33bae8a8-4ed8-4a1f-85d1-c62ff288cc61
ms.openlocfilehash: 787ead2c52f874af2ca1a02bf009da40cee875ae
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250774"
---
# <a name="how-to-call-model-defined-functions-as-object-methods"></a>Postupy: Volání modelově definovaných funkcí jako objektových metod
Toto téma popisuje, jak volat funkci definovanou modelem jako metodu <xref:System.Data.Objects.ObjectContext> objektu nebo jako statickou metodu pro vlastní třídu. *Funkce definovaná modelem* je funkce, která je definována v koncepčním modelu. Postupy v tématu popisují způsob volání těchto funkcí přímo místo jejich volání z LINQ to Entities dotazů. Informace o volání funkcí definovaných modelem v LINQ to Entitiesch dotazech naleznete [v tématu How to: Volání funkcí definovaných modelem v dotazech](how-to-call-model-defined-functions-in-queries.md).  
  
 Bez ohledu na to, zda zavoláte funkci <xref:System.Data.Objects.ObjectContext> definovanou modelem jako metodu nebo jako statickou metodu pro vlastní třídu, je nutné nejprve namapovat metodu na funkci <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>definovanou modelem. Pokud však definujete metodu <xref:System.Data.Objects.ObjectContext> třídy, je nutné <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> použít vlastnost k zveřejnění poskytovatele LINQ, zatímco při definování statické metody pro vlastní třídu je nutné použít <xref:System.Linq.IQueryable.Provider%2A> vlastnost k vystavení poskytovatele LINQ. Další informace najdete v příkladech, které následují níže uvedené postupy.  
  
 Níže uvedené postupy poskytují vysoké úrovně osnovy pro volání funkce definované modelem jako metody <xref:System.Data.Objects.ObjectContext> objektu a jako statickou metodu pro vlastní třídu. Příklady, které následují, poskytují další podrobnosti o krocích v postupech. Tyto postupy předpokládají, že jste definovali funkci v koncepčním modelu. Další informace najdete v tématu [jak: Definujte vlastní funkce v koncepčním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).  
  
### <a name="to-call-a-model-defined-function-as-a-method-on-an-objectcontext-object"></a>Volání funkce definované modelem jako metody objektu ObjectContext  
  
1. Přidejte zdrojový soubor pro rozšiřování částečné třídy odvozené od <xref:System.Data.Objects.ObjectContext> třídy automaticky generované nástroji Entity Framework. Definováním zástupné procedury CLR v samostatném zdrojovém souboru zabráníte ztrátě změn, když dojde k opětovnému vygenerování souboru.  
  
2. Přidejte do <xref:System.Data.Objects.ObjectContext> třídy metodu Common Language Runtime (CLR), která provede následující:  
  
    - Mapuje se na funkci definovanou v koncepčním modelu. Chcete-li namapovat metodu, musíte použít <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> na metodu. Všimněte si, <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> že <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametry a atributu jsou název oboru názvů koncepčního modelu a název funkce v koncepčním modelu, v uvedeném pořadí. Rozlišení názvu funkce pro LINQ rozlišuje velká a malá písmena.  
  
    - Vrátí výsledky <xref:System.Linq.IQueryProvider.Execute%2A> metody vrácené <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> vlastností.  
  
3. Volejte metodu jako člena v instanci <xref:System.Data.Objects.ObjectContext> třídy.  
  
### <a name="to-call-a-model-defined-function-as-static-method-on-a-custom-class"></a>Volání funkce definované modelem jako statické metody u vlastní třídy  
  
1. Přidejte do aplikace třídu se statickou metodou, která provede následující:  
  
    - Mapuje se na funkci definovanou v koncepčním modelu. Chcete-li namapovat metodu, musíte použít <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> na metodu. Všimněte si, <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> že <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametry a atributu jsou název oboru názvů koncepčního modelu a název funkce v koncepčním modelu, v uvedeném pořadí.  
  
    - <xref:System.Linq.IQueryable> Přijímá argument.  
  
    - Vrátí výsledky <xref:System.Linq.IQueryProvider.Execute%2A> metody vrácené <xref:System.Linq.IQueryable.Provider%2A> vlastností.  
  
2. Volání metody jako člena statické metody pro vlastní třídu  
  
## <a name="example"></a>Příklad  
 **Volání funkce definované modelem jako metody objektu ObjectContext**  
  
 Následující příklad ukazuje, jak volat funkci definovanou modelem jako metodu <xref:System.Data.Objects.ObjectContext> objektu. V příkladu se používá [model AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).  
  
 Vezměte v úvahu funkci koncepčního modelu, která vrací výnosy produktu pro určitý produkt. (Informace o přidání funkce do koncepčního modelu naleznete v tématu [How to: Definujte vlastní funkce v koncepčním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)  
  
 [!code-xml[DP L2E Methods on ObjectContext#4](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#4)]  

## <a name="example"></a>Příklad  
 Následující kód přidá metodu do `AdventureWorksEntities` třídy, která je mapována na funkci koncepčního modelu výše.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#2)]
 [!code-vb[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#2)]  
  
## <a name="example"></a>Příklad  
 Následující kód volá výše uvedenou metodu pro zobrazení výnosů produktu pro určitý produkt:  
  
 [!code-csharp[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#3)]
 [!code-vb[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak volat funkci definovanou modelem, která vrací kolekci (jako <xref:System.Linq.IQueryable%601> objekt). Zvažte níže uvedenou funkci koncepčního modelu, která vrátí `SalesOrderDetails` všechny pro dané ID produktu.  
  
 [!code-xml[DP L2E Methods on ObjectContext#7](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#7)]  
  
## <a name="example"></a>Příklad  
 Následující kód přidá metodu do `AdventureWorksEntities` třídy, která je mapována na funkci koncepčního modelu výše.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#8)]
 [!code-vb[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#8)]  
  
## <a name="example"></a>Příklad  
 Následující kód volá metodu. Všimněte si, že <xref:System.Linq.IQueryable%601> vrácený dotaz je dále vylepšený, aby vracel součet `SalesOrderDetail`řádků.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#9)]
 [!code-vb[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#9)]  
  
## <a name="example"></a>Příklad  
 **Volání funkce definované modelem jako statické metody pro vlastní třídu**  
  
 Další příklad ukazuje, jak volat funkci definovanou modelem jako statickou metodu pro vlastní třídu. V příkladu se používá [model AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).  
  
> [!NOTE]
> Při volání funkce definované model jako statické metody u vlastní třídy musí funkce definovaná modelem přijmout kolekci a vracet agregaci hodnot v kolekci.  
  
 Vezměte v úvahu funkci koncepčního modelu, která vrací výnosy produktu pro kolekci SalesOrderDetail. (Informace o přidání funkce do koncepčního modelu naleznete v tématu [How to: Definujte vlastní funkce v koncepčním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).).  
  
 [!code-xml[DP L2E Methods on ObjectContext#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#1)]
  
## <a name="example"></a>Příklad  
 Následující kód přidá do aplikace třídu, která obsahuje statickou metodu, která se mapuje na výše uvedenou funkci koncepčního modelu.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#5)]
 [!code-vb[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#5)]  
  
## <a name="example"></a>Příklad  
 Následující kód volá výše uvedenou metodu pro zobrazení výnosů produktu pro kolekci SalesOrderDetail:  
  
 [!code-csharp[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#6)]
 [!code-vb[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#6)]  
  
## <a name="see-also"></a>Viz také:

- [Soubor. edmx – přehled](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Dotazy v technologii LINQ to Entities](queries-in-linq-to-entities.md)
- [Volání funkcí v dotazech LINQ to Entities](calling-functions-in-linq-to-entities-queries.md)
