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
ms.openlocfilehash: e783ce4b95b52b86671181dfe4b316d4b91d8fc6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141534"
---
# <a name="collection-type-dependency-properties"></a>Vlastnosti závislostí typu kolekce
Toto téma obsahuje pokyny a navrhované vzory pro implementaci vlastnosti závislosti, kde je typ vlastnosti typ kolekce.  

<a name="implementing"></a>
## <a name="implementing-a-collection-type-dependency-property"></a>Implementace vlastnosti závislosti typu kolekce  
 Pro vlastnost závislosti obecně je vzor implementace, který budete postupovat, je, že definujete obálku <xref:System.Windows.DependencyProperty> vlastnosti CLR, kde je tato vlastnost zálohována identifikátorem spíše než polem nebo jinou konstrukcí. Postupujte podle stejného vzoru při implementaci vlastnosti typu kolekce. Vlastnost typu kolekce však zavádí některé složitosti vzoru vždy, když typ, který <xref:System.Windows.DependencyObject> je <xref:System.Windows.Freezable> obsažen v kolekci je sám nebo odvozené třídy.  
  
<a name="initializing"></a>
## <a name="initializing-the-collection-beyond-the-default-value"></a>Inicializace kolekce nad rámec výchozí hodnoty  
 Při vytváření vlastnosti závislosti nezadáte výchozí hodnotu vlastnosti jako počáteční hodnotu pole. Místo toho zadáte výchozí hodnotu prostřednictvím metadat vlastnosti závislosti. Pokud je vaše vlastnost typ odkazu, výchozí hodnota zadaná v metadatech vlastnosti závislostí není výchozí hodnotou pro instanci. místo toho se jedná o výchozí hodnotu, která se vztahuje na všechny instance typu. Proto musíte být opatrní, abyste nepoužívali jedinečnou statickou kolekci definovanou metadaty vlastností kolekce jako pracovní výchozí hodnotu pro nově vytvořené instance vašeho typu. Místo toho je nutné se ujistit, že záměrně nastavit hodnotu kolekce na jedinečnou kolekci (instance) jako součást logiky konstruktoru třídy. V opačném případě vytvoříte neúmyslnou třídu singleton.  
  
 Představte si následující příklad. Následující část příkladu ukazuje definici `Aquarium`třídy , která obsahuje chybu s výchozí hodnotou. Třída definuje vlastnost `AquariumObjects`závislosti typu kolekce , která <xref:System.Collections.Generic.List%601> používá <xref:System.Windows.FrameworkElement> obecný typ s omezením typu. Ve <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29> volání vlastnosti závislost metadata vytvoří výchozí hodnotu jako nový <xref:System.Collections.Generic.List%601>obecný .

> [!WARNING]
> Následující kód se nechová správně.

 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 Pokud jste však kód opustili, jak je znázorněno, je `Aquarium`tato výchozí hodnota jednoho seznamu sdílena pro všechny instance aplikace . Pokud jste spustili následující testovací kód, který má ukázat, jak `Aquarium` byste vytvořit konkretizovat dvě samostatné instance a přidat jeden jiný pro `Fish` každou z nich, uvidíte překvapivý výsledek:  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 Namísto každé kolekce s počtem jednoho, každá kolekce má počet dvou! Důvodem je, že každý `Aquarium` přidal jeho `Fish` do výchozí kolekce hodnot, které vyplývá z jednoho konstruktoru volání v metadatech a je proto sdílena mezi všechny instance. Tato situace je téměř nikdy to, co chcete.  
  
 Chcete-li tento problém vyřešit, je nutné obnovit hodnotu vlastnosti závislosti kolekce na jedinečnou instanci jako součást volání konstruktoru třídy. Vzhledem k tomu, <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29> <xref:System.Windows.DependencyPropertyKey> že vlastnost je jen pro čtení vlastnost závislosti, použijte metodu k nastavení, pomocí který je přístupný pouze v rámci třídy.  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 Nyní, pokud jste spustili stejný testovací kód znovu, můžete `Aquarium` zobrazit další očekávané výsledky, kde každý podporoval svou vlastní jedinečnou kolekci.  
  
 Pokud jste zvolili, aby byla vlastnost kolekce pro čtení a zápis, došlo by k nepatrné změně v tomto vzoru. V takovém případě můžete volat přístupový odkaz veřejné sady z konstruktoru provést inicializaci, <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> která by stále volání <xref:System.Windows.DependencyProperty> podpisu neklíč v rámci obálky sady, pomocí veřejného identifikátoru.  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a>Vykazování změn hodnoty vazby z vlastností kolekce  
 Vlastnost kolekce, která je sama o sobě vlastnost závislostí není automaticky hlásit změny jeho podvlastnosti. Pokud vytváříte vazby do kolekce, to může zabránit vazby z vykazování změny, tedy zrušení některých scénářů datové vazby. Pokud však použijete <xref:System.Windows.FreezableCollection%601> typ kolekce jako typ kolekce, pak dílčí vlastnost změny obsažené prvky v kolekci jsou správně hlášeny a vazba funguje podle očekávání.  
  
 Chcete-li povolit vazbu podvlastnosti v kolekci <xref:System.Windows.FreezableCollection%601>objektů závislostí, vytvořte <xref:System.Windows.DependencyObject> vlastnost kolekce jako typ s omezením typu pro tuto kolekci pro libovolnou odvozenou třídu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.FreezableCollection%601>
- [XAML a vlastní třídy pro WPF](xaml-and-custom-classes-for-wpf.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
- [Metadata vlastností závislosti](dependency-property-metadata.md)
