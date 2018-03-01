---
title: "Konstruktor & č. 39; &lt;název&gt;& č. 39; nelze volat sám sebe"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2361d6f4d710e17a4f4e29ac03bfde523191fa83
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="constructor-39ltnamegt39-cannot-call-itself"></a>Konstruktor & č. 39; &lt;název&gt;& č. 39; nelze volat sám sebe
A `Sub New` postup ve třídě nebo struktuře volá sám sebe.  
  
 Účelem konstruktor je k inicializaci instance třídy nebo struktura při prvním vytvoření. Třídu nebo strukturu může mít několik konstruktorů za podmínky, že všechny seznamy různých parametrů. Konstruktor může volat jiný konstruktor provést jeho funkčnost kromě vlastní. Ale je smysl pro konstruktor volat sám a ve skutečnosti výsledkem by nekonečná rekurze Pokud povolena.  
  
 **ID chyby:** BC30298  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte seznam parametr konstruktoru volána. Musí být z konstruktoru uskutečněním hovoru.  
  
2.  Pokud nemáte v úmyslu volat jiný konstruktor, odeberte `Sub New` zcela volání.  
  
## <a name="see-also"></a>Viz také  
 [Doba života objektu: Objekty vytváření a zničení](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
