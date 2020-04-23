---
title: Převaděče typů a rozšíření značek pro jazyk XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services
- XAML [XAML Services], value converters
- XAML [XAML Services], markup extension services
- value converters for XAML [XAML Services]
- XAML [XAML Services], service context
ms.assetid: db07a952-05ce-4aa4-b6f9-aac7397d0326
ms.openlocfilehash: bee94b03d4fd6e6f5ef8571e83f554b381dd6582
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071652"
---
# <a name="type-converters-and-markup-extensions-for-xaml"></a>Převaděče typů a rozšíření značek pro jazyk XAML

Převaděče typů a rozšíření značek jsou dvě techniky, které systémy typu XAML a zapisovače XAML používají ke generování komponent objektového grafu. Přestože sdílejí některé charakteristiky, převaděče typů a rozšíření značek jsou v datovém proudu uzlu XAML reprezentovány odlišně. V této sadě dokumentace převaděče typů, rozšíření značek a podobné konstrukce jsou někdy souhrnně označovány jako převaděče hodnot.

## <a name="value-converters"></a>Převaděče hodnot

V XAML převaděče hodnot se používají pro různé scénáře. V následujícím seznamu jsou uvedeny různé typy převaděčů hodnot v jazyce XAML:

- Převaděč typů

- Rozšíření o značky

- Serializátor hodnoty

- Související třída nebo třída podpory, která poskytuje logiku pro syntaxi textu XAML

## <a name="type-converters"></a>Převaděče typů

V definici služby .NET XAML jsou převaděči typu třídy, které jsou odvozeny z třídy CLR. <xref:System.ComponentModel.TypeConverter> <xref:System.ComponentModel.TypeConverter>je třída, která byla v rozhraní .NET před xaml existoval. Jeho původním účelem bylo podporovat okna vlastností a podobné textové úpravy metafory pro vlastnosti IDE. Zavedení XAML do rozhraní <xref:System.ComponentModel.TypeConverter> .NET používá k převodu syntaxe textu (jak je uvedeno v hodnotě atributu nebo uzlu hodnoty XAML) na objekt. <xref:System.ComponentModel.TypeConverter>lze také serializovat hodnotu objektu do syntaxe textu. <xref:System.ComponentModel.TypeConverter>byl také použit v předchozích implementacích XAML specifických pro architekturu v systémech Windows Presentation Foundation (WPF) a Windows Communication Foundation (WCF). Další informace o <xref:System.ComponentModel.TypeConverter> zařízení v XAML naleznete v [tématu Type Converters for XAML Overview](type-converters-overview.md).

## <a name="markup-extensions"></a>Rozšíření značek

V implementaci služby .NET XAML Services jsou rozšíření <xref:System.Windows.Markup.MarkupExtension> značek třídy, které jsou odvozeny z třídy. Rozšíření značek jsou koncept, který v tomto formuláři pochází z jazyka XAML. Můžete si myslet, že rozšíření značky jako něco jako rozšiřitelné escape sekvence, která volá do třídy služby poskytovat jeho logiku. Pokud jde o značky, procesory XAML univerzálně rozpoznají rozšíření značek textovou sekvencí, která začíná počáteční závorkou ({) v textovém řetězci.

Rozšíření značek se liší od převaděčů typů. Převaděče typu jsou obvykle spojeny s typy nebo členy. Jsou vyvolány, když vytvoření grafu objektu nebo serializace narazí na syntaxi textu, která je přidružena k těmto entitám.

Rozšíření značek jsou přidružena k jedné třídě podpůrné služby, ale lze je použít pro libovolnou hodnotu člena. (Rozšíření o značky však můžete implementovat tak, aby bylo jeho použití záměrně možné omezit na určité členy nebo cílové typy pomocí kontextu služby.) Rozšíření značek mohou přepsat přidružení převaděče typů. Nebo je můžete použít k určení hodnoty atributu pro členy, kteří by jinak nepodporovali textovou syntaxi.

Další informace o vzoru implementace rozšíření značek pro XAML naleznete v [tématu Rozšíření značek pro přehled XAML](markup-extensions-overview.md).

## <a name="value-serializers"></a>Serializátory hodnot

A <xref:System.Windows.Markup.ValueSerializer> je specializovaný převaděč typu, který je optimalizován pro převod objektu na řetězec. A <xref:System.Windows.Markup.ValueSerializer> pro XAML nemusí `ConvertFrom` implementovat metodu vůbec. Implementace <xref:System.Windows.Markup.ValueSerializer> získává služby způsobem, který <xref:System.ComponentModel.TypeConverter> je jako implementace. Virtuální metody poskytují `context` vstupní parametr. Parametr `context` je typu <xref:System.Windows.Markup.IValueSerializerContext>, který dědí z <xref:System.IServiceProvider> <xref:System.IServiceProvider.GetService%2A> rozhraní a má metodu.

V systému typu XAML a pro implementace zapisovače XAML, které používají zpracování smyčky uzlu XAML pro serializaci, je převaděč hodnot, který je přidružen k typu nebo členu, vykázán vlastní <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> vlastností. Význam pro autory XAML, kteří provádějí <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> serializaci, je, že pokud a existují, převaděč typu by měl být použit pro cestu zatížení a serializátor hodnoty by měl být použit pro cestu uložení. Pokud <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> existuje, <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> `null`ale je , převaděč typu se používá také pro uložit cestu.

## <a name="other-value-converters"></a>Jiné převaděče hodnot

Převaděč hodnot je rozšiřitelný nad rámec určitých vzorků převaděče typu nebo rozšíření značek. Toto přizpůsobení by však také vyžadovalo předefinování systému typu XAML poskytovaného službou .NET XAML Services. Stávající systém typů XAML má reprezentace a systémy vykazování pro převaděče typů, rozšíření značek a serializátory hodnot, ale ne pro vlastní formy převodu hodnoty. Pokud chcete vytvořit vlastní převaděče <xref:System.Xaml.Schema.XamlValueConverter%601> hodnot, použijte typ.

## <a name="type-converters-and-markup-extensions-in-combination"></a>Převaděče typů a rozšíření značek v kombinaci

Značky rozšíření a převaděče typu se používají pro různé situace v XAML. Přestože kontext je k dispozici pro použití rozšíření značek, typ převodu chování vlastností, kde rozšíření značky poskytuje hodnotu je obecně není kontrolována v implementacích rozšíření značky. Jinými slovy, i když rozšíření značky vrátí `ProvideValue` textový řetězec jako svůj výstup, není vyvoláno chování převodu typu na tomto řetězci, jak je použito na určitou vlastnost nebo typ hodnoty vlastnosti. Obecně je účelem rozšíření značek zpracovat řetězec a vrátit objekt bez jakéhokoli převaděče typu.

## <a name="service-context-for-a-value-converter"></a>Kontext služby pro převaděč hodnot

Při implementaci převaděče hodnot často potřebujete přístup k kontextu, ve kterém je použit převaděč hodnot. Tento kontext se označuje jako kontext služby. Kontext služby může zahrnovat informace, jako je například aktivní kontext schématu XAML, přístup k systému mapování typů, který poskytuje kontext schématu XAML a zapisovač objektů XAML a tak dále. Další informace o kontextech služby, které jsou k dispozici pro převaděč hodnot a o tom, jak získat přístup ke službám, které může poskytnout kontext [služby, naleznete v tématu Kontexty služby dostupné převaděčům typu a rozšíření o značky](service-contexts-with-type-converters-and-markup-extensions.md).

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [Přehled rozšíření značek pro jazyk XAML](markup-extensions-overview.md)
- [Přehled převaděčů typů pro jazyk XAML](type-converters-overview.md)
- [Kontexty služby dostupné pro převaděče typů a rozšíření značek](service-contexts-with-type-converters-and-markup-extensions.md)
