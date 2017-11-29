---
title: "Řídicí sekvence {} – rozšíření značek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '{}'
helpviewer_keywords:
- XAML [XAML Services], quotation mark (")
- '{} escape sequence [XAML Services]'
- XAML [XAML Services], {} escape sequence
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- escape sequence [XAML Services]
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
caps.latest.revision: "21"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: befbf9960afffcd30bc96863dcc00b4acad2c21a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-escape-sequence--markup-extension"></a><span data-ttu-id="3151b-102">{} – řídicí sekvence / rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="3151b-102">{} Escape Sequence / Markup Extension</span></span>
<span data-ttu-id="3151b-103">Poskytuje řídicí sekvence XAML pro hodnoty atributu.</span><span class="sxs-lookup"><span data-stu-id="3151b-103">Provides the XAML escape sequence for attribute values.</span></span> <span data-ttu-id="3151b-104">Řídicí sekvence umožňuje následující hodnoty atributu budou interpretovat jako literál.</span><span class="sxs-lookup"><span data-stu-id="3151b-104">The escape sequence allows the subsequent values in the attribute to be interpreted as a literal.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="3151b-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="3151b-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="3151b-106">Použití elementu vlastnosti XAML</span><span class="sxs-lookup"><span data-stu-id="3151b-106">XAML Property Element Usage</span></span>  
  
```  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="3151b-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="3151b-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3151b-108">*literalValue*</span><span class="sxs-lookup"><span data-stu-id="3151b-108">*literalValue*</span></span>|<span data-ttu-id="3151b-109">Řetězcový literál, který následuje řídicí sekvence.</span><span class="sxs-lookup"><span data-stu-id="3151b-109">The literal string that follows the escape sequence.</span></span> <span data-ttu-id="3151b-110">Obvykle obsahuje tento řetězec otevřené nebo zavřít závorek ({nebo}).</span><span class="sxs-lookup"><span data-stu-id="3151b-110">Typically this string contains an open or close brace ({ or }).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3151b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3151b-111">Remarks</span></span>  
 <span data-ttu-id="3151b-112">Řídicí sekvence ({}) se používá, aby otevřete složená závorka ({}) můžete použít jako literál v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="3151b-112">The escape sequence ({}) is used so that an open brace ({)can be used as a literal character in XAML.</span></span>  
  
 <span data-ttu-id="3151b-113">Otevřete závorek ({}) XAML čtečky obvykle používat k označení vstupní bod rozšíření značek; ale nejprve zkontrolujte další znak, který má-li zjistit, zda je pravé složené závorce (}).</span><span class="sxs-lookup"><span data-stu-id="3151b-113">XAML readers typically use the open brace ({) to denote the entry point of a markup extension; however, they first check the next character to determine whether it is a closing brace (}).</span></span> <span data-ttu-id="3151b-114">Jenom v případě, že sousedí na dva složené závorky ({}), se považují za řídicí sekvence.</span><span class="sxs-lookup"><span data-stu-id="3151b-114">Only when the two braces ({}) are adjacent, are they considered an escape sequence.</span></span>  
  
 <span data-ttu-id="3151b-115">V případě řídicí sekvence čtečky XAML by měl zpracovat zbytek řetězec jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="3151b-115">If the escape sequence is encountered, the XAML reader should process the remainder of the string as a string.</span></span> <span data-ttu-id="3151b-116">Ale pokud řídicí sekvence je použité na člena, který má převodník typu, řetězec může převod typů při ke interpretuje se zapisovačem XAML.</span><span class="sxs-lookup"><span data-stu-id="3151b-116">However, if the escape sequence is applied to a member that has a type converter, the string might undergo type conversion when it is interpreted by a XAML writer.</span></span>  
  
 <span data-ttu-id="3151b-117">Řídicí sekvence není rozšíření značek a není podporována třídou.</span><span class="sxs-lookup"><span data-stu-id="3151b-117">The escape sequence is not a markup extension and is not backed by a class.</span></span> <span data-ttu-id="3151b-118">Je však názvů, který by měly dodržovat čtečky XAML (včetně vlastní čtečky XAML).</span><span class="sxs-lookup"><span data-stu-id="3151b-118">However, it is a convention that XAML readers (including custom XAML readers) should respect.</span></span>  
  
 <span data-ttu-id="3151b-119">Uvozovky (") nelze použít jako řídicí sekvencí tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="3151b-119">A quotation mark (") cannot be used as an escape sequence in this manner.</span></span> <span data-ttu-id="3151b-120">Pokud je nutné nastavit uvozovky jako hodnotu vlastnosti noncontent vlastnosti, použijte vlastnost element syntaxi a umístěte znak uvozovek jako řetězec uvnitř elementu vlastnost nebo použijte znakové entity XML.</span><span class="sxs-lookup"><span data-stu-id="3151b-120">If you need to set a quotation mark as a property value for a noncontent property, use property element syntax and place the quotation mark as a string inside the property element, or use an XML character entity.</span></span> <span data-ttu-id="3151b-121">Pro vlastnost obsahu může být znak uvozovek celého obsahu.</span><span class="sxs-lookup"><span data-stu-id="3151b-121">For a content property, the quotation mark can be the entire content.</span></span>  
  
 <span data-ttu-id="3151b-122">Řídicí sekvence ({}) je vyžadován často, při zadávání typ XML, který musí zahrnovat kvalifikátor oboru názvů v umístění, kde se může objevit rozšíření značek XAML.</span><span class="sxs-lookup"><span data-stu-id="3151b-122">The escape sequence ({}) is frequently required when specifying an XML type that must include a namespace qualifier in a location where a XAML markup extension might appear.</span></span> <span data-ttu-id="3151b-123">To zahrnuje počáteční hodnoty atributu XAML a rozšíření značek, okamžitě po symbol rovná se (=).</span><span class="sxs-lookup"><span data-stu-id="3151b-123">This includes the start of a XAML attribute value, and in a markup extension, immediately after an equal sign (=).</span></span> <span data-ttu-id="3151b-124">Následující příklad ukazuje řídicí sekvence pro obor názvů XML, který se zobrazí na začátku hodnotu atributu XAML.</span><span class="sxs-lookup"><span data-stu-id="3151b-124">The following example shows escape sequences for an XML namespace that appears at the start of a XAML attribute value.</span></span>  
  
 [!code-xaml[XLINQExample#StackPanelResources](../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a><span data-ttu-id="3151b-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="3151b-125">See Also</span></span>  
 [<span data-ttu-id="3151b-126">Převaděče typů a rozšíření značek pro jazyk XAML</span><span class="sxs-lookup"><span data-stu-id="3151b-126">Type Converters and Markup Extensions for XAML</span></span>](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [<span data-ttu-id="3151b-127">Znakové entity XML a jazyk XAML</span><span class="sxs-lookup"><span data-stu-id="3151b-127">XML Character Entities and XAML</span></span>](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)
