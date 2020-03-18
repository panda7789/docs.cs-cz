---
title: Anonymní typy – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#]
- C# Language, anonymous types
ms.assetid: 59c9d7a4-3b0e-475e-b620-0ab86c088e9b
ms.openlocfilehash: 63bc5560ba19ff36764465a6b89b81c13beec97a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170335"
---
# <a name="anonymous-types-c-programming-guide"></a>Anonymní typy (Průvodce programováním v C#)

Anonymní typy poskytují pohodlný způsob, jak zapouzdřit sadu vlastností jen pro čtení do jednoho objektu bez nutnosti explicitně definovat typ jako první. Název typu je generován kompilátorem a není k dispozici na úrovni zdrojového kódu. Typ každé vlastnosti je odvozen kompilátorem.  
  
 Anonymní typy vytvoříte pomocí [nového](../../language-reference/operators/new-operator.md) operátoru společně s inicializátorem objektu. Další informace o inicializátorech objektů naleznete v [tématu Object and Collection Initializers](./object-and-collection-initializers.md).  
  
 Následující příklad ukazuje anonymní typ, který je `Amount` inicializován se dvěma vlastnostmi s názvem a `Message`.  
  
```csharp  
var v = new { Amount = 108, Message = "Hello" };  
  
// Rest the mouse pointer over v.Amount and v.Message in the following  
// statement to verify that their inferred types are int and string.  
Console.WriteLine(v.Amount + v.Message);  
```  
  
 Anonymní typy se obvykle používají ve [select](../../language-reference/keywords/select-clause.md) klauzuli výrazu dotazu vrátit podmnožinu vlastností z každého objektu ve zdrojové sekvenci. Další informace o dotazech naleznete v tématu [LINQ v c#](../../linq/index.md).  
  
 Anonymní typy obsahují jednu nebo více veřejných vlastností jen pro čtení. Žádné jiné druhy členů třídy, například metody nebo události, jsou platné. Výraz, který se používá k inicializaci vlastnosti, nemůže být `null`, anonymní funkcí nebo typem ukazatele.  
  
 Nejběžnější scénář je inicializovat anonymní typ s vlastnostmi z jiného typu. V následujícím příkladu předpokládejme, že existuje `Product`třída s názvem . Třída `Product` `Color` zahrnuje `Price` a vlastnosti, spolu s dalšími vlastnostmi, které vás nezajímají. Proměnná `products` je `Product` kolekce objektů. Deklarace anonymního typu `new` začíná klíčovým slovem. Deklarace inicializuje nový typ, který `Product`používá pouze dvě vlastnosti z . To způsobí, že menší množství dat, které mají být vráceny v dotazu.  
  
 Pokud nezadáte názvy členů v anonymním typu, kompilátor dává anonymním členům typu stejný název jako vlastnost, která se používá k jejich inicializaci. Je nutné zadat název vlastnosti, která je inicializována s výrazem, jak je znázorněno v předchozím příkladu. V následujícím příkladu jsou `Color` názvy vlastností anonymního typu a `Price`.  
  
 [!code-csharp[csRef30Features#81](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csRef30Features/CS/csref30.cs#81)]  
  
 Obvykle při použití anonymní typ inicializovat proměnnou, deklarujete proměnnou jako implicitně zadané místní proměnné pomocí [var](../../language-reference/keywords/var.md). Název typu nelze zadat v deklaraci proměnné, protože pouze kompilátor má přístup k základnímu názvu anonymního typu. Další informace `var`o [souborech naleznete v tématu Implicitně zadané místní proměnné](./implicitly-typed-local-variables.md).  
  
 Pole anonymně zadávaných prvků můžete vytvořit kombinací implicitně zadané místní proměnné a implicitně zadaného pole, jak je znázorněno v následujícím příkladu.  
  
```csharp  
var anonArray = new[] { new { name = "apple", diam = 4 }, new { name = "grape", diam = 1 }};  
```  
  
## <a name="remarks"></a>Poznámky  
 Anonymní typy jsou typy [tříd,](../../language-reference/keywords/class.md) které jsou odvozeny přímo z [objektu](../../language-reference/builtin-types/reference-types.md)a které nelze přetypovat na libovolný typ kromě [objektu](../../language-reference/builtin-types/reference-types.md). Kompilátor poskytuje název pro každý anonymní typ, i když aplikace nemůže získat přístup. Z hlediska za běhu společného jazyka anonymní typ se neliší od jiného typu odkazu.  
  
 Pokud dva nebo více anonymní objekt inicializátory v sestavení zadat posloupnost vlastností, které jsou ve stejném pořadí a které mají stejné názvy a typy, kompilátor zachází s objekty jako instance stejného typu. Sdílejí stejné informace o typu generované kompilátorem.  
  
 Pole, vlastnost, událost nebo návratový typ metody nelze deklarovat jako pole, vlastnost, událost nebo návratový typ metody jako pole, který má anonymní typ. Podobně nelze deklarovat formální parametr metody, vlastnost, konstruktor nebo indexer u anonymního typu. Chcete-li předat anonymní typ nebo kolekci, která obsahuje anonymní typy, jako argument metody, můžete deklarovat parametr jako objekt typu. Nicméně, dělá to poráží účel silného psaní. Pokud je nutné uložit výsledky dotazu nebo předat je mimo hranice metody, zvažte použití běžné pojmenované struktury nebo třídy namísto anonymního typu.  
  
 Vzhledem <xref:System.Object.Equals%2A> <xref:System.Object.GetHashCode%2A> k tomu, že metody a `Equals` `GetHashCode` na anonymních typech jsou definovány z hlediska a metody vlastností, dvě instance stejného anonymního typu jsou stejné pouze v případě, že jsou všechny jejich vlastnosti stejné.  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Inicializátory objektu a kolekce](./object-and-collection-initializers.md)
- [Začínáme s dotazy LINQ v jazyce C#](../concepts/linq/index.md)
- [LINQ v jazyce C#](../../linq/index.md)
