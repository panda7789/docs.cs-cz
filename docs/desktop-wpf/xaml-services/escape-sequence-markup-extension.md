---
title: '{}Escape Sequence – rozšíření značek'
ms.date: 03/30/2017
f1_keywords:
- '{}'
helpviewer_keywords:
- XAML [XAML Services], quotation mark (")
- '{} escape sequence [XAML Services]'
- XAML [XAML Services], {} escape sequence
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- escape sequence [XAML Services]
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
ms.openlocfilehash: f84243994557d76fa52d72b060a1ba35460e98b0
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071743"
---
# <a name="-escape-sequence--markup-extension"></a><span data-ttu-id="9e199-102">{}Escape sekvence / značkovací rozšíření</span><span class="sxs-lookup"><span data-stu-id="9e199-102">{} Escape sequence / markup extension</span></span>

<span data-ttu-id="9e199-103">Poskytuje řídicí sekvenci XAML pro hodnoty atributů.</span><span class="sxs-lookup"><span data-stu-id="9e199-103">Provides the XAML escape sequence for attribute values.</span></span> <span data-ttu-id="9e199-104">Sekvence escape umožňuje následné hodnoty v atributu, které mají být interpretovány jako literál.</span><span class="sxs-lookup"><span data-stu-id="9e199-104">The escape sequence allows the subsequent values in the attribute to be interpreted as a literal.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="9e199-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="9e199-105">XAML Attribute Usage</span></span>

```xaml
<object property="{} literalValue" .../>
```

## <a name="xaml-property-element-usage"></a><span data-ttu-id="9e199-106">Použití elementu vlastnosti XAML</span><span class="sxs-lookup"><span data-stu-id="9e199-106">XAML Property Element Usage</span></span>

```xaml
<object>
  <object.property>
    {} literalValue
  </object.property>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="9e199-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="9e199-107">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="9e199-108">*literalValue*</span><span class="sxs-lookup"><span data-stu-id="9e199-108">*literalValue*</span></span>|<span data-ttu-id="9e199-109">Literál řetězec, který následuje sekvence escape.</span><span class="sxs-lookup"><span data-stu-id="9e199-109">The literal string that follows the escape sequence.</span></span> <span data-ttu-id="9e199-110">Obvykle tento řetězec obsahuje otevřenou nebo zavřít složená závorka ({ nebo }).</span><span class="sxs-lookup"><span data-stu-id="9e199-110">Typically this string contains an open or close brace ({ or }).</span></span>|

## <a name="remarks"></a><span data-ttu-id="9e199-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e199-111">Remarks</span></span>

<span data-ttu-id="9e199-112">Sekvence escape{}( ) se používá tak, aby otevřená závorka ({) může být použita jako literál znak v XAML.</span><span class="sxs-lookup"><span data-stu-id="9e199-112">The escape sequence ({}) is used so that an open brace ({) can be used as a literal character in XAML.</span></span>

<span data-ttu-id="9e199-113">Čtečky XAML obvykle používají otevřenou složenou závorku ({) k označení vstupního bodu rozšíření značek; nejprve však zkontrolují další znak a zkontrolují, zda se jedná o uzavírací složenou závorku (}).</span><span class="sxs-lookup"><span data-stu-id="9e199-113">XAML readers typically use the open brace ({) to denote the entry point of a markup extension; however, they first check the next character to determine whether it is a closing brace (}).</span></span> <span data-ttu-id="9e199-114">Pouze v případě,{}že dvě závorky ( ) jsou přilehlé, jsou považovány za únikovou sekvenci.</span><span class="sxs-lookup"><span data-stu-id="9e199-114">Only when the two braces ({}) are adjacent, are they considered an escape sequence.</span></span>

<span data-ttu-id="9e199-115">Pokud dojde k escape sekvence, čtečka XAML by měl zpracovat zbytek řetězce jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="9e199-115">If the escape sequence is encountered, the XAML reader should process the remainder of the string as a string.</span></span> <span data-ttu-id="9e199-116">Pokud je však sekvence escape použita na člena, který má převaděč typu, řetězec může projít převodem typu, pokud je interpretován zapisovatelem XAML.</span><span class="sxs-lookup"><span data-stu-id="9e199-116">However, if the escape sequence is applied to a member that has a type converter, the string might undergo type conversion when it is interpreted by a XAML writer.</span></span>

<span data-ttu-id="9e199-117">Sekvence escape není rozšíření značky a není zálohována třídou.</span><span class="sxs-lookup"><span data-stu-id="9e199-117">The escape sequence is not a markup extension and is not backed by a class.</span></span> <span data-ttu-id="9e199-118">Je však konvence, která xaml čtenáři (včetně vlastních čteček XAML) by měl respektovat.</span><span class="sxs-lookup"><span data-stu-id="9e199-118">However, it is a convention that XAML readers (including custom XAML readers) should respect.</span></span>

<span data-ttu-id="9e199-119">Uvozovky (") nelze tímto způsobem použít jako řídicí sekvenci.</span><span class="sxs-lookup"><span data-stu-id="9e199-119">A quotation mark (") cannot be used as an escape sequence in this manner.</span></span> <span data-ttu-id="9e199-120">Pokud potřebujete nastavit uvozovky jako hodnotu vlastnosti pro vlastnost neobsahu, použijte syntaxi prvku vlastnosti a umístěte uvozovku jako řetězec uvnitř elementu vlastnosti nebo použijte entitu znaků XML.</span><span class="sxs-lookup"><span data-stu-id="9e199-120">If you need to set a quotation mark as a property value for a noncontent property, use property element syntax and place the quotation mark as a string inside the property element, or use an XML character entity.</span></span> <span data-ttu-id="9e199-121">Pro vlastnost obsahu může být uvozovka celý obsah.</span><span class="sxs-lookup"><span data-stu-id="9e199-121">For a content property, the quotation mark can be the entire content.</span></span>

<span data-ttu-id="9e199-122">Sekvence escape{}( ) je často vyžadována při zadávání typu XML, který musí obsahovat kvalifikátor oboru názvů v umístění, kde se může zobrazit rozšíření značek XAML.</span><span class="sxs-lookup"><span data-stu-id="9e199-122">The escape sequence ({}) is frequently required when specifying an XML type that must include a namespace qualifier in a location where a XAML markup extension might appear.</span></span> <span data-ttu-id="9e199-123">Toto umístění zahrnuje začátek hodnoty atributu XAML a v rozšíření značky bezprostředně za rovnítkem (=).</span><span class="sxs-lookup"><span data-stu-id="9e199-123">This location includes the start of a XAML attribute value, and in a markup extension immediately after an equal sign (=).</span></span> <span data-ttu-id="9e199-124">Následující příklad ukazuje sekvence escape pro obor názvů XML, který se zobrazí na začátku hodnoty atributu XAML.</span><span class="sxs-lookup"><span data-stu-id="9e199-124">The following example shows escape sequences for an XML namespace that appears at the start of a XAML attribute value.</span></span>

[!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]

## <a name="see-also"></a><span data-ttu-id="9e199-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e199-125">See also</span></span>

- [<span data-ttu-id="9e199-126">Převaděče typů a rozšíření značek pro jazyk XAML</span><span class="sxs-lookup"><span data-stu-id="9e199-126">Type Converters and Markup Extensions for XAML</span></span>](type-converters-and-markup-extensions.md)
- [<span data-ttu-id="9e199-127">Znakové entity XML a jazyk XAML</span><span class="sxs-lookup"><span data-stu-id="9e199-127">XML Character Entities and XAML</span></span>](xml-character-entities.md)
