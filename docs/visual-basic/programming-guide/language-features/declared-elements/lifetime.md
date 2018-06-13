---
title: Doba platnosti v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- static variables [Visual Basic], lifetime
- static variables [Visual Basic], Visual Basic
- declared elements [Visual Basic], lifetime
- Shared variable lifetime [Visual Basic]
- lifetime [Visual Basic], declared elements
- lifetime [Visual Basic], Visual Basic
- lifetime [Visual Basic]
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
ms.openlocfilehash: d32639f1c392d53a7e9f6258440b6c0925d27a5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654226"
---
# <a name="lifetime-in-visual-basic"></a>Doba platnosti v jazyce Visual Basic
*Životnost* deklarované elementu je doba, během které it je k dispozici pro použití. Proměnné jsou pouze elementy, které mají životnost. Pro tento účel kompilátor zpracovává parametry procedury a funkce vrátí jako zvláštních případech proměnných. Doba platnosti proměnné představuje dobu, během kterého může uchovávat hodnota. Jeho hodnota může změnit průběhu své životnosti, ale že vždy obsahuje určitou hodnotu.  
  
## <a name="different-lifetimes"></a>Různé životnosti  
 A *členské proměnné* (deklarovat na úrovni modulu, mimo libovolná procedura) obvykle má stejnou dobu života jako element, ve kterém je deklarovaná. Existuje jako samostatná kopie pro každou instanci třídu nebo strukturu, ve kterém je deklarovaná sdíleném proměnná deklarovaná ve třídě nebo struktuře. Každé takové proměnné má stejnou dobu života jako jeho instanci. Ale `Shared` proměnná má jenom jeden životnost, což trvá po celou dobu je aplikace spuštěna.  
  
 A *místní proměnné* (definovaná uvnitř procedury) existuje pouze tehdy, když je spuštěna procesu, ve kterém je deklarovaná. To platí také tohoto postupu parametry a návratový žádné funkce. Ale pokud tento postup volá další postupy, místní proměnné zachovat jejich hodnoty při vyvolání procedury.  
  
## <a name="beginning-of-lifetime"></a>Začátek platnosti  
 Doba platnosti místní proměnné začíná, když řízení zadá procesu, ve kterém je deklarovaná. Všechny místní proměnné je inicializován na výchozí hodnotu pro daný datový typ. ihned zahájí proces spuštěn. Při procesu dojde `Dim` příkaz, který určuje počáteční hodnoty, nastaví tyto proměnné tyto hodnoty, i v případě, že váš kód byl již přiřazen jiné hodnoty k nim.  
  
 Každý člen struktura proměnné je inicializován, jako by šlo samostatná proměnná. Podobně je každý prvek proměnné pole inicializován jednotlivě.  
  
 Deklarovat proměnné v bloku uvnitř procedury (například `For` smyčky) jsou inicializovány při položku k postupu. Tyto inicializacích začnou platit, zda váš kód někdy provede bloku.  
  
## <a name="end-of-lifetime"></a>Konec platnosti  
 Když ukončí proceduru, hodnoty jeho místní proměnné nejsou zachována a získá jejich paměti jazyka Visual Basic. Při dalším voláním procedury, všechny místní proměnné se znovu vytvořit a znovu inicializován.  
  
 Pokud instance třídu nebo strukturu ukončí, jeho sdíleném proměnné dojít ke ztrátě jejich paměti a jejich hodnoty. Každou novou instanci třídy třídu nebo strukturu vytvoří a znovu inicializuje jeho sdíleném proměnné. Ale `Shared` proměnné se zachovají, dokud vaše aplikace se zastaví.  
  
## <a name="extension-of-lifetime"></a>Rozšíření životnosti  
 Pokud je deklarovat místní proměnná s `Static` – klíčové slovo, je delší než doba provádění jeho procedury celé jeho životnosti. Následující tabulka ukazuje, jak deklarace procedury Určuje, jak dlouho `Static` proměnná existuje.  
  
|Postup umístění a sdílení|Statické proměnné doba platnosti začne|Statické proměnné životnost zakončení|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|V modulu (sdílené ve výchozím nastavení)|Při prvním volání procedury|Když se zastaví vaší aplikace|  
|Ve třídě `Shared` (postup není členem instance)|První postup se nazývá na konkrétní instanci nebo na samotný název třídu nebo strukturu|Když se zastaví vaší aplikace|  
|V instanci třídy ne `Shared` (postup je členem instance)|První postup se nazývá na konkrétní instanci|Uvolnění instance pro uvolňování paměti (GC)|  
  
## <a name="static-variables-of-the-same-name"></a>Statické proměnné se stejným názvem  
 Statické proměnné se stejným názvem v více než jeden postupu můžou deklarovat. Pokud to uděláte, Visual Basic – kompilátor považovat za každou takové proměnnou jako samostatný prvek. Inicializace jedné z těchto proměnných nemá vliv na ostatní hodnoty. Totéž platí i pokud definovat proceduru sadu přetížení a deklarovat statickou proměnné se stejným názvem v každé přetížení.  
  
## <a name="containing-elements-for-static-variables"></a>Obsahující elementy pro statické proměnné  
 Je tedy deklarovat statickou místní proměnné v rámci třídy, uvnitř procedury v této třídě. Statické místní proměnné v rámci struktury, ale nelze deklarovat jako člena struktura nebo jako místní proměnné procedury v rámci této struktury.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad deklaruje proměnná s [statické](../../../../visual-basic/language-reference/modifiers/static.md) – klíčové slovo. (Všimněte si, že není nutné `Dim` – klíčové slovo při [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md) , jako používá modifikátor `Static`.)  
  
### <a name="code"></a>Kód  
 [!code-vb[VbVbalrKeywords#13](../../../../visual-basic/language-reference/codesnippet/VisualBasic/lifetime_1.vb)]  
  
### <a name="comments"></a>Komentáře  
 V předchozím příkladu, proměnná `applesSold` nadále existovat za postupem `runningTotal` vrátí kód volání. Při příštím `runningTotal` je volána, `applesSold` uchovává jeho dříve vypočtenou hodnotou.  
  
 Pokud `applesSold` měl bylo deklarováno bez použití `Static`, nebude možné zachovat předchozí Akumulovaná hodnoty napříč volání `runningTotal`. Při příštím `runningTotal` byla volána `applesSold` by byly znovu vytvoří a hodnotu 0, a `runningTotal` by mít jednoduše vrátil se stejnou hodnotou, se kterým byla volána.  
  
### <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Můžete inicializovat hodnotu statické místní proměnné jako součást jeho deklaraci. Pokud je deklarovat pole jako `Static`, bude možné inicializovat jeho pořadí (počet dimenzí), délka Každá dimenze a hodnoty jednotlivých elementů.  
  
### <a name="security"></a>Zabezpečení  
 V předchozím příkladu, můžete vytvořit stejnou dobu životnosti deklarováním `applesSold` na úrovni modulu. Pokud jste změnili rozsahu proměnné tímto způsobem, ale postup by již výhradní přístup k němu. Vzhledem k tomu může další postupy k `applesSold` a změňte jeho hodnotu, může být spuštěna celkový nespolehlivé a kód může být obtížné zachovat.  
  
## <a name="see-also"></a>Viz také  
 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)  
 [Nothing](../../../../visual-basic/language-reference/nothing.md)  
 [Deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Rozsah v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Úrovně přístupu v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Proměnné](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)
