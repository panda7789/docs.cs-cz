---
title: x:Reference – rozšíření značek
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: 960f5c0e4192df72090c1a571dfc2fc5e3fd8ba3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="xreference-markup-extension"></a>x:Reference – rozšíření značek
Odkazuje na instanci, která je deklarovaná jinde v XAML značek. Odkaz na odkazuje na element `x:Name`.  
  
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
|`instancexName`|`x:Name` Hodnotu (číslo nebo <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identifikovat vlastnost) odkazované instance.|  
  
## <a name="remarks"></a>Poznámky  
 `x:Reference` poskytuje podporu úroveň jazyka XAML pro koncept odkaz na element, které je jinak implementováno v určité rozhraní, jako je například WPF.  
  
## <a name="xreference-and-wpf"></a>x: Reference a WPF  
 WPF a XAML 2006, jsou odkazy na element řešené pomocí funkce úrovni rozhraní <xref:System.Windows.Data.Binding.ElementName%2A> vazby. Pro většinu grafického subsystému WPF aplikace a scénáře <xref:System.Windows.Data.Binding.ElementName%2A> vazba by měla používat. Výjimky pro tyto obecné pokyny mohou zahrnovat případech, kde jsou kontextu dat nebo další oboru důležité informace, které datová vazba nepraktické a kde kompilace kódu není zahrnut.  
  
 `x:Reference` je konstrukt definován v jazyce XAML 2009. V grafickém subsystému WPF můžete použít funkce jazyka XAML 2009, ale jenom pro jazyk XAML, který není WPF zkompilovat kód. Zkompilovaný kód XAML a BAML formu XAML aktuálně nepodporují klíčová slova jazyka XAML 2009 a funkce.
