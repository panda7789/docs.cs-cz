---
title: Jazykové funkce jazyka XAML 2009
ms.date: 03/30/2017
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
ms.openlocfilehash: ac18be4732d223561d3a0afcef0e650587385822
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459889"
---
# <a name="xaml-2009-language-features"></a>Jazykové funkce jazyka XAML 2009
XAML 2009 je zkrácený termín pro nové funkce jazyka XAML, které rozšíří existující specifikaci jazyka XAML. XAML 2009 zavádí několik nových direktiv a konstrukcí. Patří sem [direktiva x:arguments –](x-arguments-directive.md); [direktiva x:FactoryMethod –](x-factorymethod-directive.md); [rozšíření značek x:Reference](x-reference-markup-extension.md); [direktiva x:TypeArguments –](x-typearguments-directive.md); a předdefinované typy pro společné jazykové primitivy (například `x:Char`).  
  
<a name="xaml_2009_support_in_wpf_and_visual_studio"></a>   
## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a>Podpora XAML 2009 v WPF a Visual Studiu  
 V WPF můžete použít funkce XAML 2009, ale pouze pro XAML, které nejsou kompilovány pomocí kódu WPF. Kód XAML kompilovaný s označením kódu v současnosti nepodporují klíčová slova a funkce jazyka XAML 2009.  
  
 Všimněte si, že stávající techniky pro načítání volného kódu XAML v subsystému WPF mají také možná omezení zabezpečení a přístupu k typům CLR a systém typů, který je více omezující než u kódu XAML kompilovaného značkou. Další informace najdete v tématech zabezpečení [(WPF)](../wpf/security-wpf.md) nebo [WPF Security strategie – zabezpečení platformy](../wpf/wpf-security-strategy-platform-security.md).  
  
 XAML 2009 také zavádí další funkce, které buď upravují předchozí konstrukce XAML 2006, nebo které upravují základní formuláře pro označení.  
  
### <a name="xkey-as-an-object-element"></a>X:Key – jako element Object  
 XAML 2009 může podporovat `x:Key` jako objekt (prvek vlastnosti, který má hodnotu prvku objektu); XAML 2006 se však podporuje pouze `x:Key` jako atribut. Viz část "XAML 2009" [direktivy x:Key –](x-key-directive.md).  
  
### <a name="xmlns-on-property-elements"></a>xmlns u elementů vlastností  
 XAML 2009 může podporovat definice oboru názvů XAML (xmlns) u elementů vlastností; XAML 2006 však podporuje pouze definice xmlns u elementů Object.  
  
### <a name="event-attributes"></a>Atributy události  
 Pro atributy, které jsou zajištěny událostmi, XAML 2006 předpokládá, že je zapojena kompilace kódu, a odešle události do kompilace kódu. XAML 2009 podporuje formulář s označením, který se podobá rozšíření značek, které odkládá kabeláž událostí až do doby běhu a načítání kódu XAML. Aplikace WPF a scénáře XAML pro uživatelské rozhraní WPF ale obecně tuto možnost nepoužívají. WPF a jeho implementace v jazyce XAML 2006 využívají kombinaci kabelů obslužné rutiny událostí pro směrované události definované na úrovni <xref:System.Windows.UIElement> a krok kompilátoru kódu pro většinu zpracování atributů události. Kompilátor značek také předzpracovává všechny atributy událostí nalezené v jazyce XAML, kde akce sestavení deklaruje, že je použit kompilátor značek.  
  
## <a name="see-also"></a>Viz také:

- [Přehled XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
