---
title: Podpora Namespace v modelu DOM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0548ead-0fed-41ee-b33e-117ba900d3bc
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3145df6517df9db580bfcc5d67edd9d1a61f290b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="namespace-support-in-the-dom"></a><span data-ttu-id="d7b7e-102">Podpora Namespace v modelu DOM</span><span class="sxs-lookup"><span data-stu-id="d7b7e-102">Namespace Support in the DOM</span></span>
<span data-ttu-id="d7b7e-103">XML modelu DOM (Document Object) je zcela clustery pro obor názvů.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-103">The XML Document Object Model (DOM) is completely namespace-aware.</span></span> <span data-ttu-id="d7b7e-104">Jsou podporovány pouze deklaracemi obor názvů XML dokumenty.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-104">Only namespace-aware XML documents are supported.</span></span> <span data-ttu-id="d7b7e-105">World Wide Web Consortium (W3C) určuje, že může být jiný obor názvů s deklaracemi DOM aplikace, které implementují úrovně 1 a DOM Level 2 funkce jsou clustery pro obor názvů.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-105">The World Wide Web Consortium (W3C) specifies that DOM applications that implement Level 1 can be non-namespace-aware, and DOM Level 2 features are namespace-aware.</span></span> <span data-ttu-id="d7b7e-106">Všechny funkce v modelu DOM XML jsou však obor názvů deklaracemi bez ohledu na to, pokud je metoda z úrovně 1 nebo úrovně 2 DOM doporučení.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-106">However, all features in the XML DOM are namespace-aware, regardless if the method is from the Level 1 or Level 2 DOM Recommendation.</span></span>  
  
 <span data-ttu-id="d7b7e-107">Například v nastavení jiný obor názvů s deklaracemi, volání `setAttribute("A:b", "123")`, jak je uvedeno v modelu DOM úrovně 1 doporučení, nevede atribut s předponou `A` a pro místní název `b`.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-107">For example, in a non-namespace-aware setting, calling `setAttribute("A:b", "123")`, as specified in the DOM Level 1 Recommendation, does not result in an attribute with a prefix of `A` and a local name of `b`.</span></span> <span data-ttu-id="d7b7e-108">Výsledkem by atributu s hodnotou `A:b`.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-108">It would result in an attribute with the value `A:b`.</span></span>  
  
 <span data-ttu-id="d7b7e-109">V prostředí využívající technologii obor názvů, volání DOM Level 2 `setAttribute("A:b", "123")` výsledků v atributu s předponou `A` a pro místní název `b`.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-109">In a namespace-aware environment, the call to the DOM Level 2 `setAttribute("A:b", "123")` results in an attribute with a prefix of `A` and a local name of `b`.</span></span> <span data-ttu-id="d7b7e-110">Toto je, jak rozhraní Microsoft .NET Framework DOM funguje.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-110">This is how the Microsoft .NET Framework DOM works.</span></span>  
  
 <span data-ttu-id="d7b7e-111">Pro všechny metody, která přebírají parametr name, je proto tyto metody také mít předponu pro kvalifikaci název.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-111">Therefore, for all methods that take a name parameter, these methods also take a prefix to qualify the name.</span></span> <span data-ttu-id="d7b7e-112">Parametr name, jako `A:b` v **setAttribute** metoda DOM úrovně 1, je analyzována následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="d7b7e-112">The name parameter, such as the `A:b` in the **setAttribute** DOM Level 1 method, is parsed as follows:</span></span>  
  
-   <span data-ttu-id="d7b7e-113">Pokud neexistují žádné dvojtečky (:), pak je nastavit místní název `name` parametr a předponu a NamespaceURI jsou prázdné řetězce.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-113">If there are no colon (:) characters, then the local name is set to the `name` parameter, and the prefix and NamespaceURI are empty strings.</span></span>  
  
-   <span data-ttu-id="d7b7e-114">Pokud se najde dvojtečkou název rozdělit na dvě části na základě pozice prvního znaku dvojtečkou.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-114">If a colon is found, then the name is split into two parts based on the position of the first colon character.</span></span> <span data-ttu-id="d7b7e-115">Předpona, která je nastavena na nalezen před dvojtečkou řetězec a místní název je nastaven na řetězec nalezen po dvojtečkou.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-115">The prefix is set to the string found before the colon, and local name is set to the string found after the colon.</span></span> <span data-ttu-id="d7b7e-116">Pro metody, které nepřebírají hodnotu NamespaceURI NamespaceURI není vyřešený a zůstane nastavit na prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-116">For methods that do not take a NamespaceURI value, the NamespaceURI is not resolved and remains set to empty string.</span></span> <span data-ttu-id="d7b7e-117">NamespaceURI, jinak hodnota nastavena na řetězec předaný metodě.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-117">Otherwise, the NamespaceURI is set to the string passed to the method.</span></span> <span data-ttu-id="d7b7e-118">Pokud předponu není definován, pak se **Uložit** metoda a **InnerXml** a **OuterXml** vlastnosti služeb při selhání.</span><span class="sxs-lookup"><span data-stu-id="d7b7e-118">If the prefix is undefined, then the **Save** method and **InnerXml** and **OuterXml** properties fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7b7e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7b7e-119">See Also</span></span>  
 [<span data-ttu-id="d7b7e-120">XML Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="d7b7e-120">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
