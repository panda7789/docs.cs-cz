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
ms.openlocfilehash: 7dbea2c7d4010d8defc572dbdc14a0dfd6d7601e
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484712"
---
# <a name="xnull-markup-extension"></a>x:Null – rozšíření značek
Určuje `null` hodnotu člena XAML.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>Poznámky  
 Klíčové slovo pro odkaz s hodnotou null C# v C++ a má hodnotu null. Klíčové slovo Microsoft Visual Basic pro odkaz s hodnotou null `Nothing`je, ale vždy používáte `{x:Null}` jako použití XAML bez ohledu na to, který kód na pozadí přidružujete k XAML.  
  
 Rozšíření `x:Null` značek nemá žádné nastavitelné vlastnosti.  
  
 Použití hodnoty null je často přidruženo k expozici členů XAML hodnoty CLR <xref:System.Nullable%601> .  
  
 Rozšíření značek, jako jsou všechna rozšíření značek XAML, používá složené závorky (`{,}`) pro uvozovací manipulaci s hodnotami atributů jiné než literály nebo odkazy obslužných rutin událostí. `x:Null` Syntaxe atributu je syntaxe, která se nejčastěji používá s touto příponou označení. Syntaxe `<x:Null />` elementu objektu je technicky možná, ale používá se zřídka, `x:Null` protože rozšíření značek nemá žádné poziční parametry nebo argumenty konstrukce.  
  
 Informace o rozšíření značek naleznete v tématu [rozšíření značek a WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 V .NET Framework služby XAML je zpracování tohoto rozšíření značek definováno <xref:System.Windows.Markup.NullExtension> třídou.  
  
## <a name="wpf-usage-notes"></a>Poznámky k použití WPF  
 Všimněte si `null` , že není nutně počáteční hodnota nenastavené vlastnosti závislostí typu odkazu. Počáteční výchozí hodnota se může u každé vlastnosti závislosti lišit a může být založena na metadatech specifických pro vlastnost. Mnoho vlastností závislosti nepřijímá `null` jako hodnotu, a to buď prostřednictvím kódu, nebo kódu z důvodu implementace zpětného volání ověřování. Další informace o vlastnostech závislosti najdete v tématu [Přehled vlastností závislosti](../wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [Přehled XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [Rozšíření značek a WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
