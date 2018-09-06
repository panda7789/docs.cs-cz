---
title: Anonymní typy (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#]
- C# Language, anonymous types
ms.assetid: 59c9d7a4-3b0e-475e-b620-0ab86c088e9b
ms.openlocfilehash: b732de508c8738de5e5e55168a6e17a1d88a3b02
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43779915"
---
# <a name="anonymous-types-c-programming-guide"></a>Anonymní typy (Průvodce programováním v C#)
Anonymní typy poskytují pohodlný způsob, jak zapouzdřit sadu vlastnosti jen pro čtení bez nutnosti explicitně definovat typ nejprve do jediného objektu. Název typu je generovaný kompilátorem a není k dispozici na úrovni zdrojového kódu. Typ každé vlastnosti je odvozen kompilátorem.  
  
 Vytvoříte pomocí anonymních typů [nové](../../../csharp/language-reference/keywords/new.md) operátor společně s inicializátorem objektu. Další informace o inicializátory objektů najdete v tématu [inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
 Následující příklad ukazuje anonymního typu, který je inicializován s dvě vlastnosti s názvem `Amount` a `Message`.  
  
```csharp  
var v = new { Amount = 108, Message = "Hello" };  
  
// Rest the mouse pointer over v.Amount and v.Message in the following  
// statement to verify that their inferred types are int and string.  
Console.WriteLine(v.Amount + v.Message);  
```  
  
 Anonymní typy se obvykle používají v [vyberte](../../../csharp/language-reference/keywords/select-clause.md) klauzule výrazu dotazu pro vrácení podmnožiny vlastností z jednotlivých objektů ze zdrojové sekvence. Další informace o dotazech najdete v tématu [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
 Anonymní typy obsahovat jeden nebo více veřejné vlastnosti jen pro čtení. Žádné jiné druhy členů třídy, jako je například metody nebo události, nejsou platné. Nemůže být výraz, který slouží k inicializaci vlastnosti `null`, anonymní funkci nebo typ ukazatele.  
  
 Nejběžnější scénář je inicializovat anonymní typ s vlastnostmi z jiného typu. V následujícím příkladu se předpokládá, že existuje třída s názvem `Product`. Třída `Product` zahrnuje `Color` a `Price` vlastnosti, společně s další vlastnosti, které vás nezajímají. Proměnné `products` je kolekce `Product` objekty. Anonymní typ deklarace začíná `new` – klíčové slovo. Deklarace inicializuje nový typ, který se používá pouze dvě vlastnosti z `Product`. To způsobí, že menší množství dat, který se má vrátit v dotazu.  
  
 Pokud nezadáte názvy členů v anonymním typu, kompilátor poskytuje členům anonymní typ stejný název jako vlastnost se používá k jejich inicializaci. Název vlastnosti, která je inicializována s výrazem, musíte zadat, jak je znázorněno v předchozím příkladu. V následujícím příkladu jsou názvy vlastností anonymních typů `Color` a `Price`.  
  
 [!code-csharp[csRef30Features#81](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/anonymous-types_1.cs)]  
  
 Obvykle, když pomocí anonymního typu inicializovat proměnnou, deklarujete proměnnou jako implicitně typovaná lokální proměnná s použitím [var](../../../csharp/language-reference/keywords/var.md). V deklaraci proměnné nelze zadat název typu, protože pouze kompilátor má přístup k základní název anonymního typu. Další informace o `var`, naleznete v tématu [implicitně typované lokální proměnné](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
 Kombinací implicitně typované lokální proměnnou a implicitně typovaná pole, můžete vytvořit pole anonymně typem prvků, jak je znázorněno v následujícím příkladu.  
  
```csharp  
var anonArray = new[] { new { name = "apple", diam = 4 }, new { name = "grape", diam = 1 }};  
```  
  
## <a name="remarks"></a>Poznámky  
 Anonymní typy jsou [třídy](../../../csharp/language-reference/keywords/class.md) typy, které jsou odvozeny přímo z [objekt](../../../csharp/language-reference/keywords/object.md), a která nelze přetypovat na libovolný typ s výjimkou [objekt](../../../csharp/language-reference/keywords/object.md). Kompilátor poskytuje název pro každý anonymní typ, i když vaše aplikace nejde získat přístup. Z pohledu modul common language runtime se nijak neliší od jakéhokoliv odkazového typu anonymního typu.  
  
 Pokud dva nebo více inicializátory anonymních objektů v sestavení určete pořadí vlastností, které jsou ve stejném pořadí a které mají stejné názvy a typy, kompilátor zpracovává objekty jako instance stejného typu. Sdílejí stejné informace o typu generované kompilátorem.  
  
 Nelze deklarovat pole, vlastnosti, události nebo návratového typu metody tak, že má anonymního typu. Podobně nelze deklarovat formální parametr metody, vlastnosti, konstruktor nebo indexeru tak, že má anonymního typu. K předání anonymního typu nebo kolekci, která obsahuje anonymní typy jako argument pro metodu, je možné deklarovat jako objekt typu parametru. To však poráží účel silných typů. Pokud musíte uložit výsledky dotazu nebo přenášet mimo hranice metody, zvažte použití běžné pojmenované struktury nebo třídy místo anonymního typu.  
  
 Protože <xref:System.Object.Equals%2A> a <xref:System.Object.GetHashCode%2A> z hlediska jsou definovány metody anonymních typů `Equals` a `GetHashCode` metody vlastností dva výskyty stejného anonymního typu jsou rovny, pouze pokud jejich vlastnosti jsou stejné.  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
- [Začínáme s dotazy LINQ v jazyce C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
- [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)
