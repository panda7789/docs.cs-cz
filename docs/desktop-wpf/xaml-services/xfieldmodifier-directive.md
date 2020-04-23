---
title: x:FieldModifier – direktiva
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 3e104b4c464d545e048f29901701c1c3dbb68229
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071526"
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier – direktiva
Upraví chování kompilace XAML tak, aby pole pro <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> pojmenované odkazy <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> na objekty byly definovány s přístupem namísto výchozího chování.

## <a name="xaml-attribute-usage"></a>Použití atributu XAML

```xaml
<object x:FieldModifier="Public".../>
```

## <a name="xaml-values"></a>Hodnoty XAML

|||
|-|-|
|*Veřejné*|Přesný řetězec, který <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> předáte zadat versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> se liší v závislosti na kódu na pozadí programovací jazyk, který se používá. Viz Poznámky.|

## <a name="dependencies"></a>Závislosti

 Pokud výroba XAML `x:FieldModifier` používá kdekoli, kořenový prvek této výroby XAML musí deklarovat [x:Class směrnice](xclass-directive.md).

## <a name="remarks"></a>Poznámky

`x:FieldModifier`není relevantní pro deklarování obecné úrovně přístupu třídy nebo jejích členů. Je relevantní pouze pro chování zpracování XAML při zpracování konkrétní XAML objekt, který je součástí výroby XAML a stane se objektem, který je potenciálně přístupný v grafu objektu aplikace. Ve výchozím nastavení je odkaz na pole pro takový objekt zachován jako soukromý, což brání spotřebitelům v přímé změně grafu objektu. Místo toho se očekává, že spotřebitelé ovládacího prvku upravit objekt grafu pomocí standardní vzory, které jsou povoleny programovací modely, například získáním kořen rozložení, podřízené kolekce prvků, vyhrazené veřejné vlastnosti a tak dále.

Hodnota atributu `x:FieldModifier` se liší podle programovacího jazyka a jeho účel se může lišit v konkrétních architekturách. Řetězec, který chcete použít, závisí <xref:System.CodeDom.Compiler.CodeDomProvider> na tom, jak každý jazyk implementuje jeho a převaděče typu, který vrátí k definování významů pro <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> a <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, a zda je tento jazyk rozlišována malá a velká písmena.

- Pro C#, řetězec předat <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> k `public`označení je .

- V jazyce Microsoft Visual Basic .NET <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> `Public`je řetězec, který má být určen, .

- Pro C++/CLI aktuálně neexistují žádné cíle pro XAML. proto řetězec předat není definována.

Můžete také <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> zadat`internal` ( v `Friend` jazyce C#, <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> v `NotPublic` jazyce Visual Basic), ale zadání je neobvyklé, protože jako chování je již výchozí.

<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>je výchozí chování, protože je zřídka, že kód mimo sestavení, které zkompilovalxaml potřebuje přístup k xaml-vytvořil prvek. WPF architektura zabezpečení spolu s chování kompilace XAML nedeklaruje pole, která ukládají instance prvků jako veřejné, pokud jste výslovně nastavit `x:FieldModifier` povolit veřejný přístup.

`x:FieldModifier`je relevantní pouze pro prvky s [x:Name Directive,](xname-directive.md) protože tento název se používá k odkazování na pole poté, co je veřejné.

Ve výchozím nastavení je částečná třída kořenového prvku veřejná; můžete však provést neveřejné pomocí [x:ClassModifier směrnice](xclassmodifier-directive.md). [Direktiva x:ClassModifier](xclassmodifier-directive.md) také ovlivňuje úroveň přístupu instance třídy kořenového prvku. Můžete umístit `x:Name` oba `x:FieldModifier` a na kořenový prvek, ale to pouze vytvoří kopii veřejného pole kořenový prvek, s true kořenový prvek třídy úroveň přístupu stále [řízena x:ClassModifier směrnice](xclassmodifier-directive.md).

## <a name="see-also"></a>Viz také

- [XAML a vlastní třídy pro WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [Podkladový kód a kód XAML v subsystému WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:Name – direktiva](xname-directive.md)
- [Sestavení aplikace WPF (WPF)](../../framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [x:ClassModifier – direktiva](xclassmodifier-directive.md)
