---
title: Funkce C# podporující LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: f1c045ffe311dfad851c7cace37966d8d42a22cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="c-features-that-support-linq"></a>Funkce C# podporující LINQ
Následující části jsou popsány nové jazykové konstrukty byla zavedená v C# 3.0. I když tyto nové funkce jsou používány pro určitý stupeň s [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy, nejsou omezeny na [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] a lze použít v libovolném kontextu, kde můžete najít je užitečné.  
  
## <a name="query-expressions"></a>Výrazy dotazu  
 Výrazy dotazů použít deklarativní syntaxi SQL nebo XQuery dotazu přes rozhraní IEnumerable kolekce. Při kompilování čas syntaxe dotazu je převedeno na volání metody [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] poskytovatele implementace metod rozšíření operátor standardní dotazu. Operátory standardní dotazu, které jsou v oboru tak, že zadáte odpovídající oboru názvů s řízení aplikací `using` – direktiva. Následující výraz dotazu přijímá pole řetězce, je skupin podle prvního znaku v řetězci a řadí do skupin.  
  
```  
var query = from str in stringArray  
            group str by str[0] into stringGroup  
            orderby stringGroup.Key  
            select stringGroup;  
```  
  
 Další informace najdete v tématu [LINQ – výrazy dotazů](../../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
## <a name="implicitly-typed-variables-var"></a>Implicitně typované proměnné (var)  
 Namísto explicitním zadáním typu, pokud deklarace a inicializace proměnné, můžete použít [var](../../../../csharp/language-reference/keywords/var.md) modifikátor na pokyn kompilátoru odvození a přiřadit typu, jak je vidět tady:  
  
```  
var number = 5;  
var name = "Virginia";  
var query = from str in stringArray  
            where str[0] == 'm'  
            select str;  
```  
  
 Proměnných deklarovaných jako `var` jsou, stejně jako silného typu jako proměnné s typem explicitně zadáte. Použití `var` díky je možné vytvořit anonymní typy, ale lze použít pro všechny místní proměnné. Pole lze také deklarovat s implicitní zadáním.  
  
 Další informace najdete v tématu [implicitně typované lokální proměnné](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="object-and-collection-initializers"></a>Inicializátory objektu a kolekce  
 Inicializátory objektu a kolekce umožňují inicializovat objekty bez nutnosti explicitně volání konstruktoru objektu. Inicializátory jsou obvykle používány ve výrazech dotazů, když se projektu zdrojová data do nového datového typu. Za předpokladu, že třídy s názvem `Customer` s veřejnou `Name` a `Phone` vlastnosti, inicializátoru objektu lze použít jako v následujícím kódu:  
  
```  
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };  
```  
  
 Další informace najdete v tématu [inicializátory objektu a kolekce](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
## <a name="anonymous-types"></a>Anonymní typy  
 Anonymní typ je vytvořený pomocí kompilátoru a je k dispozici pro kompilátor pouze název typu. Anonymní typy poskytnout vhodný způsob k seskupení sady vlastností dočasně ve výsledku dotazu bez nutnosti definovat samostatné pojmenovaného typu. Anonymní typy jsou inicializovány s nový výraz a inicializátoru objektu, jak je vidět tady:  
  
```  
select new {name = cust.Name, phone = cust.Phone};  
```  
  
 Další informace najdete v tématu [anonymní typy](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
## <a name="extension-methods"></a>Metody rozšíření  
 Metody rozšíření je statickou metodu, která může být přidružený k typu, takže může být volána, jako by šlo metodu instance typu. Tato funkce umožňuje, v důsledku toho "Přidat" nové metody k existujícím typům beze změny je ve skutečnosti. Standardní operátory dotazu jsou sady rozšiřující metody, které poskytují [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz funkce pro žádný typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Další informace najdete v tématu [rozšiřující metody](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
## <a name="lambda-expressions"></a>Výrazy lambda  
 Výraz lambda je vložená funkce, která používá = > – operátor k oddělení vstupní parametry z tělo funkce a může být převedena v době kompilace delegáta nebo strom výrazu se nezdařilo. V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programování, můžete narazit výrazy lambda při provedete přímá metoda volání standardní operátory dotazu.  
  
 Další informace naleznete v tématu:  
  
-   [Anonymní funkce](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [Výrazy lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [Stromy výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
  
## <a name="auto-implemented-properties"></a>Automaticky implementované vlastnosti  
 Automaticky implementované vlastnosti zkontrolujte přesnější deklarace vlastnosti. Pokud vlastnost deklarovat, jak je znázorněno v následujícím příkladu, bude vytvořen privátní, anonymní základní pole, které není přístupná kromě prostřednictvím vlastnost getter a setter.  
  
```  
public string Name {get; set;}  
```  
  
 Další informace najdete v tématu [Auto-Implemented vlastnosti](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
## <a name="see-also"></a>Viz také  
 [Language-Integrated Query (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
