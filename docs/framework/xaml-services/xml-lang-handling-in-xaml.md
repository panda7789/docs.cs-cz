---
title: "Práce s atributem xml:lang v jazyce XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
caps.latest.revision: "16"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 47dd34db82e796418b68fcf9b28ef3e4d4eaca4e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="xmllang-handling-in-xaml"></a><span data-ttu-id="1204d-102">Práce s atributem xml:lang v jazyce XAML</span><span class="sxs-lookup"><span data-stu-id="1204d-102">xml:lang Handling in XAML</span></span>
<span data-ttu-id="1204d-103">`xml:lang` Atribut je [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]-definovaný atribut, který deklaruje informace o jazyce a jazykové verzi pro element v kódu XML.</span><span class="sxs-lookup"><span data-stu-id="1204d-103">The `xml:lang` attribute is an [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]-defined attribute that declares the language and culture information for an element in XML.</span></span> <span data-ttu-id="1204d-104">Tento stejný význam atributu přetrvává v jazyce XAML; ale některé další aspekty platí.</span><span class="sxs-lookup"><span data-stu-id="1204d-104">This same meaning of the attribute persists in XAML; however, some additional considerations apply.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="1204d-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="1204d-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:lang="rfc3066lang" />  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="1204d-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="1204d-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1204d-107">*rfc3066lang*</span><span class="sxs-lookup"><span data-stu-id="1204d-107">*rfc3066lang*</span></span>|<span data-ttu-id="1204d-108">Řetězec, který je odvozený od [RFC 3066](http://go.microsoft.com/fwlink/?LinkId=132454) standardní a identifikuje jazyk nebo jazyka oblasti.</span><span class="sxs-lookup"><span data-stu-id="1204d-108">A string that is derived from the [RFC 3066](http://go.microsoft.com/fwlink/?LinkId=132454) standard and identifies either a language or a language-region.</span></span> <span data-ttu-id="1204d-109">Pokud je k tomu, jazyk a oblasti jsou oddělena pomlčkou jeden.</span><span class="sxs-lookup"><span data-stu-id="1204d-109">When it is the latter, the language and region are separated by a single hyphen.</span></span> <span data-ttu-id="1204d-110">V tématu <xref:System.Windows.Markup.XmlLanguage> Další informace o hodnoty a formát.</span><span class="sxs-lookup"><span data-stu-id="1204d-110">See <xref:System.Windows.Markup.XmlLanguage> for more information about the values and format.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1204d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1204d-111">Remarks</span></span>  
 <span data-ttu-id="1204d-112">Definice pro `xml:lang` atribut [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] je odvozený od `xml:lang` podle definice jako "speciální atribut" [!INCLUDE[TLA#tla_w3c](../../../includes/tlasharptla-w3c-md.md)] pro [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1204d-112">The definition for the `xml:lang` attribute in [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] is derived from `xml:lang` as defined as a "special attribute" by the [!INCLUDE[TLA#tla_w3c](../../../includes/tlasharptla-w3c-md.md)] for [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)].</span></span> <span data-ttu-id="1204d-113">Informace o jazyce a jazykové verzi potenciálně zpracovává různými způsoby prvky, v závislosti na jejich implementace; neexistuje však žádný výchozí [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] zpracování `xml:lang` atribut.</span><span class="sxs-lookup"><span data-stu-id="1204d-113">Language and culture information is potentially processed in different ways by elements, depending on their implementations; however, there is no default [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing of the `xml:lang` attribute.</span></span>  
  
 <span data-ttu-id="1204d-114">Výchozí hodnota `xml:lang` atribut je prázdný řetězec na úrovni atribut.</span><span class="sxs-lookup"><span data-stu-id="1204d-114">The default value of the `xml:lang` attribute is an empty string at the attribute level.</span></span>  
  
 <span data-ttu-id="1204d-115">`xml:lang` Atribut dopady a hodnota atributu jsou obecně perpetuated pro podřízené elementy, když interpretovat systémy, které fungují v `xml:lang` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1204d-115">The `xml:lang` attribute effects and the value of the attribute are generally perpetuated to child elements, when interpreted by systems that act on `xml:lang` values.</span></span>  
  
 <span data-ttu-id="1204d-116">Když interpretovat XAML zapisovače služby rozhraní .NET Framework XAML Services `xml:lang` můžete vytvořit hodnotu <xref:System.Windows.Markup.XmlLanguage> nebo <xref:System.Globalization.CultureInfo> objekty v základní objektu reprezentace; ale, že chování závisí na tom, zda zadaná hodnota parametru `xml:lang`je platná konstrukce pro tyto třídy.</span><span class="sxs-lookup"><span data-stu-id="1204d-116">When interpreted by XAML writers of .NET Framework XAML Services, an `xml:lang` value can create <xref:System.Windows.Markup.XmlLanguage> or <xref:System.Globalization.CultureInfo> objects in the underlying object representation; however, that behavior depends on whether the value specified for `xml:lang` is a valid construction for those classes.</span></span>  
  
 <span data-ttu-id="1204d-117">Rozhraní můžete vytvořit přidružení mezi framework definované vlastnosti a význam `xml:lang` v kódu XML s použitím <xref:System.Windows.Markup.XmlLangPropertyAttribute> pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1204d-117">Frameworks can create associations between framework-defined properties and the meaning of `xml:lang` in XML by applying <xref:System.Windows.Markup.XmlLangPropertyAttribute> to the property.</span></span>  
  
## <a name="wpf-usage-nodes"></a><span data-ttu-id="1204d-118">Uzly využití grafického subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="1204d-118">WPF Usage Nodes</span></span>  
 <span data-ttu-id="1204d-119">Pro prvky, které jsou odvozené třídy <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>, můžete ekvivalentní <xref:System.Windows.FrameworkElement.Language%2A> vlastnost závislosti místo `xml:lang` atribut.</span><span class="sxs-lookup"><span data-stu-id="1204d-119">For elements that are derived classes of <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement>, you can use the equivalent <xref:System.Windows.FrameworkElement.Language%2A> dependency property instead of the `xml:lang` attribute.</span></span> <span data-ttu-id="1204d-120">Ve výchozím nastavení <xref:System.Windows.FrameworkElement.Language%2A> vlastnost používá "en US", pokud není jinak nastavené, vlastnost prostřednictvím nebo zpracování `xml:lang` atribut.</span><span class="sxs-lookup"><span data-stu-id="1204d-120">By default, the <xref:System.Windows.FrameworkElement.Language%2A> property uses "en-US" if it is not otherwise set, either through the property or through processing the `xml:lang` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1204d-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="1204d-121">See Also</span></span>  
 [<span data-ttu-id="1204d-122">Globalizace pro grafický subsystém WPF</span><span class="sxs-lookup"><span data-stu-id="1204d-122">Globalization for WPF</span></span>](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)
