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
# <a name="presentationoptionsfreeze-attribute"></a><span data-ttu-id="60573-102">PresentationOptions:Freeze – atribut</span><span class="sxs-lookup"><span data-stu-id="60573-102">PresentationOptions:Freeze Attribute</span></span>
<span data-ttu-id="60573-103"><xref:System.Windows.Freezable.IsFrozen%2A> Nastaví stav`true` na obsahující<xref:System.Windows.Freezable> element.</span><span class="sxs-lookup"><span data-stu-id="60573-103">Sets the <xref:System.Windows.Freezable.IsFrozen%2A> state to `true` on the containing <xref:System.Windows.Freezable> element.</span></span> <span data-ttu-id="60573-104">Výchozí <xref:System.Windows.Freezable> chování pro atributbezzadaného<xref:System.Windows.Freezable.IsFrozen%2A> atributu je <xref:System.Windows.Freezable> v době načítání a závisí na obecném chování za běhu. `false` `PresentationOptions:Freeze`</span><span class="sxs-lookup"><span data-stu-id="60573-104">Default behavior for a <xref:System.Windows.Freezable> without the `PresentationOptions:Freeze` attribute specified is that <xref:System.Windows.Freezable.IsFrozen%2A> is `false` at load time, and dependent on general <xref:System.Windows.Freezable> behavior at runtime.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="60573-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="60573-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="60573-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="60573-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`PresentationOptions`|<span data-ttu-id="60573-107">Předpona oboru názvů XML, což může být libovolný platný řetězec předpony podle specifikace XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="60573-107">An XML namespace prefix, which can be any valid prefix string, per the XML 1.0 specification.</span></span> <span data-ttu-id="60573-108">Předpona `PresentationOptions` se používá pro účely identifikace v této dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="60573-108">The prefix `PresentationOptions` is used for identification purposes in this documentation.</span></span>|  
|`freezableElement`|<span data-ttu-id="60573-109">Prvek, který vytváří instanci jakékoli odvozené třídy <xref:System.Windows.Freezable>.</span><span class="sxs-lookup"><span data-stu-id="60573-109">An element that instantiates any derived class of <xref:System.Windows.Freezable>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60573-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="60573-110">Remarks</span></span>  
 <span data-ttu-id="60573-111">Atribut je jediný atribut nebo jiný programovací element definovaný `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` v oboru názvů XML. `Freeze`</span><span class="sxs-lookup"><span data-stu-id="60573-111">The `Freeze` attribute is the only attribute or other programming element defined in the `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML namespace.</span></span> <span data-ttu-id="60573-112">Atribut existuje v tomto speciálním oboru názvů konkrétně tak, aby jej bylo možné označit [jako ignorovatelné jako součást](mc-ignorable-attribute.md) deklarací kořenových elementů. `Freeze`</span><span class="sxs-lookup"><span data-stu-id="60573-112">The `Freeze` attribute exists in this special namespace specifically so that it can be designated as ignorable, using [mc:Ignorable Attribute](mc-ignorable-attribute.md) as part of the root element declarations.</span></span> <span data-ttu-id="60573-113">Důvod, který `Freeze` musí být možné ignorovat, je, protože ne všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementace procesoru <xref:System.Windows.Freezable> jsou schopné ukotvit během načítání [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ; Tato funkce není součástí specifikace.</span><span class="sxs-lookup"><span data-stu-id="60573-113">The reason that `Freeze` must be able to be ignorable is because not all [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementations are able to freeze a <xref:System.Windows.Freezable> at load time; this capability is not part of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] specification.</span></span>  
  
 <span data-ttu-id="60573-114">Schopnost zpracovat `Freeze` atribut je speciálně integrovaná [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro procesor, který zpracovává [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zkompilované aplikace.</span><span class="sxs-lookup"><span data-stu-id="60573-114">The ability to process the `Freeze` attribute is specifically built in to the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor that processes [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for compiled applications.</span></span> <span data-ttu-id="60573-115">Atribut není podporován žádnou třídou a syntaxe atributu není rozšiřitelná nebo upravitelná.</span><span class="sxs-lookup"><span data-stu-id="60573-115">The attribute is not supported by any class, and the attribute syntax is not extensible or modifiable.</span></span> <span data-ttu-id="60573-116">Pokud implementujete [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vlastní procesor, můžete zvolit paralelní chování [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesoru při zpracování `Freeze` atributu v <xref:System.Windows.Freezable> prvcích v době načítání.</span><span class="sxs-lookup"><span data-stu-id="60573-116">If you are implementing your own [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor you can choose to parallel the freezing behavior of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor when processing the `Freeze` attribute on <xref:System.Windows.Freezable> elements at load time.</span></span>  
  
 <span data-ttu-id="60573-117">Libovolná hodnota atributu `Freeze` s `true` výjimkou (bez rozlišování malých a velkých písmen) generuje chybu při načítání.</span><span class="sxs-lookup"><span data-stu-id="60573-117">Any value for the `Freeze` attribute other than `true` (not case sensitive) generates a load time error.</span></span> <span data-ttu-id="60573-118">(Určení `Freeze` atributu jako `false` není chyba, ale to je již `false` výchozí, takže nastavení nedělá nic).</span><span class="sxs-lookup"><span data-stu-id="60573-118">(Specifying the `Freeze` attribute as `false` is not an error, but that is already the default, so setting to `false` does nothing).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60573-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60573-119">See also</span></span>

- <xref:System.Windows.Freezable>
- [<span data-ttu-id="60573-120">Přehled zablokovatelných objektů</span><span class="sxs-lookup"><span data-stu-id="60573-120">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="60573-121">mc:Ignorable – atribut</span><span class="sxs-lookup"><span data-stu-id="60573-121">mc:Ignorable Attribute</span></span>](mc-ignorable-attribute.md)
