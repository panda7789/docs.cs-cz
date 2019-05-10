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
ms.openlocfilehash: ff820256a27ce455b8eda0c4e7192bc26a3199c3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663216"
---
# <a name="type-converters-and-markup-extensions-for-xaml"></a>Převaděče typů a rozšíření značek pro jazyk XAML
Převaděče typů a rozšíření značek jsou dvě techniky, které systémy typ XAML a XAML zapisovače používají ke generování komponenty grafu objektu. I když některé vlastnosti sdílejí, převaděče typů a rozšíření značek jsou reprezentovány odlišně v datovém proudu uzlu XAML. V této dokumentaci sady, převaděče typů, rozšíření značek a podobné konstrukce jsou někdy souhrnně označovány jako převaděče hodnot.  
  
<a name="value_converters"></a>   
## <a name="value-converters"></a>Převodníky hodnot  
 V XAML převaděče hodnot se používají pro různé scénáře. Následující seznam uvádí různé druhy převaděče hodnot v XAML:  
  
- Konvertor typu  
  
- Rozšíření značek  
  
- Serializátor hodnoty  
  
- Související třídy nebo pomocná třída, která poskytuje logiku pro textová syntaxe XAML  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>Převaděče typů  
 V definici rozhraní .NET Framework XAML Services jsou převaděče typů tříd, které jsou odvozeny z CLR <xref:System.ComponentModel.TypeConverter> třídy. <xref:System.ComponentModel.TypeConverter> je třída, která byla v rozhraní Microsoft .NET Framework před existoval XAML. Původnímu účelu se na podporu windows vlastnost a podobné úpravy metaphors založený na textu plody pro [!INCLUDE[TLA2#tla_ide](../../../includes/tla2sharptla-ide-md.md)] vlastnosti. Úvod XAML do rozhraní .NET Framework používá <xref:System.ComponentModel.TypeConverter> textová syntaxe (jak se nachází v hodnotě atributu nebo uzel hodnoty XAML) převést na objekt. <xref:System.ComponentModel.TypeConverter> Můžete také použít k serializaci hodnotu objektu na textová syntaxe. <xref:System.ComponentModel.TypeConverter> byl použit také v předchozích implementacích specifické pro architekturu XAML Windows Presentation Foundation (WPF) a Windows Communication Foundation (WCF). Další informace o <xref:System.ComponentModel.TypeConverter> v XAML, naleznete v tématu [XAML přehled převaděčů typů pro](type-converters-for-xaml-overview.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Rozšíření značek  
 V implementaci rozhraní .NET Framework XAML Services – rozšíření značek jsou třídy, které jsou odvozeny z <xref:System.Windows.Markup.MarkupExtension> třídy. Rozšíření značek jsou pojem, který v tomto formuláři je vytvořena v jazyce XAML. Rozšíření značek jako nemusí vypadat extensible řídicí sekvence, která volá služba třídě poskytnout vlastní logiku si můžete představit. Z hlediska značek procesory XAML univerzálně rozpoznat rozšíření značek podle sekvence textu, který začíná levá složená závorka ({}) v textovém řetězci.  
  
 Rozšíření značek se liší od převaděče typů. Převaděče typů jsou obvykle spojeny s typy nebo členy. Jsou vyvolány při vytvoření grafu objektu nebo serializace, zaznamená textová syntaxe, která souvisí s těmito entitami.  
  
 Rozšíření značek jsou spojeny s třídou jeden podpůrné služby, ale můžete použít pro libovolnou hodnotu člena. (Můžete ale implementovat vaše – rozšíření značek záměrně omezit jeho použití na některé členy nebo určení typů s použitím místní služby.) Rozšíření značek můžete přepsat přidružení konvertor typu. Nebo můžete využít k určete název atributu pro členy, které by jinak podporují textová syntaxe.  
  
 Další informace o implementaci vzoru rozšíření značek XAML naleznete v tématu [– rozšíření značek XAML přehled](markup-extensions-for-xaml-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Markup.MarkupExtension> a <xref:System.Windows.Markup.ValueSerializer> typy jsou v <xref:System.Windows.Markup> obor názvů a nikoli v <xref:System.Xaml> oboru názvů. To neznamená, že tyto typy jsou specifické pro WPF nebo Windows Forms technologií, které jinak naplnit oborů názvů CLR, které obsahují řetězec `Windows`. <xref:System.Windows.Markup.MarkupExtension> a <xref:System.Windows.Markup.ValueSerializer> jsou v oboru názvů System.Xaml sestavení a nejsou závislé na konkrétní verzi rozhraní framework. Tyto typy existovala v oboru názvů CLR pro [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] a zůstanou v oboru názvů CLR v [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] k vyhnuli narušení funkčnosti odkazů v existující projekty WPF. Další informace najdete v tématu [typy migrované z prostředí WPF do oboru názvů System.Xaml](types-migrated-from-wpf-to-system-xaml.md).  
  
<a name="value_serializers"></a>   
## <a name="value-serializers"></a>Hodnota Serializátorů  
 A <xref:System.Windows.Markup.ValueSerializer> je speciální typ převaděče, která je optimalizovaná pro převod objektu na řetězec. A <xref:System.Windows.Markup.ValueSerializer> pro neimplementuje XAML `ConvertFrom` metoda vůbec. A <xref:System.Windows.Markup.ValueSerializer> získá služby způsobem, který je stejná jako implementace <xref:System.ComponentModel.TypeConverter> implementace. Virtuální metody poskytují vstupní `context` parametru. `context` Je parametr typu <xref:System.Windows.Markup.IValueSerializerContext>, který dědí z <xref:System.IServiceProvider> rozhraní a má <xref:System.IServiceProvider.GetService%2A> metody.  
  
 V typu systému XAML a pro implementace zapisovače XAML, používající zpracování smyčky uzlu XAML pro serializaci převaděč hodnoty, který je přidružen typ nebo člen je ohlášena vlastní <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> vlastnost. Význam, aby uživatelé vytvářející obsah XAML, které provádějí serializace je, že pokud <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> a <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> existují, byste měli použít konvertor typu pro načíst cestu a serializátor hodnoty byste měli použít pro uložení cestu. Pokud <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> existuje, ale <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> je `null`, konvertor typu se také používá pro uložení cestu.  
  
<a name="other_value_converters"></a>   
## <a name="other-value-converters"></a>Další převaděče hodnot  
 Převaděč hodnot je možné rozšířit nad rámec určité vzory konvertor typu nebo rozšíření značek. Toto přizpůsobení by ale také vyžadovat předefinování typu systému XAML podle rozhraní .NET Framework XAML Services. V existujícím typu systému XAML je reprezentace a vytváření sestav systémy pro převaděče typů, rozšíření značek a hodnotu serializátory, ale ne pro vlastní formuláře Převod hodnoty. Pokud chcete vytvořit vlastní převodníky hodnot, použijte <xref:System.Xaml.Schema.XamlValueConverter%601> typu.  
  
<a name="type_converters_and_markup_extensions_in_combination"></a>   
## <a name="type-converters-and-markup-extensions-in-combination"></a>Převaděče typů a rozšíření značek v kombinaci  
 Rozšíření a typ převaděče značky se používají pro různé situace v XAML. I když je k dispozici pro použití rozšíření značky kontext, není chování převodu typu vlastnosti, kde rozšíření značek zajišťuje, že hodnota je obecně změnami implementace rozšíření značek. Jinými slovy i v případě, že rozšíření značek vrací textový řetězec jako jeho `ProvideValue` výstupu, není vyvolána chování převodu typu pro tento řetězec jako použitý pro určitou vlastnost nebo typ hodnoty vlastnosti. Obecně platí je účelem rozšíření značek ke zpracování řetězce a vrátit objekt bez jakékoli konvertor typu zahrnutých.  
  
<a name="service_context_for_a_value_converter"></a>   
## <a name="service-context-for-a-value-converter"></a>Kontext služby pro převaděč hodnoty  
 Při implementaci převaděč hodnoty často potřebují přístup ke kontextu, ve kterém se použije převaděč hodnoty. Tento kontext se označuje jako kontext služby. Kontext služby může obsahovat informace, jako je aktivní kontext schématu XAML, přístup k mapování systém typů, které poskytují kontext schématu XAML a XAML objektu zapisovače a tak dále. Další informace o kontexty služby dostupné pro převaděče hodnoty a jak získat přístup ke službám, které můžou poskytovat kontext služby najdete v tématu [služby kontexty dostupné pro převaděče typů a rozšíření značek](service-contexts-available-to-type-converters-and-markup-extensions.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [Přehled rozšíření značek pro jazyk XAML](markup-extensions-for-xaml-overview.md)
- [Přehled převaděčů typů pro jazyk XAML](type-converters-for-xaml-overview.md)
- [Kontexty služby dostupné pro převaděče typů a rozšíření značek](service-contexts-available-to-type-converters-and-markup-extensions.md)
