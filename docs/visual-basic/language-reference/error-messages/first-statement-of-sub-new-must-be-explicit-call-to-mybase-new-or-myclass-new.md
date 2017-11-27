---
title: "První příkaz to & č. 39; Sub – nové & č. 39; musí být explicitní volání & č. 39; MyBase.New & č. 39; nebo & č. 39; MyClass.New & č. 39; protože & č. 39; &lt;constructorname&gt;& č. 39; v základní třídě & č. 39;&lt; baseclassname&gt;& č. 39; & č. 39;&lt; derivedclassname&gt;& č. 39; je označen jako zastaralý: & č. 39;&lt; errorMessage&gt;& č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords: BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8882acd947251d85804fbefd54267ce078e31b95
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a><span data-ttu-id="b404d-102">První příkaz to & č. 39; Sub – nové & č. 39; musí být explicitní volání & č. 39; MyBase.New & č. 39; nebo & č. 39; MyClass.New & č. 39; protože & č. 39; &lt;constructorname&gt;& č. 39; v základní třídě & č. 39;&lt; baseclassname&gt;& č. 39; & č. 39;&lt; derivedclassname&gt;& č. 39; je označen jako zastaralý: & č. 39;&lt; errorMessage&gt;& č. 39;</span><span class="sxs-lookup"><span data-stu-id="b404d-102">First statement of this &#39;Sub New&#39; must be an explicit call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; because the &#39;&lt;constructorname&gt;&#39; in the base class &#39;&lt;baseclassname&gt;&#39; of &#39;&lt;derivedclassname&gt;&#39; is marked obsolete: &#39;&lt;errormessage&gt;&#39;</span></span>
<span data-ttu-id="b404d-103">Konstruktoru třídy nevyvolá explicitně konstruktoru základní třídy a konstruktoru implicitní základní třídy je označené jako <xref:System.ObsoleteAttribute> atribut a direktiva k považovat za chybu.</span><span class="sxs-lookup"><span data-stu-id="b404d-103">A class constructor does not explicitly call a base class constructor, and the implicit base class constructor is marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as an error.</span></span>  
  
 <span data-ttu-id="b404d-104">Když konstruktoru odvozené třídy nevyvolá konstruktoru základní třídy, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pokusí generovat volání implicitní konstruktor bez parametrů základní třídy.</span><span class="sxs-lookup"><span data-stu-id="b404d-104">When a derived class constructor does not call a base class constructor, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] attempts to generate an implicit call to a parameterless base class constructor.</span></span> <span data-ttu-id="b404d-105">Pokud neexistuje žádný dostupný konstruktor v základní třídy, kterou lze volat bez argumentů, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] nelze generovat implicitní volání.</span><span class="sxs-lookup"><span data-stu-id="b404d-105">If there is no accessible constructor in the base class that can be called without arguments, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] cannot generate an implicit call.</span></span> <span data-ttu-id="b404d-106">V takovém případě je označené požadovaný konstruktor <xref:System.ObsoleteAttribute> atribut, tak [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] nelze volat.</span><span class="sxs-lookup"><span data-stu-id="b404d-106">In this case, the required constructor is marked with the <xref:System.ObsoleteAttribute> attribute, so [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] cannot call it.</span></span>  
  
 <span data-ttu-id="b404d-107">Můžete označit jakékoli programovací element se už používá použitím <xref:System.ObsoleteAttribute> k němu.</span><span class="sxs-lookup"><span data-stu-id="b404d-107">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="b404d-108">Pokud to uděláte, můžete nastavit atributu <xref:System.ObsoleteAttribute.IsError%2A> vlastnost, která má buď `True` nebo `False`.</span><span class="sxs-lookup"><span data-stu-id="b404d-108">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="b404d-109">Pokud je nastavena na `True`, kompilátor zpracovává pokus o použití elementu za chybu.</span><span class="sxs-lookup"><span data-stu-id="b404d-109">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="b404d-110">Pokud je nastavena na `False`, nebo ho nechte výchozí `False`, kompilátor vydá upozornění, pokud dojde pokusu o použití elementu.</span><span class="sxs-lookup"><span data-stu-id="b404d-110">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="b404d-111">**ID chyby:** BC30920</span><span class="sxs-lookup"><span data-stu-id="b404d-111">**Error ID:** BC30920</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b404d-112">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b404d-112">To correct this error</span></span>  
  
1.  <span data-ttu-id="b404d-113">Zkontrolujte uvozovkách chybovou zprávu a proveďte příslušnou akci.</span><span class="sxs-lookup"><span data-stu-id="b404d-113">Examine the quoted error message and take appropriate action.</span></span>  
  
2.  <span data-ttu-id="b404d-114">Zahrnout volání `MyBase.New()` nebo `MyClass.New()` jako první příkaz tohoto výrazu `Sub New` v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="b404d-114">Include a call to `MyBase.New()` or `MyClass.New()` as the first statement of the `Sub New` in the derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b404d-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="b404d-115">See Also</span></span>  
 [<span data-ttu-id="b404d-116">Přehled atributy</span><span class="sxs-lookup"><span data-stu-id="b404d-116">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
