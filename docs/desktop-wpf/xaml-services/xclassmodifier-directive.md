---
title: x:ClassModifier – direktiva
ms.date: 03/30/2017
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
ms.openlocfilehash: 436204774c2d59b43a77865c666aed702f7681db
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072030"
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier – direktiva
Upravuje chování kompilace XAML, pokud `x:Class` je také k dispozici. Konkrétně namísto vytvoření `class` částečné, `Public` který má úroveň přístupu `x:Class` (výchozí), `NotPublic` za předpokladu, je vytvořen s úrovní přístupu. Toto chování ovlivňuje úroveň přístupu pro třídu ve vygenerovaných sestaveních.

## <a name="xaml-attribute-usage"></a>Použití atributu XAML

```xaml
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">
   ...
</object>
```

## <a name="xaml-values"></a>Hodnoty XAML

|||
|-|-|
|*Není veřejná*|Přesný řetězec předat zadat <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> versus se liší v závislosti na kód na pozadí programovací jazyk, který používáte. Viz Poznámky.|

## <a name="dependencies"></a>Závislosti

[x:Class](xclass-directive.md) musí být také k dispozici na stejný prvek a tento prvek musí být kořenový prvek na stránce. Další informace naleznete [ \[v oddíle\] 4.3.1.8 ms-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="remarks"></a>Poznámky

Hodnota `x:ClassModifier` v .NET XAML Services využití se liší podle programovacího jazyka. Řetězec, který chcete použít, závisí <xref:System.CodeDom.Compiler.CodeDomProvider> na tom, jak každý jazyk implementuje jeho a převaděče typu, který vrátí k definování významů pro <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> a <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, a zda je tento jazyk rozlišována malá a velká písmena.

- Pro C#, řetězec předat <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> k `internal`označení je .

- V jazyce Microsoft Visual Basic .NET <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> `Friend`je řetězec, který má být určen, .

- Pro C++/CLI neexistují žádné cíle, které podporují kompilaci XAML; proto hodnota předat není zadán.

Můžete také <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> zadat`public` ( v `Public` jazyce C#, v jazyce Visual Basic); však zadání <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> se zřídka provádí, protože <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> je již výchozí chování.

Jiné hodnoty s ekvivalentní omezení přístupové `private` úrovně uživatelského kódu, `x:ClassModifier` například v c#, nejsou relevantní, protože vnořené odkazy na třídy nejsou v XAML podporovány, a proto má <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifikátor stejný účinek.

## <a name="security-notes"></a>Bezpečnostní poznámky

Úroveň přístupu uvedená v `x:ClassModifier` písmenu a) je stále předmětem výkladu konkrétními rámci a jejich schopnostmi. WPF zahrnuje možnosti načíst a `x:ClassModifier` vytvořit `internal`instanci typů, kde je , pokud je tato třída odkazována z prostředku WPF prostřednictvím odkazu URI balíčku. V důsledku tohoto případu a potenciálně dalších, jako je implementováno `x:ClassModifier` jinými rámci, se nespoléhají výhradně na blokování všech možných pokusů o vytvoření instance.

## <a name="see-also"></a>Viz také

- [x:Class – direktiva](xclass-directive.md)
- [Podkladový kód a kód XAML v subsystému WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:FieldModifier – direktiva](xfieldmodifier-directive.md)
- [Zabezpečení (WPF)](../../framework/wpf/security-wpf.md)
- [Typy migrované z prostředí WPF do oboru názvů System.Xaml](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
