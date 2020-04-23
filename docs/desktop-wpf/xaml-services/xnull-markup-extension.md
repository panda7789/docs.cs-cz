---
title: x:Null – rozšíření značek
ms.date: 03/30/2017
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- "Null"
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
ms.openlocfilehash: b83e893f951c15eca69fbb6b002369dd723ca469
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071428"
---
# <a name="xnull-markup-extension"></a>x:Null – rozšíření značek

Určuje `null` jako hodnotu pro člena XAML.

## <a name="xaml-attribute-usage"></a>Použití atributu XAML

```xaml
<object property="{x:Null}" .../>
```

## <a name="remarks"></a>Poznámky

Klíčové slovo pro odkaz null v jazyce C# a C++ je null. Klíčové slovo jazyka Microsoft Visual `Nothing`Basic pro nulový odkaz je , ale vždy používáte `{x:Null}` jako použití XAML bez ohledu na to, který jazyk za kódem přidružíte k XAML.

Rozšíření `x:Null` značek nemá žádné vlastnosti, které by bylo možné nastavit.

Použití null je často spojena s expozicí člena <xref:System.Nullable%601> XAML clr hodnoty.

Rozšíření `x:Null` značek, stejně jako všechna rozšíření značek XAML,`{,}`používá závorky ( ) pro únik zpracování hodnot atributů, které mají být jiné než literály nebo odkazy na obslužnou rutinu události. Syntaxe atributu je syntaxe nejčastěji používaná s tímto rozšířením značek. Syntaxe `<x:Null />` prvku objektu je technicky možná, `x:Null` ale zřídka se používá, protože rozšíření značek nemá žádné poziční parametry nebo argumenty konstrukce.

Informace o rozšířeních značek naleznete v [tématech Rozšíření značek a WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).

Ve službě .NET XAML Services je zpracování pro <xref:System.Windows.Markup.NullExtension> toto rozšíření značek definováno třídou.

## <a name="wpf-usage-notes"></a>Poznámky k použití WPF

Všimněte `null` si, že není nutně počáteční unset hodnotu pro vlastnost závislost typu odkazu. Počáteční výchozí hodnota se může lišit pro každou vlastnost závislosti a může být založena na metadatech specifických pro vlastnost. Mnoho vlastností závislostí `null` nepřijímá jako hodnotu, a to buď prostřednictvím značek nebo kódu z důvodu jejich implementace zpětného volání ověření. Další informace o vlastnostech závislostí naleznete v [tématu Přehled vlastností závislostí](../../framework/wpf/advanced/dependency-properties-overview.md).

## <a name="see-also"></a>Viz také

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [Přehled XAML (WPF)](../fundamentals/xaml.md)
- [Rozšíření značek a WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
