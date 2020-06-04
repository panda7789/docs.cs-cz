---
title: První příkaz tohoto výrazu 'Sub New' musí být volání 'MyBase.New' nebo 'MyClass.New' (žádný dostupný konstruktor bez parametrů).
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: 2b9d2568fb64e4af72733ad1f3dee58aaee650e5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402976"
---
# <a name="first-statement-of-this-sub-new-must-be-a-call-to-mybasenew-or-myclassnew-no-accessible-constructor-without-parameters"></a>První příkaz tohoto výrazu 'Sub New' musí být volání 'MyBase.New' nebo 'MyClass.New' (žádný dostupný konstruktor bez parametrů).
Prvním příkazem této metody Sub New musí být volání MyBase. New nebo MyClass. New, protože základní třída \<basename> pro \<derivedname> nemá přístupnou proceduru Sub New, kterou je možné volat bez argumentů.  
  
 V odvozené třídě musí každý konstruktor volat konstruktor základní třídy ( `MyBase.New` ). Pokud má základní třída konstruktor bez parametrů, který je přístupný pro odvozené třídy, `MyBase.New` může být volána automaticky. V takovém případě musí být konstruktor základní třídy volán s parametry a tuto hodnotu nelze provést automaticky. V tomto případě musí první příkaz každého konstruktoru odvozené třídy volat parametrizovaný konstruktor pro základní třídu nebo volat jiný konstruktor v odvozené třídě, která vytvoří volání konstruktoru základní třídy.  
  
 **ID chyby:** BC30148  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Buď zavolejte `MyBase.New` , zadejte požadované parametry, nebo zavolejte rovnocenný konstruktor, který provádí takové volání.  
  
     Například pokud má základní třída konstruktor, který je deklarován jako `Public Sub New(ByVal index as Integer)` , první příkaz v konstruktoru odvozené třídy může být `MyBase.New(100)` .  
  
## <a name="see-also"></a>Viz také

- [Základní informace o dědičnosti](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
