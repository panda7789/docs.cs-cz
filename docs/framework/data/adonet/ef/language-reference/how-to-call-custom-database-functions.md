---
title: 'Postupy: Volání vlastních databázových funkcí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: f3177ab98382506770c4655c62573da5c1d96c69
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78848753"
---
# <a name="how-to-call-custom-database-functions"></a>Postupy: Volání vlastních databázových funkcí

Toto téma popisuje, jak volat vlastní funkce, které jsou definovány v databázi z v rámci LINQ na dotazy entity.

Databázové funkce, které jsou volány z LINQ na entity dotazy jsou spouštěny v databázi. Provádění funkcí v databázi může zlepšit výkon aplikace.

Níže uvedený postup poskytuje osnovu vysoké úrovně pro volání vlastní databázové funkce. Následující příklad obsahuje další podrobnosti o krocích v postupu.

## <a name="to-call-custom-functions-that-are-defined-in-the-database"></a>Volání vlastních funkcí, které jsou definovány v databázi

1. Vytvořte vlastní funkci v databázi.

     Další informace o vytváření vlastních funkcí na serveru SQL Server naleznete v tématu [CREATE FUNCTION (Transact-SQL).](/sql/t-sql/statements/create-function-transact-sql)

2. Deklarujte funkci v jazyce definice schématu úložiště (SSDL) souboru .edmx. Název funkce musí být stejný jako název funkce deklarované v databázi.

     Další informace naleznete v [tématu Function Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).

3. Přidejte odpovídající metodu do třídy v <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> kódu aplikace a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> aplikujte a na metodu Všimněte si, že a parametry atributu jsou název oboru názvů koncepčního modelu a název funkce v koncepčním modelu. Rozlišení názvu funkce pro LINQ rozlišuje malá a velká písmena.

4. Volání metody v linq entity dotazu.  

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak volat vlastní databázové funkce z v rámci linq entity dotazu. Příklad používá model školy. Informace o školním modelu naleznete v [tématu Vytvoření ukázkové databáze školy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) a [generování souboru School .edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).

Následující kód přidá `AvgStudentGrade` funkci do ukázkové databáze školy.

> [!NOTE]
> Kroky pro volání vlastní databázové funkce jsou stejné bez ohledu na databázový server. Níže uvedený kód je však specifické pro vytvoření funkce v databázi serveru SQL Server. Kód pro vytvoření vlastní funkce v jiných databázových serverech se může lišit.

[!code-sql[DP L2E MapToDBFunction#1](~/samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]

## <a name="example"></a>Příklad

Dále deklarujte funkci v jazyce definice schématu úložiště (SSDL) souboru *.edmx.* Následující kód deklaruje `AvgStudentGrade` funkci v SSDL:

[!code-xml[DP L2E MapToDBFunction#2](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]

## <a name="example"></a>Příklad

Nyní vytvořte metodu a namapujte ji na funkci deklarovanou v SSDL. Metoda v následující třídě je mapována na funkci definovanou v SSDL (výše) pomocí <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>. Při volání této metody je spuštěna odpovídající funkce v databázi.

[!code-csharp[DP L2E MapToDBFunction#3](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
[!code-vb[DP L2E MapToDBFunction#3](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]

## <a name="example"></a>Příklad

Nakonec volání metody v linq entity dotazu. Následující kód zobrazuje příjmení studentů a průměrné známky konzole:

[!code-csharp[DP L2E MapToDBFunction#4](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
[!code-vb[DP L2E MapToDBFunction#4](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]

## <a name="see-also"></a>Viz také

- [Přehled souboru .edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Dotazy v technologii LINQ to Entities](queries-in-linq-to-entities.md)
