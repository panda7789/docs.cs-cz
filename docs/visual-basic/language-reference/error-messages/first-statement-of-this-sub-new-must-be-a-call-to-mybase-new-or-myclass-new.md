---
title: První příkaz tohoto &#39;Sub New&#39; musí být volání &#39;MyBase.New&#39; nebo &#39;MyClass.New&#39; (žádný dostupný konstruktor bez parametrů)
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: 3b24385932700a4843ae295bc82ef9529cc86b9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="first-statement-of-this-39sub-new39-must-be-a-call-to-39mybasenew39-or-39myclassnew39-no-accessible-constructor-without-parameters"></a>První příkaz tohoto &#39;Sub New&#39; musí být volání &#39;MyBase.New&#39; nebo &#39;MyClass.New&#39; (žádný dostupný konstruktor bez parametrů)
Prvním příkazem 'Sub New' musí být volání 'MyBase.New' nebo 'MyClass.New', protože základní třídy\<basename >' z '\<derivedname >' nemá k přístupné 'Sub New, kterou lze volat bez argumentů.  
  
 V odvozené třídě, musí každý konstruktor volání konstruktoru základní třídy (`MyBase.New`). Pokud má konstruktor bez parametrů, které je přístupné pro odvozené třídy základní třídy `MyBase.New` může být automaticky volána. Pokud ne, konstruktoru základní třídy musí být volána s parametry, a to není možné automaticky. V takovém případě první příkaz každých konstruktoru odvozené třídy musí volat parametrizované konstruktor pro základní třídu nebo volání jiného konstruktoru odvozené třídy, která vytváří volání konstruktoru základní třídy.  
  
 **ID chyby:** BC30148  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Buď volání `MyBase.New` poskytnutí požadované parametry, nebo volejte sdílené konstruktor, který provede tyto volání.  
  
     Například, pokud základní třída má konstruktor, který je deklarován jako `Public Sub New(ByVal index as Integer)`, první příkaz v odvozené třídy konstruktor může být `MyBase.New(100)`.  
  
## <a name="see-also"></a>Viz také  
 [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
