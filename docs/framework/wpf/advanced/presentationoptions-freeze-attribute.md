---
title: PresentationOptions:Freeze – atribut
ms.date: 03/30/2017
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
ms.openlocfilehash: e60c4a505db42936f188354f52edd7832fb9632b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772837"
---
# <a name="presentationoptionsfreeze-attribute"></a><span data-ttu-id="d09b8-102">PresentationOptions:Freeze – atribut</span><span class="sxs-lookup"><span data-stu-id="d09b8-102">PresentationOptions:Freeze Attribute</span></span>
<span data-ttu-id="d09b8-103">Nastaví <xref:System.Windows.Freezable.IsFrozen%2A> do stavu `true` obsahující <xref:System.Windows.Freezable> elementu.</span><span class="sxs-lookup"><span data-stu-id="d09b8-103">Sets the <xref:System.Windows.Freezable.IsFrozen%2A> state to `true` on the containing <xref:System.Windows.Freezable> element.</span></span> <span data-ttu-id="d09b8-104">Výchozí chování <xref:System.Windows.Freezable> bez `PresentationOptions:Freeze` , který je zadán atribut <xref:System.Windows.Freezable.IsFrozen%2A> je `false` v době zatížení a závisí na Obecné <xref:System.Windows.Freezable> chování za běhu.</span><span class="sxs-lookup"><span data-stu-id="d09b8-104">Default behavior for a <xref:System.Windows.Freezable> without the `PresentationOptions:Freeze` attribute specified is that <xref:System.Windows.Freezable.IsFrozen%2A> is `false` at load time, and dependent on general <xref:System.Windows.Freezable> behavior at runtime.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="d09b8-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="d09b8-105">XAML Attribute Usage</span></span>  
  
```  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="d09b8-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="d09b8-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`PresentationOptions`|<span data-ttu-id="d09b8-107">XML obor názvů předponu, která může být libovolný řetězec platnou předponu, podle specifikace XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="d09b8-107">An XML namespace prefix, which can be any valid prefix string, per the XML 1.0 specification.</span></span> <span data-ttu-id="d09b8-108">Předpona, která `PresentationOptions` se používá pro potřeby identifikace v této dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="d09b8-108">The prefix `PresentationOptions` is used for identification purposes in this documentation.</span></span>|  
|`freezableElement`|<span data-ttu-id="d09b8-109">Element, který vytvoří instanci libovolné odvozenou třídu <xref:System.Windows.Freezable>.</span><span class="sxs-lookup"><span data-stu-id="d09b8-109">An element that instantiates any derived class of <xref:System.Windows.Freezable>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d09b8-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d09b8-110">Remarks</span></span>  
 <span data-ttu-id="d09b8-111">`Freeze` Atribut není jediným atributem nebo jiné programovací element definovaný v `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="d09b8-111">The `Freeze` attribute is the only attribute or other programming element defined in the `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML namespace.</span></span> <span data-ttu-id="d09b8-112">`Freeze` Atribut existuje v tomto oboru názvů zvláštní konkrétně tak, aby ji lze označit jako ignorable pomocí [mc: ignorable – atribut](mc-ignorable-attribute.md) jako součást deklarace kořenový element.</span><span class="sxs-lookup"><span data-stu-id="d09b8-112">The `Freeze` attribute exists in this special namespace specifically so that it can be designated as ignorable, using [mc:Ignorable Attribute](mc-ignorable-attribute.md) as part of the root element declarations.</span></span> <span data-ttu-id="d09b8-113">Z důvodu, který `Freeze` musí být schopen být ignorable není protože všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementace budou moct ukotvit <xref:System.Windows.Freezable> v okamžiku načtení; tato funkce není součástí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] specifikace.</span><span class="sxs-lookup"><span data-stu-id="d09b8-113">The reason that `Freeze` must be able to be ignorable is because not all [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementations are able to freeze a <xref:System.Windows.Freezable> at load time; this capability is not part of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] specification.</span></span>  
  
 <span data-ttu-id="d09b8-114">Možnost zpracování `Freeze` atribut je konkrétně součástí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor, který zpracovává [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro zkompilované aplikace.</span><span class="sxs-lookup"><span data-stu-id="d09b8-114">The ability to process the `Freeze` attribute is specifically built in to the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor that processes [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for compiled applications.</span></span> <span data-ttu-id="d09b8-115">Atribut nepodporuje všechny třídy a syntaxe atributu není rozšiřitelný nebo i pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="d09b8-115">The attribute is not supported by any class, and the attribute syntax is not extensible or modifiable.</span></span> <span data-ttu-id="d09b8-116">Pokud implementujete vlastní [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru, můžete se rozhodnout paralelní zmrazení chování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru při zpracování `Freeze` atribut na <xref:System.Windows.Freezable> prvky v okamžiku načtení.</span><span class="sxs-lookup"><span data-stu-id="d09b8-116">If you are implementing your own [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor you can choose to parallel the freezing behavior of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor when processing the `Freeze` attribute on <xref:System.Windows.Freezable> elements at load time.</span></span>  
  
 <span data-ttu-id="d09b8-117">Libovolná hodnota `Freeze` jiné než atribut `true` (nerozlišuje velikost písmen) generuje chybu v době zatížení.</span><span class="sxs-lookup"><span data-stu-id="d09b8-117">Any value for the `Freeze` attribute other than `true` (not case sensitive) generates a load time error.</span></span> <span data-ttu-id="d09b8-118">(Zadání `Freeze` atribut jako `false` není chybu, ale to je již ve výchozím nastavení na hodnotu tak `false` nemá žádný účinek,).</span><span class="sxs-lookup"><span data-stu-id="d09b8-118">(Specifying the `Freeze` attribute as `false` is not an error, but that is already the default, so setting to `false` does nothing).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d09b8-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d09b8-119">See also</span></span>

- <xref:System.Windows.Freezable>
- [<span data-ttu-id="d09b8-120">Přehled zablokovatelných objektů</span><span class="sxs-lookup"><span data-stu-id="d09b8-120">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="d09b8-121">mc:Ignorable – atribut</span><span class="sxs-lookup"><span data-stu-id="d09b8-121">mc:Ignorable Attribute</span></span>](mc-ignorable-attribute.md)
