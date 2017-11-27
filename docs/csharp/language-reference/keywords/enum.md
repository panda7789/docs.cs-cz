---
title: "enum (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords: enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
caps.latest.revision: "36"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 00ae9b555ae73db445fe4a4facf00753bf8c759a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="enum-c-reference"></a>enum (Referenční dokumentace jazyka C#)
`enum` – Klíčové slovo se používá k deklaraci výčet, odlišné typ, který se skládá ze sady pojmenované konstanty názvem seznamu enumerátor.  
  
 Obvykle je nejvhodnější definovat výčet přímo v oboru názvů, aby všechny třídy v oboru názvů můžete přistupovat pomocí stejné pohodlí. Výčet však mohou být také vnořené ve třídě nebo struktuře.  
  
 Ve výchozím nastavení první enumerátor má hodnotu 0 a hodnotu každé následných enumerátor je zvýšenou o hodnotu 1. Například v následujícím výčtu `Sat` je `0`, `Sun` je `1`, `Mon` je `2`, a tak dále.  
  
```  
enum Days {Sat, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 Výčty můžete použít inicializátory přepsat výchozí hodnoty, jak je znázorněno v následujícím příkladu.  
  
```  
enum Days {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 V tento výčet je nucen pořadí elementů spuštění z `1` místo `0`. Nicméně se doporučuje včetně konstanta, která má hodnotu 0. Další informace najdete v tématu [výčtové typy](../../../csharp/programming-guide/enumeration-types.md).  
  
 Každý typ výčtu je základní typ, který mohou být jakéhokoli typu integrální s výjimkou [char](../../../csharp/language-reference/keywords/char.md). Základní typ výčtu elementů výchozí hodnota je [int](../../../csharp/language-reference/keywords/int.md). Výčet integrální jiného typu, například deklarovat [bajtů](../../../csharp/language-reference/keywords/byte.md), použijte středník po identifikátor následovaný typem, jak je znázorněno v následujícím příkladu.  
  
```  
enum Days : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 Seznam schválených typy výčtu `byte`, [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [krátké](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [Celé_číslo](../../../csharp/language-reference/keywords/uint.md), [dlouho](../../../csharp/language-reference/keywords/long.md), nebo [ulong](../../../csharp/language-reference/keywords/ulong.md).  
  
 Proměnné typu `Days` lze přiřadit žádnou hodnotu v rozsahu základní typ; hodnoty nejsou omezeny na pojmenované konstanty.  
  
 Výchozí hodnota `enum E` je hodnota vyprodukované výraz `(E)0`.  
  
> [!NOTE]
>  Enumerátor nesmí obsahovat prázdné znaky v názvu.  
  
 Základní typ Určuje, jak velké úložiště je přidělen pro každý enumerátor. Nicméně je nutné převést z explicitní přetypování `enum` typu integrální typ. Například následující příkaz přiřadí enumerátor `Sun` proměnné typu [int](../../../csharp/language-reference/keywords/int.md) pomocí přetypování převést z `enum` k `int`.  
  
```  
int x = (int)Days.Sun;  
```  
  
 Když použijete <xref:System.FlagsAttribute?displayProperty=nameWithType> pro výčet, který obsahuje prvky, které mohou být kombinovány s bitové `OR` operace atribut má vliv na chování `enum` při použití s některé nástroje. Tyto změny může dojít, při použití nástrojů, jako <xref:System.Console> třídy metody a vyhodnocovací filtr výrazů. (Podívejte se na třetí příklad).  
  
## <a name="robust-programming"></a>Robustní programování  
 Stejně jako v jakékoli konstanta všechny odkazy na jednotlivé hodnoty výčtu jsou převedeny na číselné literály v době kompilace. To můžete vytvořit potenciální problémy správy verzí, jak je popsáno v [konstanty](../../../csharp/programming-guide/classes-and-structs/constants.md).  
  
 Přiřazení dalších hodnot k nové verze výčty nebo změna hodnot výčtu členy v nové verzi může způsobit problémy závislé zdrojového kódu. Hodnoty výčtu jsou často používány v [přepínač](../../../csharp/language-reference/keywords/switch.md) příkazy. Pokud do nebyly přidané další prvky `enum` typu, výchozí část výrazu switch, který lze vybrat neočekávaně.  
  
 Pokud jinými vývojáři použít kódu, měli byste jim poskytnout pokyny o tom, jak by měl svůj kód reagovat Pokud nové prvky jsou přidány do žádné `enum` typy.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu, výčet, `Days`, je deklarován. Dva výčty explicitně převést na celé číslo a přiřazený k proměnné celé číslo.  
  
 [!code-csharp[csrefKeywordsTypes#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_1.cs)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je základní typ možnost používá k deklaraci `enum` jejíž členové jsou typu `long`. Všimněte si, že i když je základní typ výčtu `long`, členové výčtu stále musí být explicitně převést na typ `long` pomocí přetypování.  
  
 [!code-csharp[csrefKeywordsTypes#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_2.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití a účinku <xref:System.FlagsAttribute?displayProperty=nameWithType> atributu u `enum` deklarace.  
  
 [!code-csharp[csrefKeywordsTypes#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_3.cs)]  
  
## <a name="comments"></a>Komentáře  
 Pokud odeberete `Flags`, v příkladu se zobrazí následující hodnoty:  
  
 `5`  
  
 `5`  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Výčtové typy](../../../csharp/programming-guide/enumeration-types.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabulka implicitních číselných převodů](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tabulka explicitních číselných převodů](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
