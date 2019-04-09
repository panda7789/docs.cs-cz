---
title: '{} Řídicí sekvence – rozšíření značek'
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
ms.openlocfilehash: 9f6743dd8a82891ac2233978550e5679130de0be
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182065"
---
# <a name="-escape-sequence--markup-extension"></a><span data-ttu-id="8fb60-102">{} – řídicí sekvence / rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="8fb60-102">{} Escape Sequence / Markup Extension</span></span>
<span data-ttu-id="8fb60-103">Poskytuje řídicí sekvence XAML pro hodnoty atributů.</span><span class="sxs-lookup"><span data-stu-id="8fb60-103">Provides the XAML escape sequence for attribute values.</span></span> <span data-ttu-id="8fb60-104">Řídicí sekvence povoluje následující hodnoty v atributu je interpretován jako literální.</span><span class="sxs-lookup"><span data-stu-id="8fb60-104">The escape sequence allows the subsequent values in the attribute to be interpreted as a literal.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="8fb60-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="8fb60-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="8fb60-106">Použití elementu vlastnosti XAML</span><span class="sxs-lookup"><span data-stu-id="8fb60-106">XAML Property Element Usage</span></span>  
  
```  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="8fb60-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="8fb60-107">XAML Values</span></span>  
  
|||  
|-|-|  
|*<span data-ttu-id="8fb60-108">literalValue</span><span class="sxs-lookup"><span data-stu-id="8fb60-108">literalValue</span></span>*|<span data-ttu-id="8fb60-109">Řetězcový literál, který následuje řídicí sekvence.</span><span class="sxs-lookup"><span data-stu-id="8fb60-109">The literal string that follows the escape sequence.</span></span> <span data-ttu-id="8fb60-110">Obvykle tento řetězec obsahuje otevřít nebo zavřít závorka ({nebo}).</span><span class="sxs-lookup"><span data-stu-id="8fb60-110">Typically this string contains an open or close brace ({ or }).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fb60-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8fb60-111">Remarks</span></span>  
 <span data-ttu-id="8fb60-112">Řídicí sekvence ({}) se používá tak, aby levou složenou závorku ({}) je možné jako literální znak v XAML.</span><span class="sxs-lookup"><span data-stu-id="8fb60-112">The escape sequence ({}) is used so that an open brace ({)can be used as a literal character in XAML.</span></span>  
  
 <span data-ttu-id="8fb60-113">Čtenáři XAML obvykle používají levou složenou závorku ({}) k označení vstupní bod rozšíření značek, ale nejprve zkontrolujte další znak k určení, zda je pravá složená závorka (}).</span><span class="sxs-lookup"><span data-stu-id="8fb60-113">XAML readers typically use the open brace ({) to denote the entry point of a markup extension; however, they first check the next character to determine whether it is a closing brace (}).</span></span> <span data-ttu-id="8fb60-114">Pouze když dvě složené závorky ({}) jsou sousedící, se považují za řídicí sekvence.</span><span class="sxs-lookup"><span data-stu-id="8fb60-114">Only when the two braces ({}) are adjacent, are they considered an escape sequence.</span></span>  
  
 <span data-ttu-id="8fb60-115">Pokud je řídicí sekvence, čtečky XAML by měl zpracovat zbývající část řetězce jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="8fb60-115">If the escape sequence is encountered, the XAML reader should process the remainder of the string as a string.</span></span> <span data-ttu-id="8fb60-116">Však pokud řídicí sekvence je u člena, který má konvertor typu, řetězec může projít převod typu při je interpretován tvůrci XAML.</span><span class="sxs-lookup"><span data-stu-id="8fb60-116">However, if the escape sequence is applied to a member that has a type converter, the string might undergo type conversion when it is interpreted by a XAML writer.</span></span>  
  
 <span data-ttu-id="8fb60-117">Řídicí sekvence není rozšíření značek a nepochází ze třídy.</span><span class="sxs-lookup"><span data-stu-id="8fb60-117">The escape sequence is not a markup extension and is not backed by a class.</span></span> <span data-ttu-id="8fb60-118">Je však konvence, který by měly dodržovat čtenáři XAML (včetně vlastních čtenáři XAML).</span><span class="sxs-lookup"><span data-stu-id="8fb60-118">However, it is a convention that XAML readers (including custom XAML readers) should respect.</span></span>  
  
 <span data-ttu-id="8fb60-119">Znak uvozovek (") nelze použít jako řídicí sekvence tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="8fb60-119">A quotation mark (") cannot be used as an escape sequence in this manner.</span></span> <span data-ttu-id="8fb60-120">Pokud je potřeba nastavit jako hodnotu vlastnosti noncontent vlastnosti uvozovku, používat syntax prvku vlastnosti a umístěte znak uvozovek jako řetězec uvnitř elementu vlastnosti nebo použít znakové entity XML.</span><span class="sxs-lookup"><span data-stu-id="8fb60-120">If you need to set a quotation mark as a property value for a noncontent property, use property element syntax and place the quotation mark as a string inside the property element, or use an XML character entity.</span></span> <span data-ttu-id="8fb60-121">Pro vlastnost obsahu může být znak uvozovek celého obsahu.</span><span class="sxs-lookup"><span data-stu-id="8fb60-121">For a content property, the quotation mark can be the entire content.</span></span>  
  
 <span data-ttu-id="8fb60-122">Řídicí sekvence ({}) je vyžadován často, při určování typu XML, který musí obsahovat obor názvů kvalifikátoru v umístění, kde se může zobrazit rozšíření značek XAML.</span><span class="sxs-lookup"><span data-stu-id="8fb60-122">The escape sequence ({}) is frequently required when specifying an XML type that must include a namespace qualifier in a location where a XAML markup extension might appear.</span></span> <span data-ttu-id="8fb60-123">To zahrnuje počáteční hodnotu atributu XAML a rozšíření značek, ihned po rovnítko (=).</span><span class="sxs-lookup"><span data-stu-id="8fb60-123">This includes the start of a XAML attribute value, and in a markup extension, immediately after an equal sign (=).</span></span> <span data-ttu-id="8fb60-124">Následující příklad ukazuje řídicí sekvence pro obor názvů XML, který se zobrazí na začátku hodnotu atributu XAML.</span><span class="sxs-lookup"><span data-stu-id="8fb60-124">The following example shows escape sequences for an XML namespace that appears at the start of a XAML attribute value.</span></span>  
  
 [!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a><span data-ttu-id="8fb60-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8fb60-125">See also</span></span>

- [<span data-ttu-id="8fb60-126">Převaděče typů a rozšíření značek pro jazyk XAML</span><span class="sxs-lookup"><span data-stu-id="8fb60-126">Type Converters and Markup Extensions for XAML</span></span>](type-converters-and-markup-extensions-for-xaml.md)
- [<span data-ttu-id="8fb60-127">Znakové entity XML a jazyk XAML</span><span class="sxs-lookup"><span data-stu-id="8fb60-127">XML Character Entities and XAML</span></span>](xml-character-entities-and-xaml.md)
