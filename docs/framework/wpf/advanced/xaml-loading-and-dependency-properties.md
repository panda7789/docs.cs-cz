---
title: Vlastnost závislostí a načítání XAML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom dependency properties [WPF]
- dependency properties [WPF], XAML loading and
- loading XML data [WPF]
ms.assetid: 6eea9f4e-45ce-413b-a266-f08238737bf2
ms.openlocfilehash: de8050e582f5b1a5a288c350c179cfa24fb5471c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186251"
---
# <a name="xaml-loading-and-dependency-properties"></a>Vlastnost závislostí a načítání XAML
Aktuální [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementace jeho [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru je ze své podstaty závislost vlastnost i vědoma. Procesor [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používá metody systému vlastností pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vlastnosti závislostí při načítání binárních a atributů zpracování, které jsou vlastnostmi závislostí. To účinně obchází obálky vlastností. Při implementaci vlastní vlastnosti závislostí, je nutné účet pro toto chování a měli byste <xref:System.Windows.DependencyObject.GetValue%2A> se <xref:System.Windows.DependencyObject.SetValue%2A>vyhnout umístění jiného kódu v obalu vlastnosti jiné než metody systému vlastností a .  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že rozumíte vlastnostem závislostí jako spotřebitel i autor a četli jste [přehled vlastností závislostí](dependency-properties-overview.md) a [vlastnosti vlastních závislostí](custom-dependency-properties.md). Měli byste také přečíst [XAML Přehled (WPF)](../../../desktop-wpf/fundamentals/xaml.md) a [XAML syntaxe podrobně](xaml-syntax-in-detail.md).  
  
<a name="implementation"></a>
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a>Implementace nakladače WPF XAML a výkon  
 Z důvodů implementace je výpočtově levnější identifikovat vlastnost jako vlastnost závislosti a přístup <xref:System.Windows.DependencyObject.SetValue%2A> k metodě systému vlastnosti k jejímu nastavení, spíše než pomocí obálky vlastnosti a jeho setter. Důvodem je, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] že procesor musí odvodit celý objektový model doprovodného kódu pouze na základě znalosti typu a vztahů členů, které jsou označeny strukturou značky a různými řetězci.  
  
 Typ je vyhledán prostřednictvím kombinace xmlns a atributy sestavení, ale identifikaci členů, určení, které by mohly podporovat nastavení jako atribut <xref:System.Reflection.PropertyInfo>a řešení, jaké typy hodnoty vlastnosti podporu by jinak vyžadovat rozsáhlé reflexe pomocí . Vzhledem k tomu, že vlastnosti závislostí na daném [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typu jsou [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] přístupné jako tabulka úložiště prostřednictvím systému vlastností, implementace <xref:System.Windows.DependencyObject.SetValue%2A> jeho procesoru <xref:System.Windows.DependencyObject> používá tuto tabulku a vyvozuje, že jakákoli daná vlastnost *ABC* může být efektivněji nastavena voláním na odvozený typ obsahující, pomocí identifikátoru vlastnosti závislostí *ABCProperty*.  
  
<a name="implications"></a>
## <a name="implications-for-custom-dependency-properties"></a>Důsledky pro vlastní vlastnosti závislostí  
 Vzhledem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] k tomu, že aktuální implementace chování procesoru [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro nastavení vlastností zcela obchází obálky, neměli byste umístit žádné další logiku do definice sady obálky pro vlastní vlastnost závislosti. Pokud vložíte tuto logiku do definice sady, pak logika nebude [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] spuštěna, když je vlastnost nastavena spíše než v kódu.  
  
 Podobně jiné aspekty procesoru, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] které získat [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] hodnoty <xref:System.Windows.DependencyObject.GetValue%2A> vlastností ze zpracování také použít spíše než pomocí obálky. Proto byste se také měli vyhnout `get` jakékoli <xref:System.Windows.DependencyObject.GetValue%2A> další implementaci v definici mimo volání.  
  
 Následující příklad je doporučená definice vlastnosti závislosti s obálkami, `public` `static` `readonly` kde je `get` `set` identifikátor vlastnosti uložen jako pole a definice a neobsahují žádný kód nad rámec nezbytných metod vlastností systému, které definují podporu vlastností závislostí.  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a>Viz také

- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Metadata vlastností závislosti](dependency-property-metadata.md)
- [Vlastnosti závislostí typu kolekce](collection-type-dependency-properties.md)
- [Zabezpečení vlastností závislosti](dependency-property-security.md)
- [Zabezpečené vzory konstruktoru pro DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md)
