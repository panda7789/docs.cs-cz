---
title: '{}Řídicí sekvence – rozšíření značek'
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
ms.openlocfilehash: b0646c62a1342eb160d1967e86ac286429013f3c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053865"
---
# <a name="-escape-sequence--markup-extension"></a><span data-ttu-id="3057d-102">{} – řídicí sekvence / rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="3057d-102">{} Escape Sequence / Markup Extension</span></span>
<span data-ttu-id="3057d-103">Poskytuje řídicí sekvenci jazyka XAML pro hodnoty atributu.</span><span class="sxs-lookup"><span data-stu-id="3057d-103">Provides the XAML escape sequence for attribute values.</span></span> <span data-ttu-id="3057d-104">Řídicí sekvence umožňuje interpretovat následné hodnoty v atributu jako literál.</span><span class="sxs-lookup"><span data-stu-id="3057d-104">The escape sequence allows the subsequent values in the attribute to be interpreted as a literal.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="3057d-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="3057d-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="3057d-106">Použití elementu vlastnosti XAML</span><span class="sxs-lookup"><span data-stu-id="3057d-106">XAML Property Element Usage</span></span>  
  
```xaml  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="3057d-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="3057d-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3057d-108">*literalValue*</span><span class="sxs-lookup"><span data-stu-id="3057d-108">*literalValue*</span></span>|<span data-ttu-id="3057d-109">Literální řetězec, který následuje za řídicí sekvencí.</span><span class="sxs-lookup"><span data-stu-id="3057d-109">The literal string that follows the escape sequence.</span></span> <span data-ttu-id="3057d-110">Tento řetězec obvykle obsahuje levou nebo uzavírací složenou závorku ({nebo}).</span><span class="sxs-lookup"><span data-stu-id="3057d-110">Typically this string contains an open or close brace ({ or }).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3057d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3057d-111">Remarks</span></span>  
 <span data-ttu-id="3057d-112">Řídicí sekvence ({}) se používá, aby bylo možné použít levou složenou závorku ({) jako literální znak v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="3057d-112">The escape sequence ({}) is used so that an open brace ({)can be used as a literal character in XAML.</span></span>  
  
 <span data-ttu-id="3057d-113">Čtečky XAML obvykle používají levou složenou závorku ({) k označení vstupního bodu rozšíření značek, ale nejprve si vyžádají další znak a určí, zda se jedná o pravou složenou závorku (}).</span><span class="sxs-lookup"><span data-stu-id="3057d-113">XAML readers typically use the open brace ({) to denote the entry point of a markup extension; however, they first check the next character to determine whether it is a closing brace (}).</span></span> <span data-ttu-id="3057d-114">Pouze v případě, že dvě složené{}závorky () jsou sousední, jsou považovány za řídicí sekvenci.</span><span class="sxs-lookup"><span data-stu-id="3057d-114">Only when the two braces ({}) are adjacent, are they considered an escape sequence.</span></span>  
  
 <span data-ttu-id="3057d-115">Pokud řídicí sekvence je zjištěna, čtečka XAML by měla zpracovat zbytek řetězce jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="3057d-115">If the escape sequence is encountered, the XAML reader should process the remainder of the string as a string.</span></span> <span data-ttu-id="3057d-116">Pokud je však řídicí sekvence použita pro člena, který má konvertor typu, může řetězec přecházet při převodu typu, když je interpretován zapisovačem XAML.</span><span class="sxs-lookup"><span data-stu-id="3057d-116">However, if the escape sequence is applied to a member that has a type converter, the string might undergo type conversion when it is interpreted by a XAML writer.</span></span>  
  
 <span data-ttu-id="3057d-117">Řídicí sekvence není rozšířením značek a není zálohována třídou.</span><span class="sxs-lookup"><span data-stu-id="3057d-117">The escape sequence is not a markup extension and is not backed by a class.</span></span> <span data-ttu-id="3057d-118">Nicméně se jedná o konvenci, kterou by měli respektovat čtenáři XAML (včetně vlastních čtenářů XAML).</span><span class="sxs-lookup"><span data-stu-id="3057d-118">However, it is a convention that XAML readers (including custom XAML readers) should respect.</span></span>  
  
 <span data-ttu-id="3057d-119">Uvozovky (") nelze použít jako řídicí sekvenci tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="3057d-119">A quotation mark (") cannot be used as an escape sequence in this manner.</span></span> <span data-ttu-id="3057d-120">Pokud potřebujete nastavit uvozovky jako hodnotu vlastnosti pro vlastnost neobsahující vlastnosti, použijte syntaxi elementu vlastností a umístěte uvozovky jako řetězec uvnitř elementu vlastnosti nebo použijte entitu znaků XML.</span><span class="sxs-lookup"><span data-stu-id="3057d-120">If you need to set a quotation mark as a property value for a noncontent property, use property element syntax and place the quotation mark as a string inside the property element, or use an XML character entity.</span></span> <span data-ttu-id="3057d-121">V případě vlastnosti obsahu může být uvozovka celým obsahem.</span><span class="sxs-lookup"><span data-stu-id="3057d-121">For a content property, the quotation mark can be the entire content.</span></span>  
  
 <span data-ttu-id="3057d-122">Řídicí sekvence ({}) se často vyžaduje při určení typu XML, který musí obsahovat kvalifikátor oboru názvů v umístění, kde se může zobrazit rozšíření značek XAML.</span><span class="sxs-lookup"><span data-stu-id="3057d-122">The escape sequence ({}) is frequently required when specifying an XML type that must include a namespace qualifier in a location where a XAML markup extension might appear.</span></span> <span data-ttu-id="3057d-123">To zahrnuje začátek hodnoty atributu XAML a v rozšíření značek hned po znaménku rovná se (=).</span><span class="sxs-lookup"><span data-stu-id="3057d-123">This includes the start of a XAML attribute value, and in a markup extension, immediately after an equal sign (=).</span></span> <span data-ttu-id="3057d-124">Následující příklad ukazuje řídicí sekvence pro obor názvů XML, který se zobrazí na začátku hodnoty atributu XAML.</span><span class="sxs-lookup"><span data-stu-id="3057d-124">The following example shows escape sequences for an XML namespace that appears at the start of a XAML attribute value.</span></span>  
  
 [!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a><span data-ttu-id="3057d-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3057d-125">See also</span></span>

- [<span data-ttu-id="3057d-126">Převaděče typů a rozšíření značek pro jazyk XAML</span><span class="sxs-lookup"><span data-stu-id="3057d-126">Type Converters and Markup Extensions for XAML</span></span>](type-converters-and-markup-extensions-for-xaml.md)
- [<span data-ttu-id="3057d-127">Znakové entity XML a jazyk XAML</span><span class="sxs-lookup"><span data-stu-id="3057d-127">XML Character Entities and XAML</span></span>](xml-character-entities-and-xaml.md)
