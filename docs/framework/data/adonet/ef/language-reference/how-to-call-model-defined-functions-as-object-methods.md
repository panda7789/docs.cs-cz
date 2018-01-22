---
title: "Postupy: volání funkce Model definován jako objekt metody"
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
ms.assetid: 33bae8a8-4ed8-4a1f-85d1-c62ff288cc61
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 81b9f8099f98915ec0b0f83dbe0f90e506cb2a79
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-model-defined-functions-as-object-methods"></a>Postupy: volání funkce Model definován jako objekt metody
Toto téma popisuje, jak volat funkci definované model jako metodu <xref:System.Data.Objects.ObjectContext> objektu nebo jako statickou metodu vlastní třídy. A *modelu definované funkce* je funkce, která je definována v konceptuálním modelu. Postupy v tomto tématu popisují, jak volat tyto funkce přímo namísto volání je z technologie LINQ dotazy entity. Informace o volání funkcí modelu definované v technologii LINQ na entity dotazy najdete v tématu [postupy: Call Model-Defined funkcí v dotazech](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md).  
  
 Zda můžete volat funkci model definován jako <xref:System.Data.Objects.ObjectContext> metoda nebo jako statickou metodu vlastní třídy, je nutné nejprve mapovat metodu do modelu definované funkce se <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>. Ale když definujete metodu na <xref:System.Data.Objects.ObjectContext> třídy, je nutné použít <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> vlastnost vystavit LINQ poskytovatele, že když definujete vlastní třídy statickou metodu, je nutné použít <xref:System.Linq.IQueryable.Provider%2A> vlastnost vystavit LINQ zprostředkovatele. Další informace najdete v tématu příklady, které postupujte podle pokynů níže.  
  
 Zadejte níže uvedených postupech obsahuje podrobný přehled pro volání funkce modelu definované jako metodu na <xref:System.Data.Objects.ObjectContext> objektu a jako statickou metodu vlastní třídy. Příklady, které poskytují podrobnější informace o krocích v postupech. V postupech se předpokládá, že jste definovali funkci v konceptuálním modelu. Další informace najdete v tématu [postupy: definování vlastní funkce v konceptuálním modelu](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).  
  
### <a name="to-call-a-model-defined-function-as-a-method-on-an-objectcontext-object"></a>K volání funkce model definován jako metodu objektu ObjectContext  
  
1.  Přidání zdrojového souboru rozšíření částečné třídy odvozené od <xref:System.Data.Objects.ObjectContext> třída, vygenerována automaticky prostřednictvím nástroje Entity Framework. Definování se zakázaným inzerováním CLR samostatného zdrojového souboru bude zabránit ke ztrátě při znovu vygeneruje soubor změny.  
  
2.  Přidat běžnou metodu language runtime (CLR) do vaší <xref:System.Data.Objects.ObjectContext> třídu, která provede následující akce:  
  
    -   Mapuje funkci definovanou v konceptuálním modelu. Chcete-li mapovat metodu, je nutné použít <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> metodě. Všimněte si, že <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametry atributu jsou název oboru názvů konceptuálního modelu a název funkce v konceptuálním modelu, v uvedeném pořadí. Funkce překladu názvů u LINQ je malá a velká písmena.  
  
    -   Vrátí výsledky <xref:System.Linq.IQueryProvider.Execute%2A> metoda, která je vrácena <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> vlastnost.  
  
3.  Volejte metodu jako člena na instanci systému <xref:System.Data.Objects.ObjectContext> třídy.  
  
### <a name="to-call-a-model-defined-function-as-static-method-on-a-custom-class"></a>K volání funkce model definován jako statickou metodu vlastní třídy  
  
1.  Přidejte třídu do vaší aplikace s statickou metodu, která provede následující akce:  
  
    -   Mapuje funkci definovanou v konceptuálním modelu. Chcete-li mapovat metodu, je nutné použít <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> metodě. Všimněte si, že <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametry atributu jsou název oboru názvů konceptuálního modelu a název funkce v konceptuálním modelu, v uvedeném pořadí.  
  
    -   Přijímá <xref:System.Linq.IQueryable> argument.  
  
    -   Vrátí výsledky <xref:System.Linq.IQueryProvider.Execute%2A> metoda, která je vrácena <xref:System.Linq.IQueryable.Provider%2A> vlastnost.  
  
2.  Volat metodu jako člen statickou metodu pro vlastní třídu  
  
## <a name="example"></a>Příklad  
 **Volání funkce modelu definované jako metodu objektu ObjectContext**  
  
 Následující příklad ukazuje, jak volat funkci definované model jako metodu <xref:System.Data.Objects.ObjectContext> objektu. V příkladu se používá [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).  
  
 Zvažte funkce konceptuálního modelu nižší, než je vrací výnosy produktu pro určitý produkt. (Informace o přidání funkce do konceptuálního modelu najdete v tématu [postupy: definování vlastní funkce v konceptuálním modelu](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).)  
  
 [!code-xml[DP L2E Methods on ObjectContext#4](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#4)]  

## <a name="example"></a>Příklad  
 Následující kód přidá metodu pro `AdventureWorksEntities` třídu, která se mapuje na výše uvedené funkce konceptuálního modelu.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#2)]
 [!code-vb[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#2)]  
  
## <a name="example"></a>Příklad  
 Následující kód volá metodu výše a zobrazte výnosy produktu pro zadaný produkt:  
  
 [!code-csharp[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#3)]
 [!code-vb[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak volat funkci definované modelu, která vrátí kolekci (jako <xref:System.Linq.IQueryable%601> objekt). Vezměte v úvahu následující konceptuálního modelu funkce, která vrátí všechny `SalesOrderDetails` pro ID daného produktu.  
  
 [!code-xml[DP L2E Methods on ObjectContext#7](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#7)]  
  
## <a name="example"></a>Příklad  
 Následující kód přidá metodu pro `AdventureWorksEntities` třídu, která se mapuje na výše uvedené funkce konceptuálního modelu.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#8)]
 [!code-vb[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#8)]  
  
## <a name="example"></a>Příklad  
 Následující kód volá metodu. Všimněte si, že vrácený <xref:System.Linq.IQueryable%601> dotazu je další vylepšení vrátit součty řádek pro každou `SalesOrderDetail`.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#9)]
 [!code-vb[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#9)]  
  
## <a name="example"></a>Příklad  
 **Volání funkce modelu definované jako statickou metodu vlastní třídy**  
  
 Další příklad ukazuje, jak volat funkci model definován jako statickou metodu vlastní třídy. V příkladu se používá [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).  
  
> [!NOTE]
>  Při volání funkce modelu definované jako statickou metodu na vlastní třídu, model definované funkce, musíte přijmout kolekce a vrátí agregace hodnot v kolekci.  
  
 Zvažte funkce konceptuálního modelu nižší, než je vrací výnosy produktu pro kolekci podrobnosti prodejní objednávky. (Informace o přidání funkce do konceptuálního modelu najdete v tématu [postupy: definování vlastní funkce v konceptuálním modelu](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).).  
  
 [!code-xml[DP L2E Methods on ObjectContext#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#1)]
  
## <a name="example"></a>Příklad  
 Následující kód přidá třídu do vaší aplikace, který obsahuje statickou metodu, která se mapuje na výše uvedené funkce konceptuálního modelu.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#5)]
 [!code-vb[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#5)]  
  
## <a name="example"></a>Příklad  
 Následující kód volá metodu výše a zobrazte výnosy produktu pro kolekci podrobnosti prodejní objednávky:  
  
 [!code-csharp[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#6)]
 [!code-vb[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#6)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled souboru EDMX](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Dotazy v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [Volání funkcí v dotazech LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
