---
title: Výraz má typ &#39; &lt;typename&gt; &#39; který je typu s omezeným přístupem a nelze použít pro přístup ke členům zděděno z &#39;objekt&#39; nebo &#39;typ hodnoty&#39;
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ab4e48c93a6a3c645bf9b5cc6c536d418022ae86
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a><span data-ttu-id="e1cae-102">Výraz má typ &#39; &lt;typename&gt; &#39; který je typu s omezeným přístupem a nelze použít pro přístup ke členům zděděno z &#39;objekt&#39; nebo &#39;typ hodnoty&#39;</span><span class="sxs-lookup"><span data-stu-id="e1cae-102">Expression has the type &#39;&lt;typename&gt;&#39; which is a restricted type and cannot be used to access members inherited from &#39;Object&#39; or &#39;ValueType&#39;</span></span>
<span data-ttu-id="e1cae-103">Výraz vyhodnocen jako typ, který nemůže být modulem common language runtime (CLR) do pole, ale přistupuje k člena, který vyžaduje zabalení.</span><span class="sxs-lookup"><span data-stu-id="e1cae-103">An expression evaluates to a type that cannot be boxed by the common language runtime (CLR) but accesses a member that requires boxing.</span></span>  
  
 <span data-ttu-id="e1cae-104">*Zabalení* odkazuje na zpracování potřeba převést na typ `Object` nebo v některých případech k <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="e1cae-104">*Boxing* refers to the processing necessary to convert a type to `Object` or, on occasion, to <xref:System.ValueType>.</span></span> <span data-ttu-id="e1cae-105">Modul CLR nelze například pole určité typy struktura <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, a <xref:System.TypedReference>.</span><span class="sxs-lookup"><span data-stu-id="e1cae-105">The common language runtime cannot box certain structure types, for example <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, and <xref:System.TypedReference>.</span></span>  
  
 <span data-ttu-id="e1cae-106">Tento výraz se pokusí použít typ s omezeným přístupem pro volání metody zděděno z <xref:System.Object> nebo <xref:System.ValueType>, jako například <xref:System.Object.GetHashCode%2A> nebo <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="e1cae-106">This expression attempts to use the restricted type to call a method inherited from <xref:System.Object> or <xref:System.ValueType>, such as <xref:System.Object.GetHashCode%2A> or <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="e1cae-107">Pro přístup k této metodě, se pokusilo jazyka Visual Basic konverzi implicitní zabalení, který způsobuje, že k této chybě.</span><span class="sxs-lookup"><span data-stu-id="e1cae-107">To access this method, Visual Basic has attempted an implicit boxing conversion that causes this error.</span></span>  
  
 <span data-ttu-id="e1cae-108">**ID chyby:** BC31393</span><span class="sxs-lookup"><span data-stu-id="e1cae-108">**Error ID:** BC31393</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e1cae-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="e1cae-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="e1cae-110">Vyhledejte výraz, který se vyhodnocuje citovaný typu.</span><span class="sxs-lookup"><span data-stu-id="e1cae-110">Locate the expression that evaluates to the cited type.</span></span>  
  
2.  <span data-ttu-id="e1cae-111">Vyhledejte část údajů, které se pokusí zavolat metodu zděděno z <xref:System.Object> nebo <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="e1cae-111">Locate the part of your statement that attempts to call the method inherited from <xref:System.Object> or <xref:System.ValueType>.</span></span>  
  
3.  <span data-ttu-id="e1cae-112">Přepište příkaz tak, aby se zabránilo volání metody.</span><span class="sxs-lookup"><span data-stu-id="e1cae-112">Rewrite the statement to avoid the method call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1cae-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1cae-113">See Also</span></span>  
 [<span data-ttu-id="e1cae-114">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="e1cae-114">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
