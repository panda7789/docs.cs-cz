---
title: Rozsah v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
ms.openlocfilehash: d6692379626d787b728d6e92bd447c4a96e6680e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656292"
---
# <a name="scope-in-visual-basic"></a>Rozsah v jazyce Visual Basic
*Oboru* deklarované elementu je sada všechen kód, který může na ni odkazuje bez určení názvu nebo ji dáte k dispozici prostřednictvím [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md). Element může mít rozsah v některém z následujících úrovní:  
  
|úroveň|Popis|  
|-----------|-----------------|  
|Rozsah bloku|K dispozici pouze v rámci kód blok, ve kterém je deklarovaná|  
|Rozsah procedury|K dispozici pro všechny kódu v rámci procesu, ve kterém je deklarovaná|  
|Rozsah modulu|K dispozici pro všechny kódu v rámci modulu, třídu nebo strukturu, ve kterém je deklarovaná|  
|Namespace oboru|K dispozici pro všechny kódu v oboru názvů, ve kterém je deklarovaná|  
  
 Tyto úrovně oboru průběh z nejbližší (bloku) na širokou (obor názvů), kde *zpomalit* znamená nejmenší sadu kód, který může odkazovat na prvek bez kvalifikace. Další informace najdete v tématu "Úrovně obor" na této stránce.  
  
## <a name="specifying-scope-and-defining-variables"></a>Určení oboru a definování proměnné  
 Můžete určit obor element při jeho deklaraci. Obor může záviset na následujících faktorech:  
  
-   Region (bloku, postup, modulu, – třída nebo struktura), ve kterém je deklarovat elementu  
  
-   Obor názvů obsahující deklaraci elementu  
  
-   Úroveň přístupu, které deklarace pro daný element  
  
 Použití pozor při definování proměnné se stejným názvem, ale jiný rozsah, protože díky tomu může vést k neočekávaným výsledkům. Další informace najdete v tématu [odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="levels-of-scope"></a>Úrovně rozsahu  
 Programovací element je k dispozici v celé oblasti, ve kterém je deklarovat. Všechny kódu ve stejné oblasti odkazovat na element bez určení názvu.  
  
### <a name="block-scope"></a>Obor bloku  
 Blok je sada uzavřené v rámci inicializace a ukončování deklarační příkazy, jako je například následující příkazy:  
  
-   `Do` A `Loop`  
  
-   `For` [`Each`] a `Next`  
  
-   `If` A `End If`  
  
-   `Select` A `End Select`  
  
-   `SyncLock` A `End SyncLock`  
  
-   `Try` A `End Try`  
  
-   `While` A `End While`  
  
-   `With` A `End With`  
  
 Pokud je deklarovat proměnnou v bloku, můžete ji pouze v tomto bloku. V následujícím příkladu, rozsah proměnná s celým číslem `cube` je blok mezi `If` a `End If`, a už se může vztahovat na `cube` při provádění předá mimo blok.  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  I když rozsah proměnné je omezený na blok, celé jeho životnosti je stále u celého procesu. Pokud zadáte během postupu bloku více než jednou, každá proměnná bloku ponechá jejich předchozí hodnotu. Chcete-li se vyhnout neočekávaným výsledkům v tomto případě, je vhodné k chybě při inicializaci bloku proměnné na začátku bloku.  
  
### <a name="procedure-scope"></a>Rozsah procedury  
 Element deklarované v rámci procedury není k dispozici mimo tohoto postupu. Pouze procedury, která obsahuje deklaraci můžete ji použít. Proměnné na této úrovni se také označují jako *místní proměnné*. Je deklarovat s [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md), bez ohledu [statické](../../../../visual-basic/language-reference/modifiers/static.md) – klíčové slovo.  
  
 Postup a bloku oboru jsou úzce související. Pokud je deklarovat proměnnou uvnitř procedury, ale mimo všechny bloky v rámci tohoto postupu si můžete představit proměnné tak, že má rozsah bloku, kde blok je celý postup.  
  
> [!NOTE]
>  Všechny místní elementy, i když jsou `Static` proměnné, jsou privátní procedury, ve kterém se zobrazí. Nelze deklarovat element pomocí [veřejné](../../../../visual-basic/language-reference/modifiers/public.md) – klíčové slovo v rámci procedury.  
  
### <a name="module-scope"></a>Rozsah modulu  
 Pro usnadnění práce jeden termín *úroveň modulu* vztahuje stejnou měrou na moduly, třídy a struktury. Prvky na této úrovni můžete tím, že příkaz deklarace mimo žádné procedury ani bloku, ale v rámci modulu, třídu nebo strukturu deklarovat.  
  
 Pokud provedete deklaraci na úrovni modulu, určuje úroveň přístupu, který zvolíte oboru. Obor názvů, který obsahuje modul, třídu nebo strukturu ovlivní také oboru.  
  
 Elementy, pro které je deklarovat [privátní](../../../../visual-basic/language-reference/modifiers/private.md) úroveň přístupu jsou dostupné pro každý postup v tomto modulu, ale nechcete žádný kód v různých modulu. `Dim` Příkaz na úrovni modulu výchozí `Private` Pokud nepoužijete všechny klíčová slova úrovně přístupu. Však můžete provádět oboru a úroveň přístupu zřejmější pomocí `Private` – klíčové slovo v `Dim` příkaz.  
  
 V následujícím příkladu, všechny postupy, které jsou definované v modulu mohou odkazovat na proměnnou string `strMsg`. Pokud je druhý postup je volána, zobrazuje obsah proměnnou řetězce `strMsg` v dialogovém okně.  
  
```  
' Put the following declaration at module level (not in any procedure).  
Private strMsg As String  
' Put the following Sub procedure in the same module.  
Sub initializePrivateVariable()  
    strMsg = "This variable cannot be used outside this module."  
End Sub  
' Put the following Sub procedure in the same module.  
Sub usePrivateVariable()  
    MsgBox(strMsg)  
End Sub  
```  
  
### <a name="namespace-scope"></a>Namespace oboru  
 Pokud je deklarovat element na úrovni pomocí modulu [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) nebo [veřejné](../../../../visual-basic/language-reference/modifiers/public.md) – klíčové slovo, je k dispozici pro všechny postupy v rámci oboru názvů, ve kterém je deklarovaný element. S následující změnou v předcházejícím příkladu proměnnou řetězce `strMsg` lze odkazovat kódem kdekoli v oboru názvů jeho deklaraci.  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 Namespace obor obsahuje vnořené obory názvů. Element dostupné v rámci oboru názvů je také k dispozici v rámci všech názvů vnořit do daného oboru názvů.  
  
 Pokud projekt neobsahuje žádné [příkaz Namespace](../../../../visual-basic/language-reference/statements/namespace-statement.md)s, které se nacházejí v projektu je v stejného oboru názvů. V takovém případě oboru názvů můžete představit jako rozsah projektu. `Public` elementy v modulu, třídu nebo strukturu jsou také k dispozici žádné projekt, který odkazuje na jejich projekt.  
  
## <a name="choice-of-scope"></a>Výběr rozsahu  
 Po deklarování proměnné, byste měli mít na paměti následující body při výběru její obor.  
  
### <a name="advantages-of-local-variables"></a>Výhody lokální proměnné  
 Lokální proměnné jsou dobrou volbou pro jakýkoli druh dočasné výpočet, z následujících důvodů:  
  
-   **Předcházení název konflikt.** Místní názvy proměnných nejsou náchylné k konfliktu. Například můžete vytvořit několik různé postupy obsahující proměnné s názvem `intTemp`. Stejně dlouho jako každý `intTemp` je deklarován jako místní proměnné, každý postup rozpozná pouze svou vlastní verzi z `intTemp`. Všechny jedním postupem změnit hodnotu v jeho místní `intTemp` bez ovlivnění `intTemp` proměnné v další postupy.  
  
-   **Využití paměti.** Lokální proměnné spotřebuje paměť pouze tehdy, když jejich postup běží. Jejich paměti je vydala, když se proces vrátí do volající kód. Naopak [sdílené](../../../../visual-basic/language-reference/modifiers/shared.md) a [statické](../../../../visual-basic/language-reference/modifiers/static.md) proměnné spotřebovávat prostředky paměti, dokud vaše aplikace se zastaví, takže použijte je pouze v případě potřeby. *Instance proměnné* využívání paměti při jejich instance i nadále existovat, což zajišťuje jejich méně efektivní než místní proměnné, ale potenciálně efektivnější než `Shared` nebo `Static` proměnné.  
  
### <a name="minimizing-scope"></a>Minimalizace oboru  
 Obecně platí, pokud deklarace, všechny proměnné nebo konstanta, je vhodné programování postupem zajistit co nejrovnoměrnější oboru (rozsah bloku je nejbližší). To pomáhá konzervaci paměti a minimalizuje případné chybnou informací odkaz na proměnnou nesprávný kód. Podobně platí, by měly deklarovat proměnnou, do které se [statické](../../../../visual-basic/language-reference/modifiers/static.md) pouze když je potřeba zachovat jeho hodnota mezi volání procedur.  
  
## <a name="see-also"></a>Viz také  
 [Deklarované charakteristiky elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Postupy: Řízení rozsahu proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)  
 [Doba platnosti v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Úrovně přístupu v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
