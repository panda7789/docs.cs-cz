---
title: Jazykové funkce jazyka XAML 2009
ms.date: 03/30/2017
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
ms.openlocfilehash: e58e6757b88958bf8a3547c8a272c2e6298dcecb
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071596"
---
# <a name="xaml-2009-language-features"></a>Jazykové funkce jazyka XAML 2009
XAML 2009 je zkrácený termín pro nové funkce jazyka XAML, které rozšiřují stávající specifikaci jazyka XAML. XAML 2009 zavádí několik nových směrnic a konstrukcí. Patří mezi ně [směrnice x:Arguments](xarguments-directive.md); [x:směrnice o výrobních metodách](xfactorymethod-directive.md); [x:Rozšíření referencí](xreference-markup-extension.md); [x:TypeArguments ;](xtypearguments-directive.md) a vestavěné typy pro běžné jazykové `x:Char`primitivy (například).

## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a>Podpora XAML 2009 ve WPF a Visual Studiu

V WPF můžete použít funkce XAML 2009, ale pouze pro XAML, který není wpf zkompilovaný značky. KódXAML zkompilovaný značkami a forma XAML BAML aktuálně nepodporují klíčová slova a funkce jazyka XAML 2009.

Všimněte si, že existující techniky pro načítání volné XAML v WPF mají také možné omezení zabezpečení a přístupu k clr typy a typ systému, které jsou více omezující než pro značky kompilované XAML. Další informace naleznete [v tématu Zabezpečení (WPF)](../../framework/wpf/security-wpf.md) nebo [WPF strategie zabezpečení - zabezpečení platformy](../../framework/wpf/wpf-security-strategy-platform-security.md).

XAML 2009 také zavádí další funkce, které buď upravit předchozí konstrukce XAML 2006 nebo které upravují základní formuláře značek.

### <a name="xkey-as-an-object-element"></a>x:Klíč jako prvek objektu

XAML 2009 `x:Key` může podporovat jako objekt (prvek vlastnosti, který má hodnotu prvku objektu); XAML 2006 však `x:Key` podporovány pouze jako atribut. Viz část "XAML 2009" [v x:Key směrnice](xkey-directive.md).

### <a name="xmlns-on-property-elements"></a>xmlns na elementy vlastností

XAML 2009 může podporovat definice oboru názvů XAML (xmlns) na prvky vlastností; XAML 2006 však podporuje pouze definice xmlns na objektových prvcích.

### <a name="event-attributes"></a>Atributy událostí

Pro atributy, které jsou podpořeny událostmi, XAML 2006 předpokládá, že se jedná o kompilaci značek a odešle události do kompilace značek. XAML 2009 podporuje formulář značky, který se podobá rozšíření značek, které odkládá zapojení události až do analýzy běhu a načítání XAML. Aplikace WPF a scénáře XAML pro uživatelské uživatelské zařízení WPF však tuto funkci obecně nepoužívají. WPF a jeho implementace XAML 2006 používá kombinaci zapojení obslužné rutiny událostí pro směrované události definované na <xref:System.Windows.UIElement> úrovni a jeho krok kompilátoru značek pro velkou část zpracování atributu události. Kompilátor značek také předem zpracuje všechny atributy událostí nalezené v XAML, kde akce sestavení deklarují, že se používá kompilátor značek.

## <a name="see-also"></a>Viz také

- [Přehled XAML (WPF)](../fundamentals/xaml.md)
