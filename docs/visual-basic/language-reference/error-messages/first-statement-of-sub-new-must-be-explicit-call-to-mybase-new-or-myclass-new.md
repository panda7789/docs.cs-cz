---
title: "Prvním příkazem této procedury 'Sub New' musí být explicitní volání 'MyBase.New' nebo 'MyClass.New', protože konstruktor '<constructorname>' v třídě Base '<baseclassname>' pro '<derivedclassname>' je označen jako zastaralý: <errormessage>"
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 33dd15e3f5f5538963597f2b00f4214895e1f47a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403002"
---
# <a name="first-statement-of-this-sub-new-must-be-an-explicit-call-to-mybasenew-or-myclassnew-because-the-constructorname-in-the-base-class-baseclassname-of-derivedclassname-is-marked-obsolete-errormessage"></a>Prvním příkazem této procedury 'Sub New' musí být explicitní volání 'MyBase.New' nebo 'MyClass.New', protože konstruktor '\<constructorname>' v třídě Base '\<baseclassname>' pro '\<derivedclassname>' je označen jako zastaralý: \<errormessage>
Konstruktor třídy explicitně nevolá konstruktor základní třídy a implicitní konstruktor základní třídy je označen <xref:System.ObsoleteAttribute> atributem a direktivou, která má být považována za chybu.  
  
 Když konstruktor odvozené třídy nevolá konstruktor základní třídy, Visual Basic se pokusí vygenerovat implicitní volání konstruktoru základní třídy bez parametrů. Pokud není k dispozici žádný konstruktor v základní třídě, který lze volat bez argumentů, Visual Basic nemůže generovat implicitní volání. V tomto případě je požadovaný konstruktor označen <xref:System.ObsoleteAttribute> atributem, takže Visual Basic nemůže volat.  
  
 Můžete označit libovolný prvek programování, který se už nepoužívá, a to tak, že <xref:System.ObsoleteAttribute> se na něj aplikuje. Pokud to uděláte, můžete vlastnost atributu nastavit <xref:System.ObsoleteAttribute.IsError%2A> na buď `True` nebo `False` . Nastavíte-li na `True` , kompilátor považuje pokus o použití prvku jako chyby. Nastavíte-li na `False` nebo jako výchozí `False` , kompilátor vydá upozornění, pokud dojde k pokusu o použití prvku.  
  
 **ID chyby:** BC30920  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Projděte si chybovou zprávu v uvozovkách a proveďte příslušnou akci.  
  
2. Zahrňte volání `MyBase.New()` nebo `MyClass.New()` jako první příkaz `Sub New` v odvozené třídě.  
  
## <a name="see-also"></a>Viz také

- [Přehled atributů](../../programming-guide/concepts/attributes/index.md)
