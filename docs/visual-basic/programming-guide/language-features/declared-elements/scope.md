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
ms.openlocfilehash: 6139af65958cefe43578f436204fa6836a71de0b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823542"
---
# <a name="scope-in-visual-basic"></a>Rozsah v jazyce Visual Basic
*Oboru* deklarované elementu je sada veškerý kód, který na ni můžete odkazovat bez kvalifikace názvu nebo ji dáte k dispozici prostřednictvím [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md). Element může mít rozsah na jednu z následujících úrovní:  
  
|úroveň|Popis|  
|-----------|-----------------|  
|Rozsah bloku|K dispozici pouze v rámci kód blok, ve kterém je deklarována|  
|Rozsah procedury|K dispozici pro všechen kód v rámci procedury, ve kterém je deklarována|  
|Rozsah modulu|K dispozici pro všechen kód v rámci modulu, třídy nebo struktury, ve kterém je deklarována|  
|Namespace oboru|K dispozici pro všechen kód v oboru názvů, ve kterém je deklarována|  
  
 Tyto úrovně oboru průběh na základě nejužší (bloku) na nejširší (obor názvů), kde *od nejužšího oboru po* znamená, že nejmenší sadu kód, který může odkazovat na prvek bez kvalifikace. Další informace najdete v tématu "Úrovně oboru" na této stránce.  
  
## <a name="specifying-scope-and-defining-variables"></a>Určení oboru a definování proměnných  
 Můžete určit obor element při jeho deklaraci. Rozsah může záviset na následujících faktorech:  
  
-   Oblast (blok, postup, modulu, třídy nebo struktury), ve kterém můžete deklarovat element  
  
-   Obor názvů obsahující deklarace prvku  
  
-   Úroveň přístupu, které deklarujete pro element  
  
 Pečlivě při definování proměnné se stejným názvem, ale jiného oboru, protože to může vést k neočekávaným výsledkům. Další informace najdete v tématu [odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="levels-of-scope"></a>Úrovně rozsahu  
 Programovací element je k dispozici v rámci oblasti, ve kterém se deklaruje. Veškerý kód ve stejné oblasti můžete odkazovat na prvek bez kvalifikace názvu.  
  
### <a name="block-scope"></a>Obor bloku  
 Blok je sadu příkazů uzavřených v rámci inicializace a ukončování příkazy deklarace, jako je následující:  
  
-   `Do` a `Loop`  
  
-   `For` [`Each`] a `Next`  
  
-   `If` a `End If`  
  
-   `Select` a `End Select`  
  
-   `SyncLock` a `End SyncLock`  
  
-   `Try` a `End Try`  
  
-   `While` a `End While`  
  
-   `With` a `End With`  
  
 Pokud deklarujete proměnnou v bloku, můžete ji použít pouze v tomto bloku. V následujícím příkladu oboru celočíselné proměnné `cube` je blok mezi `If` a `End If`, a už se můžete vrátit k `cube` při provádění předá mimo blok.  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  I v případě, že rozsah proměnné je omezen na blok, dobu života je stále celého procesu. Pokud zadáte během postupu bloku více než jednou, každý blok proměnná zachová svou předchozí hodnotu. Aby se zabránilo neočekávaným výsledkům v takovém případě je z pohledu inicializovat proměnné v bloku na začátku bloku.  
  
### <a name="procedure-scope"></a>Rozsah procedury  
 Element deklarovaný v rámci procedury není k dispozici mimo tento postup. Pouze proceduru, která obsahuje deklaraci můžete ho použít. Proměnné na této úrovni se také označují jako *lokální proměnné*. Můžete je deklarovat pomocí [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md), s nebo bez [statické](../../../../visual-basic/language-reference/modifiers/static.md) – klíčové slovo.  
  
 Postup a zároveň se zablokují oboru jsou úzce souvisí. Pokud deklarujete proměnnou uvnitř procedury, ale mimo všechny bloky v rámci tohoto postupu si můžete představit proměnnou jako s rozsahem bloku, pokud blok je celého procesu.  
  
> [!NOTE]
>  Všechny místní prvky, dokonce i v případě, že jsou `Static` proměnné, jsou privátní pro proceduru, v jakém jsou uvedeny. Nelze deklarovat element pomocí [veřejné](../../../../visual-basic/language-reference/modifiers/public.md) – klíčové slovo v rámci procedury.  
  
### <a name="module-scope"></a>Rozsah modulu  
 Pro usnadnění práce, jeden výraz *úroveň modulu* vztahuje stejnou měrou na moduly, třídy a struktury. Prvky na této úrovni můžete deklarovat umístěním příkazu deklarace mimo žádné procedury ani bloku, ale v rámci modulu, třídy nebo struktury.  
  
 Pokud provedete deklarace na úrovni modulu, zjistí úroveň přístupu, kterou zvolíte rozsah. Obor názvů obsahující modulu, třídy nebo struktury má vliv také na obor.  
  
 Prvky, pro které deklarujete [privátní](../../../../visual-basic/language-reference/modifiers/private.md) úroveň přístupu jsou k dispozici pro každý postup v tomto modulu, ale ne k libovolnému kódu ve jiný modul. `Dim` Výchozí příkaz na úrovni modulu `Private` Pokud nepoužijete klíčová slova úrovně přístupu. Však můžete provádět oboru a úroveň přístupu jasnější pomocí `Private` – klíčové slovo v `Dim` příkazu.  
  
 V následujícím příkladu všechny postupy definované v modulu mohou odkazovat na proměnné řetězce `strMsg`. Při volání druhý postup zobrazí obsah proměnné řetězce `strMsg` v dialogovém okně.  
  
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
 Je-li deklarovat element na úrovni pomocí modulu [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) nebo [veřejné](../../../../visual-basic/language-reference/modifiers/public.md) – klíčové slovo, stane se dostupným pro všechny postupy v rámci oboru názvů, ve kterém je deklarován element. S následující změnou v předchozím příkladu, Řetězcová hodnota `strMsg` lze odkazovat pomocí kódu kdekoli v deklaraci oboru názvů.  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 Namespace obor obsahuje vnořené obory názvů. Element dostupné v rámci oboru názvů je také dostupné v rámci libovolný obor názvů vnořit do daného oboru názvů.  
  
 Pokud projekt neobsahuje žádný [příkaz Namespace](../../../../visual-basic/language-reference/statements/namespace-statement.md)všechno, co v projektu jsou ve stejném oboru názvů. V takovém případě oboru názvů můžete představit jako rozsah projektu. `Public` prvky v modulu, třídy nebo struktury jsou také k dispozici do jakéhokoli projektu, který odkazuje na projekt.  
  
## <a name="choice-of-scope"></a>Výběr rozsahu  
 Při deklarování proměnné můžete by měl vzít v úvahu následující body při výběru svého oboru.  
  
### <a name="advantages-of-local-variables"></a>Výhody lokální proměnné  
 Lokální proměnné jsou dobrou volbou pro jakýkoli druh dočasné výpočtu z následujících důvodů:  
  
-   **Předcházení název konflikt.** Místní názvy proměnných nejsou náchylné k jsou v konfliktu. Například můžete vytvořit několik různých postupů obsahujícího proměnnou s názvem `intTemp`. Tak dlouho, dokud každý `intTemp` je deklarován jako místní proměnná, každý postup rozpozná pouze svou vlastní verzi z `intTemp`. Jakékoli jedné postupem můžete změnit hodnotu v jeho místní `intTemp` aniž by to ovlivnilo `intTemp` proměnné v dalších postupech.  
  
-   **Využití paměti.** Lokální proměnné využívání paměti pouze při jejich postupu běží. Když postup vrátí volajícímu kódu, se uvolní jejich paměť. Naopak [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) a [statické](../../../../visual-basic/language-reference/modifiers/static.md) proměnné spotřebovávají prostředky paměti, dokud se vaše aplikace se zastaví, proto je pouze v případě potřeby. *Instance proměnné* využívání paměti při jejich instance existuje, i nadále, což je méně efektivní než místní proměnné, ale potenciálně efektivnější než `Shared` nebo `Static` proměnné.  
  
### <a name="minimizing-scope"></a>Minimalizace oboru  
 Obecně platí, při deklarování jakoukoli proměnnou nebo konstantu, je programování je dobrým zvykem aby bylo co nejrovnoměrnější rozsah (obor bloku je nejbližší). To pomáhá šetřit paměť a minimalizuje případné chybně odkazující na proměnnou nesprávného kódu. Podobně by měla deklarovat proměnnou [statické](../../../../visual-basic/language-reference/modifiers/static.md) pouze pokud je potřeba zachovat jeho hodnotu mezi volání procedur.  
  
## <a name="see-also"></a>Viz také:

- [Deklarované charakteristiky elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Postupy: Řízení rozsahu proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [Doba platnosti v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Úrovně přístupu v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
