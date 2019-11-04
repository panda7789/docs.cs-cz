---
title: Základní typy – C# Průvodce
description: Další informace o základních typech (čísel, řetězců a objektů) ve všech C# programech
ms.date: 10/10/2016
ms.technology: csharp-fundamentals
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
ms.openlocfilehash: 7a75ad5080cd2646070447cbc3dcc46b8c73dd65
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420703"
---
# <a name="types-variables-and-values"></a>Typy, proměnné a hodnoty

C#je jazyk silného typu. Každá proměnná a konstanta má typ, stejně jako každý výraz, který je vyhodnocen na hodnotu. Každý podpis metody určuje typ pro každý vstupní parametr a pro návratovou hodnotu. Knihovna tříd .NET Framework definuje sadu předdefinovaných číselných typů i složitější typy, které reprezentují širokou škálu logických konstrukcí, jako je například systém souborů, síťová připojení, kolekce a pole objektů a data. Typický C# program používá typy z knihovny tříd a také uživatelsky definované typy, které modelují koncepty specifické pro doménu problému programu.  
  
Informace uložené v typu mohou zahrnovat následující:  
  
- Prostor úložiště, který proměnná typu vyžaduje.  
  
- Maximální a minimální hodnoty, které může představovat.  
  
- Členové (metody, pole, události atd.), které obsahuje.  
  
- Základní typ, ze kterého dědí.  
  
- Místo, kde bude přidělena paměť pro proměnné v době běhu.  
  
- Druhy operací, které jsou povoleny.  
  
Kompilátor používá informace o typu k ujištění, že všechny operace, které jsou provedeny ve vašem kódu, jsou *typově bezpečné*. Například pokud deklarujete proměnnou typu [int](language-reference/builtin-types/integral-numeric-types.md), kompilátor vám umožní použít proměnnou v operaci sčítání a odčítání. Pokud se pokusíte provést stejné operace s proměnnou typu [bool](language-reference/keywords/bool.md), kompilátor vygeneruje chybu, jak je znázorněno v následujícím příkladu:  
  
[!code-csharp[Type Safety](../../samples/snippets/csharp/concepts/basic-types/type-safety.cs)]  
  
> [!NOTE]  
> C a C++ vývojáři Všimněte si, že C#v není hodnota [bool](language-reference/keywords/bool.md) převoditelná na [int](language-reference/builtin-types/integral-numeric-types.md).  
  
Kompilátor vloží informace o typu do spustitelného souboru jako metadata. Modul CLR (Common Language Runtime) používá tato metadata v době běhu k dalšímu zajištění bezpečnosti typu při přidělování a uvolňování paměti.  

## <a name="specifying-types-in-variable-declarations"></a>Určení typů v deklaracích proměnných

Pokud deklarujete proměnnou nebo konstantu v programu, je nutné buď zadat její typ, nebo použít klíčové slovo [var](language-reference/keywords/var.md) , aby kompilátor mohl daný typ odvodit. Následující příklad ukazuje některé deklarace proměnných, které používají předdefinované číselné typy a komplexní uživatelsky definované typy:  
  
[!code-csharp[Variable Declaration](../../samples/snippets/csharp/concepts/basic-types/variable-declaration.cs)]  
  
Typy parametrů metody a návratové hodnoty jsou uvedeny v signatuře metody. Následující signatura ukazuje metodu, která vyžaduje [int](language-reference/builtin-types/integral-numeric-types.md) jako vstupní argument a vrací řetězec:  
  
[!code-csharp[Method Signature](../../samples/snippets/csharp/concepts/basic-types/method-signature.cs)]  
  
Po deklarování proměnné nemůže být znovu deklarována s novým typem a nelze jí přiřadit hodnotu, která není kompatibilní s deklarovaným typem. Například nelze deklarovat [int](language-reference/builtin-types/integral-numeric-types.md) a přiřadit jí logickou hodnotu [true](language-reference/keywords/true-literal.md). Hodnoty lze však převést na jiné typy, například když jsou přiřazeny k novým proměnným nebo předány jako argumenty metody. *Konverze typu* , která nezpůsobí ztrátu dat, je automaticky prováděna kompilátorem. Převod, který může způsobit ztrátu dat, vyžaduje *přetypování* ve zdrojovém kódu.

Další informace naleznete v tématu [přetypování a převody typu](programming-guide/types/casting-and-type-conversions.md).

## <a name="built-in-types"></a>Předdefinované typy

C#poskytuje standardní sadu předdefinovaných číselných typů k vyjádření celých čísel, hodnot s plovoucí desetinnou čárkou, logických výrazů, textových znaků, desetinných hodnot a dalších typů dat. Existují také předdefinované typy **řetězců** a **objektů** . Jsou k dispozici pro použití v jakémkoli C# programu. Další informace o předdefinovaných typech najdete v [referenční tabulce pro předdefinované typy](language-reference/keywords/built-in-types-table.md).  
  
## <a name="custom-types"></a>Vlastní typy

Použijete konstrukce [struct](language-reference/keywords/class.md), [Class](language-reference/keywords/class.md), [Interface](language-reference/keywords/interface.md)a [Enum](language-reference/keywords/enum.md) k vytvoření vlastních typů. Knihovna tříd .NET Framework sám o sobě kolekce vlastních typů poskytovaných Microsoftem, které můžete použít ve svých vlastních aplikacích. Ve výchozím nastavení jsou nejčastěji používané typy v knihovně tříd k dispozici v jakémkoli C# programu. Ostatní budou k dispozici pouze v případě, že explicitně přidáte odkaz na projekt do sestavení, ve kterém jsou definovány. Poté, co má kompilátor odkaz na sestavení, můžete deklarovat proměnné (a konstanty) typů deklarovaných v tomto sestavení ve zdrojovém kódu.
  
## <a name="generic-types"></a>Obecné typy

Typ lze deklarovat s jedním nebo více *parametry typu* , které slouží jako zástupný text pro skutečný typ ( *konkrétní typ*), který klientský kód poskytne při vytváření instance typu. Tyto typy se nazývají *Obecné typy*. Například .NET Framework typ <xref:System.Collections.Generic.List%601> má jeden parametr typu, který je podle konvence dán názvem *t*. Při vytváření instance typu zadáte typ objektů, které bude seznam obsahovat, například řetězec:  
  
[!code-csharp[Generic types](../../samples/snippets/csharp/concepts/basic-types/generic-type.cs)]
  
Použití parametru typu umožňuje znovu použít stejnou třídu pro uchování libovolného typu elementu, aniž by bylo nutné převést každý prvek na [Object](language-reference/builtin-types/reference-types.md#the-object-type). Třídy obecné kolekce se nazývají *kolekce se silnými typy* , protože kompilátor zná konkrétní typ prvků kolekce a může vyvolat chybu v době kompilace, pokud se například pokusíte přidat celé číslo do objektu `strings` v části předchozí příklad. Další informace najdete v tématu [Obecné typy](programming-guide/generics/index.md).

## <a name="implicit-types-anonymous-types-and-tuple-types"></a>Implicitní typy, anonymní typy a typy řazené kolekce členů

Jak bylo uvedeno dříve, můžete implicitně napsat místní proměnnou (ale ne členy třídy) pomocí klíčového slova [var](language-reference/keywords/var.md) . Proměnná stále přijímá typ v době kompilace, ale typ je poskytován kompilátorem. Další informace naleznete v tématu [implicitně typované lokální proměnné](programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
V některých případech je nevhodné vytvořit pojmenovaný typ pro jednoduché sady souvisejících hodnot, které nechcete ukládat nebo předávat mimo hranice metody. Pro tento účel můžete vytvořit *anonymní typy* . Další informace najdete v tématu [anonymní typy](programming-guide/classes-and-structs/anonymous-types.md).

Je běžné, že chcete vrátit více než jednu hodnotu z metody. Lze vytvořit *typy řazené kolekce členů* , které vracejí více hodnot v rámci jediného volání metody. Další informace najdete v tématu [řazené kolekce členů](tuples.md).

## <a name="the-common-type-system"></a>Obecný systém typů

Je důležité porozumět dvěma základním bodům o typu systému v .NET Framework:  
  
- Podporuje princip dědičnosti. Typy mohou být odvozeny od jiných typů, které se nazývají *základní typy*. Odvozený typ dědí (s určitými omezeními) metody, vlastnosti a další členy základního typu. Základní typ může být odvozen z jiného typu. v takovém případě odvozený typ dědí členy obou základních typů v rámci své Hierarchie dědičnosti. Všechny typy, včetně předdefinovaných číselných typů, jako je napříkladC# <xref:System.Int32> (klíčové slovo:`int`), jsou odvozeny z jednoho základního typu, kterýC# je<xref:System.Object>(klíčové slovo:`object`). Tato hierarchie sjednoceného typu se nazývá CTS ( [Common Type System](../standard/common-type-system.md) ). Další informace o dědičnosti v C#naleznete v tématu [Dědičnost](programming-guide/classes-and-structs/inheritance.md).  
  
- Každý typ v CTS je definován buď jako *typ hodnoty* , nebo jako *typ odkazu*. To zahrnuje všechny vlastní typy v knihovně tříd .NET Framework a také vlastní uživatelsky definované typy. Typy, které definujete pomocí klíčového slova [struct](language-reference/keywords/struct.md) , jsou typy hodnot; všechny předdefinované číselné typy jsou **struktury**. Další informace o typech hodnot naleznete v tématu [struktury](structs.md). Typy, které definujete pomocí klíčového slova [Class](language-reference/keywords/class.md) , jsou odkazové typy. Další informace o typech odkazů naleznete v tématu [třídy](programming-guide/classes-and-structs/classes.md). Typy odkazů a typy hodnot mají odlišná pravidla kompilace a jiné chování za běhu.

## <a name="see-also"></a>Viz také:

- [Struktury](structs.md)
- [Třídy](programming-guide/classes-and-structs/classes.md)
