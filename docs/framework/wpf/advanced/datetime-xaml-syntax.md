---
title: "DateTime – syntaxe v jazyce XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DateTime XAML syntax [WPF], strings for
- DateTime XAML syntax [WPF], where used
- short date format [WPF], DateTime
- DateTime XAML syntax [WPF]
- DateTime XAML text [WPF]
- DateTime XAML syntax [WPF], format strings for
ms.assetid: 5901710a-609b-40c8-9d65-f0016cd9090b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55e261018e6c7b9fea9ad449c5e92a131df40807
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="datetime-xaml-syntax"></a>DateTime – syntaxe v jazyce XAML
Některé ovládací prvky, jako například <xref:System.Windows.Controls.Calendar> a <xref:System.Windows.Controls.DatePicker>, mít vlastnosti, které používají <xref:System.DateTime> typu. I když obvykle zadejte počáteční datum nebo čas pro tyto ovládací prvky v kódu v době běhu je zadat v jazyce XAML počáteční datum nebo čas. Analyzátor WPF XAML zpracovává analýze <xref:System.DateTime> hodnoty pomocí předdefinovaných syntaxe text XAML. Toto téma popisuje, jaké jsou specifikace <xref:System.DateTime> XAML textových syntaxi.  
  
  
<a name="where_datetime_xaml_syntax_is_used"></a>   
## <a name="when-to-use-datetime-xaml-syntax"></a>Při použití syntaxe XAML data a času  
 Nastavení kalendářních dat v jazyce XAML není vždy nutné a dokonce nemusí být žádoucí. Například můžete použít <xref:System.DateTime.Now%2A?displayProperty=nameWithType> vlastnost inicializovat data v době běhu, nebo můžete udělat všechny datum úpravy pro kalendář v kódu založené na vstup uživatele. Ale existují scénáře, kde můžete data pevný kódu do <xref:System.Windows.Controls.Calendar> a <xref:System.Windows.Controls.DatePicker> v šabloně ovládacího prvku. <xref:System.DateTime> XAML syntaxe musí být použita pro tyto scénáře.  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a>Syntaxe jazyka XAML data a času je nativní chování  
 <xref:System.DateTime>je třída, která je definována v knihovnách základní třídy modulu CLR. Z důvodu jak základní třídy knihovny vztahují k zbytek modulu CLR, není možné použít <xref:System.ComponentModel.TypeConverterAttribute> třídy a používání převaděče typů ke zpracování řetězců z XAML a převést tak, aby <xref:System.DateTime> v době běhu objektu modelu. Neexistuje žádné `DateTimeConverter` – třída, která poskytuje chování převod; převod chování popsané v tomto tématu je nativní pro analyzátor WPF XAML.  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>   
## <a name="format-strings-for-datetime-xaml-syntax"></a>Řetězce formátu data a času XAML syntaxe  
 Můžete zadat formát <xref:System.DateTime> s řetězci formátu. Řetězce formátu formalizujte syntaxe text, který slouží k vytvoření hodnoty. <xref:System.DateTime>hodnoty pro existující WPF řídí obecně pouze použití datum součástí <xref:System.DateTime> a není součástí čas.  
  
 Při zadávání <xref:System.DateTime> v jazyce XAML, můžete použít některý z řetězce formátu zcela zaměnitelným významem.  
  
 Můžete také použít formáty a formát řetězce, které nejsou konkrétně zobrazeny v tomto tématu. Technicky XAML pro žádné <xref:System.DateTime> hodnotu, která je zadána a potom analyzovat analyzátorem jazyka XAML WPF používá interní volání <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>, proto můžete použít libovolný řetězec, který bude přijímat <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> pro váš jazyk XAML vstup. Další informace naleznete v tématu <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
>  Syntaxe jazyka XAML data a času vždy používá `en-us` jako <xref:System.Globalization.CultureInfo> pro jeho nativní převod. Toto není ovlivněné <xref:System.Windows.FrameworkElement.Language%2A> hodnotu nebo `xml:lang` hodnoty v jazyce XAML, protože převod XAML úroveň atributu typu funguje bez tohoto kontextu. Nepokoušejte se promítnout řetězce formátu kvůli kulturního změny, jako jsou pořadí, ve kterém dne a měsíce zobrazí tady uvedené. Řetězce formátu vidět tady jsou řetězce přesném formátu, který použije při analýze XAML bez ohledu na ostatní nastavení jazykové verze.  
  
 Následující části popisují některé nejběžnější <xref:System.DateTime> řetězce formátu.  
  
### <a name="short-date-pattern-d"></a>Vzoru krátkého data ("d")  
 Následující příklad zobrazuje formát krátkého data <xref:System.DateTime> v jazyce XAML:  
  
 `M/d/YYYY`  
  
 Toto je nejjednodušší podobě Určuje všechny potřebné informace pro typické použití ovládacích prvků WPF a nemůže mít vliv náhodných časových pásmech versus komponentu dobu a proto se doporučuje namísto jiných formátů.  
  
 Například zadejte datum 1. června 2010, použijte následující řetězec:  
  
 `3/1/2010`  
  
 Další informace naleznete v tématu <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>.  
  
### <a name="sortable-datetime-pattern-s"></a>Řazení vzor data a času ("s")  
 Následující příklad zobrazuje seřaditelný <xref:System.DateTime> vzoru v jazyce XAML:  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 Například zadejte datum 1. června 2010, použijte následující řetězec (čas, které součásti jsou zadali jako 0):  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a>Vzor RFC1123 ("r")  
 Vzor RFC1123 je užitečné, protože by mohlo být vstup řetězce z jiné datum generátory, kteří také používají vzor RFC1123 důvodů neutrální jazykovou verzi. Následující příklad zobrazuje RFC1123 <xref:System.DateTime> vzoru v jazyce XAML:  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 Například zadejte datum 1. června 2010, použijte následující řetězec (čas, které součásti jsou zadali jako 0):  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a>Ostatní formáty a vzorce  
 Jak jsme uvedli dříve, <xref:System.DateTime> v jazyce XAML, lze zadat jako libovolný řetězec, který se dá použít jako vstupní pro <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>. To zahrnuje dalších formalizovanou formátů (například <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>) a formáty, které nejsou stanovení jako konkrétní <xref:System.Globalization.DateTimeFormatInfo> formuláře. Například formulář `YYYY/mm/dd` je přijatelné pro jako vstupní <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>. Toto téma se nebude pokoušet popisují všechny možné formáty, které fungovat a místo toho doporučuje vzoru krátkého data z hlediska standardní.  
  
## <a name="see-also"></a>Viz také  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
