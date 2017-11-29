---
title: "x:FieldModifier – direktiva"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
caps.latest.revision: "15"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 77745744c0da1e4b4425af6d8e4319faaf524908
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier – direktiva
Mění chování kompilace XAML tak, aby definice polí pro objekt s názvem odkazy s <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> přístup místo <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> výchozí chování.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object x:FieldModifier="Public".../>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|*Veřejné*|S přesným řetězcem předat zadejte <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> se liší v závislosti na programovací jazyk kódu, který se používá. V části poznámky.|  
  
## <a name="dependencies"></a>Závislosti  
 Pokud používá provozní XAML `x:FieldModifier` kdekoli, musí deklarovat kořenový element výrobu XAML [x: Class – direktiva](../../../docs/framework/xaml-services/x-class-directive.md).  
  
## <a name="remarks"></a>Poznámky  
 `x:FieldModifier`není relevantní pro deklarování úroveň přístupu obecné třídy nebo její členy. Bylo relevantních pouze pro zpracování XAML chování při zpracování konkrétní objekt XAML, který je součástí provozní XAML a že bude objekt, který je přístupný potenciálně v grafu objektů aplikace. Ve výchozím nastavení odkaz na pole pro takový objekt se ukládají privátní, která zabraňuje řízení příjemci přímém upravování grafu objektu. Místo toho příjemci řízení očekává se, že změna grafu objektů pomocí standardní vzorů, které jsou povolené programovací modely, například získáním kořenu rozložení, podřízený element kolekcí vyhrazených veřejné vlastnosti a tak dále.  
  
 Hodnota `x:FieldModifier` atributu se liší podle programovacího jazyka a jeho účel se může lišit v konkrétní rozhraní. Řetězec, který má použít, závisí na tom, jak každý z těchto jazyků implementuje jeho <xref:System.CodeDom.Compiler.CodeDomProvider> a převaděče typů vrátí k definování významy pro <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> a <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, a jestli je tento jazyk velká a malá písmena.  
  
-   Pro [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], řetězec pro určení <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> je `public`.  
  
-   Pro [!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)], řetězec pro určení <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> je `Public`.  
  
-   Pro [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], aktuálně neexistují žádné cíle pro jazyk XAML; proto řetězec předat není definovaný.  
  
 Můžete také zadat <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> (`internal` v [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], `Friend` v [!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)]) ale zadání <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> neobvyklé protože `NotPublic` jako výchozí nastavení je již chování.  
  
 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>výchozí chování je, protože je jen zřídka, že kód mimo sestavení, které zkompilovat XAML potřebuje přístup k prvku vytvořit XAML. Architektura zabezpečení WPF společně s XAML kompilace chování nebude deklarovat pole, které ukládají element instance jako veřejné, není-li konkrétně nastavena `x:FieldModifier` umožňující veřejný přístup.  
  
 `x:FieldModifier`platí pouze pro elementy [x: Name – direktiva](../../../docs/framework/xaml-services/x-name-directive.md) protože tento název se používá k odkazování pole po veřejné.  
  
 Ve výchozím nastavení je veřejný; třídu pro kořenový element však můžete u ní nastavit neveřejní pomocí [x: ClassModifier – direktiva](../../../docs/framework/xaml-services/x-classmodifier-directive.md). [X: ClassModifier – direktiva](../../../docs/framework/xaml-services/x-classmodifier-directive.md) ovlivní také úroveň přístupu tohoto instance třídy kořenový element. Můžete vložit obě `x:Name` a `x:FieldModifier` v kořenovém elementu, ale pouze ke zkopírování veřejné pole kořenový element s true kořenový element třída úroveň přístupu stále řízené [x: ClassModifier – direktiva](../../../docs/framework/xaml-services/x-classmodifier-directive.md).  
  
## <a name="see-also"></a>Viz také  
 [XAML a vlastní třídy pro grafický subsystém WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [Kódu a XAML v grafickém subsystému WPF](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [x: Name – direktiva](../../../docs/framework/xaml-services/x-name-directive.md)  
 [Vytvoření aplikace WPF (WPF)](../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [x: ClassModifier – direktiva](../../../docs/framework/xaml-services/x-classmodifier-directive.md)
