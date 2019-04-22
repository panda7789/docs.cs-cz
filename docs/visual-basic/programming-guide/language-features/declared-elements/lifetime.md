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
ms.openlocfilehash: 7a8730834c5241ddb1271d689cdda8942741f15f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58824920"
---
# <a name="lifetime-in-visual-basic"></a>Doba platnosti v jazyce Visual Basic
*Životnost* deklarované elementu je časové období, během které je k dispozici pro použití. Proměnné jsou pouze prvky, které mají životnost. Pro tento účel kompilátor zpracovává parametry procedury a funkce vrátí jako zvláštní případy proměnných. Životnost proměnné představuje dobu, během které může obsahovat hodnotu. Můžete změnit její hodnotu za dobu života, ale vždy obsahuje některá z hodnot.  
  
## <a name="different-lifetimes"></a>Různé životnosti  
 A *členskou proměnnou* (deklarovanou na úrovni modulu, mimo všechny procedury) obvykle má stejnou dobu platnosti jako element, ve kterém je deklarována. Nesdílené proměnná deklarovaná ve třídě nebo struktuře existuje jako samostatná kopie pro každou instanci třídy nebo struktury, ve kterém je deklarována. Každá tato proměnná má stejnou dobu platnosti jako jeho instanci. Ale `Shared` proměnná má pouze jeden životnost, která má platnost po celou dobu spuštění aplikace.  
  
 A *lokální proměnná* (deklarované uvnitř procedury) existuje pouze během procesu, ve kterém je deklarována. To platí také parametry tohoto postupu a jakékoli návratová hodnota funkce. Ale pokud tento postup vyžaduje další postupy, místní proměnné zachovat jejich hodnoty jsou spuštěné volané procedury.  
  
## <a name="beginning-of-lifetime"></a>Počáteční doba života  
 Doba života místní proměnné začíná, když ovládacího prvku zadá procedura, ve kterém je deklarována. Každý místní proměnná je inicializována na výchozí hodnotu pro jeho datový typ jako postup začíná systémem. Pokud nalezne podle postupu `Dim` příkaz, který určuje počáteční hodnoty, nastaví těchto proměnných na tyto hodnoty, i v případě, že váš kód bylo již přiřazené jiné hodnoty.  
  
 Každý člen struktury proměnná je inicializována, jako by šlo samostatná proměnná. Podobně každý prvek proměnnou pole je inicializován jednotlivě.  
  
 Proměnné deklarované v rámci bloku uvnitř procedury (například `For` smyčky) jsou inicializovány při vstupu do procesu. Tyto inicializace projeví, jestli váš kód nikdy provede blok.  
  
## <a name="end-of-lifetime"></a>Konec životnosti  
 Když ukončí proceduru hodnoty své místní proměnné nejsou zachovány a Visual Basic uvolňování jejich paměti. Při příštím volání procedury, všech místních proměnných jsou znovu vytvořena a opakování inicializace odběrů.  
  
 Při ukončení instance třídy nebo struktury, jeho nesdílených proměnných dojít ke ztrátě jejich paměť a jejich hodnoty. Každá nová instance třídy nebo struktury vytvoří a znovu inicializuje jeho nesdílených proměnných. Ale `Shared` proměnné jsou zachovaná, dokud se vaše aplikace se zastaví.  
  
## <a name="extension-of-lifetime"></a>Prodloužení doby života  
 Pokud je deklarovat lokální proměnnou s `Static` – klíčové slovo, dobu života je delší než doba provádění její postup. Následující tabulka ukazuje, jak deklaraci procedury Určuje, jak dlouho `Static` existuje proměnná.  
  
|Postup umístění a sdílení|Statickou životnost proměnné začíná|Životnosti statických proměnných končí|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|V modulu (sdílené ve výchozím nastavení)|Při prvním volání procedury|Když aplikace přestane fungovat|  
|Ve třídě `Shared` (Procedura není člen instance.)|Při prvním volání procedury na konkrétní instanci nebo na samotný název třídy nebo struktury|Když aplikace přestane fungovat|  
|V instanci dané třídy ne `Shared` (postup je členem instance)|Při prvním volání procedury na konkrétní instanci|Uvolnění instance pro uvolňování paměti (GC)|  
  
## <a name="static-variables-of-the-same-name"></a>Statické proměnné se stejným názvem  
 Je možné deklarovat statické proměnné se stejným názvem ve více než jeden postup. Pokud to uděláte, kompilátor jazyka Visual Basic, bude považovat za každou takové proměnnou jako samostatný prvek. Inicializace jednoho z těchto proměnných nemá vliv na ostatní hodnoty. To samé platí, pokud se definuje proceduru sadu přetížení a deklarovat statickou proměnnou se stejným názvem v každé přetížení.  
  
## <a name="containing-elements-for-static-variables"></a>Obsahuje elementy pro statické proměnné  
 Statické místní proměnné v rámci třídy, je možné deklarovat tedy uvnitř procedury v dané třídě. Statické místní proměnné v rámci struktury, ale nelze deklarovat jako člen struktury nebo jako místní proměnná procedury v rámci struktury.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad deklaruje proměnnou s [statické](../../../../visual-basic/language-reference/modifiers/static.md) – klíčové slovo. (Všimněte si, že není nutné `Dim` – klíčové slovo při [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) , jako používá modifikátor `Static`.)  
  
### <a name="code"></a>Kód  
 [!code-vb[VbVbalrKeywords#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#13)]  
  
### <a name="comments"></a>Komentáře  
 V předchozím příkladu je proměnná `applesSold` i nadále existovat za postupem `runningTotal` vrátí volajícímu kódu. Při příštím `runningTotal` je volána, `applesSold` uchovává jeho dříve počítanou hodnotu.  
  
 Pokud `applesSold` kdyby byly deklarovány bez použití `Static`, předchozí celkové hodnoty by zachovaná napříč volání `runningTotal`. Při příštím `runningTotal` byla volána `applesSold` by byly znovu vytvořeny a inicializovány na hodnotu 0, a `runningTotal` by mít jednoduše vrátí stejnou hodnotu, se kterým byla volána.  
  
### <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Můžete inicializovat hodnotou statické místní proměnné jako součást její deklarace. Pokud deklarujete pole bude `Static`, můžete inicializovat pořadím (počet rozměrů), délka každé dimenze a hodnoty jednotlivých prvků.  
  
### <a name="security"></a>Zabezpečení  
 V předchozím příkladu, můžete vytvořit stejnou dobu života deklarováním `applesSold` na úrovni modulu. Pokud jste změnili rozsahu proměnné tímto způsobem, ale postup by již výhradní přístup k němu. Protože může zpřístupnit další postupy `applesSold` a změňte tuto hodnotu, Mezisoučet může nespolehlivé a může být obtížnější údržbu kódu.  
  
## <a name="see-also"></a>Viz také:

- [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [Deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Obor v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Úrovně přístupu v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Proměnné](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Static](../../../../visual-basic/language-reference/modifiers/static.md)
