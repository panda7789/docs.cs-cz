---
title: 'První příkaz tohoto &#39;Sub New&#39; musí být explicitní volání &#39;MyBase.New&#39; nebo &#39;MyClass.New&#39; protože &#39; &lt;constructorname&gt; &#39; v základní třídě &#39; &lt;baseclassname&gt; &#39; z &#39; &lt;derivedclassname&gt; &#39; je označen jako zastaralý: &#39; &lt;errormessage&gt;&#39;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7690c9dcdb97e63959d2f0e31791d55ee7b09ffc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a>První příkaz tohoto &#39;Sub New&#39; musí být explicitní volání &#39;MyBase.New&#39; nebo &#39;MyClass.New&#39; protože &#39; &lt;constructorname&gt; &#39; v základní třídě &#39; &lt;baseclassname&gt; &#39; z &#39; &lt;derivedclassname&gt; &#39; je označen jako zastaralý: &#39; &lt;errormessage&gt;&#39;
Konstruktoru třídy nevyvolá explicitně konstruktoru základní třídy a konstruktoru implicitní základní třídy je označené jako <xref:System.ObsoleteAttribute> atribut a direktiva k považovat za chybu.  
  
 Když konstruktoru odvozené třídy základní třídy konstruktor nevolá, pokusí se jazyka Visual Basic generovat volání implicitní konstruktor bez parametrů základní třídy. Pokud neexistuje žádný dostupný konstruktor v základní třídy, kterou lze volat bez argumentů, Visual Basic nelze vygenerovat implicitní volání. V takovém případě je označené požadovaný konstruktor <xref:System.ObsoleteAttribute> atributů, takže ji nelze volat jazyka Visual Basic.  
  
 Můžete označit jakékoli programovací element se už používá použitím <xref:System.ObsoleteAttribute> k němu. Pokud to uděláte, můžete nastavit atributu <xref:System.ObsoleteAttribute.IsError%2A> vlastnost, která má buď `True` nebo `False`. Pokud je nastavena na `True`, kompilátor zpracovává pokus o použití elementu za chybu. Pokud je nastavena na `False`, nebo ho nechte výchozí `False`, kompilátor vydá upozornění, pokud dojde pokusu o použití elementu.  
  
 **ID chyby:** BC30920  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte uvozovkách chybovou zprávu a proveďte příslušnou akci.  
  
2.  Zahrnout volání `MyBase.New()` nebo `MyClass.New()` jako první příkaz tohoto výrazu `Sub New` v odvozené třídě.  
  
## <a name="see-also"></a>Viz také  
 [Přehled atributy](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
