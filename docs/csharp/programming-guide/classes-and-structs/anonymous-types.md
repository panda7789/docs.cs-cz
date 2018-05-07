---
title: Anonymní typy (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#]
- C# Language, anonymous types
ms.assetid: 59c9d7a4-3b0e-475e-b620-0ab86c088e9b
ms.openlocfilehash: 40c709e8a68f3a095672a9d4b7aacde5c62e12af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="anonymous-types-c-programming-guide"></a>Anonymní typy (Průvodce programováním v C#)
Anonymní typy poskytují pohodlný způsob pro zapouzdření sadu vlastností jen pro čtení bez nutnosti explicitně zadat typ nejprve do jednoho objektu. Název typu je generován kompilátoru a není k dispozici na úrovni zdrojového kódu. Kompilátor odvodí typ každou vlastnost.  
  
 Anonymní typy vytvoříte pomocí [nové](../../../csharp/language-reference/keywords/new.md) operátor společně s inicializátoru objektu. Další informace o inicializátory objektů najdete v tématu [inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
 Následující příklad ukazuje anonymní typ, který je inicializován s dvě vlastnosti s názvem `Amount` a `Message`.  
  
```csharp  
var v = new { Amount = 108, Message = "Hello" };  
  
// Rest the mouse pointer over v.Amount and v.Message in the following  
// statement to verify that their inferred types are int and string.  
Console.WriteLine(v.Amount + v.Message);  
```  
  
 Anonymní typy jsou obvykle používaných v [vyberte](../../../csharp/language-reference/keywords/select-clause.md) klauzule výrazu dotazu k návratu podmnožinu vlastnosti z každého objektu ve zdrojové sekvence. Další informace o dotazech naleznete v tématu [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
 Anonymní typy obsahovat jeden nebo více veřejné jen pro čtení vlastnosti. Žádné jiné druhy členy třídy, jako je například metody nebo událostí, jsou platné. Výraz, který se používá k chybě při inicializaci vlastnost nesmí být `null`, anonymní funkce nebo ukazatel typu.  
  
 Nejběžnější scénář je k chybě při inicializaci anonymní typ s vlastnostmi z jiného typu. V následujícím příkladu se předpokládá, že existuje třída s názvem `Product`. Třída `Product` zahrnuje `Color` a `Price` vlastnosti společně s další vlastnosti, které vás zajímají není. Proměnné `products` je kolekce `Product` objekty. Deklaraci anonymního typu začíná `new` – klíčové slovo. Inicializuje nový typ, který se používá pouze dvě vlastnosti z deklaraci `Product`. To způsobí, že menší množství dat, který se má vrátit v dotazu.  
  
 Pokud nezadáte názvy členů v anonymní typ, kompilátor poskytuje členů anonymní typ stejný název jako vlastnost k chybě při inicializaci je používán. Název vlastnosti, která je během inicializace s výrazem, musí zadat, jak je znázorněno v předchozím příkladu. V následujícím příkladu jsou názvy vlastností anonymního typu `Color` a `Price`.  
  
 [!code-csharp[csRef30Features#81](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/anonymous-types_1.cs)]  
  
 Obvykle použijete-li k chybě při inicializaci proměnné anonymní typ, můžete deklarovat proměnnou jako implicitně typovaná místní proměnné pomocí [var](../../../csharp/language-reference/keywords/var.md). Název typu nelze zadat v deklarace proměnné, protože pouze kompilátoru má přístup k základní název anonymního typu. Další informace o `var`, najdete v části [implicitně typované lokální proměnné](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
 Můžete vytvořit pole anonymně typové elementů kombinací implicitně typovaná místní proměnné a implicitně typovaná pole, jak je znázorněno v následujícím příkladu.  
  
```csharp  
var anonArray = new[] { new { name = "apple", diam = 4 }, new { name = "grape", diam = 1 }};  
```  
  
## <a name="remarks"></a>Poznámky  
 Anonymní typy jsou [třída](../../../csharp/language-reference/keywords/class.md) typy, které jsou odvozeny přímo z [objekt](../../../csharp/language-reference/keywords/object.md), a který nelze převést na libovolný typ kromě [objekt](../../../csharp/language-reference/keywords/object.md). Kompilátor poskytuje název pro každý anonymní typ, i když k nim nemá přístup vaší aplikace. Z pohledu modul common language runtime anonymní typ se neliší od jiných odkazového typu.  
  
 Pokud dva nebo více inicializátory anonymní objekt v sestavení zadat posloupnost vlastnosti, které jsou ve stejném pořadí a které mají stejné názvy a typy, kompilátor objekty považuje za instance stejného typu. Budou sdílet stejné informace generované kompilátorem typu.  
  
 Pole, vlastnost, událost nebo návratový typ metody tak, že má anonymní typ nelze deklarovat. Podobně nelze deklarovat formální parametr metoda, vlastnost, konstruktor nebo indexer tak, že má anonymního typu. Předávání anonymní typ nebo kolekce, která obsahuje anonymní typy jako argument pro metodu, můžou deklarovat parametr jako typ objektu. To však účinně chrání před účelem silného typování. Pokud musí ukládání výsledků dotazu nebo předejte je mimo hranice metoda, zvažte použití obyčejnou struktura s názvem nebo třída místo anonymního typu.  
  
 Protože <xref:System.Object.Equals%2A> a <xref:System.Object.GetHashCode%2A> metody pro anonymní typy jsou definovány z hlediska `Equals` a `GetHashCode` vlastností dvě instance stejného typu anonymní metody jsou stejné, pouze v případě, že jejich vlastnosti jsou stejné.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [Začínáme s dotazy LINQ v jazyce C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)
