---
title: Základní typy – průvodce v C#
description: Další informace o základní typy (číselné, řetězce a objektu) ve všech aplikacích jazyka C#
ms.date: 10/10/2016
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
ms.openlocfilehash: dc91452bb261b7c799cf3b69cab5b33175148b8a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646745"
---
# <a name="types-variables-and-values"></a>Typy, proměnných a hodnot

C# je silně typovaný jazyk. Všechny proměnné a konstanty mají typ, stejně jako každý výraz, který se vyhodnotí na hodnotu. Každý podpis metody Určuje typ každého vstupního parametru a vracené hodnoty. Knihovna tříd rozhraní .NET Framework definuje sadu předdefinovaných číselných typů, jakož i složitější typy, které představují širokou škálu logických konstrukcí, jako je například systém souborů, připojení k síti, kolekce a pole objektů a data. Typické programu v C# používá typy z knihovny tříd i uživatelské typy, které modelují koncepty, které jsou specifické pro problematiku programu.  
  
Informace uložené v typu může patřit také následující:  
  
- Prostor úložiště, který vyžaduje proměnnou typu.  
  
- Maximální a minimální hodnoty, které mohou představovat.  
  
- Členy (metody, pole, události atd.), které obsahuje.  
  
- Základní typ, který dědí z.  
  
- Umístění, kde bude přidělena paměť pro proměnné v době běhu.  
  
- Typy operací, které jsou povoleny.  
  
Kompilátor používá informace o typu, abyste měli jistotu, že jsou všechny operace, které jsou prováděny ve vašem kódu *bezpečnost typů*. Například, pokud deklarujete proměnnou typu [int](language-reference/keywords/int.md), kompilátor umožňuje také použít proměnné a operace odčítání. Pokud se pokusíte provést tyto stejné operace na proměnnou typu [bool](language-reference/keywords/bool.md), kompilátor vygeneruje chybu, jak je znázorněno v následujícím příkladu:  
  
[!code-csharp[Type Safety](../../samples/snippets/csharp/concepts/basic-types/type-safety.cs)]  
  
> [!NOTE]  
> Vývojáře v C a C++, Všimněte si, že v jazyce C#, [bool](language-reference/keywords/bool.md) není převoditelná na [int](language-reference/keywords/int.md).  
  
Kompilátor vloží informace o typu do spustitelného souboru jako metadata. Common language runtime (CLR) používá tato metadata za běhu, aby byla dále podpořena bezpečnost typů, při přidělování a uvolňování paměti.  

## <a name="specifying-types-in-variable-declarations"></a>Určení typů v deklaracích proměnných

Pokud deklarujete proměnnou nebo konstantní v programu, musíte buď určit její typ nebo použít [var](language-reference/keywords/var.md) – klíčové slovo, abyste umožnili kompilátoru odvodit typ. Následující příklad ukazuje některé deklarace proměnných, které používají předdefinované číselné typy a komplexní typy definované uživatelem:  
  
[!code-csharp[Variable Declaration](../../samples/snippets/csharp/concepts/basic-types/variable-declaration.cs)]  
  
Typy parametrů metod a vrácené hodnoty jsou uvedeny v podpisu metody. Následující podpis představuje metodu, která vyžaduje [int](language-reference/keywords/int.md) jako vstupní argument a vrátí řetězec:  
  
[!code-csharp[Method Signature](../../samples/snippets/csharp/concepts/basic-types/method-signature.cs)]  
  
Jakmile je proměnná deklarována, nemůže být znovu deklarována s novým typem a nelze jí přiřadit hodnotu, která není kompatibilní s příslušným deklarovaným typem. Například nelze deklarovat [int](language-reference/keywords/int.md) a přiřadit mu hodnotu typu Boolean [true](language-reference/keywords/true.md). Hodnoty však lze převést na jiné typy, například když jsou přiřazeny nové proměnné nebo předány jako argumenty metody. A *převod typu* fakturuje se u tohoto nezpůsobí ztrátu dat probíhá automaticky kompilátorem. Vyžaduje převod, který může způsobit ztrátu dat *přetypování* ve zdrojovém kódu.

Další informace najdete v tématu [přetypování a převody typu](programming-guide/types/casting-and-type-conversions.md).

## <a name="built-in-types"></a>Vestavěné typy

Jazyk C# poskytuje standardní sadu předdefinovaných číselných typů k vyjádření celočíselných hodnot, s plovoucí desetinnou čárkou hodnoty bodů, logických výrazů, znaků textu, desetinných míst a dalších typů dat. Existují také vestavěné **řetězec** a **objekt** typy. Toto jsou k dispozici pro použití v libovolném programu C#. Další informace o předdefinovaných typech naleznete v tématu [referenční tabulky pro typy](language-reference/keywords/reference-tables-for-types.md).  
  
## <a name="custom-types"></a>Vlastní typy

Můžete použít [struktura](language-reference/keywords/class.md), [třídy](language-reference/keywords/class.md), [rozhraní](language-reference/keywords/interface.md), a [výčtu](language-reference/keywords/enum.md) konstrukce k tvorbě vlastních typů. Samotné knihovny tříd rozhraní .NET Framework je kolekce vlastních typů společnosti Microsoft, můžete použít ve svých vlastních aplikacích. Nejčastěji používané typy v knihovně tříd jsou standardně k dispozici v libovolném programu C#. Ostatní jsou k dispozici pouze v případě, že explicitně přidáte odkaz na sestavení, ve kterém jsou definovány. Poté, co kompilátor získá odkaz na sestavení, můžete deklarovat proměnné (a konstanty) typů deklarovaných v daném sestavení ve zdrojovém kódu.
  
## <a name="generic-types"></a>Obecné typy

Typ lze deklarovat s jedním nebo více *parametry typu* , které slouží jako zástupný symbol pro skutečný typ ( *konkrétní typ*), že kód klienta poskytne při vytváření instance daného typu. Tyto typy jsou označovány jako *obecných typů*. Například typ rozhraní .NET Framework <xref:System.Collections.Generic.List%601> má jeden parametr typu, které podle konvence je označen názvem *T*. Při vytváření instance typu, je třeba zadat typ objektů, které budou obsahovat seznam, například řetězec:  
  
[!code-csharp[Generic types](../../samples/snippets/csharp/concepts/basic-types/generic-type.cs)]
  
Použití parametru typu umožňuje znovu použít stejné třídy pro uložení libovolného typu prvku, aniž by bylo nutné převést každý prvek na [objekt](language-reference/keywords/object.md). Obecné třídy kolekcí se nazývají *silně typované kolekce* protože kompilátor zná konkrétní typ prvků kolekci a může vyvolat chyby při kompilaci, pokud, například pokusu o přidání celého čísla `strings` objekt v předchozím příkladu. Další informace najdete v tématu [obecných typů](programming-guide/generics/index.md).

## <a name="implicit-types-anonymous-types-and-tuple-types"></a>Implicitní typy, anonymní typy a typy řazené kolekce členů

Jak bylo uvedeno dříve, můžete implicitně zadat místní proměnnou (ale ne členy třídy) pomocí [var](language-reference/keywords/var.md) – klíčové slovo. Proměnná stále přijímá typ v době kompilace, ale typ je poskytován kompilátorem. Další informace najdete v tématu [implicitně typované lokální proměnné](programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
V některých případech je nevhodné vytvářet pojmenované typy pro jednoduché sady souvisejících hodnot, které nezamýšlíte ukládat ani přenášet mimo hranice metody. Můžete vytvořit *anonymní typy* pro tento účel. Další informace najdete v tématu [anonymní typy](programming-guide/classes-and-structs/anonymous-types.md).

Je běžné vyžadovat vrácení více než jednu hodnotu z metody. Můžete vytvořit *typy řazené kolekce členů* , který vrátí více hodnot v rámci jednoho volání metody. Další informace najdete v tématu [řazené kolekce členů](tuples.md)

## <a name="the-common-type-system"></a>Obecný systém typů

Je důležité porozumět dvěma základním principům systému typu v rozhraní .NET Framework:  
  
- Podporuje princip dědičnosti. Typy lze odvodit z jiných typů nazývaných *základní typy*. Odvozený typ zdědí (s určitými omezeními) metody, vlastnosti a ostatní členy základního typu. Základní typ lze odvozovat z některých jiných typů, ve kterém případě odvozený typ dědí členy obou základních typů v hierarchii dědičnosti. Všechny typy včetně předdefinovaných číselných typů, jako například <xref:System.Int32> (C# – klíčové slovo: `int`), jsou odvozeny výsledku z jednoho základního typu, které jsou <xref:System.Object> (C# – klíčové slovo: `object`). Tato hierarchie jednotného typu se nazývá [obecný systém typů](../standard/common-type-system.md) (CTS). Další informace o dědičnosti v C# najdete v tématu [dědičnosti](programming-guide/classes-and-structs/inheritance.md).  
  
- Každý typ v CTS je definována buď jako *typ hodnoty* nebo *odkazovat na typ*. To zahrnuje všechny vlastní typy v knihovně tříd rozhraní .NET Framework a také vlastní uživatelem definované typy. Typy, které definujete pomocí [struktura](language-reference/keywords/struct.md) – klíčové slovo jsou typy hodnot; předdefinované číselné typy jsou **struktury**. Další informace o typech hodnot naleznete v tématu [struktury](structs.md). Typy, které definujete pomocí [třídy](language-reference/keywords/class.md) – klíčové slovo jsou referenční typy. Další informace o typech odkazu viz [třídy](classes.md). Typy odkazů a typy hodnot mají jiná pravidla pro kompilaci a jiné chování za běhu.

## <a name="see-also"></a>Viz také:

- [Struktury](structs.md)
- [Třídy](classes.md)
