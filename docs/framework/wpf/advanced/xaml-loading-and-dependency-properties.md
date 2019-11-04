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
ms.openlocfilehash: 57c25297f995acd1ef307466258b5f4e03cc3098
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459542"
---
# <a name="xaml-loading-and-dependency-properties"></a>Vlastnost závislostí a načítání XAML
Aktuální [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementace jeho [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru je podstatou závislá na vlastnostech. Procesor [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] při načítání binárních [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a zpracování atributů, které jsou vlastnostmi závislosti, používá systémové metody vlastností pro vlastnosti závislosti. To efektivně obchází obálky vlastností. Když implementujete vlastní vlastnosti závislosti, je nutné, abyste se přihlédli k tomuto chování a neměli byste zacházet s vložením dalšího kódu do obálky vlastností, která je jiná než metody systému vlastností <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A>.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu se předpokládá, že porozumíte vlastnostem závislosti jak pro uživatele, tak pro autora a máte [Přehled vlastností závislosti](dependency-properties-overview.md) čtení a [vlastní vlastnosti závislostí](custom-dependency-properties.md). Měli byste také podrobně přečíst [přehledy jazyka XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) a [syntaxi XAML](xaml-syntax-in-detail.md).  
  
<a name="implementation"></a>   
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a>Implementace zavaděče XAML pro WPF a výkon  
 Z důvodů implementace je výpočetně levnější určit vlastnost jako vlastnost závislosti a získat přístup k metodě systému vlastností <xref:System.Windows.DependencyObject.SetValue%2A> k jejímu nastavení namísto použití obálky vlastností a její metody setter. Důvodem je, že procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] musí odvodit celý objektový model pro zálohovaný kód pouze na vědomí typu a členů vztahů, které jsou označeny strukturou značky a různými řetězci.  
  
 Typ je vyhledán kombinací atributů xmlns a Assembly, ale Identifikujte členy, určíte, které by mohly podporovat nastavování jako atribut, a řešení, které typy podporují, jinak vyžadovat velký odraz. použití <xref:System.Reflection.PropertyInfo>. Vzhledem k tomu, že vlastnosti závislosti daného typu jsou přístupné jako tabulka úložiště prostřednictvím systému vlastností, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementace jeho [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru používá tuto tabulku a odvodí, že je možné tuto vlastnost *ABC* efektivněji nastavit pomocí volání <xref:System.Windows.DependencyObject.SetValue%2A> u obsahujícího typu odvozené <xref:System.Windows.DependencyObject> pomocí identifikátoru vlastnosti závislosti *ABCProperty*.  
  
<a name="implications"></a>   
## <a name="implications-for-custom-dependency-properties"></a>Důsledky pro vlastní vlastnosti závislosti  
 Vzhledem k tomu, že aktuální implementace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] chování procesoru [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro nastavení vlastností obchází obálky zcela, neměli byste do definice sady pro vlastní vlastnost závislosti vkládat žádné další logiky. Pokud tuto logiku vložíte do definice sady, pak nebude logika provedena, pokud je vlastnost nastavena v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] spíše než v kódu.  
  
 Podobně další aspekty [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru, které získávají hodnoty vlastností ze zpracování [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] také používají <xref:System.Windows.DependencyObject.GetValue%2A> místo použití obálky. Proto byste se měli také vyhnout jakékoli další implementaci v definici `get` mimo volání <xref:System.Windows.DependencyObject.GetValue%2A>.  
  
 V následujícím příkladu je doporučena definice vlastnosti závislosti s obálkami, kde je identifikátor vlastnosti uložen jako `public` `static` `readonly` pole a definice `get` a `set` neobsahují žádný kód nad potřebnou vlastností. systémové metody, které definují vlastnost závislosti, se zálohuje.  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Metadata vlastností závislosti](dependency-property-metadata.md)
- [Vlastnosti závislostí typu kolekce](collection-type-dependency-properties.md)
- [Zabezpečení vlastností závislosti](dependency-property-security.md)
- [Zabezpečené vzory konstruktoru pro DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md)
