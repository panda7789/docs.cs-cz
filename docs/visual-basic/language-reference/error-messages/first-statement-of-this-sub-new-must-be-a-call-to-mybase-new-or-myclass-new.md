---
title: První příkaz tohoto výrazu 'Sub New' musí být volání 'MyBase.New' nebo 'MyClass.New' (žádný dostupný konstruktor bez parametrů).
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: 160e4d512a1533b3c89a1af50b47600ca6df51c2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592048"
---
# <a name="first-statement-of-this-sub-new-must-be-a-call-to-mybasenew-or-myclassnew-no-accessible-constructor-without-parameters"></a>První příkaz tohoto výrazu 'Sub New' musí být volání 'MyBase.New' nebo 'MyClass.New' (žádný dostupný konstruktor bez parametrů).
Prvním příkazem této 'Sub New musí být volání 'MyBase.New' nebo 'MyClass.New', protože základní třída\<basename > "z"\<derivedname >' nemá přístupné 'Sub New, kterou lze volat bez argumentů.  
  
 V odvozené třídě, musí každý konstruktor volat konstruktor základní třídy (`MyBase.New`). Pokud základní třída nemá konstruktor bez parametrů, který je přistupovat k odvozeným třídám `MyBase.New` může být automaticky volána. V opačném případě musí být volána konstruktor základní třídy s parametry, a to nemůže udělat automaticky. V tomto případě první příkaz každý konstruktoru odvozené třídy musí volat do parametrizovaného konstruktoru v základní třídě nebo volání jiného konstruktoru v odvozené třídě, která provádí volání konstruktoru základní třídy.  
  
 **ID chyby:** BC30148  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Buď zavolat `MyBase.New` poskytnutí požadovaných parametrů, nebo volat konstruktor druhé strany, která provádí těchto volání.  
  
     Například, pokud základní třída nemá konstruktor, který je deklarován jako `Public Sub New(ByVal index as Integer)`, první příkaz v odvozený konstruktor třídy může být `MyBase.New(100)`.  
  
## <a name="see-also"></a>Viz také:

- [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
