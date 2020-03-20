---
title: DateTime – syntaxe v jazyce XAML
ms.date: 03/30/2017
helpviewer_keywords:
- DateTime XAML syntax [WPF], strings for
- DateTime XAML syntax [WPF], where used
- short date format [WPF], DateTime
- DateTime XAML syntax [WPF]
- DateTime XAML text [WPF]
- DateTime XAML syntax [WPF], format strings for
ms.assetid: 5901710a-609b-40c8-9d65-f0016cd9090b
ms.openlocfilehash: 57b73d3b80f0392b99aacfbfac4d8709f72d52e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186334"
---
# <a name="datetime-xaml-syntax"></a>DateTime – syntaxe v jazyce XAML
Některé ovládací prvky, například <xref:System.Windows.Controls.Calendar> a <xref:System.DateTime> <xref:System.Windows.Controls.DatePicker>, mají vlastnosti, které používají typ. I když obvykle zadáte počáteční datum nebo čas pro tyto ovládací prvky v kódu na pozadí za běhu, můžete zadat počáteční datum nebo čas v XAML. Analyzátor WPF XAML zpracovává analýzu <xref:System.DateTime> hodnot pomocí předdefinované syntaxe textu XAML. Toto téma popisuje specifika <xref:System.DateTime> syntaxe textu XAML.  

<a name="where_datetime_xaml_syntax_is_used"></a>
## <a name="when-to-use-datetime-xaml-syntax"></a>Kdy použít syntaxi XAML DateTime  
 Nastavení dat v XAML není vždy nutné a nemusí být ani žádoucí. Můžete například použít <xref:System.DateTime.Now%2A?displayProperty=nameWithType> vlastnost k inicializaci data v době běhu nebo můžete provést všechny úpravy data pro kalendář v kódu na pozadí na základě vstupu uživatele. Existují však scénáře, kde můžete chtít pevně <xref:System.Windows.Controls.Calendar> kódovat data do a v <xref:System.Windows.Controls.DatePicker> šabloně ovládacího prvku. Pro <xref:System.DateTime> tyto scénáře musí být použita syntaxe XAML.  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a>Syntaxe XAML DateTime je nativní chování  
 <xref:System.DateTime>je třída, která je definována v knihovnách základních tříd CLR. Vzhledem k tomu, jak knihovny základní třídy se vztahují ke <xref:System.ComponentModel.TypeConverterAttribute> zbytku CLR, není možné použít na třídu a <xref:System.DateTime> použít převaděč typu pro zpracování řetězců z XAML a převést je v objektovém modelu za běhu. Neexistuje žádná `DateTimeConverter` třída, která poskytuje chování převodu; chování převodu popsané v tomto tématu je nativní pro analyzátor WPF XAML.  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>
## <a name="format-strings-for-datetime-xaml-syntax"></a>Formátovat řetězce pro syntaxi XAML DateTime  
 Formát a můžete určit <xref:System.DateTime> pomocí formátovacího řetězce. Formátovací řetězce formalizují syntaxi textu, kterou lze použít k vytvoření hodnoty. <xref:System.DateTime>hodnoty pro existující ovládací prvky WPF obecně <xref:System.DateTime> používají pouze časové komponenty a nikoli časové součásti.  
  
 Při zadávání <xref:System.DateTime> v XAML, můžete použít některý z formátovacích řetězců zaměnitelně.  
  
 Můžete také použít formáty a formátovací řetězce, které nejsou konkrétně uvedeny v tomto tématu. Technicky xaml pro <xref:System.DateTime> libovolnou hodnotu, která je zadána a poté analyzována analyzátorem <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>WPF XAML, <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> používá interní volání , proto můžete použít libovolný řetězec přijatý pro vstup XAML. Další informace naleznete v tématu <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
> Syntaxe DateTime XAML `en-us` vždy <xref:System.Globalization.CultureInfo> používá jako pro jeho nativní převod. To není ovlivněno <xref:System.Windows.FrameworkElement.Language%2A> hodnotou nebo `xml:lang` hodnotou v XAML, protože převod typu typu na úrovni atributu XAML funguje bez tohoto kontextu. Nepokoušejte se interpolovat zde zobrazené formátovací řetězce z důvodu kulturních změn, jako je například pořadí, ve kterém se den a měsíc zobrazují. Zde uvedené formátovací řetězce jsou přesné formátovací řetězce používané při analýzě XAML bez ohledu na jiné nastavení jazykové verze.  
  
 Následující části popisují některé <xref:System.DateTime> běžné formátovací řetězce.  
  
### <a name="short-date-pattern-d"></a>Krátký vzor data ("d")  
 Následující ukazuje krátký formát data <xref:System.DateTime> pro v XAML:  
  
 `M/d/YYYY`  
  
 Toto je nejjednodušší formulář, který určuje všechny potřebné informace pro typické použití ovládacími prvky WPF a nemůže být ovlivněn náhodným posunem časového pásma oproti časové součásti, a proto se doporučuje v jiných formátech.  
  
 Chcete-li například zadat datum 1.  
  
 `3/1/2010`  
  
 Další informace naleznete v tématu <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>.  
  
### <a name="sortable-datetime-pattern-s"></a>Sortable DateTime vzor ("s")  
 Následující ukazuje seřaditelný <xref:System.DateTime> vzor v XAML:  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 Chcete-li například zadat datum 1.  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a>RFC1123 Vzor ("r")  
 RFC1123 vzor je užitečné, protože může být vstup řetězce z jiných generátorů data, které také používají RFC1123 vzor pro jazykovou verzi invariantní důvodů. Následující ukazuje RFC1123 <xref:System.DateTime> vzor v XAML:  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 Chcete-li například zadat datum 1.  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a>Další formáty a vzorky  
 Jak již bylo <xref:System.DateTime> uvedeno dříve, v XAML lze zadat jako <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>libovolný řetězec, který je přijatelný jako vstup pro . To zahrnuje další formalizované formáty (například <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>) a formáty, které nejsou formalizovány jako konkrétní <xref:System.Globalization.DateTimeFormatInfo> formulář. Například formulář `YYYY/mm/dd` je přijatelný jako <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>vstup pro . Toto téma se nepokouší popsat všechny možné formáty, které fungují, a místo toho doporučuje vzor krátkého data jako standardní postup.  
  
## <a name="see-also"></a>Viz také

- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
