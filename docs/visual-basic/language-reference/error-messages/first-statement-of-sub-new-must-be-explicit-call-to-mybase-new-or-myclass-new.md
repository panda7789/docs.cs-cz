---
title: "Prvním příkazem této procedury 'Sub New' musí být explicitní volání 'MyBase.New' nebo 'MyClass.New', protože konstruktor '<constructorname>' v třídě Base '<baseclassname>' pro '<derivedclassname>' je označen jako zastaralý: <errormessage>"
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 31f92d1e52e50b2a87fd6a6af6e3c87292f4437f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268790"
---
# <a name="first-statement-of-this-sub-new-must-be-an-explicit-call-to-mybasenew-or-myclassnew-because-the-constructorname-in-the-base-class-baseclassname-of-derivedclassname-is-marked-obsolete-errormessage"></a>Prvním příkazem této 'Sub New musí být explicitní volání 'MyBase.New' nebo 'MyClass.New', protože '\<constructorname >' v základní třídě\<baseclassname > "z"\<derivedclassname > "je označená jako zastaralá:"\< chybová zpráva > "
Konstruktor třídy explicitně volat konstruktor základní třídy a konstruktoru implicitní základní třídy je označený <xref:System.ObsoleteAttribute> atribut a směrnice považovat za chybu.  
  
 Když konstruktoru odvozené třídy volat konstruktor základní třídy, Visual Basic se pokusí vygenerovat implicitní volání konstruktoru bez parametrů základní třídy. Pokud není žádný dostupný konstruktor v základní třídě, kterou lze volat bez argumentů, Visual Basic nelze generovat implicitní volání. V takovém případě je požadovaný konstruktor označený atributem <xref:System.ObsoleteAttribute> atribut, takže ji nelze volat jazyka Visual Basic.  
  
 Můžete označit libovolný programovací element jako se už používá použitím <xref:System.ObsoleteAttribute> k němu. Pokud to uděláte, můžete nastavit atributu <xref:System.ObsoleteAttribute.IsError%2A> vlastnost buď `True` nebo `False`. Pokud ji nastavíte na `True`, kompilátor zpracovává pokus o použití prvku za chybu. Pokud ji nastavíte na `False`, nebo jej jako výchozí `False`, kompilátor vyvolá upozornění, pokud se pokus o použití elementu.  
  
 **ID chyby:** BC30920  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte v uvozovkách chybovou zprávu a proveďte příslušné akce.  
  
2.  Zahrnout volání `MyBase.New()` nebo `MyClass.New()` jako prvním příkazem `Sub New` v odvozené třídě.  
  
## <a name="see-also"></a>Viz také:
- [Přehled atributy](../../../visual-basic/programming-guide/concepts/attributes/index.md)

