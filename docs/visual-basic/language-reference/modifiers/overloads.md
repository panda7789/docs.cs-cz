---
title: "Přetížení (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Overloads
- Overloads
helpviewer_keywords:
- Overloads keyword [Visual Basic]
- hiding by signature
- Shadows keyword [Visual Basic]
- signature, hiding by
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a23a6b91681cbd814ac96464e1c340be99a0ecf0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="overloads-visual-basic"></a>Přetížení (Visual Basic)
Určuje, že vlastnost nebo postup redeclares existující vlastnosti nebo postupy se stejným názvem.  
  
## <a name="remarks"></a>Poznámky  
 *Přetížení* je postupem poskytnutí více než jednu definici pro danou vlastnost nebo postup název ve stejném oboru. Redeclaring vlastnosti nebo postup pomocí různých podpisu se někdy označuje jako *skrytí podle podpisu*.  
  
## <a name="rules"></a>Pravidla  
  
-   **Kontext deklarace.** Můžete použít `Overloads` jenom v příkazu deklarace vlastnosti nebo postupu.  
  
-   **Kombinovaná parametrů.** Nelze zadat `Overloads` společně s [stínů](../../../visual-basic/language-reference/modifiers/shadows.md) v deklaraci stejný postup.  
  
-   **Vyžaduje rozdíly.** *Podpis* v tomto prohlášení musí být odlišný od podpis každé vlastnosti nebo procedury, která ho přetížení. Podpis zahrnuje název vlastnosti nebo postup společně s následující:  
  
    -   počet parametrů  
  
    -   pořadí parametrů  
  
    -   datové typy parametrů  
  
    -   počet parametrů typu (pro obecný postup)  
  
    -   Návratový typ (pouze pro proceduru operátor převodu)  
  
     Všechny přetížení musí mít stejný název, ale každý se musí lišit od všech ostatních počítačů v jedné nebo více předchozích ohledech. To umožňuje kompilátoru k rozlišení, kterou verzi má použijte, pokud kód volá vlastnost nebo postupu.  
  
-   **Nepovolené rozdíly.** Změna jednoho nebo více následujících není platný pro přetížení vlastnosti nebo postupu, protože nejsou součástí podpis:  
  
    -   zda vrátí hodnotu (pro proceduru)  
  
    -   datový typ vrácené hodnoty (s výjimkou operátora převodu)  
  
    -   názvy parametrů nebo parametry typu  
  
    -   omezení parametrů typů (pro obecný postup)  
  
    -   klíčová slova – modifikátor parametrů (například `ByRef` nebo `Optional`)  
  
    -   Vlastnost nebo postup modifikátor klíčová slova (například `Public` nebo `Shared`)  
  
-   **Volitelné modifikátor.** Není nutné použít `Overloads` modifikátor při definování více přetížené vlastnosti nebo postupy ve stejné třídě. Ale pokud používáte `Overloads` v jednom z deklarací, musíte použít ji ve všech z nich.  
  
-   **Stínový provoz a přetížení.** `Overloads`Můžete také použít stínové existujícího člena nebo sadu přetěžované členy v základní třídě. Při použití `Overloads` tímto způsobem je deklarovat vlastnosti nebo metody se stejným názvem a stejný seznam parametrů jako člen základní třídy a nezadáte `Shadows` – klíčové slovo.  
  
 Pokud používáte `Overrides`, kompilátor implicitně přidá `Overloads` tak, aby vaše knihovna rozhraní API pro práci s C# snadněji.  
  
 `Overloads` Modifikátor lze použít v těchto kontexty:  
  
 [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator – příkaz](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [Stínů](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Přetížení procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Postupy: definice operátora převodu](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
