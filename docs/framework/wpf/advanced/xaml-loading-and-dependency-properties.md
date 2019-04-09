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
ms.openlocfilehash: 4db87c5f266a9eed136f0651f48d11720abede65
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083828"
---
# <a name="xaml-loading-and-dependency-properties"></a>Vlastnost závislostí a načítání XAML
Aktuální [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provádění jeho [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru je ze své podstaty používající vlastnost závislosti. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Procesor při načítání binární soubor používá metody vlastností systému pro vlastnosti závislosti [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a při zpracovávání atributů, které jsou vlastnosti závislosti. To efektivně obchází vlastnost obálky. Pokud implementujete vlastní vlastnosti závislosti, musí odpovídat tomuto chování a by měl předejde jakýkoli jiný kód v vaši Obálka vlastnosti než metody vlastností systému <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A>.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že pochopit vlastnosti závislostí i jako příjemce a Autor a přečetl [přehled vlastností závislosti](dependency-properties-overview.md) a [vlastní vlastnosti závislosti](custom-dependency-properties.md). Doporučujeme mít přečíst [přehled XAML (WPF)](xaml-overview-wpf.md) a [syntaxe XAML v podrobnosti o](xaml-syntax-in-detail.md).  
  
<a name="implementation"></a>   
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a>Implementace zavaděč WPF XAML a výkonu  
 Z důvodu implementace, je výpočetně levnější k identifikaci vlastnost jako vlastnost závislosti a přístupu v systému vlastností <xref:System.Windows.DependencyObject.SetValue%2A> metody nastavte ho, spíš než obálka vlastnosti a její metody setter. Důvodem je, že [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru musí odvodit celý objekt modelu kódu zálohování založen pouze na vztahy, které jsou označeny konstrukcí kódu a různých řetězců znalost typů a členů.  
  
 Typ se hledá pomocí kombinace xmlns a atributy sestavení, ale členů určující, které můžou podporovat i nastavena jako atribut, identifikace a řešení, jaké typy, které podporují hodnoty vlastností by jinak vyžadují rozsáhlé reflexe pomocí <xref:System.Reflection.PropertyInfo>. Protože jsou k dispozici jako úložiště tabulky prostřednictvím vlastnosti systému, vlastnosti závislosti na daný typ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provádění jeho [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor používá tuto tabulku a odvodí z něj všechny zadané vlastnosti *ABC* můžete nastavit efektivněji voláním <xref:System.Windows.DependencyObject.SetValue%2A> obsahující <xref:System.Windows.DependencyObject> odvozeného typu, pomocí identifikátoru vlastnosti závislosti *ABCProperty*.  
  
<a name="implications"></a>   
## <a name="implications-for-custom-dependency-properties"></a>Důsledky pro vlastní vlastnosti závislosti  
 Protože aktuální [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provádění [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] chování procesoru pro nastavení vlastnosti obchází obálkami úplně, žádná další logika by neměl umístit do definice sady obálky pro vaše vlastní závislost vlastnost. Pokud vložíte tuto logiku v definici sady a potom logiku nebude provedeno, když je nastavena [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] spíše než v kódu.  
  
 Podobně, pracovat s dalšími aspekty [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor, který získat hodnoty vlastností z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zpracování také použití <xref:System.Windows.DependencyObject.GetValue%2A> místo použití obálky. Proto byste se měli také vyhnout jakékoli další použití v `get` definice nad rámec <xref:System.Windows.DependencyObject.GetValue%2A> volání.  
  
 V následujícím příkladu je definice vlastnosti doporučené závislostí s obálky, identifikátor vlastnosti se mají ukládat jako `public` `static` `readonly` pole a `get` a `set` definice neobsahují žádný kód nad rámec metod systém nezbytné vlastnosti, které definují vlastnosti závislosti zálohování.  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Přehled XAML (WPF)](xaml-overview-wpf.md)
- [Metadata vlastností závislosti](dependency-property-metadata.md)
- [Vlastnosti závislostí typu kolekce](collection-type-dependency-properties.md)
- [Zabezpečení vlastností závislosti](dependency-property-security.md)
- [Zabezpečené vzory konstruktoru pro DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md)
