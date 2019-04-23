---
title: PresentationOptions:Freeze – atribut
ms.date: 03/30/2017
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
ms.openlocfilehash: e60c4a505db42936f188354f52edd7832fb9632b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074654"
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
 `Freeze` Atribut není jediným atributem nebo jiné programovací element definovaný v `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` oboru názvů XML. `Freeze` Atribut existuje v tomto oboru názvů zvláštní konkrétně tak, aby ji lze označit jako ignorable pomocí [mc: ignorable – atribut](mc-ignorable-attribute.md) jako součást deklarace kořenový element. Z důvodu, který `Freeze` musí být schopen být ignorable není protože všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementace budou moct ukotvit <xref:System.Windows.Freezable> v okamžiku načtení; tato funkce není součástí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] specifikace.  
  
 Možnost zpracování `Freeze` atribut je konkrétně součástí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor, který zpracovává [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro zkompilované aplikace. Atribut nepodporuje všechny třídy a syntaxe atributu není rozšiřitelný nebo i pro úpravy. Pokud implementujete vlastní [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru, můžete se rozhodnout paralelní zmrazení chování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru při zpracování `Freeze` atribut na <xref:System.Windows.Freezable> prvky v okamžiku načtení.  
  
 Libovolná hodnota `Freeze` jiné než atribut `true` (nerozlišuje velikost písmen) generuje chybu v době zatížení. (Zadání `Freeze` atribut jako `false` není chybu, ale to je již ve výchozím nastavení na hodnotu tak `false` nemá žádný účinek,).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Freezable>
- [Přehled zablokovatelných objektů](freezable-objects-overview.md)
- [mc:Ignorable – atribut](mc-ignorable-attribute.md)
