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
ms.openlocfilehash: c9fb030e6f819b1ca463199a76acd32cb1865f33
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458936"
---
# <a name="datetime-xaml-syntax"></a>DateTime – syntaxe v jazyce XAML
Některé ovládací prvky, například <xref:System.Windows.Controls.Calendar> a <xref:System.Windows.Controls.DatePicker>, mají vlastnosti, které používají typ <xref:System.DateTime>. I když obvykle zadáte počáteční datum nebo čas pro tyto ovládací prvky v kódu za běhu, můžete zadat počáteční datum nebo čas v jazyce XAML. Analyzátor XAML jazyka WPF zpracovává analýzu <xref:System.DateTime> hodnot pomocí předdefinované syntaxe textu v jazyce XAML. Toto téma popisuje konkrétní syntaxi textu <xref:System.DateTime> XAML.  

<a name="where_datetime_xaml_syntax_is_used"></a>   
## <a name="when-to-use-datetime-xaml-syntax"></a>Kdy použít syntaxi jazyka XAML jazyka DateTime  
 Nastavení dat v jazyce XAML není vždy nutné a nemusí být ani žádoucí. Například můžete použít vlastnost <xref:System.DateTime.Now%2A?displayProperty=nameWithType> k inicializaci data v době běhu, nebo můžete provést všechny úpravy kalendářních dat kalendáře v kódu na základě vstupu uživatele. Existují však situace, kdy můžete chtít data pevně code do <xref:System.Windows.Controls.Calendar> a <xref:System.Windows.Controls.DatePicker> v šabloně ovládacího prvku. Pro tyto scénáře se musí použít syntaxe <xref:System.DateTime> XAML.  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a>Syntaxe jazyka XAML v jazyce DateTime je nativní chování  
 <xref:System.DateTime> je třída, která je definována v knihovně základních tříd modulu CLR. Vzhledem k tomu, jak základní knihovny tříd souvisejí se zbytkem CLR, není možné použít <xref:System.ComponentModel.TypeConverterAttribute> pro třídu a použít konvertor typu pro zpracování řetězců z jazyka XAML a jejich převod na <xref:System.DateTime> v objektovém modelu run time. Neexistuje žádná `DateTimeConverter` třída, která poskytuje chování převodu; chování převodu popsané v tomto tématu je nativní pro analyzátor XAML WPF.  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>   
## <a name="format-strings-for-datetime-xaml-syntax"></a>Řetězce formátu pro syntaxi jazyka XAML typu DateTime  
 Můžete určit formát <xref:System.DateTime> s formátovacím řetězcem. Řetězce formátu formalizovat textovou syntaxí, která se dá použít k vytvoření hodnoty. <xref:System.DateTime> hodnoty pro existující ovládací prvky WPF obecně používají pouze součásti data pro <xref:System.DateTime> a nikoli časové komponenty.  
  
 Při zadávání <xref:System.DateTime> v jazyce XAML můžete použít libovolný formátovací řetězec.  
  
 Můžete také použít formáty a formátovací řetězce, které nejsou výslovně uvedeny v tomto tématu. Technicky, XAML pro jakoukoli <xref:System.DateTime> hodnotu, která je určena a následně analyzována analyzátorem XAML jazyka WPF, používá k <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>interní volání, takže můžete použít libovolný řetězec přijatý <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> pro vstup XAML. Další informace najdete v tématu <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
> Syntaxe jazyka XAML typu DateTime vždy používá `en-us` jako <xref:System.Globalization.CultureInfo> pro svůj nativní převod. To není ovlivněno hodnotou <xref:System.Windows.FrameworkElement.Language%2A> hodnoty nebo `xml:lang` hodnotou v jazyce XAML, protože převod typu na úrovni atributu XAML funguje bez tohoto kontextu. Nepokoušejte se interpolovat formátovací řetězce, které jsou zde uvedeny, z důvodu kulturní variace, jako je například pořadí, ve kterém se zobrazuje den a měsíc. Formátovací řetězce, které jsou zde uvedeny, jsou přesné formátovací řetězce používané při analýze XAML bez ohledu na jiné nastavení jazykové verze.  
  
 V následujících částech jsou popsány některé běžné řetězce formátu <xref:System.DateTime>.  
  
### <a name="short-date-pattern-d"></a>Vzor krátkého formátu data ("d")  
 Následující příklad ukazuje formát krátkého formátu data pro <xref:System.DateTime> v jazyce XAML:  
  
 `M/d/YYYY`  
  
 Toto je nejjednodušší forma, která určuje všechny potřebné informace pro typické použití pomocí ovládacích prvků WPF a nemůže být ovlivněna neúmyslnými posuny časového pásma oproti časové komponentě a je proto doporučena v jiných formátech.  
  
 Chcete-li například zadat datum od 1. června 2010, použijte následující řetězec:  
  
 `3/1/2010`  
  
 Další informace najdete v tématu <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>.  
  
### <a name="sortable-datetime-pattern-s"></a>Seřadit vzorek DateTime ("s")  
 Následující příklad znázorňuje řazení <xref:System.DateTime> vzoru v jazyce XAML:  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 Chcete-li například zadat datum od 1. června 2010, použijte následující řetězec (čas, kdy jsou komponenty zadány jako 0):  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a>RFC1123 vzor ("r")  
 Vzor RFC1123 je užitečný, protože by se mohlo jednat o vstup řetězce z jiného generátoru dat, který také používá vzor RFC1123 pro invariantní jazykové důvody. Následující příklad ukazuje vzor RFC1123 <xref:System.DateTime> v jazyce XAML:  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 Chcete-li například zadat datum od 1. června 2010, použijte následující řetězec (čas, kdy jsou komponenty zadány jako 0):  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a>Jiné formáty a vzory  
 Jak bylo uvedeno dříve, <xref:System.DateTime> v jazyce XAML lze zadat jako libovolný řetězec, který je přijatelný jako vstup pro <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>. To zahrnuje další formální formáty (například <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>) a formáty, které nejsou formální jako konkrétní <xref:System.Globalization.DateTimeFormatInfo> formuláře. Například `YYYY/mm/dd` formuláře je přijatelné jako vstup pro <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>. Toto téma se nepokouší popsat všechny možné formáty, které fungují, a místo toho doporučuje vzor krátkého data jako standardní postup.  
  
## <a name="see-also"></a>Viz také:

- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
