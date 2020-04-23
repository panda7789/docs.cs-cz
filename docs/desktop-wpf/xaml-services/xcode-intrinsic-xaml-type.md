---
title: x:Code – vnitřní typ jazyka XAML
ms.date: 03/30/2017
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
ms.openlocfilehash: 4da72ed630c1df001e3fd6c7e55f866b94c4d9b1
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071554"
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code – vnitřní typ jazyka XAML
Umožňuje umístění kódu v rámci výroby XAML. Takový kód může být buď zkompilován libovolnou implementací procesoru XAML, která zkompiluje XAML, nebo ponechán v produkci XAML pro pozdější použití, jako je interpretace runtime.

## <a name="xaml-object-element-usage"></a>Použití elementu objektu XAML

```xaml
<x:Code>
   // code instructions, usually enclosed by CDATA...
</x:Code>
```

## <a name="remarks"></a>Poznámky

Kód v `x:Code` rámci prvku direktivy XAML je stále interpretován v rámci obecného oboru názvů XML a k dispozici obory názvů XAML. Proto je obvykle nutné uzavřít kód používaný `x:Code` pro `CDATA` uvnitř segmentu.

`x:Code`není povoleno pro všechny možné mechanismy nasazení výroby XAML. Ve specifických architekturách (například WPF) musí být kód zkompilován. V jiných architekturách `x:Code` použití může být obecně zakázáno.

Pro architektury, které `x:Code` umožňují spravovaný obsah, `x:Code` správný kompilátor jazyka pro obsah je určen nastavení a cíle obsahující projekt, který se používá ke kompilaci aplikace.

## <a name="wpf-usage-notes"></a>Poznámky k použití WPF

Kód deklarovaný v rámci `x:Code` wpf má několik významných omezení:

- Prvek `x:Code` směrnice musí být okamžitý podřízený prvek kořenový prvek výroby XAML.

- [x:Class Směrnice](xclass-directive.md) musí být uvedeny na nadřazený kořenový prvek.

- Kód umístěný `x:Code` v rámci bude zpracovánkompilací, která bude v rámci částečné třídy, která je již vytvořena pro tuto stránku XAML. Proto veškerý kód, který definujete, musí být členy nebo proměnnými této částečné třídy.

- Nelze definovat další třídy, jiné než vnoření třídy uvnitř částečné třídy (vnoření je povoleno, ale není typické, protože vnořené třídy nelze odkazovat v XAML). Obory názvů CLR jiné než obor názvů, který se používá pro existující částečnou třídu, nelze definovat ani přidat.

- Odkazy na entity kódu mimo obor názvů CLR částečné třídy musí být všechny plně kvalifikované. Pokud jsou deklarovány členy přepsání na částečné třídy přepsat členy, musí být zadán s klíčovým slovem přepsat specifické pro jazyk. Pokud členové `x:Code` deklarované v oboru konfliktu s členy částečné třídy vytvořené z XAML, takovým způsobem, že kompilátor hlásí konflikt, soubor XAML nelze kompilovat nebo načíst.

## <a name="see-also"></a>Viz také

- [x:Class – direktiva](xclass-directive.md)
- [Podkladový kód a kód XAML v subsystému WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [Přehled XAML (WPF)](../fundamentals/xaml.md)
