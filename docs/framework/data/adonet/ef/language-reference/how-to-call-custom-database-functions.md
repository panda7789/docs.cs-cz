---
title: 'Postupy: volání funkce vlastní databáze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: 790bb8d4ea1e146d94ea7cf153b8909c6cc1af7a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-call-custom-database-functions"></a>Postupy: volání funkce vlastní databáze
Toto téma popisuje, jak volat vlastní funkce, které jsou definovány v databázi z v rámci LINQ dotazy entity.  
  
 Funkce databáze, které se nazývají z technologie LINQ na entity dotazy jsou spouštěny v databázi. Provádění funkcí v databázi může zlepšit výkon aplikace.  
  
 Následující postup obsahovala hrubý nástin pro volání funkce vlastní databázi. Příklad, který následuje obsahuje více podrobností o kroků v postupu.  
  
### <a name="to-call-custom-functions-that-are-defined-in-the-database"></a>K volání vlastní funkce, které jsou definovány v databázi  
  
1.  Vytvoření vlastní funkce ve vaší databázi.  
  
     Další informace o vytvoření vlastní funkce v systému SQL Server najdete v tématu [CREATE FUNCTION (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkID=139871).  
  
2.  Funkce v jazyce definici schématu (SSDL) úložiště souboru .edmx deklarujte. Název funkce musí být stejný jako název funkce deklarované v databázi.  
  
     Další informace najdete v tématu [funkce elementu (SSDL)](http://msdn.microsoft.com/library/b60cfc3d-8b93-423e-8c99-b867256640a4).  
  
3.  Přidat odpovídající metodu do třídy v kódu aplikace a aplikovat <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> metodě Všimněte si, že <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametry atributu jsou název oboru názvů konceptuálního modelu a název funkce v konceptuálním model v uvedeném pořadí. Funkce překladu názvů u LINQ je malá a velká písmena.  
  
4.  Volání metody v dotazu LINQ to Entities.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak volat funkci vlastní databázi z v rámci LINQ entity dotazu. V příkladu školní modelu. Informace o modelu školní najdete v tématu [vytváření ukázkovou databázi školy](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) a [generování školní .edmx souboru](http://msdn.microsoft.com/library/c48b3907-a8be-4fe6-884c-e95af1852758).  
  
 Následující kód přidá `AvgStudentGrade` funkce ukázkovou databázi školy.  
  
> [!NOTE]
>  Postup pro volání funkce vlastní databáze je stejný bez ohledu na serveru databáze. Následující kód je však specifické pro vytvoření funkce v databázi systému SQL Server. Kód pro vytvoření vlastní funkce v jiných databázových serverů se můžou lišit.  
  
 [!code-sql[DP L2E MapToDBFunction#1](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]  
  
## <a name="example"></a>Příklad  
 V dalším kroku deklarujte funkce v jazyce definici schématu (SSDL) úložiště souboru .edmx. Následující kód deklaruje `AvgStudentGrade` funkce v SSDL:  
  
 [!code-xml[DP L2E MapToDBFunction#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]  
  
## <a name="example"></a>Příklad  
 Teď vytvořte metodu a namapovat je funkce deklarované v SSDL. Metoda v následující třídy je namapovaná na funkci definovanou v SSDL (výše) pomocí <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>. Pokud tato metoda je volána, je spustit odpovídající funkce v databázi.  
  
 [!code-csharp[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
 [!code-vb[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Nakonec volejte metodu v dotazu LINQ to Entities. Následující kód zobrazí studentů příjmení a průměrná tříd do konzoly:  
  
 [!code-csharp[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
 [!code-vb[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled souboru EDMX](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Dotazy v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
