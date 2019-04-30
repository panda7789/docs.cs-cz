---
title: x:Reference – rozšíření značek
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: 960f5c0e4192df72090c1a571dfc2fc5e3fd8ba3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938876"
---
# <a name="xreference-markup-extension"></a>x:Reference – rozšíření značek
Odkazuje na instanci, která je někde jinde deklarovaný ve značkách XAML. Odkaz na odkazuje na element `x:Name`.  
  
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
|`instancexName`|`x:Name` Hodnotu (nebo hodnota <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identifikované vlastnosti) odkazované instance.|  
  
## <a name="remarks"></a>Poznámky  
 `x:Reference` poskytuje podporu na úrovni jazyka XAML pro pojem referenční dokumentace elementu, jinak implementovaný v konkrétní architektury, jako jsou WPF.  
  
## <a name="xreference-and-wpf"></a>x: Reference a WPF  
 V XAML 2006 a WPF, odkazy na prvky se tak vyřeší, funkce úrovni architektury <xref:System.Windows.Data.Binding.ElementName%2A> vazby. Pro většinu aplikací WPF a scénáře <xref:System.Windows.Data.Binding.ElementName%2A> vazba by měla i nadále sloužit. Výjimky z této obecné pokyny mohou zahrnovat případy, kde jsou kontext dat nebo jiných oborů aspekty, které usnadňují vytváření datových vazeb nepraktické a není součástí kompilace označení.  
  
 `x:Reference` použít konstrukce definované v XAML 2009. V WPF můžete použít funkce XAML 2009, ale pouze pro XAML, který není kompilována značka WPF. Kompilována značka XAML a formulář BAML z XAML aktuálně nepodporují klíčová slova jazyka XAML 2009 a funkce.
