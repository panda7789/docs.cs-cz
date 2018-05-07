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
ms.openlocfilehash: 28e121e73ad4bd8ab70aed5f651418eb309b0c03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="xaml-loading-and-dependency-properties"></a>Vlastnost závislostí a načítání XAML
Aktuální [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provádění jeho [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru je ze své podstaty vědět vlastnost závislosti. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Procesoru používá metody systému vlastností vlastností závislostí při načítání binární [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a zpracování atributy, které jsou vlastnosti závislosti. To efektivně obchází obálky vlastnost. Při implementaci vlastní závislosti vlastnosti, musí účet pro toto chování a byste neměli umístění jakýkoli jiný kód ve vaší vlastnost obálku než metody vlastností systému <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A>.  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že pochopit vlastností závislostí jak jako příjemce a autora a přečetli [přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md) a [vlastní závislosti vlastnosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md). Měli byste také mít si přečíst [přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) a [XAML syntaxe v podrobností](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
<a name="implementation"></a>   
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a>Implementace zavaděč WPF XAML a výkonu  
 Z důvodů implementace, je u levnější identifikovat vlastnost jako vlastnost závislosti a přístup k systému vlastnost <xref:System.Windows.DependencyObject.SetValue%2A> metodu a nastavit ho, místo obálku vlastnost a její setter. Důvodem je, že [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor musí odvodit celý objekt modelu kódu zálohování na základě pouze na znalost typu a členu vztahy, které jsou označeny strukturu kód a různé řetězců.  
  
 Typ je prohledávat pomocí kombinace xmlns a atributů sestavení, ale identifikace členů, určení, která by mohla podporovat, je nastaven jako atribut, a řešení, jaké typy podporují hodnoty vlastností by jinak vyžadovat rozsáhlé reflexe pomocí <xref:System.Reflection.PropertyInfo>. Vzhledem k tomu, že jsou dostupné jako tabulku úložiště pomocí vlastnosti systému, vlastností závislostí na daný typ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provádění jeho [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru na základě této tabulky a odvodí, že jakékoli zadána vlastnost *ABC* můžete nastavit efektivněji voláním <xref:System.Windows.DependencyObject.SetValue%2A> na obsahující <xref:System.Windows.DependencyObject> odvozeného typu pomocí identifikátoru vlastnosti závislosti *ABCProperty*.  
  
<a name="implications"></a>   
## <a name="implications-for-custom-dependency-properties"></a>Důsledky pro vlastní závislosti vlastnosti  
 Protože aktuální [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementace [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] chování procesoru pro nastavení vlastnosti obchází obálky zcela a veškeré další logiky nesmí put do sady definice obálku pro vlastnost vaše vlastní závislosti. Pokud vložíte tuto logiku v definici sady, pak logiku nebudou provedeny, když je vlastnost nastavena [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] spíše než v kódu.  
  
 Podobně další aspekty [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor, který získat hodnoty vlastností z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zpracování taky použití <xref:System.Windows.DependencyObject.GetValue%2A> místo pomocí obálku. Proto byste neměli také všechny další implementace v `get` definice nad rámec <xref:System.Windows.DependencyObject.GetValue%2A> volání.  
  
 Následující příklad je definice vlastnosti doporučené závislostí s obálky, se uloží identifikátor vlastnosti jako `public` `static` `readonly` pole a `get` a `set` definice neobsahují žádný kód nad rámec metody systému nezbytné vlastnosti, které definují vlastnosti závislosti zálohování.  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Metadata vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [Vlastnosti závislostí typu kolekce](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md)  
 [Zabezpečení vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-property-security.md)  
 [Zabezpečené vzory konstruktoru pro DependencyObjects](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md)
