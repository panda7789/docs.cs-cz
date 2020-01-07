---
title: Doba platnosti
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
ms.openlocfilehash: 293537ad33c8e751d49d820fc57ea525e68bc203
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347765"
---
# <a name="lifetime-in-visual-basic"></a>Doba platnosti v jazyce Visual Basic
*Životnost* deklarovaného prvku je doba, během které je možné ho použít. Proměnné jsou jedinými prvky, které mají dobu života. Pro účely tohoto účelu Kompilátor považuje parametry procedury a vrátí funkce jako zvláštní případy proměnných. Životnost proměnné představuje časové období, během kterého může uchovávat hodnotu. Jeho hodnota se může změnit během své životnosti, ale vždycky uchovává nějakou hodnotu.  
  
## <a name="different-lifetimes"></a>Různé životnosti  
 *Členská proměnná* (deklarovaná na úrovni modulu, mimo jakoukoliv proceduru) má obvykle stejnou životnost jako element, ve kterém je deklarována. Nesdílená Proměnná deklarovaná ve třídě nebo struktuře existuje jako samostatná kopie pro každou instanci třídy nebo struktury, ve které je deklarována. Každá taková proměnná má stejnou životnost jako její instance. Proměnná `Shared` však má pouze jednu dobu života, která trvá po celou dobu běhu aplikace.  
  
 *Lokální proměnná* (deklarovaná uvnitř procedury) existuje pouze v případě, že je spuštěna procedura, ve které je deklarována. To platí také pro parametry této procedury a pro všechny vrácené funkce. Nicméně pokud tento postup volá jiné postupy, místní proměnné uchovávají jejich hodnoty, i když jsou spuštěny volané procedury.  
  
## <a name="beginning-of-lifetime"></a>Začátek platnosti  
 Doba života místní proměnné začíná, když ovládací prvek zadá proceduru, ve které je deklarována. Každá místní proměnná je inicializována na výchozí hodnotu pro svůj datový typ, jakmile se procedura začne spouštět. Když procedura narazí na příkaz `Dim`, který určuje počáteční hodnoty, nastaví tyto proměnné na tyto hodnoty, a to i v případě, že k nim kód již přiřadil jiné hodnoty.  
  
 Každý člen proměnné struktury je inicializován, jako by šlo o samostatnou proměnnou. Podobně každý element proměnné pole se inicializuje samostatně.  
  
 Proměnné deklarované v rámci bloku uvnitř procedury (například smyčka `For`) jsou inicializovány při vstupu do procedury. Tyto inicializace se projeví bez ohledu na to, jestli váš kód někdy spustí blok.  
  
## <a name="end-of-lifetime"></a>Konec platnosti  
 Když se procedura ukončí, hodnoty jejich místních proměnných se nezachovají a Visual Basic znovu vytvoří nárok na jejich paměť. Při příštím volání procedury budou všechny místní proměnné vytvořeny afresh a znovu inicializovány.  
  
 Po ukončení instance třídy nebo struktury ztratí jejich nesdílené proměnné svou paměť a jejich hodnoty. Každá nová instance třídy nebo struktury vytvoří a znovu inicializuje své nesdílené proměnné. Nicméně proměnné `Shared` jsou zachovány, dokud vaše aplikace nepřestane běžet.  
  
## <a name="extension-of-lifetime"></a>Rozšíření doby života  
 Pokud deklarujete místní proměnnou s klíčovým slovem `Static`, jeho životnost je delší než doba provádění jeho procedury. Následující tabulka ukazuje, jakým způsobem deklarace procedury určuje, jak dlouho existuje `Static` proměnná.  
  
|Umístění procedury a sdílení|Začíná životnost statických proměnných.|Ukončení životnosti statických proměnných|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|V modulu (ve výchozím nastavení Shared)|Při prvním volání procedury|Když vaše aplikace přestane běžet|  
|Ve třídě `Shared` (procedura není členem instance)|Při prvním volání procedury buď na konkrétní instanci, nebo v samotném názvu třídy nebo struktury|Když vaše aplikace přestane běžet|  
|V instanci třídy není `Shared` (procedura je člen instance).|Při prvním volání procedury na konkrétní instanci|Při uvolnění instance pro uvolňování paměti (GC)|  
  
## <a name="static-variables-of-the-same-name"></a>Statické proměnné se stejným názvem  
 Statické proměnné můžete deklarovat se stejným názvem ve více než jednom postupu. Pokud to uděláte, kompilátor Visual Basic považuje každou takovou proměnnou za samostatný prvek. Inicializace jedné z těchto proměnných nemá vliv na hodnoty ostatních. Totéž platí, pokud definujete proceduru se sadou přetížení a deklarujete statickou proměnnou se stejným názvem v každém přetížení.  
  
## <a name="containing-elements-for-static-variables"></a>Obsahující elementy pro statické proměnné  
 Můžete deklarovat statickou místní proměnnou v rámci třídy, to je uvnitř procedury v této třídě. Nemůžete však deklarovat statickou místní proměnnou v rámci struktury, buď jako člen struktury, nebo jako místní proměnnou procedury v rámci této struktury.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad deklaruje proměnnou s klíčovým slovem [static](../../../../visual-basic/language-reference/modifiers/static.md) . (Všimněte si, že klíčové slovo `Dim` nepotřebujete, pokud [příkaz Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) používá modifikátor, jako je například `Static`.)  
  
### <a name="code"></a>Kód  
 [!code-vb[VbVbalrKeywords#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#13)]  
  
### <a name="comments"></a>Komentáře  
 V předchozím příkladu proměnná `applesSold` nadále existuje poté, co procedura `runningTotal` vrátí na volající kód. Při příštím `runningTotal` je zavolána `applesSold` zachová dříve vypočítanou hodnotu.  
  
 Pokud byla `applesSold` deklarována bez použití `Static`, předchozí akumulované hodnoty nebudou zachovány v rámci volání `runningTotal`. Při příštím `runningTotal`, `applesSold` by byl znovu vytvořen a inicializován na hodnotu 0 a `runningTotal` by měla jednoduše vracet stejnou hodnotu, se kterou byla volána.  
  
### <a name="compile-the-code"></a>Kompilace kódu  
 Hodnotu statické lokální proměnné můžete inicializovat jako součást její deklarace. Pokud deklarujete pole, které má být `Static`, můžete inicializovat jeho pořadí (počet rozměrů), délku jednotlivých dimenzí a hodnoty jednotlivých prvků.  
  
### <a name="security"></a>Zabezpečení –  
 V předchozím příkladu můžete vytvořením stejné životnosti tím, že deklarujete `applesSold` na úrovni modulu. Pokud jste změnili rozsah proměnné tímto způsobem, ale k tomuto postupu již nebude mít výhradní přístup. Vzhledem k tomu, že jiné postupy mohly získat přístup k `applesSold` a změně její hodnoty, může být průběžný součet nespolehlivý a může být obtížné zachovat kód.  
  
## <a name="see-also"></a>Viz také:

- [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [Deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Obor v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Úrovně přístupu v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Proměnné](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Static](../../../../visual-basic/language-reference/modifiers/static.md)
