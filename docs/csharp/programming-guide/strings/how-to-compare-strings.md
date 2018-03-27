---
title: "Postupy: porovnávání řetězců (C# Průvodce programováním)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
ms.assetid: e1268e28-ee98-4695-98e9-92280f1c33c0
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4837fa57c962cba841ffcc83c5bd4475a4faff0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-compare-strings-c-programming-guide"></a>Postupy: porovnávání řetězců (C# Průvodce programováním)

Při porovnávání řetězců jste generovala výsledek, který je uveden jeden řetězec je větší nebo menší než druhý, nebo zda jsou si rovny dva řetězce. Pravidla, podle kterých je určit výsledek se liší v závislosti na tom, jestli fungují *pořadí porovnání* nebo *Porovnání zohledňující jazykovou verzi*. Je důležité použít správný typ porovnání pro konkrétní úlohu.

 Až budete mít k porovnání nebo seřadit hodnoty dvou řetězců bez ohledu na jazykové konvence, použijte základní pořadí porovnání. Základní pořadí porovnání (`System.StringComparison.Ordinal`) je malá a velká písmena, což znamená, že dva řetězce musí odpovídat znak pro znaků: "a" není rovno "A" nebo "A". Je variace často používané `System.StringComparison.OrdinalIgnoreCase`, který bude shodovat s "a", "A", a "A". `StringComparison.OrdinalIgnoreCase`často se používá k porovnání názvy souborů, názvy cest, síťových cest a jiný řetězec, jehož hodnota nezmění podle národního prostředí uživatele počítače. Další informace naleznete v tématu <xref:System.StringComparison?displayProperty=nameWithType>.

 Porovnání zohledňující jazykovou verzi jsou obvykle používány k porovnání a řazení řetězců, které jsou vstupní koncoví uživatelé, protože znaky a řazení konvence tyto řetězce se můžou lišit podle národního prostředí uživatele počítače. I řetězce, které obsahují stejné znaky může seřadit odlišně v závislosti na jazykové verze aktuálního vlákna.

> [!NOTE]
> Při porovnávání řetězců byste měli použít metody, které explicitně zadat, jaký typ porovnání, který chcete provést. Díky kódu mnohem víc udržovatelný a čitelné. Pokud je to možné, použijte přetížení metody <xref:System.String?displayProperty=nameWithType> a <xref:System.Array?displayProperty=nameWithType> třídy trvají <xref:System.StringComparison> parametru výčtu, můžete určit, jaký typ porovnání k provedení. Je vyhýbat se používání `==` a `!=` operátory při porovnávání řetězců. Navíc vyhýbat se používání <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody instance, protože žádný z přetížení trvá <xref:System.StringComparison>.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak správně porovnávání řetězců, jejichž hodnoty nedojde ke změně podle národního prostředí uživatele počítače. Kromě toho také ukazuje *interning řetězec* funkce jazyka C#. Když program deklaruje minimálně dva identické řetězec proměnné, kompilátor je uloží všechny ve stejném umístění. Při volání <xref:System.Object.ReferenceEquals%2A> metoda, uvidíte, že dva řetězce ve skutečnosti odkazovat na stejný objekt v paměti. Použití <xref:System.String.Copy%2A?displayProperty=nameWithType> metoda zrušení interning, jak je znázorněno v příkladu.

[!code-csharp[csProgGuideStrings#11](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#11)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak porovnat řetězce upřednostňovaný způsob, jak pomocí <xref:System.String?displayProperty=nameWithType> metod, které berou <xref:System.StringComparison> výčtu. Všimněte si, že <xref:System.String.CompareTo%2A?displayProperty=nameWithType> instance metody nejsou zde použít, protože žádný z přetížení trvá <xref:System.StringComparison>.

[!code-csharp[csProgGuideStrings#31](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#31)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak řadit a hledat řetězce v matici způsobem zohledňující jazykovou verzi pomocí statické <xref:System.Array> metod, které berou <xref:System.StringComparer?displayProperty=nameWithType> parametr.

[!code-csharp[csProgGuideStrings#32](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#32)]

Kolekce tříd, například <xref:System.Collections.Hashtable?displayProperty=nameWithType>, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>, a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> mít konstruktory, které provést <xref:System.StringComparer?displayProperty=nameWithType> parametr, pokud je typ elementy nebo klíčů `string`. Obecně platí, by měl používat tyto konstruktory, kdykoli je to možné a zadat buď `Ordinal` nebo `OrdinalIgnoreCase`.

## <a name="see-also"></a>Viz také
 <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>  
 <xref:System.StringComparer?displayProperty=nameWithType>  
 [Řetězce](../../../csharp/programming-guide/strings/index.md)  
 [Porovnávání řetězců](../../../standard/base-types/comparing.md)  
 [Globalizace a lokalizace aplikací](/visualstudio/ide/globalizing-and-localizing-applications)