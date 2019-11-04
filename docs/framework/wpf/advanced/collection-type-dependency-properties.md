---
title: Vlastnosti závislostí typu kolekce
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [WPF], dependency
- properties [WPF], collection-type
- dependency properties [WPF]
- collection-type properties [WPF]
ms.assetid: 99f96a42-3ab7-4f64-a16b-2e10d654e97c
ms.openlocfilehash: f7f8c25844f41dd8915c0f4404d6714b4c81233c
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458476"
---
# <a name="collection-type-dependency-properties"></a>Vlastnosti závislostí typu kolekce
Toto téma poskytuje pokyny a navrhované vzory pro implementaci vlastnosti závislosti, kde typ vlastnosti je typ kolekce.  

<a name="implementing"></a>   
## <a name="implementing-a-collection-type-dependency-property"></a>Implementace vlastnosti závislostí typu kolekce  
 Pro vlastnost závislosti obecně platí, že následující způsob implementace je definovat obálku vlastností CLR, kde je tato vlastnost zajištěna pomocí identifikátoru <xref:System.Windows.DependencyProperty>, nikoli pole nebo jiné konstrukce. Při implementaci vlastnosti typu kolekce budete postupovat podle stejného vzoru. Nicméně vlastnost typu kolekce zavádí složitou složitost na vzor vždy, když typ, který je obsažen v kolekci, je sám <xref:System.Windows.DependencyObject> nebo <xref:System.Windows.Freezable> odvozenou třídou.  
  
<a name="initializing"></a>   
## <a name="initializing-the-collection-beyond-the-default-value"></a>Inicializuje se kolekce nad rámec výchozí hodnoty.  
 Při vytváření vlastnosti závislosti neurčíte výchozí hodnotu vlastnosti jako počáteční hodnotu pole. Místo toho zadáte výchozí hodnotu prostřednictvím metadat vlastnosti závislostí. Pokud je vlastnost typem odkazu, výchozí hodnota zadaná v metadatech vlastnosti závislosti není výchozí hodnotou pro instanci. místo toho je výchozí hodnota, která se vztahuje na všechny instance daného typu. Proto musíte mít pozor, abyste nepoužívali statickou kolekci v jednotném definování metadat vlastnosti kolekce jako pracovní výchozí hodnotu pro nově vytvořené instance daného typu. Místo toho je nutné zajistit, aby byla hodnota kolekce záměrně nastavena na jedinečnou kolekci (instance) jako součást logiky konstruktoru třídy. V opačném případě budete mít vytvořenou neúmyslnou třídu singleton.  
  
 Vezměte v úvahu následující příklad. Následující část příkladu ukazuje definici pro třídu `Aquarium`. Třída definuje vlastnost závislosti typu kolekce `AquariumObjects`, která používá obecný typ <xref:System.Collections.Generic.List%601> s omezením typu <xref:System.Windows.FrameworkElement>. V <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29> volání vlastnosti závislosti vytvoří metadata výchozí hodnotu jako nový obecný <xref:System.Collections.Generic.List%601>.  
  
 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 Nicméně, pokud jste kód právě opustili, jak je znázorněno, bude pro všechny instance `Aquarium`sdílena výchozí hodnota v jednom seznamu. Pokud jste spustili následující testovací kód, který je určen k zobrazení, jak byste vytvořili instanci dvou samostatných `Aquarium` instancí a přidáte do každého z nich jednu jinou `Fish`, zobrazí se výsledek překvapivé:  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 Místo každé kolekce s počtem jedna kolekce má počet dvou. Důvodem je, že každá `Aquarium` přidala svůj `Fish` do výchozí kolekce hodnot, která je výsledkem jednoho volání konstruktoru v metadatech a je proto sdílena mezi všemi instancemi. Tato situace je téměř nikdy nežádoucí.  
  
 Chcete-li tento problém vyřešit, je nutné nastavit hodnotu vlastnosti závislosti kolekce na jedinečnou instanci jako součást volání konstruktoru třídy. Vzhledem k tomu, že vlastnost je vlastnost závislosti jen pro čtení, použijte metodu <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29> k jejímu nastavení pomocí <xref:System.Windows.DependencyPropertyKey>, který je přístupný pouze v rámci třídy.  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 Pokud teď znovu spustíte stejný testovací kód, mohli byste zobrazit očekávané výsledky, kde každá `Aquarium` podporovala vlastní jedinečnou kolekci.  
  
 Pokud se rozhodnete, že máte vlastnost kolekce pro čtení i zápis, měla by se v tomto vzoru mírně variace. V takovém případě můžete zavolat přístup k veřejné sadě z konstruktoru k provedení inicializace, což by stále volalo nonkey podpis <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> v rámci nastavené obálky s použitím identifikátoru Public <xref:System.Windows.DependencyProperty>.  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a>Vytváření sestav – změny hodnot vazeb z vlastností kolekce  
 Vlastnost kolekce, která je sám vlastností závislosti, neoznamuje automaticky změny jejích podvlastností. Pokud vytváříte vazby do kolekce, může to zabránit vazbě při vytváření sestav, čímž dojde k neověřování některých scénářů datové vazby. Nicméně pokud použijete typ kolekce <xref:System.Windows.FreezableCollection%601> jako typ kolekce, pak se změny podvlastností na obsažené prvky v kolekci správně nahlásí a vazba funguje podle očekávání.  
  
 Chcete-li povolit vazbu podvlastností v kolekci objektů závislosti, vytvořte vlastnost Collection jako typ <xref:System.Windows.FreezableCollection%601>s omezením typu pro tuto kolekci na jakoukoli <xref:System.Windows.DependencyObject> odvozenou třídu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.FreezableCollection%601>
- [XAML a vlastní třídy pro WPF](xaml-and-custom-classes-for-wpf.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
- [Metadata vlastností závislosti](dependency-property-metadata.md)
