---
title: Převaděče typů a rozšíření značek pro jazyk XAML
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], type converter services
- XAML [XAML Services], value converters
- XAML [XAML Services], markup extension services
- value converters for XAML [XAML Services]
- XAML [XAML Services], service context
ms.assetid: db07a952-05ce-4aa4-b6f9-aac7397d0326
caps.latest.revision: 13
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 34d48e7de0269449bd4ed6eedb83a7464b6d3d50
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="type-converters-and-markup-extensions-for-xaml"></a>Převaděče typů a rozšíření značek pro jazyk XAML
Převaděče typů a rozšíření značek jsou dvě techniky, které systémy typ jazyka XAML a XAML zapisovače použít ke generování součásti grafu objektu. I když některé vlastnosti sdílejí, převaděče typů a rozšíření značek jsou reprezentované jinak v datový proud uzlu XAML. V této dokumentaci sady, převaděčů typů, rozšíření značek a podobné konstrukce jsou někdy souhrnně označovány jako převodníky hodnot.  
  
<a name="value_converters"></a>   
## <a name="value-converters"></a>Převodníky hodnot  
 V jazyce XAML se používají převodníky hodnot pro různé scénáře. Následující seznam obsahuje různé typy převodníky hodnot v jazyce XAML:  
  
-   převaděče typů  
  
-   – Rozšíření značek  
  
-   Serializátor hodnota  
  
-   Související nebo podporu třída, která poskytuje logiku pro textových syntaxi jazyka XAML  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>Převaděče typů  
 V definici rozhraní .NET Framework XAML Services převaděče typů jsou třídy, které jsou odvozeny od CLR <xref:System.ComponentModel.TypeConverter> třídy. <xref:System.ComponentModel.TypeConverter> je třída, která byla v [!INCLUDE[TLA#tla_netframewk](../../../includes/tlasharptla-netframewk-md.md)] dříve, než vznikla XAML. Původnímu účelu se na podporu vlastnost windows a podobné úpravy metaphors založený na textu plody pro [!INCLUDE[TLA2#tla_ide](../../../includes/tla2sharptla-ide-md.md)] vlastnosti. Zavedení XAML do rozhraní .NET Framework používá <xref:System.ComponentModel.TypeConverter> převést na objekt textových syntaxi (jak se nachází v hodnotě atributu nebo hodnotu uzlu XAML). <xref:System.ComponentModel.TypeConverter> Můžete také použít k serializaci hodnotu objektu na text syntaxe. <xref:System.ComponentModel.TypeConverter> byla také použita v předchozích implementacích XAML konkrétní rozhraní v [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] a Windows Communication Foundation (WCF). Další informace o <xref:System.ComponentModel.TypeConverter> v jazyce XAML, najdete v části [převaděčů typů pro jazyk XAML přehled](../../../docs/framework/xaml-services/type-converters-for-xaml-overview.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Rozšíření značek  
 Implementace rozhraní .NET Framework XAML Services rozšíření značek jsou třídy, které jsou odvozeny od <xref:System.Windows.Markup.MarkupExtension> třídy. Rozšíření značek jsou pojem, který v tomto formuláři je vytvořena podle jazyka XAML. Si můžete představit rozšíření značek, že je něco podobného jako extensible řídicí sekvencí, který zavolá třídu služby zajistit svou logikou. Z hlediska značek procesory XAML všeobecně rozpoznat rozšíření značek pořadí text, který začíná žádná levá složená závorka ({}) v textovém řetězci.  
  
 Rozšíření značek se liší od převaděče typů. Převaděče typů jsou obvykle spojené s typy nebo členy. Jsou vyvolány když vytvoření grafu objektu nebo serializace zaznamená syntaxe text, který je přidružen tyto entity.  
  
 Rozšíření značek jsou spojeny s třídou, jeden podpůrné služby, ale můžete použít pro žádnou hodnotu člena. (Můžete ale implementovat vaše – rozšíření značek úmyslně omezení jeho použití na některé členy nebo cílové typy pomocí kontext služby.) Rozšíření značek můžete přepsat přidružení převaděče typu. Nebo je můžete zadat hodnotu atributu pro členy, které by jinak podporují textových syntaxi.  
  
 Další informace o implementaci vzoru rozšíření značek pro jazyk XAML najdete v tématu [XAML přehled rozšíření značek pro](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Markup.MarkupExtension> a <xref:System.Windows.Markup.ValueSerializer> typy jsou oba seznamy v <xref:System.Windows.Markup> obor názvů a nikoli v <xref:System.Xaml> oboru názvů. To neznamená, že tyto typy jsou specifické pro buď WPF nebo Windows Forms technologie, které jinak naplnit CLR obory názvů, které obsahují řetězec `Windows`. <xref:System.Windows.Markup.MarkupExtension> a <xref:System.Windows.Markup.ValueSerializer> jsou v sestavení System.Xaml a mít žádné konkrétní framework závislostí. Tyto typy existovalo v oboru názvů CLR pro [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] a zůstanou v oboru názvů CLR v [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] předejdete nejnovější odkazy ve existující projekty WPF. Další informace najdete v tématu [typy migrované z grafického subsystému WPF do oboru názvů System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md).  
  
<a name="value_serializers"></a>   
## <a name="value-serializers"></a>Hodnota Serializátorů  
 A <xref:System.Windows.Markup.ValueSerializer> se speciálním typem převaděč, která je optimalizovaná pro převod objekt na řetězec. A <xref:System.Windows.Markup.ValueSerializer> pro XAML nemusí implementovat `ConvertFrom` metoda vůbec. A <xref:System.Windows.Markup.ValueSerializer> získá služby způsobem, který je stejná jako implementace <xref:System.ComponentModel.TypeConverter> implementace. Virtuální metody poskytují vstup `context` parametr. `context` Parametr je typu <xref:System.Windows.Markup.IValueSerializerContext>, který dědí z <xref:System.IServiceProvider> rozhraní a má <xref:System.IServiceProvider.GetService%2A> metoda.  
  
 V systému typu XAML a pro implementace zapisovače XAML, které používají zpracování smyčky uzlu XAML pro serializaci převaděč hodnoty, který je přidružený typ nebo člen je hlášen vlastní <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> vlastnost. Význam do zapisovače XAML, které provádějí serializace je, že pokud <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> a <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> existuje, převaděče typů se má používat pro zatížení cesta a hodnota serializátoru, který má být použit pro uložení cestu. Pokud <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> existuje, ale <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> je `null`, převaděče typů se taky používá pro uložení cestu.  
  
<a name="other_value_converters"></a>   
## <a name="other-value-converters"></a>Další převodníky hodnot  
 Převaděč hodnoty je rozšiřitelný určité vzory převaděče typů nebo rozšíření značek. Toto vlastní nastavení však by vyžadovaly předefinování systém typů XAML jako poskytované rozhraní .NET Framework XAML Services. Existující systém typů XAML má reprezentace a vytváření sestav systémy pro převaděče typů, rozšíření značek a serializátorů hodnotu, ale ne pro vlastní formy převod hodnoty. Pokud chcete vytvořit vlastní hodnotu převaděče, použijte <xref:System.Xaml.Schema.XamlValueConverter%601> typu.  
  
<a name="type_converters_and_markup_extensions_in_combination"></a>   
## <a name="type-converters-and-markup-extensions-in-combination"></a>Převaděče typů a rozšíření značek v kombinaci  
 Rozšíření a typ převaděče značek se používají pro různé situace v jazyce XAML. I když kontext je k dispozici pro použití rozšíření značek, chování převodu typu vlastností, kde rozšíření značek poskytuje že hodnotu je obecně kontrolována v implementacích rozšíření značek. Jinými slovy i v případě, že rozšíření značek vrátí textový řetězec jako jeho `ProvideValue` výstupu typ převodu chování na tento řetězec jako použít pro určitou vlastnost nebo typ hodnoty vlastnosti není vyvolána. Obecně platí je účelem rozšíření značek zpracovat řetězec a vrátí objekt bez jakékoli převaděče typů související se situací.  
  
<a name="service_context_for_a_value_converter"></a>   
## <a name="service-context-for-a-value-converter"></a>Kontext služby pro převaděč hodnoty  
 Pokud implementujete převaděč hodnoty, často potřebují přístup k kontext, ve kterém se použije převaděč hodnoty. Tento kontext se označuje jako kontext služby. Kontext služby může obsahovat informace, jako je active kontext schématu XAML, přístup k systému mapování typu, který kontext schématu XAML a zapisovače objektu XAML zadejte a tak dále. Další informace o kontexty služby dostupné pro převaděče hodnotu a postupy pro přístup ke službám, které může poskytovat kontext služby najdete v tématu [služby kontexty dostupné pro převaděče typů a rozšíření značek](../../../docs/framework/xaml-services/service-contexts-available-to-type-converters-and-markup-extensions.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Markup.MarkupExtension>  
 <xref:System.Xaml.XamlObjectWriter>  
 [Přehled rozšíření značek pro jazyk XAML](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)  
 [Přehled převaděčů typů pro jazyk XAML](../../../docs/framework/xaml-services/type-converters-for-xaml-overview.md)  
 [Kontexty služby dostupné pro převaděče typů a rozšíření značek](../../../docs/framework/xaml-services/service-contexts-available-to-type-converters-and-markup-extensions.md)
