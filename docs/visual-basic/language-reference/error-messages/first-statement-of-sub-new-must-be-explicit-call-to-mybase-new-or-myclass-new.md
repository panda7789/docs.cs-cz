---
title: 'První příkaz tohoto &#39;Sub New&#39; musí být explicitní volání &#39;MyBase.New&#39; nebo &#39;MyClass.New&#39; protože &#39; &lt;constructorname&gt; &#39; v základní třídě &#39; &lt;baseclassname&gt; &#39; z &#39; &lt;derivedclassname&gt; &#39; je označen jako zastaralý: &#39; &lt;errormessage&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: dbce2a9edcc38ff137cb7ec0c97e5c259c0a0979
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589890"
---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a><span data-ttu-id="e0376-102">První příkaz tohoto &#39;Sub New&#39; musí být explicitní volání &#39;MyBase.New&#39; nebo &#39;MyClass.New&#39; protože &#39; &lt;constructorname&gt; &#39; v základní třídě &#39; &lt;baseclassname&gt; &#39; z &#39; &lt;derivedclassname&gt; &#39; je označen jako zastaralý: &#39; &lt;errormessage&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="e0376-102">First statement of this &#39;Sub New&#39; must be an explicit call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; because the &#39;&lt;constructorname&gt;&#39; in the base class &#39;&lt;baseclassname&gt;&#39; of &#39;&lt;derivedclassname&gt;&#39; is marked obsolete: &#39;&lt;errormessage&gt;&#39;</span></span>
<span data-ttu-id="e0376-103">Konstruktoru třídy nevyvolá explicitně konstruktoru základní třídy a konstruktoru implicitní základní třídy je označené jako <xref:System.ObsoleteAttribute> atribut a direktiva k považovat za chybu.</span><span class="sxs-lookup"><span data-stu-id="e0376-103">A class constructor does not explicitly call a base class constructor, and the implicit base class constructor is marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as an error.</span></span>  
  
 <span data-ttu-id="e0376-104">Když konstruktoru odvozené třídy základní třídy konstruktor nevolá, pokusí se jazyka Visual Basic generovat volání implicitní konstruktor bez parametrů základní třídy.</span><span class="sxs-lookup"><span data-stu-id="e0376-104">When a derived class constructor does not call a base class constructor, Visual Basic attempts to generate an implicit call to a parameterless base class constructor.</span></span> <span data-ttu-id="e0376-105">Pokud neexistuje žádný dostupný konstruktor v základní třídy, kterou lze volat bez argumentů, Visual Basic nelze vygenerovat implicitní volání.</span><span class="sxs-lookup"><span data-stu-id="e0376-105">If there is no accessible constructor in the base class that can be called without arguments, Visual Basic cannot generate an implicit call.</span></span> <span data-ttu-id="e0376-106">V takovém případě je označené požadovaný konstruktor <xref:System.ObsoleteAttribute> atributů, takže ji nelze volat jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e0376-106">In this case, the required constructor is marked with the <xref:System.ObsoleteAttribute> attribute, so Visual Basic cannot call it.</span></span>  
  
 <span data-ttu-id="e0376-107">Můžete označit jakékoli programovací element se už používá použitím <xref:System.ObsoleteAttribute> k němu.</span><span class="sxs-lookup"><span data-stu-id="e0376-107">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="e0376-108">Pokud to uděláte, můžete nastavit atributu <xref:System.ObsoleteAttribute.IsError%2A> vlastnost, která má buď `True` nebo `False`.</span><span class="sxs-lookup"><span data-stu-id="e0376-108">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="e0376-109">Pokud je nastavena na `True`, kompilátor zpracovává pokus o použití elementu za chybu.</span><span class="sxs-lookup"><span data-stu-id="e0376-109">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="e0376-110">Pokud je nastavena na `False`, nebo ho nechte výchozí `False`, kompilátor vydá upozornění, pokud dojde pokusu o použití elementu.</span><span class="sxs-lookup"><span data-stu-id="e0376-110">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="e0376-111">**ID chyby:** BC30920</span><span class="sxs-lookup"><span data-stu-id="e0376-111">**Error ID:** BC30920</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e0376-112">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="e0376-112">To correct this error</span></span>  
  
1.  <span data-ttu-id="e0376-113">Zkontrolujte uvozovkách chybovou zprávu a proveďte příslušnou akci.</span><span class="sxs-lookup"><span data-stu-id="e0376-113">Examine the quoted error message and take appropriate action.</span></span>  
  
2.  <span data-ttu-id="e0376-114">Zahrnout volání `MyBase.New()` nebo `MyClass.New()` jako první příkaz tohoto výrazu `Sub New` v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="e0376-114">Include a call to `MyBase.New()` or `MyClass.New()` as the first statement of the `Sub New` in the derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0376-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0376-115">See Also</span></span>  
 [<span data-ttu-id="e0376-116">Přehled atributy</span><span class="sxs-lookup"><span data-stu-id="e0376-116">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
