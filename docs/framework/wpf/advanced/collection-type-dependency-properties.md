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
ms.openlocfilehash: 21f260262d434ffe3685b226193f2d6cd2125549
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548427"
---
# <a name="collection-type-dependency-properties"></a>Vlastnosti závislostí typu kolekce
Toto téma obsahuje pokyny a doporučené způsoby pro implementace vlastnosti závislosti, kde je typ vlastnosti typu kolekce.  
  
 
  
<a name="implementing"></a>   
## <a name="implementing-a-collection-type-dependency-property"></a>Implementace vlastnosti závislostí typu kolekce  
 Pro vlastnost závislosti obecně implementaci vzoru, který sledujete je, že definujete [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnost obálku, ve kterém je zajištěná tuto vlastnost <xref:System.Windows.DependencyProperty> identifikátor spíše než pole nebo jiné konstrukce. Můžete sledovat tento stejný vzor při implementaci vlastnosti typu kolekce. Však vlastnost typ kolekce zavádí některé složitost se vzorem pokaždé, když je typ, který je součástí kolekce <xref:System.Windows.DependencyObject> nebo <xref:System.Windows.Freezable> odvozené třídy.  
  
<a name="initializing"></a>   
## <a name="initializing-the-collection-beyond-the-default-value"></a>Inicializace kolekce nad výchozí hodnotu  
 Když vytvoříte vlastnost závislosti, nezadávejte výchozí hodnota vlastnosti jako počáteční hodnotu pole. Místo toho zadat výchozí hodnotu prostřednictvím metadata vlastností závislosti. Pokud je vaše vlastnost Typ odkazu, výchozí hodnota zadaná v metadata vlastností závislosti není výchozí hodnotu na instanci; Místo toho je výchozí hodnotu, která se vztahuje na všechny instance daného typu. Proto musí být opatrní nechcete použít singulární statických určené kolekce metadat vlastností s výchozí hodnotou pracovní pro nově vytvořená instance stejného typu. Místo toho je třeba že záměrně nastavena hodnota kolekce pro kolekci jedinečné (instance) jako součást logiky konstruktoru třídy. V opačném případě bude vytvoříte třídu neúmyslnému typu singleton.  
  
 Podívejte se na následující příklad. Následující části v příkladu je uvedena definice pro třídu `Aquarium`. Třída definuje vlastnost závislostí typu kolekce `AquariumObjects`, který používá Obecné <xref:System.Collections.Generic.List%601> typ s <xref:System.Windows.FrameworkElement> omezení typu. V <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29> volání pro vlastnost závislosti, metadata vytvoří výchozí hodnotu bude nový obecný <xref:System.Collections.Generic.List%601>.  
  
 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 Ale pokud ponecháte jenom kód, jak je znázorněno, tato výchozí hodnota jednoho seznamu sdílí se pro všechny výskyty `Aquarium`. Pokud jste spustili následující testovací kód, který se má zobrazit, jak byste měli vytvořit instanci dva samostatné `Aquarium` instance a přidat jiné jeden `Fish` u každého z nich, zobrazí se překvapivé výsledek:  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 Ne každá kolekce s počtem jedna Každá kolekce má dva počet! Důvodem je, že každý `Aquarium` přidá jeho `Fish` na výchozí hodnotu kolekce, která je výsledkem volání jediný konstruktor v metadatech a proto jsou sdílena mezi všemi instancemi. Tato situace je téměř nikdy co chcete.  
  
 Chcete-li tento problém, je nutné obnovit hodnota vlastnosti závislostí kolekce na instanci jedinečný jako součást volání konstruktoru třídy. Vzhledem k tomu, je vlastnost závislosti jen pro čtení, je použít <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29> metody, nastavte pomocí <xref:System.Windows.DependencyPropertyKey> , který je přístupný jenom v rámci třídy.  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 Nyní, pokud jste spustili, že stejné znovu otestujte kódu, je možné, uvidíte více očekávané výsledky, kde každý `Aquarium` podporované svou vlastní jedinečnou kolekci.  
  
 Bude mírné variantou tento model Pokud jste zvolili možnost vaší kolekce vlastnost, pro čtení i zápis. V takovém případě lze volat veřejná přístupová metoda set z konstruktoru provést inicializaci, což by stále volání nonkey podpis <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> v rámci vaší sady obálky, pomocí veřejného <xref:System.Windows.DependencyProperty> identifikátor.  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a>Hlášení změn vazby hodnoty z vlastnosti kolekce  
 Vlastnost kolekce, který je sám vlastnost závislosti automaticky nehlásí změny k jeho objektu třídy subproperties. Při vytváření vazby do kolekce, můžou zabránit vazbě z hlášení změn, tedy zrušení platnosti některých scénáře datových vazeb. Nicméně pokud použijete typ kolekce <xref:System.Windows.FreezableCollection%601> jako typ kolekce, pak podvlastností změny jeho prvky v kolekci správně označené a vazby funguje podle očekávání.  
  
 Povolit dílčí vlastnosti vazba v objektu kolekce závislost, vytvořit vlastnost kolekce jako typ <xref:System.Windows.FreezableCollection%601>, s omezením typu pro tuto kolekci na jakýkoli <xref:System.Windows.DependencyObject> odvozené třídy.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.FreezableCollection%601>
- [XAML a vlastní třídy pro WPF](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [Vlastní vlastnosti závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
- [Metadata vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)
