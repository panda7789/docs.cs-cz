---
title: Konstruktor '<name>' nemůže volat sám sebe.
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 6abb6dde624e129b52fefecf8c51e6cde2567ae1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409800"
---
# <a name="constructor-name-cannot-call-itself"></a>Konstruktor '\<name>' nemůže volat sám sebe.
`Sub New`Procedura ve třídě nebo struktuře volá sama sebe.  
  
 Účelem konstruktoru je inicializace instance třídy nebo struktury při jejím prvním vytvoření. Třída nebo struktura může mít několik konstruktorů za předpokladu, že všechny mají jiný seznam parametrů. Konstruktor je povolen pro volání jiného konstruktoru, aby se jeho funkce mohla provádět navíc. Nejedná se ale o stejný konstruktor, který by sám volal, a ve skutečnosti by to vedlo k nekonečné rekurzi, pokud je to povoleno.  
  
 **ID chyby:** BC30298  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Ověřte seznam parametrů volaného konstruktoru. Měl by být jiný než konstruktor, který provádí volání.  
  
2. Pokud nechcete volat jiný konstruktor, odeberte `Sub New` volání zcela.  
  
## <a name="see-also"></a>Viz také

- [Doba života objektu: Vytváření a zničení objektů](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
