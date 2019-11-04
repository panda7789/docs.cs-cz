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
ms.openlocfilehash: 7312c59cdcddfdbda39a4a9f05788b6a021f9b75
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459587"
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code – vnitřní typ jazyka XAML
Umožňuje umístění kódu v rámci výroby XAML. Takový kód může být zkompilován v jakékoli implementaci procesoru XAML, která kompiluje XAML nebo ponechána v produkci XAML pro pozdější použití, jako je například interpretace modulem runtime.  
  
## <a name="xaml-object-element-usage"></a>Použití elementu objektu XAML  
  
```xaml  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a>Poznámky  
 Kód v rámci elementu direktivy `x:Code` XAML je stále interpretován v rámci obecného oboru názvů XML a poskytnuté obory názvů XAML. Proto je obvykle nutné uzavřít kód, který se používá pro `x:Code` uvnitř segmentu `CDATA`.  
  
 `x:Code` není povolený pro všechny možné mechanismy nasazení v produkci XAML. V konkrétních rozhraních (například WPF) musí být kód zkompilován. V jiných rozhraních může být použití `x:Code` obecně zakázáno.  
  
 Pro architektury, které povolují spravovaný obsah `x:Code`, je správný kompilátor jazyka, který se má použít pro `x:Code` obsah, určen nastavením a cíli obsahujícího projektu, který se používá ke kompilaci aplikace.  
  
## <a name="wpf-usage-notes"></a>Poznámky k použití WPF  
 Kód deklarovaný v rámci `x:Code` pro WPF má několik důležitých omezení:  
  
- Element direktivy `x:Code` musí být bezprostředním podřízeným elementem kořenového elementu v produkci XAML.  
  
- v nadřazeném kořenovém elementu musí být zadána [direktiva x:Class](x-class-directive.md) .  
  
- Kód umístěný v rámci `x:Code` bude zpracován kompilací, aby byl v rámci oboru částečné třídy, která je již vytvořena pro tuto stránku XAML. Proto všechen kód, který definujete, musí být členy nebo proměnné této dílčí třídy.  
  
- Nelze definovat další třídy, jiné než vnořování třídy uvnitř dílčí třídy (vnořování je povoleno, ale není to obvyklé, protože vnořené třídy nemohou být v jazyce XAML odkazovány). Obory názvů CLR jiné než obor názvů, který se používá pro existující částečnou třídu, nelze definovat ani přidat do.  
  
- Odkazy na entity kódu mimo obor názvů částečného CLR třídy musí být plně kvalifikované. Pokud jsou členové deklarováni, je nutné zadat klíčové slovo override pro částečnou třídu. Jsou-li členové deklarované v `x:Code` rozsahu v konfliktu se členy částečné třídy vytvořenými z jazyka XAML, takovým způsobem, který kompilátor ohlásí konflikt, nemůže soubor XAML kompilovat nebo načíst.  
  
## <a name="see-also"></a>Viz také:

- [x:Class – direktiva](x-class-directive.md)
- [Podkladový kód a kód XAML v subsystému WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [Přehled XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
