---
title: x:Member – direktiva
ms.date: 03/30/2017
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
ms.openlocfilehash: e82bb6397404ee466a12ab438585ae1898c34d1a
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071470"
---
# <a name="xmember-directive"></a>x:Member – direktiva
Deklaruje člen XAML v přirážce.

## <a name="xaml-object-element-usage"></a>Použití elementu objektu XAML

```xaml
<object x:Class="className">
  <x:Members>
    <x:Member Name="propertyName"/>
    additionalMembers
  </x:Members>
</object>
```

## <a name="xaml-values"></a>Hodnoty XAML

|||
|-|-|
|`className`|Název záložní třídy nebo částečné třídy pro výrobu XAML.|
|`memberName`|Název člena definované vlastnosti.|

## <a name="remarks"></a>Poznámky

V implementaci služby .NET XAML Services . `x:Member`nemá přímý typ zálohování, ale je <xref:System.Windows.Markup.MemberDefinition> podporován třídou. V datovém proudu uzlu XAML je `x:Member` prvek `Member`reprezentován jako člen s názvem z oboru názvů XAML jazyka XAML jazyka XAML. Člen `Member` obsahuje atributy deklarované značkou.

Význam `Name` a `Type` nejsou přiřazeny na úrovni služby .NET XAML Services. Jsou uloženy v počátečním datovém proudu uzlu XAML jako řetězcové hodnoty, které mají být interpretovány později podle pravidel, která mohou být uložena konkrétními rámci. Význam může zarovnat k názvu XAML a typu XAML, což znamená nebo může být platný pouze v systému typu zálohování, v závislosti na implementaci.

Chcete-li podporovat `x:Members` praktické použití jako prostředek k určení definice členů ve značkách, musí být členy přidruženy ke třídě, která může být změněna. Zamýšlený model je, který `x:Members` existuje jako člen typu, `x:Class`který určuje . Mechanismus pro přisuzování typů a členů nebo pro vytváření definic dynamických členů však není podporován na úrovni služby .NET XAML Services. To je ponecháno na jednotlivé architektury, které mají modely aplikací, které podporují definice členů z XAML. MSBUILD obvykle sestavení akce, které značky kompilovat XAML a buď integrovat s kódem na pozadí nebo vyrábět čisté z XAML sestavení jsou potřebné pro podporu této funkce.

## <a name="xproperty-for-windows-workflow-foundation"></a>x:Vlastnost pro Nadaci pracovního postupu Windows

Pro Windows Workflow `x:Property` Foundation definuje členy vlastní aktivity složené výhradně v XAML nebo XAML definované dynamické členy pro návrháře aktivit s kódem na pozadí. `x:Class`musí být také uveden na kořenovém prvku výroby XAML. Toto není požadavek na úrovni služby .NET XAML, ale stane se požadavkem při načtení výroby XAML akcemi sestavení MSBUILD, které podporují vlastní aktivity a Windows Workflow Foundation XAML obecně. Windows Workflow Foundation nepoužívá čistý název typu XAML jako `x:Property` `Type` jeho zamýšlenou hodnotu pro atribut a místo toho používá konvenci, která zde není popsána. Další informace naleznete v tématu [DynamicActivity Creation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).
