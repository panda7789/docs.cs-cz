---
title: Rozsah
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
ms.openlocfilehash: 1bee904996257474b7457b2aefb1f17d250933cb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410731"
---
# <a name="scope-in-visual-basic"></a>Rozsah v jazyce Visual Basic

*Obor* deklarovaného prvku je sada veškerého kódu, který se na něj může odkazovat bez kvalifikovaného názvu nebo jeho zpřístupnění prostřednictvím [příkazu Imports (obor názvů a typ .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md). Element může mít obor na jedné z následujících úrovní:

|Úroveň|Description|
|-----------|-----------------|
|Rozsah bloku|K dispozici pouze v bloku kódu, ve kterém je deklarována|
|Rozsah procedury|K dispozici pro veškerý kód v rámci postupu, ve kterém je deklarována|
|Rozsah modulu|K dispozici pro veškerý kód v rámci modulu, třídy nebo struktury, ve které je deklarována|
|Obor názvů|K dispozici pro veškerý kód v oboru názvů, ve kterém je deklarována|

Tyto úrovně postupu rozsahu od nejužšího (bloku) po nejširší (obor názvů), kde *nejužší rozsah* znamená nejmenší sadu kódu, který může odkazovat na prvek bez kvalifikace. Další informace najdete v části "úrovně oboru" na této stránce.

## <a name="specifying-scope-and-defining-variables"></a>Určení rozsahu a definování proměnných

Rozsah prvku určíte při jeho deklaraci. Rozsah může záviset na následujících faktorech:

- Oblast (blok, procedura, modul, třída nebo struktura), ve které deklarujete element

- Obor názvů obsahující deklaraci elementu

- Úroveň přístupu, kterou deklarujete pro element

Pokud definujete proměnné se stejným názvem, ale s jiným rozsahem, postupujte opatrně, protože by to mohlo vést k neočekávaným výsledkům. Další informace naleznete v tématu [odkazy na deklarované elementy](references-to-declared-elements.md).

## <a name="levels-of-scope"></a>Úrovně rozsahu

Programový prvek je k dispozici v celé oblasti, ve které jej deklarujete. Veškerý kód ve stejné oblasti může odkazovat na prvek bez kvalifikovaného názvu.

### <a name="block-scope"></a>Rozsah bloku

Blok je sada příkazů, které jsou uzavřeny v rámci inicializační a ukončovací příkazy deklarace, například následující:

- `Do` a `Loop`

- `For`[ `Each` ] a`Next`

- `If` a `End If`

- `Select` a `End Select`

- `SyncLock` a `End SyncLock`

- `Try` a `End Try`

- `While` a `End While`

- `With` a `End With`

Pokud deklarujete proměnnou v rámci bloku, můžete ji použít pouze v rámci tohoto bloku. V následujícím příkladu je rozsah proměnné celého čísla `cube` blok mezi `If` a `End If` a nemůžete již odkazovat na, `cube` Pokud provádění projde z bloku.

```vb
If n < 1291 Then
    Dim cube As Integer
    cube = n ^ 3
End If
```

> [!NOTE]
> I v případě, že rozsah proměnné je omezen na blok, je jeho životnost stále i u celého postupu. Pokud zadáte blok více než jednou během postupu, každá proměnná bloku uchová svou předchozí hodnotu. Chcete-li se vyhnout neočekávaným výsledkům v takovém případě, je vhodné inicializovat blokové proměnné na začátku bloku.

### <a name="procedure-scope"></a>Rozsah procedury

Element deklarovaný v proceduře není k dispozici mimo tento postup. Může použít pouze postup, který obsahuje deklaraci. Proměnné na této úrovni se označují také jako *místní proměnné*. Deklarujete je pomocí [příkazu Dim](../../../language-reference/statements/dim-statement.md)s klíčovým slovem [static](../../../language-reference/modifiers/static.md) nebo bez něj.

Postup a rozsah bloku úzce souvisejí. Pokud deklarujete proměnnou uvnitř procedury, ale mimo libovolný blok v rámci této procedury, můžete si považovat proměnnou jako s rozsahem bloku, kde blok je celý postup.

> [!NOTE]
> Všechny místní prvky, i když jsou `Static` proměnné, jsou soukromé pro proceduru, ve které se vyskytují. V proceduře nelze deklarovat žádný element pomocí klíčového slova [Public](../../../language-reference/modifiers/public.md) .

### <a name="module-scope"></a>Rozsah modulu

Pro usnadnění práce se *úroveň modulu* s jedním termínem aplikuje rovnoměrně na moduly, třídy a struktury. Můžete deklarovat prvky na této úrovni tím, že umístíte příkaz deklarace mimo jakýkoli postup nebo blok, ale v rámci modulu, třídy nebo struktury.

Při vytváření deklarace na úrovni modulu určuje úroveň přístupu, kterou zvolíte, obor. Obor názvů, který obsahuje modul, třídu nebo strukturu, má vliv také na obor.

Prvky, pro které deklarujete úroveň [privátního](../../../language-reference/modifiers/private.md) přístupu, jsou k dispozici pro každý postup v daném modulu, ale nikoli pro jakýkoliv kód v jiném modulu. `Dim` `Private` Pokud nepoužíváte žádná klíčová slova úrovně přístupu, příkaz na úrovni modulu se nastaví na výchozí hodnotu. Pomocí `Private` klíčového slova v příkazu však můžete nastavit rozsah a úroveň přístupu `Dim` .

V následujícím příkladu mohou všechny procedury definované v modulu odkazovat na řetězcovou proměnnou `strMsg` . Při volání druhého postupu se v dialogovém okně zobrazí obsah řetězcové proměnné `strMsg` .

```vb
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

### <a name="namespace-scope"></a>Obor názvů

Pokud deklarujete element na úrovni modulu pomocí klíčového slova [Friend](../../../language-reference/modifiers/friend.md) nebo [Public](../../../language-reference/modifiers/public.md) , bude zpřístupněn všem procedurám v rámci oboru názvů, ve kterém je element deklarován. S následující změnou v předchozím příkladu může být řetězcová proměnná `strMsg` odkazována pomocí kódu kdekoli v oboru názvů své deklarace.

```vb
' Include this declaration at module level (not inside any procedure).
Public strMsg As String
```

Obor názvů zahrnuje vnořené obory názvů. Element dostupný v rámci oboru názvů je také k dispozici v rámci jakéhokoli oboru názvů vnořeného uvnitř daného oboru názvů.

Pokud projekt neobsahuje žádné [Příkazy oboru názvů](../../../language-reference/statements/namespace-statement.md), je vše v projektu ve stejném oboru názvů. V tomto případě lze obor názvů představit jako rozsah projektu. `Public`prvky v modulu, třídě nebo struktuře jsou také k dispozici pro každý projekt, který odkazuje na svůj projekt.

## <a name="choice-of-scope"></a>Volba rozsahu

Při deklaraci proměnné byste měli při výběru jejího rozsahu brát v úvahu následující body.

### <a name="advantages-of-local-variables"></a>Výhody místních proměnných

Místní proměnné jsou dobrou volbou pro jakýkoliv druh dočasného výpočtu, a to z následujících důvodů:

- **Vyhnout se konfliktu názvů.** Názvy místních proměnných nejsou náchylné ke konfliktu. Můžete například vytvořit několik různých postupů obsahujících proměnnou s názvem `intTemp` . Pokud `intTemp` je každý deklarován jako místní proměnná, každý postup rozpoznává pouze svou vlastní verzi `intTemp` . Kterýkoli z těchto postupů může změnit hodnotu v místním prostředí, `intTemp` aniž by to ovlivnilo `intTemp` proměnné v jiných postupech.

- **Spotřeba paměti.** Místní proměnné spotřebovávají paměť pouze v době, kdy je spuštěn jejich postup. Jejich paměť je uvolněna v případě, že se procedura vrátí na volající kód. Naproti tomu [sdílené](../../../language-reference/modifiers/shared.md) a [statické](../../../language-reference/modifiers/static.md) proměnné využívají paměťové prostředky, dokud se vaše aplikace neukončí, takže je používejte, jenom když je to potřeba. *Proměnné instance* spotřebovávají paměť, zatímco jejich instance stále existují, což snižuje efektivitu než lokální proměnné, ale potenciálně účinnější než `Shared` nebo `Static` proměnných.

### <a name="minimizing-scope"></a>Minimalizace rozsahu

Obecně platí, že při deklaraci jakékoli proměnné nebo konstanty je dobrým postupem způsob, jak rozsah co nejblíže omezit (rozsah bloku je nejužší). To pomáhá šetřit paměť a minimalizovat šance na to, že váš kód chybně odkazuje na nesprávnou proměnnou. Podobně byste měli deklarovat proměnnou, která bude [statická](../../../language-reference/modifiers/static.md) pouze v případě, že je nutné zachovat hodnotu mezi voláními procedur.

## <a name="see-also"></a>Viz také

- [Deklarované charakteristiky elementů](declared-element-characteristics.md)
- [Postupy: Řízení rozsahu proměnné](how-to-control-the-scope-of-a-variable.md)
- [Doba platnosti v jazyce Visual Basic](lifetime.md)
- [Úrovně přístupu v Visual Basic](access-levels.md)
- [Odkazy na deklarované elementy](references-to-declared-elements.md)
- [Deklarace proměnné](../variables/variable-declaration.md)
