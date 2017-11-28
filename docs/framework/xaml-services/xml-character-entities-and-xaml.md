---
title: "Znakové entity XML a jazyk XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- '&'
- '&amp'
- '&gt'
- '&lt'
helpviewer_keywords:
- XAML [XAML Services], special characters
- ampersand (&) [XAML Services]
- special characters [XAML Services]
- apostrophe (') [XAML Services]
- greater-than (>) character [XAML Services]
- XAML [XAML Services], quotation mark (")
- XAML [XAML Services], apostrophe (')
- '& (ampersand) [XAML Services]'
- XAML [XAML Services], & (ampersand)
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- less-than (<) character [XAML Services]
ms.assetid: 6896d0ce-74f7-420a-9ab4-de9bbf390e8d
caps.latest.revision: "23"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 5973c67b26e07bba69383cc625ff34493d825a41
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xml-character-entities-and-xaml"></a><span data-ttu-id="5566e-102">Znakové entity XML a jazyk XAML</span><span class="sxs-lookup"><span data-stu-id="5566e-102">XML Character Entities and XAML</span></span>
<span data-ttu-id="5566e-103">XAML používá entity znaků, které jsou definované v kódu XML pro speciální znaky.</span><span class="sxs-lookup"><span data-stu-id="5566e-103">XAML uses character entities defined in XML for special characters.</span></span> <span data-ttu-id="5566e-104">Toto téma popisuje některé konkrétní znak entit a obecné požadavky na dalších konceptech XML v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="5566e-104">This topic describes some specific character entities and general considerations for other XML concepts in XAML.</span></span>  
  
<a name="character_entities_and_escaping_issues_that_are_unique_to_xaml"></a>   
## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a><span data-ttu-id="5566e-105">Znakové entity a problémy uvozovací znaky, které jsou jedinečné pro XAML</span><span class="sxs-lookup"><span data-stu-id="5566e-105">Character Entities and Escaping Issues That Are Unique to XAML</span></span>  
 <span data-ttu-id="5566e-106">Kód jazyka XAML se většinou používá stejné entity znaků a řídicích sekvencí, které jsou definovány v kódu XML.</span><span class="sxs-lookup"><span data-stu-id="5566e-106">XAML markup typically uses the same character entities and escape sequences that are defined in XML.</span></span>  
  
 <span data-ttu-id="5566e-107">Hlavní výjimkou je, který složené závorky ({a}) mají význam v jazyce XAML, protože tyto znaky informovat procesor XAML posloupnost znaků uvedené ve složených závorkách musí být interpretaci jako rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="5566e-107">The main exception is that braces ({ and }) have significance in XAML because these characters inform a XAML processor that a character sequence enclosed by braces must be interpreted as a markup extension.</span></span> <span data-ttu-id="5566e-108">Další informace o rozšíření značek najdete v tématu [XAML přehled rozšíření značek pro](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5566e-108">For more information about markup extensions, see [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).</span></span>  
  
 <span data-ttu-id="5566e-109">Ale můžete pořád zobrazit složené závorky jako literály pomocí řídicí sekvence, které je specifický pro XAML místo XML.</span><span class="sxs-lookup"><span data-stu-id="5566e-109">However, you can still display the braces as literal characters by using an escape sequence that is particular to XAML instead of XML.</span></span> <span data-ttu-id="5566e-110">Další informace najdete v tématu [{} řídicí sekvence – rozšíření značek](escape-sequence-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="5566e-110">For more information, see [{} Escape Sequence - Markup Extension](escape-sequence-markup-extension.md).</span></span>  
  
 <span data-ttu-id="5566e-111">Všimněte si, že zpětné lomítko (\\) nevyžaduje řídicí sekvence, pokud se zpracovává jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="5566e-111">Note that a backslash (\\) does not require an escape sequence when it is handled as a string.</span></span>  
  
<a name="xml_character_entities"></a>   
## <a name="xml-character-entities"></a><span data-ttu-id="5566e-112">Znakové entity XML</span><span class="sxs-lookup"><span data-stu-id="5566e-112">XML Character Entities</span></span>  
 <span data-ttu-id="5566e-113">Jak je uvedeno nahoře, většina entity znaků a řídicích sekvencí, které jsou obvykle používány k zápisu kódu XAML jsou definovány XML.</span><span class="sxs-lookup"><span data-stu-id="5566e-113">As mentioned previously, most character entities and escape sequences that are typically used to write XAML markup are defined by XML.</span></span> <span data-ttu-id="5566e-114">Toto téma neposkytuje úplný seznam těchto entitách; podrobné referenční pro entity naleznete v dokumentaci k externí, jako v specifikace XML.</span><span class="sxs-lookup"><span data-stu-id="5566e-114">This topic does not provide the complete list of these entities; a detailed reference for the entities can be found in external documentation, such as in XML specifications.</span></span> <span data-ttu-id="5566e-115">Ale pro usnadnění práce v tomto tématu jsou uvedeny některé konkrétní znakové entity XML, které jsou obvykle používány v XAML značek.</span><span class="sxs-lookup"><span data-stu-id="5566e-115">However, for convenience, this topic lists some of the specific XML character entities that are typically used in XAML markup.</span></span>  
  
|<span data-ttu-id="5566e-116">Znak</span><span class="sxs-lookup"><span data-stu-id="5566e-116">Character</span></span>|<span data-ttu-id="5566e-117">Entity</span><span class="sxs-lookup"><span data-stu-id="5566e-117">Entity</span></span>|<span data-ttu-id="5566e-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5566e-118">Notes</span></span>|  
|---------------|------------|-----------|  
|<span data-ttu-id="5566e-119">& (ampersand)</span><span class="sxs-lookup"><span data-stu-id="5566e-119">& (ampersand)</span></span>|&amp;|<span data-ttu-id="5566e-120">Musí použít u hodnot atributů i obsahu elementu.</span><span class="sxs-lookup"><span data-stu-id="5566e-120">Must be used both for attribute values and for content of an element.</span></span>|  
|<span data-ttu-id="5566e-121">> (větší – než znak)</span><span class="sxs-lookup"><span data-stu-id="5566e-121">> (greater-than character)</span></span>|&gt;|<span data-ttu-id="5566e-122">Je nutné použít hodnotu atributu, ale > je přijatelné jako obsah stejně dlouho jako element < není předcházet.</span><span class="sxs-lookup"><span data-stu-id="5566e-122">Must be used for an attribute value, but > is acceptable as the content of an element as long as < does not precede it.</span></span>|  
|<span data-ttu-id="5566e-123">< (menší – než znak)</span><span class="sxs-lookup"><span data-stu-id="5566e-123">< (less-than character)</span></span>|&lt;|<span data-ttu-id="5566e-124">Je nutné použít hodnotu atributu, ale \< je přijatelné jako obsah elementu stejně dlouho jako > nedodrží ho.</span><span class="sxs-lookup"><span data-stu-id="5566e-124">Must be used for an attribute value, but \< is acceptable as the content of an element as long as > does not follow it.</span></span>|  
|<span data-ttu-id="5566e-125">"(dvojité uvozovky)</span><span class="sxs-lookup"><span data-stu-id="5566e-125">" (straight quotation mark)</span></span>|&quot;|<span data-ttu-id="5566e-126">Je nutné použít hodnotu atributu, ale dvojité uvozovky (") se dá použít jako obsahu elementu.</span><span class="sxs-lookup"><span data-stu-id="5566e-126">Must be used for an attribute value, but a straight quotation mark (") is acceptable as the content of an element.</span></span> <span data-ttu-id="5566e-127">Všimněte si, že hodnoty atributu může být uzavřená pomocí přímých apostrof (') nebo pomocí dvojité uvozovky ("); podle toho, která znak zobrazí první definuje skříni hodnotu atributu a alternativní uvozovky lze jako literál v hodnotě.</span><span class="sxs-lookup"><span data-stu-id="5566e-127">Note that attribute values may be enclosed either by a single straight quotation mark (') or by a straight quotation mark ("); whichever character appears first defines the attribute value enclosure, and the alternative quote can then be used as a literal within the value.</span></span>|  
|<span data-ttu-id="5566e-128">' (jednoduché uvozovky)</span><span class="sxs-lookup"><span data-stu-id="5566e-128">' (single straight quotation mark)</span></span>|&apos;|<span data-ttu-id="5566e-129">Je nutné použít hodnotu atributu, ale je přijatelné jako obsah elementu přímých apostrof (').</span><span class="sxs-lookup"><span data-stu-id="5566e-129">Must be used for an attribute value, but a single straight quotation mark (') is acceptable as the content of an element.</span></span> <span data-ttu-id="5566e-130">Všimněte si, že hodnoty atributu může být uzavřená pomocí přímých apostrof (') nebo pomocí dvojité uvozovky ("); podle toho, která znak zobrazí první definuje skříni hodnotu atributu a alternativní uvozovky lze jako literál v hodnotě.</span><span class="sxs-lookup"><span data-stu-id="5566e-130">Note that attribute values may be enclosed either by a single straight quotation mark (') or by a straight quotation mark ("); whichever character appears first defines the attribute value enclosure, and the alternative quote can then be used as a literal within the value.</span></span>|  
|<span data-ttu-id="5566e-131">(čísla mapování)</span><span class="sxs-lookup"><span data-stu-id="5566e-131">(numeric character mappings)</span></span>|<span data-ttu-id="5566e-132">&#*[celé číslo]* ; nebo & #x*[šestnáctkových]*;</span><span class="sxs-lookup"><span data-stu-id="5566e-132">&#*[integer]*; or &#x*[hex]*;</span></span>|<span data-ttu-id="5566e-133">XAML podporuje mapování čísla do kódování, které je aktivní.</span><span class="sxs-lookup"><span data-stu-id="5566e-133">XAML supports numeric character mappings into the encoding that is active.</span></span>|  
|<span data-ttu-id="5566e-134">(pevná místa)</span><span class="sxs-lookup"><span data-stu-id="5566e-134">(nonbreaking space)</span></span>|<span data-ttu-id="5566e-135">&\#160; (za předpokladu, že kódování UTF-8)</span><span class="sxs-lookup"><span data-stu-id="5566e-135">&\#160; (assuming UTF-8 encoding)</span></span>|<span data-ttu-id="5566e-136">Pro prvky toku dokumentu nebo prvky, které trvat text například WPF <xref:System.Windows.Controls.TextBox>, pevné mezery nejsou normalized mimo značku, i pro `xml:space="default"`.</span><span class="sxs-lookup"><span data-stu-id="5566e-136">For flow document elements, or elements that take text such as the WPF <xref:System.Windows.Controls.TextBox>, nonbreaking spaces are not normalized out of the markup, even for `xml:space="default"`.</span></span> <span data-ttu-id="5566e-137">(Další informace najdete v tématu [zpracování prázdných znaků v jazyce XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).)</span><span class="sxs-lookup"><span data-stu-id="5566e-137">(For more information, see [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).)</span></span>|  
  
<a name="xml_comment_format"></a>   
## <a name="xml-comment-format"></a><span data-ttu-id="5566e-138">Formát komentáře XML</span><span class="sxs-lookup"><span data-stu-id="5566e-138">XML Comment Format</span></span>  
 <span data-ttu-id="5566e-139">XAML používá formát komentáře XML: spuštění komentář je `<!--`, je na konci komentáře `-->,` a pořadí `--` nesmí vyskytovat v rámci komentář.</span><span class="sxs-lookup"><span data-stu-id="5566e-139">XAML uses the XML comment format: the start of the comment is `<!--`, the end of comment is `-->,` and the sequence `--` must not occur within the comment.</span></span>  
  
<a name="xml_processing_instructions"></a>   
## <a name="xml-processing-instructions"></a><span data-ttu-id="5566e-140">Pokyny pro zpracování XML</span><span class="sxs-lookup"><span data-stu-id="5566e-140">XML Processing Instructions</span></span>  
 <span data-ttu-id="5566e-141">XAML zpracovává pokyny pro zpracování XML podle specifikace XML, které stavu pokynů musí předána.</span><span class="sxs-lookup"><span data-stu-id="5566e-141">XAML handles XML processing instructions according to XML specifications, which state that the instructions must be passed through.</span></span> <span data-ttu-id="5566e-142">XAML zpracování v rozhraní .NET Framework XAML Services nepoužívá instrukcí pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="5566e-142">XAML processing in .NET Framework XAML Services  does not use any processing instructions.</span></span> <span data-ttu-id="5566e-143">Jiné existující rozhraní používající XAML také nepoužívejte pokyny pro zpracování z XAML.</span><span class="sxs-lookup"><span data-stu-id="5566e-143">Other existing frameworks that use XAML also do not use processing instructions from XAML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5566e-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="5566e-144">See Also</span></span>  
 [<span data-ttu-id="5566e-145">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="5566e-145">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="5566e-146">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="5566e-146">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="5566e-147">XamlName – gramatika</span><span class="sxs-lookup"><span data-stu-id="5566e-147">XamlName Grammar</span></span>](../../../docs/framework/xaml-services/xamlname-grammar.md)  
 [<span data-ttu-id="5566e-148">Zpracování prázdných znaků v jazyce XAML</span><span class="sxs-lookup"><span data-stu-id="5566e-148">Whitespace Processing in XAML</span></span>](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)
