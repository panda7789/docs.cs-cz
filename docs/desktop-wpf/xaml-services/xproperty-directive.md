---
title: x:Property – direktiva
ms.date: 03/30/2017
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
ms.openlocfilehash: 2804ec935d0626cba9ef050f70a3266cf23bcce0
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071407"
---
# <a name="xproperty-directive"></a>x:Property – direktiva

Deklaruje vlastnost XAML ve značkách.

## <a name="xaml-object-element-usage"></a>Použití elementu objektu XAML

```xaml
<object x:Class="className">
  <x:Members>
    <x:Property Name="propertyName" Type="propertyType"/>
    additionalProperties
  </x:Members>
</object>
```

## <a name="xaml-values"></a>Hodnoty XAML

|||
|-|-|
|`className`|Název záložní třídy nebo částečné třídy pro výrobu XAML.|
|`propertyName`|Název člena definované vlastnosti.|
|`propertyType`|Název typu (nebo jiný řetězec formuláře, specifické pro architekturu), který určuje typ této vlastnosti.|

## <a name="remarks"></a>Poznámky

V implementaci služby .NET XAML Services . `x:Property`nemá přímý typ zálohování, ale je <xref:System.Windows.Markup.PropertyDefinition> podporován třídou. V datovém proudu uzlu XAML je `x:Property` prvek `Property`reprezentován jako člen s názvem z oboru názvů XAML jazyka XAML jazyka XAML. Člen `Property` hold atributy deklarované značky.

Význam `Name` a `Type` nejsou přiřazeny na úrovni služby .NET XAML Services. Jsou uloženy v počátečním datovém proudu uzlu XAML jako řetězcové hodnoty, které mají být interpretovány později podle pravidel, která mohou být uložena konkrétními rámci. Význam může zarovnat k názvu XAML a typu XAML, což znamená nebo může být platný pouze v systému typu zálohování, v závislosti na implementaci.

Chcete-li podporovat `x:Members` praktické použití jako prostředek k určení definice členů ve značkách, musí být členy přidruženy ke třídě, která může být změněna. Zamýšlený model je, který `x:Members` existuje jako člen typu, `x:Class`který určuje . Mechanismus pro přisuzování typů a členů nebo pro vytváření definic dynamických členů však není podporován na úrovni služby .NET XAML Services. To je ponecháno na jednotlivé architektury, které mají modely aplikací, které podporují definice členů z XAML. MSBUILD obvykle sestavení akce, které značky kompilovat XAML a buď integrovat s kódem na pozadí nebo vyrábět čisté z XAML sestavení jsou potřebné pro podporu této funkce.

## <a name="xproperty-for-windows-workflow-foundation"></a>x:Vlastnost pro Nadaci pracovního postupu Windows

Pro Windows Workflow `x:Property` Foundation definuje členy vlastní aktivity složené výhradně v XAML nebo XAML definované dynamické členy pro návrháře aktivit s kódem na pozadí. `x:Class`musí být také uveden na kořenovém prvku výroby XAML. Toto není požadavek na úrovni služby .NET XAML, ale stane se požadavkem při načtení výroby XAML akcemi sestavení MSBUILD, které podporují vlastní aktivity a Windows Workflow Foundation XAML obecně. Windows Workflow Foundation nepoužívá čistý název typu XAML jako `x:Property` `Type` jeho zamýšlenou hodnotu pro atribut a místo toho používá konvenci, která zde není popsána. Další informace naleznete v tématu [DynamicActivity Creation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).
