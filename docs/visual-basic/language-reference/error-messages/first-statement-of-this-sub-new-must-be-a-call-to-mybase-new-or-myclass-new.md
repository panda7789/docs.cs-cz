---
title: Prvním příkazem této &#39;proceduru Sub New&#39; musí být volání konstruktoru &#39;MyBase.New&#39; nebo &#39;MyClass.New&#39; (žádný dostupný konstruktor bez parametrů)
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: 75832ae88908094c1cb74ce04ad84c0d2ae91e68
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728892"
---
# <a name="first-statement-of-this-39sub-new39-must-be-a-call-to-39mybasenew39-or-39myclassnew39-no-accessible-constructor-without-parameters"></a>Prvním příkazem této &#39;proceduru Sub New&#39; musí být volání konstruktoru &#39;MyBase.New&#39; nebo &#39;MyClass.New&#39; (žádný dostupný konstruktor bez parametrů)
Prvním příkazem této 'Sub New musí být volání 'MyBase.New' nebo 'MyClass.New', protože základní třída\<basename > "z"\<derivedname >' nemá přístupné 'Sub New, kterou lze volat bez argumentů.  
  
 V odvozené třídě, musí každý konstruktor volat konstruktor základní třídy (`MyBase.New`). Pokud základní třída nemá konstruktor bez parametrů, který je přistupovat k odvozeným třídám `MyBase.New` může být automaticky volána. V opačném případě musí být volána konstruktor základní třídy s parametry, a to nemůže udělat automaticky. V tomto případě první příkaz každý konstruktoru odvozené třídy musí volat do parametrizovaného konstruktoru v základní třídě nebo volání jiného konstruktoru v odvozené třídě, která provádí volání konstruktoru základní třídy.  
  
 **ID chyby:** BC30148  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Buď zavolat `MyBase.New` poskytnutí požadovaných parametrů, nebo volat konstruktor druhé strany, která provádí těchto volání.  
  
     Například, pokud základní třída nemá konstruktor, který je deklarován jako `Public Sub New(ByVal index as Integer)`, první příkaz v odvozený konstruktor třídy může být `MyBase.New(100)`.  
  
## <a name="see-also"></a>Viz také:
- [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
