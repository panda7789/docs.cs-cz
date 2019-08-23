---
title: 'Postupy: Volání vlastních databázových funkcí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: 6ddd6ebc6215ec17fa416fb0de8f81cf631365db
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936046"
---
# <a name="how-to-call-custom-database-functions"></a>Postupy: Volání vlastních databázových funkcí
Toto téma popisuje, jak volat vlastní funkce, které jsou definovány v databázi nástroje v rámci LINQ to Entities dotazů.  
  
 Databázové funkce, které jsou volány z LINQ to Entities dotazy, jsou spouštěny v databázi. Spouštění funkcí v databázi může zlepšit výkon aplikace.  
  
 Následující postup poskytuje osnovu vysoké úrovně pro volání vlastní databázové funkce. Následující příklad poskytuje další podrobnosti o krocích v postupu.  
  
### <a name="to-call-custom-functions-that-are-defined-in-the-database"></a>Volání vlastních funkcí, které jsou definovány v databázi  
  
1. Vytvořte vlastní funkci v databázi.  
  
     Další informace o vytváření vlastních funkcí v SQL Server naleznete v tématu [Create Function (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkID=139871).  
  
2. Deklarujte funkci v souboru SSDL (Store Schema Definition Language) souboru. edmx. Název funkce musí být stejný jako název funkce deklarované v databázi.  
  
     Další informace naleznete v tématu [Function Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).  
  
3. Přidejte odpovídající metodu do třídy v kódu aplikace a použijte <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> pro metodu Všimněte si <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> , že parametry a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> jsou v oboru názvů koncepčního modelu a názvu funkce v koncepčním rozhraní. model v uvedeném pořadí. Rozlišení názvu funkce pro LINQ rozlišuje velká a malá písmena.  
  
4. Volání metody v dotazu LINQ to Entities.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak volat vlastní databázovou funkci v rámci LINQ to Entitiesho dotazu. V příkladu se používá školní model. Informace o školním modelu najdete v tématu [vytvoření ukázkové školní databáze](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) a [Vytvoření souboru School. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).  
  
 Následující kód přidá `AvgStudentGrade` funkci do ukázkové databáze School.  
  
> [!NOTE]
> Postup volání vlastní databázové funkce je stejný bez ohledu na databázový server. Níže uvedený kód je však specifický pro vytvoření funkce v databázi SQL Server. Kód pro vytvoření vlastní funkce v jiných databázových serverech se může lišit.  
  
 [!code-sql[DP L2E MapToDBFunction#1](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]  
  
## <a name="example"></a>Příklad  
 Dále Deklarujte funkci v souboru SSDL (Store Schema Definition Language) souboru. edmx. Následující kód deklaruje `AvgStudentGrade` funkci ve SSDL:  
  
 [!code-xml[DP L2E MapToDBFunction#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]  
  
## <a name="example"></a>Příklad  
 Nyní vytvořte metodu a namapujte ji na funkci deklarovanou ve SSDL. Metoda v následující třídě je namapována na funkci definovanou v SSDL (výše) pomocí <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>. Při volání této metody se spustí odpovídající funkce v databázi.  
  
 [!code-csharp[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
 [!code-vb[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Nakonec zavolejte metodu v dotazu LINQ to Entities. Následující kód zobrazuje poslední názvy studentů a průměrné úrovně pro konzolu:  
  
 [!code-csharp[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
 [!code-vb[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]  
  
## <a name="see-also"></a>Viz také:

- [Soubor. edmx – přehled](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Dotazy v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
