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
ms.openlocfilehash: 71c29cc6d1c7955b889a56b0a6629690a2947c78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="collection-type-dependency-properties"></a>Vlastnosti závislostí typu kolekce
Toto téma obsahuje pokyny a navrhované vzory pro implementaci vlastnost závislosti, kde je typ vlastnosti typu kolekce.  
  
 
  
<a name="implementing"></a>   
## <a name="implementing-a-collection-type-dependency-property"></a>Implementace vlastnost závislosti typ kolekce  
 Pro vlastnost závislosti implementace vzor, který budete postupovat podle je obecně můžete definovat [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnost obálky, kde je zajištěna tuto vlastnost <xref:System.Windows.DependencyProperty> identifikátor místo pole nebo jiné konstrukce. Provedením tohoto stejného vzoru při implementaci vlastnost typu kolekce. Však vlastnost typu kolekce zavádí některé složitost se vzorem vždy, když se o typ, který je obsažen v rámci kolekce <xref:System.Windows.DependencyObject> nebo <xref:System.Windows.Freezable> odvozené třídy.  
  
<a name="initializing"></a>   
## <a name="initializing-the-collection-beyond-the-default-value"></a>Inicializace kolekce překračuje výchozí hodnota  
 Když vytvoříte vlastnost závislosti, nezadávejte vlastnost výchozí hodnotu jako hodnota počáteční pole. Místo toho zadat výchozí hodnotu prostřednictvím metadata vlastnosti závislosti. Pokud je vaše vlastnost typu odkazu., výchozí hodnota zadaná v metadatech vlastnost závislosti není výchozí hodnotu na instanci; Místo toho je výchozí hodnotu, která platí pro všechny instance typu. Musí být proto opatrní nechcete použít kolekci singulární statické definované metadata vlastnosti kolekce jako pracovní výchozí hodnota pro nově vytvořená instance stejného typu. Místo toho je třeba se záměrně nastavena hodnota kolekce do kolekce jedinečný (instance) jako součást logiky konstruktor – třída. V opačném případě bude vytvořená třídu neúmyslnému singleton.  
  
 Podívejte se na následující příklad. V následující části Tento příklad zobrazuje definici pro třídu `Aquarium`. Třída definuje vlastnost závislost typu kolekce `AquariumObjects`, Obecné, který používá <xref:System.Collections.Generic.List%601> zadejte s <xref:System.Windows.FrameworkElement> typ omezení. V <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29> volání pro vlastnost závislosti, metadata vytvoří výchozí hodnotu na nové obecného <xref:System.Collections.Generic.List%601>.  
  
 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 Ale pokud jste právě nechali kód, jak je znázorněno, tato jediný seznam Výchozí hodnota je sdílena pro všechny instance `Aquarium`. Pokud jste spustili následující testovací kód, který se má zobrazit, jak by doložit dva samostatné `Aquarium` instance a přidejte jeden jiný `Fish` ke každému z nich, zobrazí se překvapivé výsledek:  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 Místo nutnosti započítává jako jeden Každá kolekce Každá kolekce má dva počet! Důvodem je, že každý `Aquarium` přidat jeho `Fish` do kolekce výchozí hodnotu, která je výsledkem volání jednoho konstruktor v metadatech a proto jsou sdílena mezi všechny instance. Tato situace je téměř žádné co chcete použít.  
  
 Chcete-li tento problém, musí vynulovat hodnotu vlastnosti závislosti kolekce k instanci jedinečný v rámci volání konstruktoru třídy. Protože vlastnost je vlastnost závislosti jen pro čtení, můžete použít <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29> metodu a nastavit, pomocí <xref:System.Windows.DependencyPropertyKey> , je k dispozici pouze v rámci třídy.  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 Nyní, pokud jste spustili, že stejný kód test znovu, se může zobrazí více očekávané výsledky, kde každý `Aquarium` podporované svůj vlastní jedinečný kolekce.  
  
 By mírné variace v tomto vzoru Pokud jste zvolili pro vaše kolekce vlastností se pro čtení a zápis. V takovém případě může volat přistupujícího objektu veřejná sada z konstruktoru udělat inicializaci, což by stále volání nonkey podpis <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> v rámci vaší sady obálky, pomocí veřejné <xref:System.Windows.DependencyProperty> identifikátor.  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a>Vytváření sestav vazby změnám hodnoty z vlastnosti kolekce  
 Vlastnost kolekce, který je sám vlastnost závislosti automaticky nehlásí změny k jeho podvlastnosti. Při vytváření vazby na kolekci, může bránit vazbu z hlášení změn, proto zneplatnění některé scénáře datových vazeb. Ale pokud používáte typ kolekce <xref:System.Windows.FreezableCollection%601> jako typ kolekce, pak dílčí vlastnosti změny obsažené elementů v kolekci jsou správně hlášené a vazba funguje podle očekávání.  
  
 Chcete-li povolit vazby dílčí vlastnosti v objektu kolekce závislost, vytvořit kolekci jako typ <xref:System.Windows.FreezableCollection%601>, s omezením na typ pro tuto kolekci do jakéhokoli <xref:System.Windows.DependencyObject> odvozené třídy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.FreezableCollection%601>  
 [XAML a vlastní třídy pro WPF](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Vlastní vlastnosti závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Metadata vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)
