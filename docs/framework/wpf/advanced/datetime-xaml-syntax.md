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
ms.openlocfilehash: d7fe5f15f79ab068e88c3fb6f7b7cac0986aa636
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146494"
---
# <a name="datetime-xaml-syntax"></a>DateTime – syntaxe v jazyce XAML
Některé ovládací prvky, jako například <xref:System.Windows.Controls.Calendar> a <xref:System.Windows.Controls.DatePicker>, mají vlastnosti, které používají <xref:System.DateTime> typu. I když obvykle zadat počáteční datum a čas pro tyto ovládací prvky v kódu v době běhu je zadat v XAML počáteční datum nebo čas. Analyzátor WPF XAML zpracovává analýzu <xref:System.DateTime> hodnoty pomocí předdefinovaných textová syntaxe XAML. Toto téma popisuje, jaké jsou specifikace <xref:System.DateTime> textová syntaxe XAML.  

<a name="where_datetime_xaml_syntax_is_used"></a>   
## <a name="when-to-use-datetime-xaml-syntax"></a>Kdy použít syntaxe XAML data a času  
 Nastavení dat v XAML není vždy nutné a dokonce nemusí být žádoucí. Například můžete použít <xref:System.DateTime.Now%2A?displayProperty=nameWithType> vlastnost inicializovat data v době běhu, nebo můžete udělat všechny úpravy dat pro kalendáře v kódu na základě uživatelského zadání. Ale existují scénáře, kde můžete data pevně zakódovat do <xref:System.Windows.Controls.Calendar> a <xref:System.Windows.Controls.DatePicker> v šabloně ovládacího prvku. <xref:System.DateTime> Syntaxe XAML musí být použita pro tyto scénáře.  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a>Syntaxe XAML data a času je nativní chování  
 <xref:System.DateTime> je třída, která je definována v knihovně základních tříd modulu CLR. Z důvodu knihovny základních tříd vztah k rest modulu CLR, není možné použít <xref:System.ComponentModel.TypeConverterAttribute> třídy a použitím konvertor typu pro zpracování řetězců z XAML a převést tak, aby <xref:System.DateTime> v době běhu objektový model. Neexistuje žádná `DateTimeConverter` třída, která poskytuje chování převodu; převod chování popsané v tomto tématu je nativní pro analyzátor WPF XAML.  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>   
## <a name="format-strings-for-datetime-xaml-syntax"></a>Formátovací řetězce pro syntaxe XAML data a času  
 Můžete zadat formát <xref:System.DateTime> pomocí formátovacího řetězce. Řetězce formátu formalizujte syntaxe textu, který slouží k vytvoření hodnoty. <xref:System.DateTime> hodnoty pro WPF existující ovládací prvky používejte obecně pouze datum součástí <xref:System.DateTime> a nikoli komponenty času.  
  
 Při zadávání <xref:System.DateTime> v XAML, můžete použít některý z formátovací řetězce Zaměnitelně.  
  
 Můžete také použít formáty a formát řetězce, které nejsou konkrétně uvedené v tomto tématu. Technicky vzato XAML pro všechny <xref:System.DateTime> hodnotu, která je zadána a pak analyzovat analyzátorem WPF XAML používá interní volání <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>, proto můžete použít libovolný řetězec, který přijal <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> vaší XAML vstup. Další informace naleznete v tématu <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
>  Syntaxe XAML data a času vždy používá `en-us` jako <xref:System.Globalization.CultureInfo> jeho nativní převodu. To není ovlivněn <xref:System.Windows.FrameworkElement.Language%2A> hodnotu nebo `xml:lang` hodnota v XAML, protože převod typu úroveň atributu XAML funguje bez daného kontextu. Nepokoušejte se interpolovat formátovací řetězce je znázorněno zde kvůli kulturní variace, jako například pořadí, ve kterém se zobrazí datum a měsíce. Formát řetězce je vidět tady jsou řetězce přesném formátu, který použije při analýze XAML bez ohledu na jiné nastavení jazykové verze.  
  
 Následující části popisují některé nejběžnější <xref:System.DateTime> řetězce formátu.  
  
### <a name="short-date-pattern-d"></a>Vzor krátkého formátu data ("d")  
 Následující příklad zobrazuje formát krátkého formátu data <xref:System.DateTime> v XAML:  
  
 `M/d/YYYY`  
  
 Toto je nejjednodušší podobě, který určuje všechny potřebné informace pro typické použití ovládacích prvků WPF a nemůže být ovlivněny náhodného časových pásmech a složku času a doporučuje se přes jiné formáty.  
  
 Například zadejte datum 1. června 2010, použijte následující řetězec:  
  
 `3/1/2010`  
  
 Další informace naleznete v tématu <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>.  
  
### <a name="sortable-datetime-pattern-s"></a>Vzor seřaditelného data a času ("s")  
 Následující příklad zobrazuje Univerzální seřaditelný <xref:System.DateTime> vzoru v XAML:  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 Například zadejte datum 1. června 2010, použijte následující řetězce (čas, které součásti jsou zadány jako 0):  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a>Vzor RFC1123 ("r")  
 Vzor RFC1123 je užitečné, protože by mohlo být vstupní řetězec z jiné datum generátorů, které také používají vzor RFC1123 důvodů invariantní jazykovou verzi. Následující příklad zobrazuje RFC1123 <xref:System.DateTime> vzoru v XAML:  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 Například zadejte datum 1. června 2010, použijte následující řetězce (čas, které součásti jsou zadány jako 0):  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a>Další formáty a vzory  
 Jak bylo uvedeno dříve, <xref:System.DateTime> v XAML lze zadat jako libovolný řetězec, který je přijatelné pro jako vstupní <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>. Jedná se o další oficiální formáty (třeba <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>) a formátů, které nejsou stanovení jako konkrétní <xref:System.Globalization.DateTimeFormatInfo> formuláře. Například formulář `YYYY/mm/dd` je přijatelné pro jako vstupní <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>. Toto téma se nebude pokoušet popisují všechny možné formáty, které pracují a místo toho doporučuje vzor krátkého formátu data jako standardním postupem.  
  
## <a name="see-also"></a>Viz také:

- [Přehled XAML (WPF)](xaml-overview-wpf.md)
