---
title: x:Members – direktiva
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: c751a4f1cdea8dce7ef5165f5225ab3a825c7344
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071463"
---
# <a name="xmembers-directive"></a>x:Members – direktiva
Obsahuje sadu členů, které jsou definovány ve značkách, které platí pro x:Class nadřazeného prvku.

## <a name="xaml-attribute-usage"></a>Použití atributu XAML

```xaml
<object x:Class="className">
<x:Members>
  oneOrMoreMembers
</x:Members
</object>
```

## <a name="xaml-values"></a>Hodnoty XAML

|||
|-|-|
|`className`|Název záložní třídy nebo částečné třídy pro výrobu XAML. Viz Poznámky.|
|`oneOrMoreMembers`|Jeden nebo více prvků objektu, které představují definice členů. Obvykle se jedná `x:Property` o objektové prvky. Viz Poznámky.|

## <a name="remarks"></a>Poznámky

V implementaci služby .NET XAML Services neexistuje žádná `x:Members`záložní třída nebo základní implementace člena pro . `x:Members`je speciální člen XAML, který může existovat jako člen libovolného typu. V datovém proudu uzlu `x:Members` XAML je `Members`reprezentován jako člen s názvem , z oboru názvů XAML jazyka XAML. Člen `Members` obsahuje obecný seznam `Member` objektů jen pro čtení. V typické značky jednotlivých `x:Property` členů jsou určeny jako prvky vlastností. `x:Property`je přesnější typ speciálně pro vlastnosti typů `x:Member`a je přiřaditelný . Další informace naleznete [v tématu x:Property Directive](xproperty-directive.md).

Chcete-li podporovat `x:Members` praktické použití jako prostředek k určení definice členů ve značkách, musí být členy přidruženy ke třídě, která může být změněna. Zamýšlený model je, který `x:Members` existuje jako člen typu, `x:Class`který určuje . Mechanismus pro přisuzování typů a členů nebo pro vytváření definic dynamických členů však není podporován na úrovni služby .NET XAML Services. To je ponecháno na jednotlivé architektury, které mají modely aplikací, které podporují definice členů z XAML. MSBUILD obvykle sestavení akce, které značky kompilovat XAML a buď integrovat s kódem na pozadí nebo vyrábět čisté z XAML sestavení jsou potřebné pro podporu této funkce.

## <a name="xmembers-for-windows-workflow-foundation"></a>x:Členové pro Nadaci pracovního postupu Windows

Pro Windows Workflow `x:Members` Foundation obsahuje členy vlastní aktivity složené výhradně v XAML nebo XAML definované dynamické členy pro návrháře aktivit s kódem na pozadí. `x:Class`musí být také uveden na kořenovém prvku výroby XAML. Toto není požadavek na úrovni služby .NET XAML, ale stane se požadavkem při načtení výroby XAML akcemi sestavení MSBUILD, které podporují vlastní aktivity a Windows Workflow Foundation XAML obecně. `x:Members`musí být první podřízený prvek ve značkách elementu objektu, který deklaruje `x:Class`.
