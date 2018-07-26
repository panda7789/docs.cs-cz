---
title: Funkce C# podporující LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: f1c045ffe311dfad851c7cace37966d8d42a22cc
ms.sourcegitcommit: f6343b070f3c66877338a05c8bfb0be9985255e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2018
ms.locfileid: "39220734"
---
# <a name="c-features-that-support-linq"></a>Funkce C# podporující LINQ
Následující část představuje nové jazykové konstrukce zavedené v jazyce C# 3.0. I když tyto nové funkce se používají v míře s [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy, nejsou omezena na [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] a můžete použít v libovolném kontextu, kde můžete najít je užitečné.  
  
## <a name="query-expressions"></a>Výrazy dotazu  
 Výrazy dotazů pomocí deklarativní syntaxe SQL nebo výraz XQuery podobný dotaz nad kolekcí IEnumerable. Při kompilaci syntaxe dotazu čas převést na volání metody [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] implementace poskytovatele rozšíření metody standardních dotazovacích operátorů. Operátory standardního dotazu, které jsou v oboru tak, že zadáte odpovídající obor názvů s řízení aplikací `using` směrnice. Následující výraz dotazu přijímá pole řetězců, skupin podle prvního znaku v řetězci a řadí skupiny.  
  
```  
var query = from str in stringArray  
            group str by str[0] into stringGroup  
            orderby stringGroup.Key  
            select stringGroup;  
```  
  
 Další informace najdete v tématu [LINQ – výrazy dotazů](../../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
## <a name="implicitly-typed-variables-var"></a>Implicitně typované proměnné (var)  
 Namísto explicitního určení typu, když deklarujete a inicializujete proměnnou, můžete použít [var](../../../../csharp/language-reference/keywords/var.md) modifikátor, abyste instruovali kompilátor k odvození a přiřadit typ, jak je znázorněno zde:  
  
```  
var number = 5;  
var name = "Virginia";  
var query = from str in stringArray  
            where str[0] == 'm'  
            select str;  
```  
  
 Proměnné deklarované jako `var` jsou stejně jako silného typu jako proměnné, jejíž typ zadat explicitně. Použití `var` je možné vytvořit anonymní typy, ale je možné pro všechny místní proměnné. Pole lze také deklarovat pomocí implicitního zápisu.  
  
 Další informace najdete v tématu [implicitně typované lokální proměnné](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="object-and-collection-initializers"></a>Inicializátory objektu a kolekce  
 Inicializátory objektu a kolekce umožňují inicializace objektů bez explicitního volání konstruktoru objektu. Inicializátory jsou obvykle používány ve výrazech dotazů, když jsou zdroje dat projektu do nového datového typu. Za předpokladu, že třídu s názvem `Customer` pomocí veřejného `Name` a `Phone` vlastnosti, inicializátor objektu můžete použít stejně jako v následujícím kódu:  
  
```  
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };  
```  
  
 Další informace najdete v tématu [inicializátory objektu a kolekce](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
## <a name="anonymous-types"></a>Anonymní typy  
 Anonymní typ, který je vytvořen kompilátorem a název typu je dostupná jenom pro kompilátor. Anonymní typy poskytují pohodlný způsob, jak seskupit sadu vlastností dočasně ve výsledku dotazu bez nutnosti definovat samostatně pojmenovaných typů. Anonymní typy jsou inicializovány s výraz new a inicializátoru objektu, jak je znázorněno zde:  
  
```  
select new {name = cust.Name, phone = cust.Phone};  
```  
  
 Další informace najdete v tématu [anonymní typy](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
## <a name="extension-methods"></a>Metody rozšíření  
 Rozšiřující metoda je statická metoda, která může být přidružený k typu, aby může být volán, jako by šlo o metodu instance na typu. Tato funkce umožňuje, v důsledku toho "Přidání" nové metody ke stávajícím typům bez skutečně jejich úpravou. Operátory standardního dotazu představují sadu rozšiřujících metod, které poskytují [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazování funkce pro libovolný typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Další informace najdete v tématu [rozšiřující metody](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
## <a name="lambda-expressions"></a>Výrazy lambda  
 Výraz lambda je vložená funkce, která používá = > – operátor k oddělení vstupní parametry z těla funkce a je možné převést v době kompilace, delegáta nebo strom výrazů. V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programování, můžete narazit výrazy lambda při provedení volání přímé metody standardních dotazovacích operátorů.  
  
 Další informace naleznete v tématu:  
  
-   [Anonymní funkce](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [Výrazy lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [Stromy výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
  
## <a name="auto-implemented-properties"></a>Automaticky implementované vlastnosti  
 Automaticky implementované vlastnosti stručnější Zkontrolujte deklaraci vlastnosti. Když deklarujete vlastnost, jak je znázorněno v následujícím příkladu, kompilátor vytvoří privátní, anonymní pomocným polem, které nejsou přístupné s výjimkou prostřednictvím vlastnosti getter a setter.  
  
```  
public string Name {get; set;}  
```  
  
 Další informace najdete v tématu [implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
## <a name="see-also"></a>Viz také  
 [Language-Integrated Query (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
