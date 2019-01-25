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
ms.openlocfilehash: 5f0856f50e73a090d0ef624e2fb894d68b73c07e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553318"
---
# <a name="xnull-markup-extension"></a>x:Null – rozšíření značek
Určuje `null` jako hodnotu pro člena XAML.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>Poznámky  
 Klíčové slovo pro odkaz s hodnotou null v C# a [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] má hodnotu null. Microsoft Visual Basic klíčové slovo pro odkaz s hodnotou null je `Nothing`, ale vždy používají `{x:Null}` jako bez ohledu na to XAML použití modelu code-behind jazyk, který přidružíte k XAML.  
  
 `x:Null` Nemá žádné nastavitelné vlastnosti rozšíření značek.  
  
 Null využití je často přidružený vystavení člena XAML CLR <xref:System.Nullable%601> hodnotu.  
  
 `x:Null` – Rozšíření značek, stejně jako všechna rozšíření značek XAML, používá složené závorky (`{,}`) pro uvození zpracování hodnoty atributů, aby byla jiná než literály nebo odkazy na obslužnou rutinu události. Syntaxe atributu je syntaxe nejčastěji používané u tohoto rozšíření značek. Syntaxi elementu objektu `<x:Null />` je technicky možné, ale je použita jen zřídka, protože `x:Null` – rozšíření značek nemá žádné poziční parametry a argumenty konstrukce.  
  
 Informace o rozšíření značek, naleznete v tématu [– rozšíření značek a WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 V rozhraní .NET Framework XAML Services zpracování tohoto rozšíření značek definováno <xref:System.Windows.Markup.NullExtension> třídy.  
  
## <a name="wpf-usage-notes"></a>Poznámky k použití WPF  
 Všimněte si, že `null` není nutně zrušit nastavení počáteční hodnotu pro vlastnost závislosti typu odkazu. Počáteční výchozí hodnota pro každou vlastnost závislostí se může lišit a může být založen na metadata specifická pro vlastnost. Mnoho vlastností závislostí nepřijímají `null` jako hodnotu, buď prostřednictvím značek nebo kódu z důvodu jejich implementace zpětného volání pro ověření. Další informace o vlastnosti závislosti, naleznete v tématu [přehled vlastností závislosti](../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.DependencyProperty.UnsetValue>
- [Přehled XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [Rozšíření značek a WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
