---
title: Modifikátory přístupu (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: ec275d4782fee047b16fd114c4d22ceb03eecb11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33314106"
---
# <a name="access-modifiers-c-programming-guide"></a>Modifikátory přístupu (Průvodce programováním v C#)
Všechny typy a členy typu mít úrovni přístupu, který řídí, zda lze použít z jiný kód ve vaší sestavení nebo jiné sestavení. Následující modifikátory přístupu můžete použít k určení usnadnění typ nebo člen při deklarujte ji:  
  
 [public](../../../csharp/language-reference/keywords/public.md)  
 Typ nebo člen je přístupná jiným kódem ve stejném sestavení nebo jiné sestavení, které na ni odkazuje. 
  
 [private](../../../csharp/language-reference/keywords/private.md)  
 Typ nebo člen jsou přístupné pouze prostřednictvím kódu ve stejné třídě nebo struktuře.  
  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 Typ nebo člen jsou přístupné pouze prostřednictvím kódu ve stejné třídě nebo ve třídě, která je odvozená od třídy.  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 Typ nebo člen je přístupný kód ve stejném sestavení, ale nikoli z jiné sestavení.  
  
 [chráněné interní](../../../csharp/language-reference/keywords/protected-internal.md) typ nebo člen je přístupný pomocí žádný kód v sestavení, ve kterém je deklarovaná nebo v odvozené třídě v jiném sestavení. 

 [privátní chráněné](../../../csharp/language-reference/keywords/private-protected.md) typ nebo člen je přístupný pouze v rámci jeho deklarující sestavení kódu ve stejné třídě nebo v typu, který je odvozen od třídy.
  
 Následující příklady ukazují, jak určit modifikátory přístupu pro typ a člen:  
  
 [!code-csharp[csProgGuideObjects#72](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_1.cs)]  
  
 Ne všechny modifikátory přístupu můžou používat všechny typy nebo členy ve všech kontextech a v některých případech je usnadnění člena typu omezené usnadnění jeho obsahující typu. Následující části obsahují další podrobnosti o usnadnění přístupu.  
  
## <a name="class-and-struct-accessibility"></a>Třída a usnadnění – struktura  
 Třídy a struktury, které jsou deklarované přímo v rámci oboru názvů (v jiná slova, které nejsou vnořené v jiných třídy nebo struktury) může být veřejné nebo interní. Interní je výchozí, pokud není zadán žádný – modifikátor přístupu.  
  
 Struktura členů, včetně vnořené třídy a struktury, lze deklarovat jako veřejné, interní nebo privátní. Třídy členů, včetně vnořené třídy a struktury, může být veřejné, chráněné interní, chráněné, interní, privátní chráněný nebo privátní. Úroveň přístupu pro členy třídy a struktury členy, včetně vnořené třídy a struktury, je soukromé ve výchozím nastavení. Privátní vnořené typy nejsou dostupné z oblasti mimo nadřazeného typu.  
  
 Odvozené třídy nemohou mít větší usnadnění než jejich základní typy. Jinými slovy, nemůže mít veřejnou třídu `B` která je odvozena z interní třídy `A`. Pokud to bylo povoleno, bude mít vliv na provádění `A` veřejné, protože všechny chráněné nebo interní členy `A` jsou přístupné z odvozené třídy.  
  
 Můžete povolit konkrétní ostatních sestavení pomocí InternalsVisibleToAttribute přístup k vaší interní typy. Další informace najdete v tématu [přátelských sestavení](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).  
  
## <a name="class-and-struct-member-accessibility"></a>Třída a usnadnění přístupu členů struktury  
 Členy třídy (včetně vnořené třídy a struktury) lze deklarovat s žádným z šesti typy přístupu. Členové struktury nelze deklarovat jako chráněný, protože struktury nepodporují dědičnosti.  
  
 Za normálních okolností usnadnění člena není větší než usnadnění typ, který ji obsahuje. Veřejné členem interní třída však může být dostupné z oblasti mimo sestavení, pokud člen implementuje metody rozhraní nebo přepsání virtuální metody, které jsou definovány v základní třídě veřejné.  
  
 Typ člena, který je pole, vlastnost nebo události musí být dostupné jako člena samotného. Podobně návratový typ a typy parametrů kteréhokoli člena, který je metoda, indexer nebo delegáta musí být dostupné jako člena samotného. Například nemůže mít veřejnou metodu `M` třídy, který vrací `C` Pokud `C` je také veřejné. Podobně, nemůže mít chráněná vlastnost typu `A` Pokud `A` je deklarován jako soukromé.  
  
 Uživatelem definované operátory musí být vždy deklarován jako veřejné. Další informace najdete v tématu [– operátor (referenční dokumentace jazyka C#)](../../../csharp/language-reference/keywords/operator.md).  
  
 Finalizační metody nemůže mít modifikátory dostupnosti.  
  
 Nastavení úrovně přístupu pro člena třídě nebo struktuře, přidejte příslušné – klíčové slovo deklarace členů, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideObjects#73](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_2.cs)]  
  
> [!NOTE]
>  Úroveň chráněné interní usnadnění znamená chráněný nebo interní, není chráněný a interní. Jinými slovy chráněného člena interní přístupná z libovolné třídy ve stejném sestavení, včetně odvozené třídy. Usnadnění přístupu k pouze odvozené třídy ve stejném sestavení, deklarovat interní vlastní třídy, a omezit deklarovat její členy jako chráněný. Navíc počínaje 7.2 C#, použijte modifikátor privátní chráněného přístupu k dosažení stejného výsledku nevyžaduje, aby interní třída obsahující.  
  
## <a name="other-types"></a>Jiné typy  
 Rozhraní deklarovat přímo v oboru názvů lze deklarovat jako veřejný nebo interní a, stejně jako tříd a struktur, výchozí rozhraní pro přístup k interní. Členové rozhraní jsou vždy veřejné, protože účelem rozhraní je povolíte další typy pro přístup k třídě nebo struktuře. Žádné modifikátory přístupu je použít pro členy rozhraní.  
  
 Členové výčtu jsou vždy veřejné a mohou být použity žádné modifikátory přístupu.  
  
 Delegáti chovat jako třídy a struktury. Ve výchozím nastavení mají interní přístup při deklarované přímo v rámci oboru názvů a soukromý přístup při vnořený.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Rozhraní](../../../csharp/programming-guide/interfaces/index.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [protected internal](../../../csharp/language-reference/keywords/protected-internal.md)  
 [private protected](../../../csharp/language-reference/keywords/private-protected.md)  
 [class](../../../csharp/language-reference/keywords/class.md)  
 [struct](../../../csharp/language-reference/keywords/struct.md)  
 [interface](../../../csharp/language-reference/keywords/interface.md)
