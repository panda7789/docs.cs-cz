---
title: 'Prvním příkazem této &#39;proceduru Sub New&#39; musí být explicitní volání konstruktoru &#39;MyBase.New&#39; nebo &#39;MyClass.New&#39; vzhledem k tomu, &#39; &lt;constructorname&gt; &#39; v základní třídě &#39; &lt;baseclassname&gt; &#39; z &#39; &lt;derivedclassname&gt; &#39; je označená jako zastaralá: &#39; &lt;errormessage&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 9d07a68fd8d9790178427c512375323f23f46772
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566770"
---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a>Prvním příkazem této &#39;proceduru Sub New&#39; musí být explicitní volání konstruktoru &#39;MyBase.New&#39; nebo &#39;MyClass.New&#39; vzhledem k tomu, &#39; &lt;constructorname&gt; &#39; v základní třídě &#39; &lt;baseclassname&gt; &#39; z &#39; &lt;derivedclassname&gt; &#39; je označená jako zastaralá: &#39; &lt;errormessage&gt;&#39;
Konstruktor třídy explicitně volat konstruktor základní třídy a konstruktoru implicitní základní třídy je označený <xref:System.ObsoleteAttribute> atribut a směrnice považovat za chybu.  
  
 Když konstruktoru odvozené třídy volat konstruktor základní třídy, Visual Basic se pokusí vygenerovat implicitní volání konstruktoru bez parametrů základní třídy. Pokud není žádný dostupný konstruktor v základní třídě, kterou lze volat bez argumentů, Visual Basic nelze generovat implicitní volání. V takovém případě je požadovaný konstruktor označený atributem <xref:System.ObsoleteAttribute> atribut, takže ji nelze volat jazyka Visual Basic.  
  
 Můžete označit libovolný programovací element jako se už používá použitím <xref:System.ObsoleteAttribute> k němu. Pokud to uděláte, můžete nastavit atributu <xref:System.ObsoleteAttribute.IsError%2A> vlastnost buď `True` nebo `False`. Pokud ji nastavíte na `True`, kompilátor zpracovává pokus o použití prvku za chybu. Pokud ji nastavíte na `False`, nebo jej jako výchozí `False`, kompilátor vyvolá upozornění, pokud se pokus o použití elementu.  
  
 **ID chyby:** BC30920  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte v uvozovkách chybovou zprávu a proveďte příslušné akce.  
  
2.  Zahrnout volání `MyBase.New()` nebo `MyClass.New()` jako prvním příkazem `Sub New` v odvozené třídě.  
  
## <a name="see-also"></a>Viz také:
- [Přehled atributy](../../../visual-basic/programming-guide/concepts/attributes/index.md)

