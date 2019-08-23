---
title: Modifikátory přístupu – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: 266ece1e63bf6d32bf59406dbc72a9e6bd92eb45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924542"
---
# <a name="access-modifiers-c-programming-guide"></a>Modifikátory přístupu (Průvodce programováním v C#)
Všechny typy a členy typu mají úroveň přístupnosti, která určuje, zda lze použít z jiného kódu v sestavení nebo v jiných sestaveních. Následující modifikátory přístupu můžete použít k určení přístupnosti typu nebo člena při jeho deklaraci:  
  
 [public](../../language-reference/keywords/public.md)  
 Na daný typ nebo člen je možné přistupovat jakýkoli jiný kód ve stejném sestavení nebo jiném sestavení, které na něj odkazuje. 
  
 [private](../../language-reference/keywords/private.md)  
 Typ nebo člen může být k dispozici pouze pomocí kódu ve stejné třídě nebo struktuře.  
  
 [protected](../../language-reference/keywords/protected.md)  
 Typ nebo člen může být k dispozici pouze pomocí kódu ve stejné třídě nebo ve třídě, která je odvozena z této třídy.  
 [internal](../../language-reference/keywords/internal.md)  
 K typu nebo členu může být přistup libovolným kódem ve stejném sestavení, ale nikoli z jiného sestavení.  
  
 [chráněná interní](../../language-reference/keywords/protected-internal.md) K typu nebo členu lze přistupovat jakýmkoli kódem v sestavení, ve kterém je deklarován, nebo z odvozené třídy v jiném sestavení. 

 [soukromé chráněné](../../language-reference/keywords/private-protected.md) K typu nebo členu lze přistupovat pouze v rámci deklarovaného sestavení, kódu ve stejné třídě nebo v typu, který je odvozen z této třídy.
  
 Následující příklady ukazují, jak zadat modifikátory přístupu pro typ a člen:  
  
 [!code-csharp[csProgGuideObjects#72](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#72)]  
  
 Ne všechny modifikátory přístupu lze použít pro všechny typy nebo členy ve všech kontextech a v některých případech je přístupnost člena typu omezená přístupností jeho nadřazeného typu. Následující části obsahují další podrobnosti o usnadnění přístupu.  
  
## <a name="class-and-struct-accessibility"></a>Přístupnost třídy a struktury  
 Třídy a struktury, které jsou deklarovány přímo v rámci oboru názvů (jinými slovy, které nejsou vnořené v jiných třídách nebo strukturách) mohou být buď veřejné, nebo interní. Interní je výchozí, pokud není zadán modifikátor přístupu.  
  
 Členy struktury, včetně vnořených tříd a struktur, lze deklarovat jako veřejné, interní nebo soukromé. Členy třídy, včetně vnořených tříd a struktur, mohou být veřejné, chráněné interní, chráněné, interní, privátní nebo privátní. Úroveň přístupu pro členy třídy a členy struktury, včetně vnořených tříd a struktur, je ve výchozím nastavení soukromá. Soukromé vnořené typy nejsou přístupné z vnějšku nadřazeného typu.  
  
 Odvozené třídy nemohou mít větší přístupnost než jejich základní typy. Jinými slovy, nemůžete mít veřejnou třídu `B` , která je odvozena z interní třídy. `A` Pokud to bylo povoleno, mělo by to mít vliv `A` na veřejné, protože všichni chránění nebo interní `A` členové jsou k dispozici z odvozené třídy.  
  
 Můžete povolit konkrétním jiným sestavením přístup k interním typům pomocí InternalsVisibleToAttribute. Další informace naleznete v tématu [Friend Assemblies](../../../standard/assembly/friend-assemblies.md).  
  
## <a name="class-and-struct-member-accessibility"></a>Přístupnost třídy a člena struktury  
 Členy třídy (včetně vnořených tříd a struktur) lze deklarovat s libovolným šesti typy přístupu. Členy struktury nejde deklarovat jako chráněné, protože struktury nepodporují dědění.  
  
 V normálním případě přístupnost člena není větší než přístupnost typu, který ho obsahuje. Veřejný člen interní třídy však může být přístupný mimo sestavení, pokud člen implementuje metody rozhraní nebo přepíše virtuální metody, které jsou definovány ve veřejné základní třídě.  
  
 Typ každého členu, který je pole, vlastnost nebo událost musí být k dispozici alespoň jako člen samotný. Podobně, návratový typ a typy parametrů každého člena, který je metoda, indexer nebo delegát, musí být k dispozici alespoň jako samotný člen. Například nemůžete mít veřejnou metodu `M` , která vrací třídu `C` , pokud `C` není také veřejná. Podobně nemůžete mít chráněnou vlastnost typu `A` , pokud `A` je deklarována jako soukromá.  
  
 Uživatelem definované operátory musí být vždy deklarovány jako veřejné a statické. Další informace naleznete v tématu [přetížení operátoru](../../language-reference/operators/operator-overloading.md).  
  
 Finalizační metody nemůžou mít modifikátory dostupnosti.  
  
 Chcete-li nastavit úroveň přístupu pro člena třídy nebo struktury, přidejte příslušné klíčové slovo do deklarace člena, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideObjects#73](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#73)]  
  
> [!NOTE]
> Chráněná interní úroveň přístupnosti znamená chráněný nebo interní, nechráněnou a interní. Jinými slovy, chráněný interní člen může být k dispozici z libovolné třídy ve stejném sestavení, včetně odvozených tříd. Chcete-li omezit přístupnost jenom na odvozené třídy ve stejném sestavení, deklarujte samotnou třídu jako interní a deklarujte její členy jako chráněnou. Počínaje verzí C# 7,2 můžete také použít modifikátor privátního chráněného přístupu, abyste dosáhli stejného výsledku bez nutnosti vytvořit interní obsahující třídu.  
  
## <a name="other-types"></a>Další typy  
 Rozhraní deklarovaná přímo v rámci oboru názvů lze deklarovat jako veřejné nebo interní a stejně jako třídy a struktury, výchozí nastavení rozhraní pro interní přístup. Členy rozhraní jsou vždy veřejné, protože účelem rozhraní je povolit jiným typům přístup ke třídě nebo struktuře. Pro členy rozhraní nelze použít žádné modifikátory přístupu.  
  
 Členy výčtu jsou vždy veřejné a nelze použít žádné modifikátory přístupu.  
  
 Delegáti se chovají jako třídy a struktury. Ve výchozím nastavení mají interní přístup, pokud jsou deklarovány přímo v rámci oboru názvů a soukromý přístup, je-li vnořen.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](./index.md)
- [Rozhraní](../interfaces/index.md)
- [private](../../language-reference/keywords/private.md)
- [public](../../language-reference/keywords/public.md)
- [internal](../../language-reference/keywords/internal.md)
- [protected](../../language-reference/keywords/protected.md)
- [protected internal](../../language-reference/keywords/protected-internal.md)
- [private protected](../../language-reference/keywords/private-protected.md)
- [class](../../language-reference/keywords/class.md)
- [struct](../../language-reference/keywords/struct.md)
- [interface](../../language-reference/keywords/interface.md)
