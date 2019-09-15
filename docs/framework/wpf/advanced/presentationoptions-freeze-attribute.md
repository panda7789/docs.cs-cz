---
title: PresentationOptions:Freeze – atribut
ms.date: 03/30/2017
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
ms.openlocfilehash: d3e0cee293a9585b972b0145da953976ed94b74c
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991431"
---
# <a name="presentationoptionsfreeze-attribute"></a>PresentationOptions:Freeze – atribut
<xref:System.Windows.Freezable.IsFrozen%2A> Nastaví stav`true` na obsahující<xref:System.Windows.Freezable> element. Výchozí <xref:System.Windows.Freezable> chování pro atributbezzadaného<xref:System.Windows.Freezable.IsFrozen%2A> atributu je <xref:System.Windows.Freezable> v době načítání a závisí na obecném chování za běhu. `false` `PresentationOptions:Freeze`  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`PresentationOptions`|Předpona oboru názvů XML, což může být libovolný platný řetězec předpony podle specifikace XML 1,0. Předpona `PresentationOptions` se používá pro účely identifikace v této dokumentaci.|  
|`freezableElement`|Prvek, který vytváří instanci jakékoli odvozené třídy <xref:System.Windows.Freezable>.|  
  
## <a name="remarks"></a>Poznámky  
 Atribut je jediný atribut nebo jiný programovací element definovaný `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` v oboru názvů XML. `Freeze` Atribut existuje v tomto speciálním oboru názvů konkrétně tak, aby jej bylo možné označit [jako ignorovatelné jako součást](mc-ignorable-attribute.md) deklarací kořenových elementů. `Freeze` Důvod, který `Freeze` musí být možné ignorovat, je, protože ne všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementace procesoru <xref:System.Windows.Freezable> jsou schopné ukotvit během načítání [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ; Tato funkce není součástí specifikace.  
  
 Schopnost zpracovat `Freeze` atribut je speciálně integrovaná [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro procesor, který zpracovává [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zkompilované aplikace. Atribut není podporován žádnou třídou a syntaxe atributu není rozšiřitelná nebo upravitelná. Pokud implementujete [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vlastní procesor, můžete zvolit paralelní chování [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesoru při zpracování `Freeze` atributu v <xref:System.Windows.Freezable> prvcích v době načítání.  
  
 Libovolná hodnota atributu `Freeze` s `true` výjimkou (bez rozlišování malých a velkých písmen) generuje chybu při načítání. (Určení `Freeze` atributu jako `false` není chyba, ale to je již `false` výchozí, takže nastavení nedělá nic).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Freezable>
- [Přehled zablokovatelných objektů](freezable-objects-overview.md)
- [mc:Ignorable – atribut](mc-ignorable-attribute.md)
