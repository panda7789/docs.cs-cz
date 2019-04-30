---
title: Jazykové funkce jazyka XAML 2009
ms.date: 03/30/2017
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
ms.openlocfilehash: 05f811cd0d95f7605963dae851430fb6bf0e9f7a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938799"
---
# <a name="xaml-2009-language-features"></a>Jazykové funkce jazyka XAML 2009
XAML 2009 je zkrácený tvar vlastností termín pro nové funkce jazyka XAML, které rozšiřují existující specifikace jazyka XAML. XAML 2009 zavádí několik nových direktivách a konstrukce. Patří mezi ně [x: Arguments – direktiva](x-arguments-directive.md); [x: FactoryMethod – direktiva](x-factorymethod-directive.md); [x: Reference – rozšíření značek](x-reference-markup-extension.md); [x: TypeArguments – direktiva ](x-typearguments-directive.md); a předdefinované typy obecných primitiv jazyka (například `x:Char`).  
  
<a name="xaml_2009_support_in_wpf_and_visual_studio"></a>   
## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a>XAML 2009 podporu ve WPF a sady Visual Studio  
 V WPF můžete použít funkce XAML 2009, ale pouze pro XAML, který není kompilována značka WPF. Kompilována značka XAML a formulář BAML z XAML aktuálně nepodporují klíčová slova jazyka XAML 2009 a funkce.  
  
 Mějte na paměti, že stávající metody pro načítání dojde ke ztrátě XAML ve WPF je navíc možné zabezpečení a přístup k omezení na typy CLR a systém typů, které jsou více omezující než kompilována značka XAML. Další informace najdete v tématu [zabezpečení (WPF)](../wpf/security-wpf.md) nebo [strategie zabezpečení WPF – zabezpečení platformy](../wpf/wpf-security-strategy-platform-security.md).  
  
 XAML 2009 zavádí také další funkce, že buď upravte předchozí XAML 2006 konstrukce nebo který měnit základní kód formuláře.  
  
### <a name="xkey-as-an-object-element"></a>x: Key jako Element objektu  
 XAML 2009 může podporovat `x:Key` jako objekt (prvek vlastnosti, která má hodnotu elementu objektu), ale pouze podporované XAML 2006 `x:Key` jako atribut. Viz část "XAML 2009" [x: Key – direktiva](x-key-directive.md).  
  
### <a name="xmlns-on-property-elements"></a>atribut xmlns v prvcích vlastností  
 XAML 2009 můžete podporovat na elementy vlastnosti; definice oboru názvů (xmlns) XAML XAML 2006 však podporuje pouze xmlns definice prvků objektu.  
  
### <a name="event-attributes"></a>Atributy události  
 Pro atributy, které se zálohují na události XAML 2006 předpokládá, že značky kompilace se tak zapojí a odesílá události do kompilace označení. XAML 2009 podporuje značky formuláře, který vypadá podobně jako rozšíření značek, které odloží propojování událostí až do běhu analýzy a načítání XAML. Ale aplikace WPF a scénáře rozhraní WPF XAML obecně nepoužívejte tuto funkci. WPF a implementaci XAML 2006 používá kombinaci její obslužná rutina události pro směrované události definované na <xref:System.Windows.UIElement> úroveň a jeho značky kompilátoru krok pro velkou část jeho atribut zpracování událostí. Kompilátor kód také upraví atributy události v XAML, kde akce sestavení deklarovat, že kompilátor kód používá.  
  
## <a name="see-also"></a>Viz také:

- [Přehled XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
