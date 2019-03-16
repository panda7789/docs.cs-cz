---
title: x:FieldModifier – direktiva
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 27ff9d027f5ff5155543097b7f0f0c2839387fe5
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2019
ms.locfileid: "58042448"
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier – direktiva
Upravuje chování sestavení XAML, takže pole pro odkazy na pojmenované objekty jsou definovány pomocí <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> přístup místo <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> výchozí chování.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object x:FieldModifier="Public".../>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|*Public*|Přesná předáte k určení <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> oproti <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> se liší v závislosti na použití modelu code-behind programovací jazyk, který se používá. Viz poznámky.|  
  
## <a name="dependencies"></a>Závislosti  
 Pokud používáte produkční XAML `x:FieldModifier` kdekoli, musí deklarovat kořenový prvek XAML výrobu [x: Class – direktiva](x-class-directive.md).  
  
## <a name="remarks"></a>Poznámky  
 `x:FieldModifier` není relevantní pro deklarování úroveň přístupu obecné třídy nebo její členy. Je relevantní pouze pro zpracování XAML chování při určitý objekt XAML, který je součástí výroby XAML zpracování a bude objekt, který je potenciálně nelze v grafu objektů aplikace. Ve výchozím nastavení referenční dokumentace polí pro takový objekt se ukládají privátní, která zabraňuje ovládacího prvku spotřebitele Úprava objektu grafu přímo. Místo toho ovládacího prvku spotřebitele se očekává, že upravit graf objektu pomocí standardní vzory, které jsou povolené pomocí programovacích modelů, jako například získáním kořenové rozložení podřízený prvek kolekce, vyhrazené veřejné vlastnosti a tak dále.  
  
 Hodnota `x:FieldModifier` atributu se liší podle programovací jazyk a jejím účelem se může lišit v konkrétní rozhraní. Řetězec, který má použít, závisí na způsob implementace každý jazyk jeho <xref:System.CodeDom.Compiler.CodeDomProvider> a vrátí k definování význam pro typ převaděče <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> a <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, a zda je daný jazyk malá a velká písmena.  
  
-   Pro jazyk C#, řetězec, který má předat určit <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> je `public`.  
  
-   Pro Microsoft Visual Basic .NET, řetězec, který má předat určit <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> je `Public`.  
  
-   Pro [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], aktuálně neexistují žádné cíle pro XAML, proto není definováno řetězec, který má předat.  
  
 Můžete také určit <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> (`internal` v C#, `Friend` v jazyce Visual Basic) ale zadat <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> neobvyklá protože `NotPublic` je již výchozí chování.  
  
 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> je výchozí chování, protože je zřídka, že kód mimo sestavení, který zkompiluje XAML potřebuje přístup k prvku XAML vytvořit. Architektura WPF zabezpečení spolu s chování kompilace XAML nebude deklarovat pole, které ukládají instance elementu jako veřejné, pokud je výslovně nastavit `x:FieldModifier` umožní veřejný přístup.  
  
 `x:FieldModifier` platí pouze pro elementy se [x: Name – direktiva](x-name-directive.md) protože tento název slouží jako odkaz pole poté, co je veřejný.  
  
 Ve výchozím nastavení je veřejný; částečné třídy pro kořenový element ale můžete si je neveřejné pomocí [x: ClassModifier – direktiva](x-classmodifier-directive.md). [X: ClassModifier – direktiva](x-classmodifier-directive.md) ovlivní také úroveň přístupu je instance třídy kořenový element. Můžete umístit i `x:Name` a `x:FieldModifier` v kořenovém adresáři element, ale pouze ke zkopírování veřejné pole kořenový element s true kořenový element třídy úroveň přístupu stále řídí [x: ClassModifier – direktiva](x-classmodifier-directive.md).  
  
## <a name="see-also"></a>Viz také:
- [XAML a vlastní třídy pro WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [Podkladový kód a kód XAML v subsystému WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:Name – direktiva](x-name-directive.md)
- [Sestavení aplikace WPF (WPF)](../wpf/app-development/building-a-wpf-application-wpf.md)
- [x:ClassModifier – direktiva](x-classmodifier-directive.md)
