---
title: Konstruktor &#39; &lt;název&gt; &#39; nemůže volat sám sebe
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 4a02277893147716098a3dcc327e221e0775d476
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662722"
---
# <a name="constructor-39ltnamegt39-cannot-call-itself"></a>Konstruktor &#39; &lt;název&gt; &#39; nemůže volat sám sebe
A `Sub New` postupu ve třídě nebo struktuře zavolá sama sebe.  
  
 Konstruktor slouží k inicializaci instance třídy nebo struktury při prvním vytvoření. Třídy nebo struktury může mít několik konstruktorů, pokud mají všechny seznamy různých parametrů. Konstruktor je povolený pro volání jiného konstruktoru k provádění svých funkcí, kromě svou vlastní. Ale je pro konstruktor k volat sám sebe a ve skutečnosti by způsobil nekonečnou rekurzi Pokud povolena.  
  
 **ID chyby:** BC30298  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte seznam parametrů volání konstruktoru. Musí být odlišný od u konstruktoru uskutečněním hovoru.  
  
2.  Pokud je nemáte v úmyslu volání jiný konstruktor, odeberte `Sub New` zcela volání.  
  
## <a name="see-also"></a>Viz také:
- [Doba života objektu: Způsob vytváření a zničení objektů](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
