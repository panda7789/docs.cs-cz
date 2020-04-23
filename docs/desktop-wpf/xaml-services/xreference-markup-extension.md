---
title: x:Reference – rozšíření značek
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: f06e259893111a436e5afe2df754c3edee326d54
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071379"
---
# <a name="xreference-markup-extension"></a>x:Reference – rozšíření značek

Odkazuje na instanci, která je deklarována jinde ve značkách XAML. Odkaz odkazuje na prvek `x:Name`.

## <a name="xaml-attribute-usage"></a>Použití atributu XAML

```xaml
<object property="{x:Reference instancexName}" .../>
```

## <a name="xaml-object-element-usage"></a>Použití elementu objektu XAML

```xaml
<object>
  <object.property>
    <x:Reference Name="instancexName"/>
  </object.property>
</object>
```

## <a name="xaml-values"></a>Hodnoty XAML

|||
|-|-|
|`instancexName`|Hodnota `x:Name` (nebo hodnota <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identified vlastnost) odkazované instance.|

## <a name="remarks"></a>Poznámky

`x:Reference`poskytuje podporu na jazykové úrovni XAML pro koncept odkazu na prvek, který byl jinak implementován v konkrétních architekturách, jako je WPF.

## <a name="xreference-and-wpf"></a>x:Reference a WPF

V WPF a XAML 2006 jsou odkazy na element y <xref:System.Windows.Data.Binding.ElementName%2A> adresovány funkcí vazby na úrovni rozhraní. Pro většinu wpf aplikací <xref:System.Windows.Data.Binding.ElementName%2A> a scénářů by měla být stále použita vazba. Výjimky z těchto obecných pokynů mohou zahrnovat případy, kdy existují kontext dat nebo jiné aspekty oboru, které činí vazbu dat nepraktickou a kde se nejedná o kompilaci značek.

`x:Reference`je konstrukce definovaná v XAML 2009. V WPF můžete použít funkce XAML 2009, ale pouze pro XAML, který není wpf zkompilovaný značky. KódXAML zkompilovaný značkami a forma XAML BAML aktuálně nepodporují klíčová slova a funkce jazyka XAML 2009.
