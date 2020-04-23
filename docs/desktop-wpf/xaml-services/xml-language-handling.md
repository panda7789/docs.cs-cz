---
title: Práce s atributem xml:lang v jazyce XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: b5a06adbb7cb874bc09899118f13b91fbec7a85e
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071442"
---
# <a name="xmllang-handling-in-xaml"></a>Práce s atributem xml:lang v jazyce XAML

Atribut `xml:lang` je atribut definovaný jazykem XML, který deklaruje informace o jazyce a jazykové verzi pro prvek ve formátu XML. Stejný význam atributu přetrvává v XAML; platí však některé další aspekty.

## <a name="xaml-attribute-usage"></a>Použití atributu XAML

```xaml
<object xml:lang="rfc3066lang" />
```

## <a name="xaml-values"></a>Hodnoty XAML

|||
|-|-|
|*rfc3066lang*|Řetězec, který je odvozen ze standardu [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) a identifikuje jazyk nebo jazykovou oblast. Pokud je to druhé, jazyk a oblast jsou odděleny jedním pomlčkou. Další <xref:System.Windows.Markup.XmlLanguage> informace o hodnotách a formátu naleznete v tématu.|

## <a name="remarks"></a>Poznámky

Definice atributu `xml:lang` v [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] je odvozena od definovaného `xml:lang` jako "zvláštní atribut" konsorciem W3C (World Wide Web Consortium) pro JAZYK XML. Informace o jazyce a jazykové verzi jsou potenciálně zpracovávány různými způsoby prvky v závislosti na jejich implementaci; však neexistuje žádné [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] výchozí `xml:lang` zpracování atributu.

Výchozí hodnota atributu `xml:lang` je prázdný řetězec na úrovni atributu.

Atribut `xml:lang` účinky a hodnota atributu jsou obecně udržovat podřízené prvky, při interpretaci systémy, které působí na `xml:lang` hodnoty.

Při interpretaci autory XAML služby .NET `xml:lang` XAML Services může hodnota vytvořit <xref:System.Windows.Markup.XmlLanguage> nebo <xref:System.Globalization.CultureInfo> objekty v reprezentaci podkladového objektu; však toto chování závisí na `xml:lang` tom, zda je zadaná hodnota pro platné konstrukce pro tyto třídy.

Architektury můžete vytvořit přidružení mezi vlastnostmi definované `xml:lang` v rámci <xref:System.Windows.Markup.XmlLangPropertyAttribute> a význam v xml použitím na vlastnost.

## <a name="wpf-usage-nodes"></a>Uzly využití WPF

Pro prvky, které <xref:System.Windows.FrameworkElement> jsou <xref:System.Windows.FrameworkContentElement>odvozené třídy <xref:System.Windows.FrameworkElement.Language%2A> nebo , můžete `xml:lang` použít ekvivalentní závislost vlastnost namísto atributu. Ve výchozím <xref:System.Windows.FrameworkElement.Language%2A> nastavení vlastnost používá "en US", pokud není jinak nastavena, `xml:lang` buď prostřednictvím vlastnosti, nebo zpracováním atributu.

## <a name="see-also"></a>Viz také

- [Globalizace pro WPF](../../framework/wpf/advanced/globalization-for-wpf.md)
