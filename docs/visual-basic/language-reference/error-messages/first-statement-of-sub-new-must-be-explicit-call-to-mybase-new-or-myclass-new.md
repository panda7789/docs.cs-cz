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
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a>První příkaz to & č. 39; Sub – nové & č. 39; musí být explicitní volání & č. 39; MyBase.New & č. 39; nebo & č. 39; MyClass.New & č. 39; protože & č. 39; &lt;constructorname&gt;& č. 39; v základní třídě & č. 39;&lt; baseclassname&gt;& č. 39; & č. 39;&lt; derivedclassname&gt;& č. 39; je označen jako zastaralý: & č. 39;&lt; errorMessage&gt;& č. 39;
Konstruktoru třídy nevyvolá explicitně konstruktoru základní třídy a konstruktoru implicitní základní třídy je označené jako <xref:System.ObsoleteAttribute> atribut a direktiva k považovat za chybu.  
  
 Když konstruktoru odvozené třídy nevyvolá konstruktoru základní třídy, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pokusí generovat volání implicitní konstruktor bez parametrů základní třídy. Pokud neexistuje žádný dostupný konstruktor v základní třídy, kterou lze volat bez argumentů, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] nelze generovat implicitní volání. V takovém případě je označené požadovaný konstruktor <xref:System.ObsoleteAttribute> atribut, tak [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] nelze volat.  
  
 Můžete označit jakékoli programovací element se už používá použitím <xref:System.ObsoleteAttribute> k němu. Pokud to uděláte, můžete nastavit atributu <xref:System.ObsoleteAttribute.IsError%2A> vlastnost, která má buď `True` nebo `False`. Pokud je nastavena na `True`, kompilátor zpracovává pokus o použití elementu za chybu. Pokud je nastavena na `False`, nebo ho nechte výchozí `False`, kompilátor vydá upozornění, pokud dojde pokusu o použití elementu.  
  
 **ID chyby:** BC30920  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte uvozovkách chybovou zprávu a proveďte příslušnou akci.  
  
2.  Zahrnout volání `MyBase.New()` nebo `MyClass.New()` jako první příkaz tohoto výrazu `Sub New` v odvozené třídě.  
  
## <a name="see-also"></a>Viz také  
 [Přehled atributy](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
