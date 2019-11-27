---
title: On Error – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.OnError
helpviewer_keywords:
- Visual Basic code, control flow
- Resume Next statement [Visual Basic]
- errors [Visual Basic], trapping
- error handling, On Error statement
- Next statement [Visual Basic], On Error
- control flow [Visual Basic], branching
- Error keyword [Visual Basic]
- execution [Visual Basic], conditional
- Resume statement [Visual Basic], and On Error statement
- Error statement [Visual Basic], and On Error statement
- GoTo statement [Visual Basic], and On Error statement
- branching [Visual Basic], on error
- conditional statements [Visual Basic], On Error
- On Error statement [Visual Basic], syntax
- On keyword [Visual Basic]
- run-time errors [Visual Basic], handling
- On Error statement [Visual Basic]
ms.assetid: ff947930-fb84-40cf-bd66-1ea219561d5c
ms.openlocfilehash: d62c2ba1849b7015ed877d503220026a2dfeff57
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353808"
---
# <a name="on-error-statement-visual-basic"></a>On Error – příkaz (Visual Basic)
Povoluje rutinu zpracování chyb a určuje umístění rutiny v rámci procedury; lze také použít k zakázání rutiny zpracování chyb. Příkaz `On Error` se používá při zpracování nestrukturovaných chyb a lze jej použít namísto strukturovaného zpracování výjimek. [Strukturované zpracování výjimek](../../../standard/exceptions/index.md) je integrováno do .NET, je obecně efektivnější, a proto se doporučuje při zpracování běhových chyb v aplikaci.

 Bez zpracování chyb nebo zpracování výjimek by jakákoli chyba za běhu, ke které dochází, je závažná: zobrazí se chybová zpráva a běh se zastaví.

> [!NOTE]
> Klíčové slovo `Error` se používá také v [příkazu Error](../../../visual-basic/language-reference/statements/error-statement.md), který je podporovaný z důvodu zpětné kompatibility.

## <a name="syntax"></a>Syntaxe

```vb
On Error { GoTo [ line | 0 | -1 ] | Resume Next }
```

## <a name="parts"></a>Součásti

|Termín|Definice|
|---|---|
|`GoTo` *řádek*|Povoluje rutinu zpracování chyb, která začíná na řádku zadaném *v argumentu* Required. Argument *line* je libovolný řádek popisku nebo čísla řádku. Pokud dojde k chybě za běhu, ovládací prvky se řídí na zadaný řádek, čímž se aktivuje obslužná rutina chyb. Zadaný řádek musí být ve stejné proceduře jako příkaz `On Error` nebo dojde k chybě při kompilaci.|
|`GoTo 0`|Zakáže povolenou obslužnou rutinu chyb v aktuální proceduře a obnoví ji na `Nothing`.|
|`GoTo -1`|Zakáže povolenou výjimku v aktuální proceduře a obnoví ji na `Nothing`.|
|`Resume Next`|Určuje, že pokud dojde k chybě za běhu, řízení přejde na příkaz ihned po příkazu, kde došlo k chybě, a provádění pokračuje od tohoto bodu. Použijte tento formulář místo `On Error GoTo` při přístupu k objektům.|

## <a name="remarks"></a>Poznámky

> [!NOTE]
> Doporučujeme používat strukturované zpracování výjimek v kódu, kdykoli je to možné, místo použití nestrukturovaného zpracování výjimek a příkazu `On Error`. Další informace najdete v tématu [Try... Zachytit... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).

 Obslužná rutina chyby "Enabled" je ta, která je zapnutá příkazem `On Error`. Obslužná rutina chyb "aktivní" je povolená obslužná rutina, která zpracovává chybu.

 Pokud dojde k chybě, když je aktivní obslužná rutina chyby (mezi výskytem chyby a `Resume`, `Exit Sub`, `Exit Function`nebo příkazem `Exit Property`), obslužná rutina chyby aktuální procedury nemůže zpracovat chybu. Řízení se vrátí do volající procedury.
  
 Pokud volající procedura má povolenou obslužnou rutinu chyb, je aktivována, aby zpracovala chybu. Pokud je obslužná rutina chyby volajícího procesu také aktivní, řízení projde předchozími volajícími procedurami, dokud není povolena, ale neaktivní obslužná rutina chyby. Pokud tato obslužná rutina chyb nenajde, je chyba závažná v okamžiku, kdy k ní došlo.
  
 Pokaždé, když obslužná rutina chyby předá řízení zpět do volající procedury, tato procedura se stal aktuálním postupem. Jakmile je chyba zpracována obslužnou rutinou chyby v jakémkoli postupu, spuštění pokračuje v aktuální proceduře v místě určeném příkazem `Resume`.
  
> [!NOTE]
> Rutina zpracování chyb není `Sub` procedura nebo procedura `Function`. Je oddíl kódu označený popiskem řádku nebo číslem řádku.
  
## <a name="number-property"></a>Číselná vlastnost
 Rutiny zpracování chyb spoléhají na hodnotu vlastnosti `Number` objektu `Err`, aby bylo možné určit příčinu chyby. Rutina by měla testovat nebo ukládat relevantní hodnoty vlastností v objektu `Err` před tím, než může dojít k jakékoli jiné chybě nebo před procedurou, která by mohla způsobit volání chyby. Hodnoty vlastností v objektu `Err` odrážejí pouze nejaktuálnější chybu. Chybová zpráva přidružená k `Err.Number` je obsažena v `Err.Description`.  
  
## <a name="throw-statement"></a>Throw – příkaz  
 Chyba, která je vyvolána pomocí metody `Err.Raise` nastaví vlastnost `Exception` na nově vytvořenou instanci třídy <xref:System.Exception>. Aby bylo možné podporovat vyvolávání výjimek odvozených typů výjimek, je příkaz `Throw` podporován v jazyce. To přijímá jeden parametr, který je instancí výjimky, která má být vyvolána. Následující příklad ukazuje, jak lze tyto funkce použít s existující podporou zpracování výjimek:

 [!code-vb[VbVbalrErrorHandling#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#17)]  
  
 Všimněte si, že příkaz `On Error GoTo` provádí depeše všech chyb bez ohledu na třídu výjimky.
  
## <a name="on-error-resume-next"></a>Při chybě obnovit další
 `On Error Resume Next` způsobí, že provádění pokračuje s příkazem hned po příkazu, který způsobil chybu za běhu, nebo s příkazem hned za posledním voláním metody, která obsahuje příkaz `On Error Resume Next`. Tento příkaz umožňuje, aby provádění pokračovalo navzdory chybě v době běhu. Můžete umístit rutinu pro zpracování chyb, kde by došlo k chybě místo přenosu řízení do jiného umístění v rámci postupu. Příkaz `On Error Resume Next` se neaktivuje při volání jiné procedury, takže byste měli spustit příkaz `On Error Resume Next` v každé rutině s názvem rutinou, pokud chcete v rámci této rutiny zpracovat vložené chyby.
  
> [!NOTE]
> `On Error Resume Next` konstrukce může být vhodnější pro `On Error GoTo` při zpracování chyb generovaných při přístupu k jiným objektům. Kontrola `Err` po každé interakci s objektem odebere nejednoznačnost, ke kterému byl objekt přidaný pomocí kódu. Můžete si být jistí, který objekt umístil kód chyby do `Err.Number`a který objekt původně vygeneroval chybu (objekt zadaný v `Err.Source`).

## <a name="on-error-goto-0"></a>Při chybě GoTo 0
 `On Error GoTo 0` zakáže zpracování chyb v aktuálním postupu. Nespecifikuje řádek 0 jako začátek kódu pro zpracování chyb, a to i v případě, že procedura obsahuje řádek s číslem 0. Bez příkazu `On Error GoTo 0` je obslužná rutina chyby automaticky zakázána při ukončení procedury.

## <a name="on-error-goto--1"></a>Při chybě GoTo-1
 `On Error GoTo -1` zakáže výjimku v aktuální proceduře. Neurčuje řádek-1 jako začátek kódu pro zpracování chyb, a to i v případě, že procedura obsahuje řádek s číslem 1. Bez příkazu `On Error GoTo -1` je výjimka automaticky zakázána při ukončení procedury.

 Chcete-li zabránit spuštění kódu pro zpracování chyb, když nedošlo k žádné chybě, umístěte `Exit Sub`, `Exit Function`nebo `Exit Property` příkaz těsně před rutinu zpracování chyb, jako v následujícím fragmentu:

 [!code-vb[VbVbalrErrorHandling#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#18)]

 V tomto příkladu kód pro ošetření chyb následuje za příkazem `Exit Sub` a předchází příkazu `End Sub`, který jej oddělí od toku procedury. Kód pro zpracování chyb lze umístit kdekoli v proceduře.

## <a name="untrapped-errors"></a>Nepřesahovat chyby
 Nezachycené chyby v objektech se vrátí do řídicí aplikace, když je objekt spuštěn jako spustitelný soubor. V rámci vývojového prostředí se chyby bez přesahů vrátí do řídicí aplikace pouze v případě, že jsou nastaveny správné možnosti. Popis možností nastavení, které by měly být nastaveny během ladění, jak je nastavit a zda může hostitel vytvořit třídy, najdete v dokumentaci hostitelské aplikace.

 Vytvoříte-li objekt, který přistupuje k jiným objektům, měli byste se pokusit zpracovat jakékoli neošetřené chyby, které přejdou zpět. Pokud nemůžete, namapujte kódy chyb v `Err.Number` na jednu z vašich vlastních chyb a pak je předejte volajícímu objektu. Tuto chybu byste měli zadat přidáním kódu chyby do `VbObjectError` konstanty. Například pokud kód chyby je 1052, přiřaďte ho následujícím způsobem:

 [!code-vb[VbVbalrErrorHandling#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#19)]

> [!CAUTION]
> Systémové chyby během volání knihoven DLL (Dynamic-Link Library) systému Windows nevyvolávají výjimky a nemohou být zachyceny pomocí Visual Basic soutisku chyb. Při volání funkcí knihoven DLL byste měli kontrolovat každou vrácenou hodnotu pro úspěch nebo neúspěch (podle specifikací rozhraní API) a v případě selhání kontrolovat hodnotu vlastnosti `LastDLLError` objektu `Err`.

## <a name="example"></a>Příklad
 Tento příklad nejprve používá příkaz `On Error GoTo` k určení umístění rutiny zpracování chyb v rámci procedury. V příkladu se při pokusu o dělení nulou vygeneruje chybová zpráva číslo 6. Chyba je zpracována v rutině zpracování chyb a ovládací prvek je poté vrácen do příkazu, který způsobil chybu. Příkaz `On Error GoTo 0` vypne soutisk chyb. Pak příkaz `On Error Resume Next` slouží k odložení soutisku chyb, takže kontext pro chybu vygenerovanou dalším příkazem může být pro určitý objekt známý. Všimněte si, že `Err.Clear` slouží k vymazání vlastností objektu `Err` po zpracování chyby.

 [!code-vb[VbVbalrErrorHandling#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#20)]

## <a name="requirements"></a>Požadavky
 **Obor názvů:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)

 **Sestavení:** Knihovna Visual Basic runtime (v souboru Microsoft. VisualBasic. dll)

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Number%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Description%2A>
- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [Příkaz End](../../../visual-basic/language-reference/statements/end-statement.md)
- [Příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Příkaz Resume](../../../visual-basic/language-reference/statements/resume-statement.md)
- [Chybové zprávy](../../../visual-basic/language-reference/error-messages/index.md)
- [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
