---
title: PresentationOptions:Freeze – atribut
ms.date: 03/30/2017
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
ms.openlocfilehash: 9909a4170bdb217f91a1fc5713e89bb3a979a999
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512174"
---
# <a name="presentationoptionsfreeze-attribute"></a>PresentationOptions:Freeze – atribut
Nastaví <xref:System.Windows.Freezable.IsFrozen%2A> do stavu `true` obsahující <xref:System.Windows.Freezable> elementu. Výchozí chování <xref:System.Windows.Freezable> bez `PresentationOptions:Freeze` , který je zadán atribut <xref:System.Windows.Freezable.IsFrozen%2A> je `false` v době zatížení a závisí na Obecné <xref:System.Windows.Freezable> chování za běhu.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```  
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
|`PresentationOptions`|XML obor názvů předponu, která může být libovolný řetězec platnou předponu, podle specifikace XML 1.0. Předpona, která `PresentationOptions` se používá pro potřeby identifikace v této dokumentaci.|  
|`freezableElement`|Element, který vytvoří instanci libovolné odvozenou třídu <xref:System.Windows.Freezable>.|  
  
## <a name="remarks"></a>Poznámky  
 `Freeze` Atribut není jediným atributem nebo jiné programovací element definovaný v `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` oboru názvů XML. `Freeze` Atribut existuje v tomto oboru názvů zvláštní konkrétně tak, aby ji lze označit jako ignorable pomocí [mc: ignorable – atribut](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) jako součást deklarace kořenový element. Z důvodu, který `Freeze` musí být schopen být ignorable není protože všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementace budou moct ukotvit <xref:System.Windows.Freezable> v okamžiku načtení; tato funkce není součástí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] specifikace.  
  
 Možnost zpracování `Freeze` atribut je konkrétně součástí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor, který zpracovává [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro zkompilované aplikace. Atribut nepodporuje všechny třídy a syntaxe atributu není rozšiřitelný nebo i pro úpravy. Pokud implementujete vlastní [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru, můžete se rozhodnout paralelní zmrazení chování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru při zpracování `Freeze` atribut na <xref:System.Windows.Freezable> prvky v okamžiku načtení.  
  
 Libovolná hodnota `Freeze` jiné než atribut `true` (nerozlišuje velikost písmen) generuje chybu v době zatížení. (Zadání `Freeze` atribut jako `false` není chybu, ale to je již ve výchozím nastavení na hodnotu tak `false` nemá žádný účinek,).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Freezable>
- [Přehled zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
- [mc:Ignorable – atribut](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)
