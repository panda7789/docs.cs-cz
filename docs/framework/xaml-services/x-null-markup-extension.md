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
ms.openlocfilehash: ff82b0bfc1983240431e582dbd78778dc4469241
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459946"
---
# <a name="xnull-markup-extension"></a>x:Null – rozšíření značek
Určuje `null` jako hodnotu pro člena XAML.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>Poznámky  
 Klíčové slovo pro odkaz s hodnotou null C# v C++ a má hodnotu null. Klíčové slovo Microsoft Visual Basic pro odkaz s hodnotou null je `Nothing`, ale vždy používáte `{x:Null}` jako použití XAML bez ohledu na to, který jazyk kódu, který přidružíte k XAML.  
  
 Rozšíření `x:Null` značek nemá žádné nastavitelné vlastnosti.  
  
 Použití hodnoty null je často přidruženo k expozici člena XAML <xref:System.Nullable%601> Value.  
  
 `x:Null` rozšíření značek, jako jsou všechna rozšíření značek jazyka XAML, používá složené závorky (`{,}`) pro uvozovací manipulaci s hodnotami atributů jiné než literály nebo reference obslužných rutin událostí. Syntaxe atributu je syntaxe, která se nejčastěji používá s touto příponou označení. Syntaxe elementu objektu `<x:Null />` je technicky možná, ale používá se zřídka, protože rozšíření značek `x:Null` nemá žádné poziční parametry nebo argumenty konstrukce.  
  
 Informace o rozšíření značek naleznete v tématu [rozšíření značek a WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 V .NET Framework služby XAML je zpracování tohoto rozšíření značek definováno <xref:System.Windows.Markup.NullExtension> třídou.  
  
## <a name="wpf-usage-notes"></a>Poznámky k použití WPF  
 Všimněte si, že `null` není nutně počáteční hodnotou pro vlastnost závislosti typu odkazu. Počáteční výchozí hodnota se může u každé vlastnosti závislosti lišit a může být založena na metadatech specifických pro vlastnost. Mnoho vlastností závislosti nepřijímá `null` jako hodnotu, a to buď prostřednictvím kódu, nebo kódu z důvodu svých implementací zpětného volání ověřování. Další informace o vlastnostech závislosti najdete v tématu [Přehled vlastností závislosti](../wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [Přehled XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
- [Rozšíření značek a WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
