---
title: Modifikátory přístupu (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: 6be0ae4f6497dfb2db9607f61c4ede5083d57dc7
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48036250"
---
# <a name="access-modifiers-c-programming-guide"></a>Modifikátory přístupu (Průvodce programováním v C#)
Všechny typy a členy typu mít úrovni přístupu, které řídí, jestli je možné použít od jiného kódu v sestavení nebo jiná sestavení. Následující modifikátory přístupu můžete použít k určení přístupnost typu nebo členu při jeho deklaraci:  
  
 [public](../../../csharp/language-reference/keywords/public.md)  
 Tento typ nebo člen je přístupný libovolnému jinému kódu ve stejném sestavení nebo libovolnému sestavení která na něj odkazuje. 
  
 [private](../../../csharp/language-reference/keywords/private.md)  
 Tento typ nebo člen je přístupný pouze kódu ve stejné třídě nebo struktuře.  
  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 Tento typ nebo člen je přístupný pouze kódu ve stejné třídě, nebo ve třídě, která je odvozena z třídy.  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 Tento typ nebo člen je přístupný libovolnému kódu ve stejném sestavení, ale ne z jiného sestavení.  
  
 [interní chráněné](../../../csharp/language-reference/keywords/protected-internal.md) tento typ nebo člen je přístupný libovolnému kódu v sestavení, ve kterém je deklarována, nebo z odvozené třídy v jiném sestavení. 

 [privátní, chráněné](../../../csharp/language-reference/keywords/private-protected.md) tento typ nebo člen je přístupný pouze v rámci jeho deklarovaného sestavení kódu ve stejné třídě, nebo typ, který je odvozen z této třídy.
  
 Následující příklady ukazují, jak zadat modifikátory přístupu na typů a členů:  
  
 [!code-csharp[csProgGuideObjects#72](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_1.cs)]  
  
 Ne všechny modifikátory přístupu může využívat všechny typy nebo členy ve všech kontextech, a v některých případech je omezená dostupnost člena typu usnadnění jeho nadřazeného typu. Následující oddíly poskytují další podrobnosti o usnadnění přístupu.  
  
## <a name="class-and-struct-accessibility"></a>Třídy a struktury přístupnost  
 Třídy a struktury, které jsou deklarovány přímo v rámci oboru názvů (jinými slovy, které nejsou vnořené v rámci jiné třídy nebo struktury) může být veřejné nebo interní. Interní je výchozí nastavení, pokud není zadána žádná modifikátor přístupu.  
  
 Členy struktury, včetně vnořené třídy a struktury, mohou být deklarovány jako veřejné, interní nebo privátní. Třída členů, včetně vnořené třídy a struktury, můžou být veřejné, chráněné vnitřní, chráněný, interní, private, protected nebo private. Úroveň přístupu pro členy třídy a členy struktury, včetně vnořených třídách a strukturách, je ve výchozím nastavení privátní. Privátní vnořené typy nejsou dostupné z oblasti mimo nadřazeného typu.  
  
 Odvozené třídy nemůže mít vyšší dostupnost než jejich základní typy. Jinými slovy, nemůže mít veřejnou třídu `B` , která je odvozena z interní třída `A`. Pokud to bylo povoleno, bude mít vliv na provádění `A` veřejné, protože všechny chráněné nebo interní členy `A` jsou přístupné z odvozené třídy.  
  
 Můžete povolit konkrétní jiná sestavení pro přístup k interní typy s použitím atributu InternalsVisibleToAttribute. Další informace najdete v tématu [přátelských sestavení](../concepts/assemblies-gac/friend-assemblies.md).  
  
## <a name="class-and-struct-member-accessibility"></a>Třídy a přístupnost členů struktury  
 Členy třídy (včetně vnořené třídy a struktury) mohou být deklarovány s žádným z šesti typy přístupu. Členy struktury nejde deklarovat jako chránit, protože struktury nepodporují dědičnosti.  
  
 Za normálních okolností přístupnost člena není větší než přístupnost typu, který jej obsahuje. Veřejný člen interní třídy však může být dostupné z oblasti mimo sestavení, pokud člen implementuje metody rozhraní nebo přepsání virtuální metody, které jsou definovány v veřejnou základní třídu.  
  
 Typ člena, který je pole, vlastnost nebo událost musí být přinejmenším stejně dostupná jako samotný člen. Podobně návratový typ a typy parametrů jakéhokoli členu, který je metoda, indexer nebo delegáta musí být přinejmenším stejně dostupná jako samotný člen. Například nemůžete mít veřejnou metodu `M` , který vrátí třídu `C` Pokud `C` je také veřejné. Podobně, nemůže mít chráněné vlastnosti typu `A` Pokud `A` je deklarována jako soukromá.  
  
 Operátory definované uživatelem musí být vždy deklarována jako veřejná. Další informace najdete v tématu [– operátor (referenční dokumentace jazyka C#)](../../../csharp/language-reference/keywords/operator.md).  
  
 Finalizační metody nemůže mít modifikátory.  
  
 K nastavení úrovně přístupu pro člen třídy nebo struktury, přidejte odpovídající klíčové slovo deklarace člena, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideObjects#73](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_2.cs)]  
  
> [!NOTE]
>  Na úrovni chráněného interní přístupnost znamená, že není chráněné nebo interní chráněné a interní. Jinými slovy chráněné vnitřní člen je přístupný z jiné třídy ve stejném sestavení, včetně odvozených tříd. Pokud chcete omezit přístup k pouze odvozené třídy ve stejném sestavení, deklarujte interní vlastní třídy a deklarovat její členy jako chráněný. Také od C# 7.2, použijte modifikátor privátní chráněného přístupu k dosažení stejného výsledku bez nutnost třídu obsahující interní.  
  
## <a name="other-types"></a>Jiné typy  
 Rozhraní deklarován přímo v rámci oboru názvů lze deklarovat jako veřejný nebo interní a stejně jako třídy a struktury, výchozí rozhraní pro přístup k interní. Členy rozhraní jsou vždy veřejné, protože rozhraní slouží k povolení dalších typů pro přístup k třídě nebo struktuře. Žádné modifikátory přístupu můžete použít pro členy rozhraní.  
  
 Členy výčtu jsou vždycky veřejné a lze použít bez přístupu modifikátory přístupu.  
  
 Delegáty se chovat jako třídy a struktury. Ve výchozím nastavení mají interní přístup při deklaraci přímo v rámci oboru názvů a soukromý přístup při vnořené.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Rozhraní](../../../csharp/programming-guide/interfaces/index.md)  
- [private](../../../csharp/language-reference/keywords/private.md)  
- [public](../../../csharp/language-reference/keywords/public.md)  
- [internal](../../../csharp/language-reference/keywords/internal.md)  
- [protected](../../../csharp/language-reference/keywords/protected.md)  
- [protected internal](../../../csharp/language-reference/keywords/protected-internal.md)  
- [private protected](../../../csharp/language-reference/keywords/private-protected.md)  
- [class](../../../csharp/language-reference/keywords/class.md)  
- [struct](../../../csharp/language-reference/keywords/struct.md)  
- [interface](../../../csharp/language-reference/keywords/interface.md)
