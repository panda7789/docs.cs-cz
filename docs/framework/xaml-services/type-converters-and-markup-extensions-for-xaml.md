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
ms.openlocfilehash: d31d970e8e95726aa789f853ac12c4830498a743
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796826"
---
# <a name="type-converters-and-markup-extensions-for-xaml"></a>Převaděče typů a rozšíření značek pro jazyk XAML
Převaděče typů a rozšíření značek jsou dvě metody, které používají systémy typů XAML a zapisovače XAML ke generování komponent grafu objektů. I když sdílí některé charakteristiky, převaděče typů a rozšíření značek jsou v datovém proudu uzlu XAML reprezentovány jinak. V této sadě dokumentace jsou převaděče typů, přípony značek a podobné konstrukce někdy souhrnně označovány jako převaděče hodnot.  
  
<a name="value_converters"></a>   
## <a name="value-converters"></a>Převaděče hodnot  
 V jazyce XAML jsou převaděče hodnot používány pro různé scénáře. V následujícím seznamu jsou uvedeny různé typy převaděčů hodnot v jazyce XAML:  
  
- Konvertor typu  
  
- Rozšíření značek  
  
- Serializátor hodnoty  
  
- Související třída nebo třída podpory, která poskytuje logiku pro syntaxi textu XAML  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>Převaděče typů  
 V definici .NET Framework XAML Services jsou převaděče typů třídy, které jsou odvozeny od <xref:System.ComponentModel.TypeConverter> třídy CLR. <xref:System.ComponentModel.TypeConverter>je třída, která byla v Microsoft .NET Framework před tím, než XAML existovala. Jeho původní účelem bylo podporovat okna vlastností a podobné textové úpravy metaphors pro vlastnosti IDE. Zavedení XAML pro .NET Framework používá <xref:System.ComponentModel.TypeConverter> k převodu syntaxe textu (jak je uvedeno v hodnotě atributu nebo uzlu hodnoty XAML) do objektu. <xref:System.ComponentModel.TypeConverter>lze také použít k serializaci hodnoty objektu na syntaxi textu. <xref:System.ComponentModel.TypeConverter>bylo použito také v předchozích implementacích XAML specifických pro rozhraní v Windows Presentation Foundation (WPF) a Windows Communication Foundation (WCF). Další informace o modulu <xref:System.ComponentModel.TypeConverter> v jazyce XAML naleznete v tématu [Přehled převaděčů typů pro jazyk XAML](type-converters-for-xaml-overview.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Rozšíření značek  
 Ve .NET Framework implementaci služeb XAML jsou rozšíření značek třídy, které jsou odvozeny z <xref:System.Windows.Markup.MarkupExtension> třídy. Rozšíření značek jsou koncept, který v tomto formuláři pochází z jazyka XAML. Rozšíření značek si můžete představit jako rozšiřitelnou řídicí sekvenci, která volá do třídy služby, aby poskytovala svou logiku. V souvislosti s označením procesory XAML univerzálně rozpoznávají rozšíření značek pomocí textové sekvence, která začíná levou složenou závorkou ({) v textovém řetězci.  
  
 Rozšíření značek se od převaděčů typů liší. Převaděče typů jsou obvykle přidruženy k typům nebo členům. Jsou vyvolány, když vytvoření grafu objektu nebo serializace nalezne textovou syntaxi spojenou s těmito entitami.  
  
 Rozšíření značek jsou přidružena k jedné podpůrné třídě služby, ale lze ji použít pro libovolnou hodnotu člena. (Nicméně můžete implementovat rozšíření značek k úmyslnému omezení jeho použití na určité členy nebo cílové typy pomocí kontextu služby.) Rozšíření značek mohou přepsat přidružení konvertoru typu. Nebo je můžete použít k zadání hodnoty atributu pro členy, kteří jinak nepodporují syntaxi textu.  
  
 Další informace o vzoru implementace rozšíření značek pro jazyk XAML naleznete v tématu [Přehled rozšíření značek pro jazyk XAML](markup-extensions-for-xaml-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Markup.MarkupExtension> <xref:System.Windows.Markup.ValueSerializer> <xref:System.Xaml> Typy a jsou v oborunázvůivoborunázvů.<xref:System.Windows.Markup> To neznamená, že tyto typy jsou specifické pro technologie WPF nebo model Windows Forms, které jinak naplňují obory názvů CLR obsahující řetězec `Windows`. <xref:System.Windows.Markup.MarkupExtension>a <xref:System.Windows.Markup.ValueSerializer> jsou v sestavení System. XAML a nemají žádnou konkrétní závislost architektury. Tyto typy existovaly v oboru názvů CLR pro .NET Framework 3,0 a zůstávají v oboru názvů CLR v .NET Framework 4, aby nedocházelo k přerušení odkazů v existujících projektech WPF. Další informace naleznete v tématu [typy migrované z WPF do System. XAML](types-migrated-from-wpf-to-system-xaml.md).  
  
<a name="value_serializers"></a>   
## <a name="value-serializers"></a>Serializátory hodnot  
 <xref:System.Windows.Markup.ValueSerializer> Je specializovaný konvertor typu, který je optimalizován pro převod objektu na řetězec. Pro XAML nemusí `ConvertFrom` metodu implementovat vůbec. <xref:System.Windows.Markup.ValueSerializer> Implementace získá služby způsobem, který je <xref:System.ComponentModel.TypeConverter> jako implementace. <xref:System.Windows.Markup.ValueSerializer> Virtuální metody poskytují vstupní `context` parametr. Parametr je typu <xref:System.Windows.Markup.IValueSerializerContext> ,kterýdědíz<xref:System.IServiceProvider.GetService%2A> rozhraní a má metodu. <xref:System.IServiceProvider> `context`  
  
 V systému typů XAML a pro implementaci zapisovače XAML, které používají zpracování smyčky uzlů XAML pro serializaci, je převaděč hodnot, který je přidružen k typu nebo členu, hlášen <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> podle vlastní vlastnosti. Význam pro zapisovače XAML, který provádí serializaci, je <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> , <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> že pokud existují a, musí být použit konvertor typu pro cestu načtení a serializátor hodnoty by měl být použit pro cestu pro uložení. Pokud <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> existuje, <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> ale `null`je, převaděč typu se používá také pro cestu pro uložení.  
  
<a name="other_value_converters"></a>   
## <a name="other-value-converters"></a>Další převaděče hodnot  
 Konvertor hodnot je rozšiřitelný nad rámec specifických vzorů konvertoru typu nebo rozšíření značek. Nicméně toto přizpůsobení by vyžadovalo také předefinování systému typu XAML, jak poskytuje .NET Framework služby XAML. Existující systém typů XAML obsahuje reprezentace a systémy vytváření sestav pro převaděče typů, rozšíření značek a serializace hodnot, ale nikoli pro vlastní formy převodu hodnot. Pokud chcete vytvořit vlastní převaděče hodnot, použijte <xref:System.Xaml.Schema.XamlValueConverter%601> typ.  
  
<a name="type_converters_and_markup_extensions_in_combination"></a>   
## <a name="type-converters-and-markup-extensions-in-combination"></a>Převaděče typů a rozšíření značek v kombinaci  
 Rozšíření značek a převaděče typů se používají pro různé situace v jazyce XAML. Přestože je kontext k dispozici pro použití rozšíření značek, chování konverze typu vlastností, kde rozšíření značek poskytuje hodnotu obecně není zaškrtnuto v implementacích rozšíření značek. Jinými slovy, i když rozšíření značek vrátí textový řetězec jako svůj `ProvideValue` výstup, chování konverze typu u tohoto řetězce, jak je použito na konkrétní vlastnost nebo typ hodnoty vlastnosti není vyvoláno. Obecně platí, že účelem rozšíření označení je zpracování řetězce a vrácení objektu bez jakéhokoli konvertoru typu.  
  
<a name="service_context_for_a_value_converter"></a>   
## <a name="service-context-for-a-value-converter"></a>Kontext služby pro konvertor hodnot  
 Při implementaci převaděče hodnot často potřebujete přístup k kontextu, ve kterém je použit převaděč hodnoty. Tento kontext je známý jako kontext služby. Kontext služby může zahrnovat informace, jako je například aktivní kontext schématu XAML, přístup k systému mapování typů, který kontext schématu XAML a zapisovač objektů XAML poskytují atd. Další informace o kontextech služby dostupných pro konvertor hodnot a o tom, jak získat přístup ke službám, které může poskytovat kontext služby, najdete v tématu kontexty [služby dostupné pro převaděče typů a rozšíření značek](service-contexts-available-to-type-converters-and-markup-extensions.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [Přehled rozšíření značek pro jazyk XAML](markup-extensions-for-xaml-overview.md)
- [Přehled převaděčů typů pro jazyk XAML](type-converters-for-xaml-overview.md)
- [Kontexty služby dostupné pro převaděče typů a rozšíření značek](service-contexts-available-to-type-converters-and-markup-extensions.md)
