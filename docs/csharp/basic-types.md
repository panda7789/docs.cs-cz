---
title: Základní typy – příručka jazyka C#
description: Informace o základních typech (číselné číslovky, řetězce a objekt) ve všech programech jazyka C#
ms.date: 10/10/2016
ms.technology: csharp-fundamentals
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
ms.openlocfilehash: bb2177026afb2eef2e14ece0c306bfd3ffe7af39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673261"
---
# <a name="types-variables-and-values"></a>Typy, proměnné a hodnoty

C# je jazyk silného typu. Každá proměnná a konstanta má typ, stejně jako každý výraz, který je vyhodnocen na hodnotu. Každý podpis metody určuje typ pro každý vstupní parametr a pro vrácenou hodnotu. Knihovna tříd rozhraní .NET Framework definuje sadu předdefinovaných číselných typů a také složitější typy, které představují širokou škálu logických konstrukcí, jako je systém souborů, síťová připojení, kolekce a pole objektů a kalendářních dat. Typický program jazyka C# používá typy z knihovny tříd, stejně jako uživatelem definované typy, které modelují koncepty, které jsou specifické pro problémovou doménu programu.  
  
Informace uložené v typu mohou zahrnovat následující:  
  
- Úložný prostor, který vyžaduje proměnná typu.  
  
- Maximální a minimální hodnoty, které může představovat.  
  
- Členové (metody, pole, události a tak dále), které obsahuje.  
  
- Základní typ, ze kterých dědí.  
  
- Umístění, kde bude paměť pro proměnné přidělena v době běhu.  
  
- Druhy operací, které jsou povoleny.  
  
Kompilátor používá informace o typu k ujistěte se, že všechny operace, které jsou prováděny ve vašem kódu jsou *typově bezpečné*. Například pokud deklarujete proměnnou typu [int](language-reference/builtin-types/integral-numeric-types.md), kompilátor umožňuje použít proměnnou navíc a odčítání operace. Pokud se pokusíte provést stejné operace s proměnnou typu [bool](language-reference/builtin-types/bool.md), kompilátor vygeneruje chybu, jak je znázorněno v následujícím příkladu:  
  
[!code-csharp[Type Safety](../../samples/snippets/csharp/concepts/basic-types/type-safety.cs)]  
  
> [!NOTE]  
> C a C++ vývojáři, všimněte si, že v Jazyce C#, [bool](language-reference/builtin-types/bool.md) není konvertibilní [int](language-reference/builtin-types/integral-numeric-types.md).  
  
Kompilátor vloží informace o typu do spustitelného souboru jako metadata. Modul CLR (COMMON Language runtime) používá tato metadata za běhu k dalšímu zajištění bezpečnosti typů při připřidělování a deklaracích paměti.  

## <a name="specifying-types-in-variable-declarations"></a>Určení typů v deklaracích proměnných

Když deklarujete proměnnou nebo konstantu v programu, musíte buď zadat její typ, nebo pomocí klíčového slova [var,](language-reference/keywords/var.md) aby kompilátor odvodil typ. Následující příklad ukazuje některé deklarace proměnných, které používají předdefinované číselné typy i složité uživatelem definované typy:  
  
[!code-csharp[Variable Declaration](../../samples/snippets/csharp/concepts/basic-types/variable-declaration.cs)]  
  
Typy parametrů metody a vrácené hodnoty jsou určeny v podpisu metody. Následující podpis zobrazuje metodu, která vyžaduje [int](language-reference/builtin-types/integral-numeric-types.md) jako vstupní argument a vrátí řetězec:  
  
[!code-csharp[Method Signature](../../samples/snippets/csharp/concepts/basic-types/method-signature.cs)]  
  
Po deklarování proměnné nelze znovu deklarovat s novým typem a nelze jí přiřadit hodnotu, která není kompatibilní s deklarovaným typem. Například nelze deklarovat [int](language-reference/builtin-types/integral-numeric-types.md) a pak mu `true`přiřadit logickou hodnotu . Hodnoty však mohou být převedeny na jiné typy, například když jsou přiřazeny k novým proměnným nebo předány jako argumenty metody. *Převod typu,* který nezpůsobí ztrátu dat, provádí automaticky kompilátor. Převod, který může způsobit ztrátu dat vyžaduje *přetypávání* ve zdrojovém kódu.

Další informace naleznete v [tématu Casting a převody typů](programming-guide/types/casting-and-type-conversions.md).

## <a name="built-in-types"></a>Předdefinované typy

C# poskytuje standardní sadu předdefinovaných číselných typů představujících celá čísla, hodnoty s plovoucí desetinnou čárkou, logické výrazy, textové znaky, desetinné hodnoty a další typy dat. Existují také vestavěné typy **řetězců** a **objektů.** Ty jsou k dispozici pro použití v libovolném programu Jazyka C#. Úplný seznam předdefinovaných typů naleznete [v tématu Předdefinované typy](language-reference/builtin-types/built-in-types.md).
  
## <a name="custom-types"></a>Vlastní typy

Konstrukce [struktury](language-reference/keywords/class.md), [třídy](language-reference/keywords/class.md), [rozhraní](language-reference/keywords/interface.md)a [výčtu](language-reference/builtin-types/enum.md) slouží k vytvoření vlastních typů. Samotná knihovna tříd rozhraní .NET Framework je kolekce vlastních typů poskytovaných společností Microsoft, které můžete použít ve vlastních aplikacích. Ve výchozím nastavení jsou nejčastěji používané typy v knihovně tříd k dispozici v libovolném programu jazyka C#. Jiné budou k dispozici pouze v případě, že explicitně přidáte odkaz na projekt do sestavení, ve kterém jsou definovány. Poté, co kompilátor má odkaz na sestavení, můžete deklarovat proměnné (a konstanty) typů deklarovaných v tomto sestavení ve zdrojovém kódu.
  
## <a name="generic-types"></a>Obecné typy

Typ může být deklarován s jedním nebo více *parametry typu,* které slouží jako zástupný symbol pro skutečný typ *(konkrétní typ),* který klientský kód poskytne při vytvoření instance typu. Tyto typy se nazývají *obecné typy*. Například typ <xref:System.Collections.Generic.List%601> rozhraní .NET Framework má jeden parametr typu, který podle konvence je uveden název *T*. Při vytváření instance typu určíte typ objektů, které bude seznam obsahovat, například řetězec:  
  
[!code-csharp[Generic types](../../samples/snippets/csharp/concepts/basic-types/generic-type.cs)]
  
Použití parametru type umožňuje znovu použít stejnou třídu pro uložení libovolného typu prvku, aniž by bylo nutné převést každý prvek na [objekt](language-reference/builtin-types/reference-types.md#the-object-type). Obecné kolekce třídy se nazývají *kolekce silného typu,* protože kompilátor zná konkrétní typ kolekce prvků a může vyvolat chybu v době kompilace, `strings` pokud se například pokusíte přidat celé číslo k objektu v předchozím příkladu. Další informace naleznete [v tématu Generics](programming-guide/generics/index.md).

## <a name="implicit-types-anonymous-types-and-tuple-types"></a>Implicitní typy, anonymní typy a typy řazené kolekce členů

Jak již bylo uvedeno dříve, můžete implicitně zadat místní proměnnou (ale ne členy třídy) pomocí klíčového slova [var.](language-reference/keywords/var.md) Proměnná stále přijímá typ v době kompilace, ale typ je poskytován kompilátorem. Další informace naleznete [v tématu Implicitně zadané místní proměnné](programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
V některých případech je nepohodlné vytvořit pojmenovaný typ pro jednoduché sady souvisejících hodnot, které nemáte v úmyslu ukládat nebo předat mimo hranice metody. Pro tento účel můžete vytvořit *anonymní typy.* Další informace naleznete [v tématu Anonymous types](programming-guide/classes-and-structs/anonymous-types.md).

Je běžné chtít vrátit více než jednu hodnotu z metody. Můžete vytvořit *řazené kolekce členů typy,* které vracejí více hodnot v volání jedné metody. Další informace naleznete v tématu [Tuples](tuples.md).

## <a name="the-common-type-system"></a>Společný typový systém

Je důležité pochopit dva základní body o systému typů v rozhraní .NET Framework:  
  
- Podporuje princip dědičnosti. Typy mohou být odvozeny z jiných typů, *nazývaných základní typy*. Odvozený typ dědí (s určitými omezeními) metody, vlastnosti a další členy základního typu. Základní typ může zase odvodit z jiného typu, v takovém případě odvozený typ dědí členy obou základních typů v hierarchii dědičnosti. Všechny typy, včetně předdefinovaných <xref:System.Int32> číselných typů, `int`například (klíčové slovo C#: <xref:System.Object> ), jsou `object`nakonec odvozeny z jednoho základního typu, což je (klíčové slovo C#: ). Tato jednotná hierarchie typů se nazývá [systém běžných typů](../standard/common-type-system.md) (CTS). Další informace o dědičnosti v c# naleznete v [tématu Dědičnost](programming-guide/classes-and-structs/inheritance.md).  
  
- Každý typ v CTS je definován jako *typ hodnoty* nebo *typ odkazu*. To zahrnuje všechny vlastní typy v knihovně tříd .NET a také vlastní uživatelem definované typy. Typy, které definujete `struct` `enum` pomocí klíčového slova nebo, jsou typy hodnot. Další informace o typech hodnot naleznete v [tématu Value types](language-reference/builtin-types/value-types.md). Typy, které definujete pomocí klíčového slova [třídy,](language-reference/keywords/class.md) jsou typy odkazů. Další informace o typech odkazů naleznete v [tématu Classes](programming-guide/classes-and-structs/classes.md). Typy odkazů a typy hodnot mají různá pravidla kompilace a různé chování za běhu.

## <a name="see-also"></a>Viz také

- [Typy struktur](language-reference/builtin-types/struct.md)
- [Typy výčtu](language-reference/builtin-types/enum.md)
- [Třídy](programming-guide/classes-and-structs/classes.md)
