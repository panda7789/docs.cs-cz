---
title: Základní typy - Průvodce C#
description: Další informace o základní typy (číslice, řetězce a objekt) ve všech aplikacích jazyka C#
ms.date: 10/10/2016
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
ms.openlocfilehash: 2e62a461e41f4172bd6dd512a71babb998924978
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="types-variables-and-values"></a>Typy, proměnných a hodnot  
C# je jazyk silného typu. Všechny proměnné a konstanta má typ, stejně jako každý výraz, který se vyhodnotí na hodnotu. Každý podpis metody Určuje typ pro každý vstupní parametr a návratovou hodnotu. Knihovna tříd rozhraní .NET Framework definuje sadu předdefinovaných číselnými typy a také více komplexní typy, které představují širokou škálu Logická konstrukce, jako je například systém souborů, připojení k síti, kolekce a pole objektů a dat. Typické programu v C# používá typy z knihovny tříd a uživatelem definované typy, které model koncepty, které jsou specifické pro program problém domény.  
  
Informace uložené v typu patří:  
  
-   Prostor úložiště, který vyžaduje proměnné typu.  
  
-   Maximální a minimální hodnoty, které může představovat.  
  
-   Členy (metody, pole, události a tak dále), které obsahuje.  
  
-   Základní typ, který dědí z.  
  
-   Umístění, kde se přidělí paměť pro proměnné v době běhu.  
  
-   Typy operací, které jsou povoleny.  
  
Kompilátor používá informace o typu a ujistěte se, že jsou všechny operace, které se provádí v kódu *bezpečnost typů*. Například, pokud deklarace proměnné typu [int](language-reference/keywords/int.md), kompilátor umožňuje dále používat proměnné a operace odčítání. Pokud se pokusíte provést tyto stejné operace v proměnné typu [bool](language-reference/keywords/bool.md), kompilátor vygeneruje chybu, jak je znázorněno v následujícím příkladu:  
  
[!code-csharp[Type Safety](../../samples/snippets/csharp/concepts/basic-types/type-safety.cs)]  
  
> [!NOTE]  
>  Jazyk C a C++ vývojáře, Všimněte si, že v jazyce C#, [bool](language-reference/keywords/bool.md) není převoditelná na [int](language-reference/keywords/int.md).  
  
Kompilátor vloží informace o typu do spustitelného souboru jako metadata. Modul CLR (CLR) používá aby metadata v době běhu k další zajistit bezpečnost typů, při přiděluje a uvolňuje volné paměti.  

## <a name="specifying-types-in-variable-declarations"></a>Určení typů v deklarace proměnných  
Když deklarovat proměnnou nebo konstantní v programu, musíte buď zadat typ, nebo použít [var](language-reference/keywords/var.md) – klíčové slovo umožníte kompilátoru odvození typu. Následující příklad ukazuje některé deklarace proměnných, které používají integrované číselnými typy a komplexní uživatelem definované typy:  
  
[!code-csharp[Variable Declaration](../../samples/snippets/csharp/concepts/basic-types/variable-declaration.cs)]  
  
Typy metoda parametry a návratové hodnoty jsou určené v podpis metody. Následující podpis ukazuje metodu, která vyžaduje [int](language-reference/keywords/int.md) jako vstupní argument a vrátí řetězec:  
  
[!code-csharp[Method Signature](../../samples/snippets/csharp/concepts/basic-types/method-signature.cs)]  
  
Po je deklarovaná proměnné, nelze ji znovu deklarované s nový typ a nelze přiřadit hodnotu, která není kompatibilní s příslušným deklarovaným typem. Například nelze deklarovat [int](language-reference/keywords/int.md) a přiřaďte ho logickou hodnotu z [true](language-reference/keywords/true.md). Hodnoty však můžete převést na jiné typy, např. Pokud jsou přiřazovány nové proměnné nebo předány jako argumenty metoda. A *typ – převod* této nemá příčina ztrátě dat se provádí automaticky kompilátorem. Vyžaduje převod, který může způsobit ztrátu dat *přetypování* ve zdrojovém kódu. 

Další informace najdete v tématu [převody přetypování a typ](programming-guide/types/casting-and-type-conversions.md).
 
## <a name="built-in-types"></a>Vestavěné typy
C# obsahuje standardní sadu předdefinovaných číselnými typy představují celá čísla, číslo s plovoucí čárkou bodu hodnoty, logické výrazy, textových znaků, desetinná čísla a dalších typů dat. Existují také předdefinované **řetězec** a **objekt** typy. Tyto jsou k dispozici pro použití v libovolné aplikaci C#. Další informace o předdefinovaných typů najdete v tématu [referenční tabulky pro typy](language-reference/keywords/reference-tables-for-types.md).  
  
## <a name="custom-types"></a>Vlastní typy  
Můžete použít [struktura](language-reference/keywords/class.md), [třída](language-reference/keywords/class.md), [rozhraní](language-reference/keywords/interface.md), a [výčtu](language-reference/keywords/enum.md) konstrukty, které vytvořit vlastní typy. Knihovna tříd rozhraní .NET Framework, samotné je kolekce vlastních typů od společnosti Microsoft, který můžete použít ve svých vlastních aplikacích. Ve výchozím nastavení jsou k dispozici v libovolné aplikaci C# nejčastěji používané typy v knihovně tříd. Jiné jsou k dispozici pouze v případě, že explicitně přidat odkaz na projekt na sestavení, ve kterém jsou definovány. Po kompilátor obsahuje odkaz na sestavení, můžou deklarovat proměnné (a konstanty) z typů deklarované v této sestavě ve zdrojovém kódu. 
  
## <a name="generic-types"></a>Obecné typy  
Typ lze deklarovat s jedním nebo více *parametry typu* slouží jako zástupný symbol pro skutečný typ ( *konkrétní typ*), kód klienta bude poskytovat při vytváření instance typu. Tyto typy jsou označovány jako *obecné typy*. Například typ rozhraní .NET Framework <xref:System.Collections.Generic.List%601> má jeden parametr typu, který podle konvence je přiřazen název *T*. Při vytváření instance typu, je třeba zadat typ objektů, které bude obsahovat seznam, například řetězec:  
  
[!code-csharp[Generic types](../../samples/snippets/csharp/concepts/basic-types/generic-type.cs)] 
  
Použití parametru typu umožňuje opakovaně použít stejnou třídu pro uložení všech typ elementu, aniž by bylo nutné převést každý element na [objekt](language-reference/keywords/object.md). Obecné třídy kolekcí se nazývají *silného typu kolekce* protože kompilátor zná konkrétní typ elementů kolekci a může vygenerovat chybu v kompilaci v případě, například pokusíte přidat do celéčíslo`strings` objektu v předchozím příkladu. Další informace najdete v tématu [obecné typy](programming-guide/generics/index.md). 

## <a name="implicit-types-anonymous-types-and-tuple-types"></a>Implicitní typy, anonymní typy a typy řazené kolekce členů  
Jak jsme uvedli dříve, můžete implicitně zadat místní proměnné (ale ne členy třídy) pomocí [var](language-reference/keywords/var.md) – klíčové slovo. Proměnná typu stále obdrží při kompilaci, ale typ zajišťuje kompilátoru. Další informace najdete v tématu [implicitně typované lokální proměnné](programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
V některých případech je nepraktické vytvoření pojmenovaného typu pro jednoduché sady souvisejících hodnot, které nemáte v úmyslu k uložení nebo předejte mimo hranice metoda. Můžete vytvořit *anonymní typy* pro tento účel. Další informace najdete v tématu [anonymní typy](programming-guide/classes-and-structs/anonymous-types.md).

Je běžné, který chcete vrátit více než jednu hodnotu z metody. Můžete vytvořit *řazené kolekce členů typy* , vrátí více hodnot v rámci jednoho volání metody. Další informace najdete v tématu [řazených kolekcí členů](tuples.md)

## <a name="the-common-type-system"></a>Obecný systém typů  
Je důležité pochopit dva základní body o systém typů v rozhraní .NET Framework:  
  
-   Podporuje se zásadou dědičnosti. Typy můžete odvozena od ostatních typů názvem *základní typy*. Odvozený typ dědí (s určitými omezeními), metody, vlastnosti a ostatním členům základního typu. Základní typ můžete zase odvozen od jiný typ, ve kterém případ odvozený typ dědí členů oba základní typy v hierarchii dědičnosti. Všechny typy, včetně předdefinovaných číselnými typy, jako například <xref:System.Int32> (C# – klíčové slovo: `int`), jsou odvozeny nakonec z jedné základní typ, který je <xref:System.Object> (C# – klíčové slovo: `object`). Tato hierarchie jednotná typ je volána [obecný systém typů](../standard/common-type-system.md) (STS). Další informace o dědičnosti v jazyce C#, najdete v části [dědičnosti](programming-guide/classes-and-structs/inheritance.md).  
  
-   Každý typ v CTS je definován jako buď *typ hodnoty* nebo *odkazují na typ*. To zahrnuje všechny vlastní typy v knihovně tříd rozhraní .NET Framework a také vlastní uživatelem definované typy. Typy, které se definují pomocí [struktura](language-reference/keywords/struct.md) – klíčové slovo jsou typy hodnot, jsou předdefinované číselnými typy **struktury**. Další informace o typech hodnota najdete v tématu [struktury](structs.md). Typy, které se definují pomocí [třída](language-reference/keywords/class.md) – klíčové slovo je odkaz na typy. Další informace o odkazové typy najdete v tématu [třídy](classes.md). Typy odkazů a hodnotových typů mají různá pravidla kompilaci a různé chování v běhu.
 
  
## <a name="see-also"></a>Viz také
[Struktury](structs.md)
[třídy](classes.md)
