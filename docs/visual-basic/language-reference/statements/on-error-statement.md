---
title: On Error – příkaz (Visual Basic)
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
ms.openlocfilehash: 170cc4a42eda0b54d1e252104a702e008af7a336
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671826"
---
# <a name="on-error-statement-visual-basic"></a>On Error – příkaz (Visual Basic)
Povoluje rutinu zpracování chyb a určuje umístění rutiny v rámci procedury; lze také použít k zakázání rutiny zpracování chyb. `On Error` Příkaz se používá při zpracování nestrukturovaných chyb a lze jej použít namísto strukturovaného zpracování výjimek. [Strukturované zpracování výjimek](../../../standard/exceptions/index.md) je integrováno do .NET, je obecně efektivnější, a proto se doporučuje při zpracování běhových chyb v aplikaci.

 Bez zpracování chyb nebo zpracování výjimek by jakákoli chyba za běhu, ke které dochází, je závažná: zobrazí se chybová zpráva a běh se zastaví.

> [!NOTE]
>  Klíčové slovo se používá také v [příkazu Error](../../../visual-basic/language-reference/statements/error-statement.md), který je podporovaný z důvodu zpětné kompatibility. `Error`

## <a name="syntax"></a>Syntaxe

```vb
On Error { GoTo [ line | 0 | -1 ] | Resume Next }
```

## <a name="parts"></a>Součásti

|Termín|Definice|
|---|---|
|`GoTo`*čára*|Povoluje rutinu zpracování chyb, která začíná na řádku zadaném *v argumentu* Required. Argument *line* je libovolný řádek popisku nebo čísla řádku. Pokud dojde k chybě za běhu, ovládací prvky se řídí na zadaný řádek, čímž se aktivuje obslužná rutina chyb. Zadaný řádek musí být ve stejné proceduře jako `On Error` příkaz nebo dojde k chybě při kompilaci.|
|`GoTo 0`|Zakáže povolenou obslužnou rutinu chyb v aktuální proceduře a obnoví ji `Nothing`na.|
|`GoTo -1`|Zakáže povolenou výjimku v aktuální proceduře a obnoví ji na `Nothing`.|
|`Resume Next`|Určuje, že pokud dojde k chybě za běhu, řízení přejde na příkaz ihned po příkazu, kde došlo k chybě, a provádění pokračuje od tohoto bodu. Použijte tento formulář místo toho `On Error GoTo` , abyste měli přístup k objektům.|

## <a name="remarks"></a>Poznámky

> [!NOTE]
>  Doporučujeme používat strukturované zpracování výjimek v kódu, kdykoli je to možné, místo použití nestrukturovaného zpracování výjimek a `On Error` příkazu. Další informace najdete v tématu [Try... Zachytit... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).

 Obslužná rutina chyby "Enabled" je ta, která je zapnutá `On Error` příkazem. Obslužná rutina chyb "aktivní" je povolená obslužná rutina, která zpracovává chybu.

 Pokud dojde k chybě, když je aktivní `Resume`obslužná rutina chyby (mezi výskytem chyby a příkazem, `Exit Sub`, `Exit Function`nebo `Exit Property` ), obslužná rutina chyby aktuální procedury nemůže zpracovat chybu. Řízení se vrátí do volající procedury.
  
 Pokud volající procedura má povolenou obslužnou rutinu chyb, je aktivována, aby zpracovala chybu. Pokud je obslužná rutina chyby volajícího procesu také aktivní, řízení projde předchozími volajícími procedurami, dokud není povolena, ale neaktivní obslužná rutina chyby. Pokud tato obslužná rutina chyb nenajde, je chyba závažná v okamžiku, kdy k ní došlo.
  
 Pokaždé, když obslužná rutina chyby předá řízení zpět do volající procedury, tato procedura se stal aktuálním postupem. Jakmile je chyba zpracována obslužnou rutinou chyby v jakémkoli postupu, provádění pokračuje v aktuální proceduře v místě určeném `Resume` příkazem.
  
> [!NOTE]
>  Rutina `Sub` zpracování chyb není procedura `Function` nebo procedura. Je oddíl kódu označený popiskem řádku nebo číslem řádku.
  
## <a name="number-property"></a>Číselná vlastnost
 Rutiny zpracování chyb spoléhají na hodnotu ve `Number` vlastnosti `Err` objektu, aby bylo možné určit příčinu chyby. Rutina by měla testovat nebo ukládat relevantní hodnoty vlastností v `Err` objektu, než může dojít k jakékoli jiné chybě nebo před procedurou, která by mohla způsobit volání chyby. Hodnoty vlastností v `Err` objektu odrážejí pouze nejaktuálnější chybu. Chybová zpráva přidružená k `Err.Number` nástroji je obsažena v. `Err.Description`  
  
## <a name="throw-statement"></a>Throw – příkaz  
 Chyba, která je vyvolána `Err.Raise` metodou, `Exception` nastaví vlastnost na <xref:System.Exception> nově vytvořenou instanci třídy. Aby bylo možné podporovat vyvolávání výjimek odvozených typů výjimek, `Throw` je příkaz podporován v jazyce. To přijímá jeden parametr, který je instancí výjimky, která má být vyvolána. Následující příklad ukazuje, jak lze tyto funkce použít s existující podporou zpracování výjimek:

 [!code-vb[VbVbalrErrorHandling#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#17)]  
  
 Všimněte si, `On Error GoTo` že příkaz provádí depeše všech chyb bez ohledu na třídu výjimek.
  
## <a name="on-error-resume-next"></a>Při chybě obnovit další
 `On Error Resume Next`způsobí, že provádění pokračuje s příkazem hned po příkazu, který způsobil chybu za běhu, nebo s příkazem hned za posledním voláním metody, která obsahuje `On Error Resume Next` příkaz. Tento příkaz umožňuje, aby provádění pokračovalo navzdory chybě v době běhu. Můžete umístit rutinu pro zpracování chyb, kde by došlo k chybě místo přenosu řízení do jiného umístění v rámci postupu. Příkaz se neaktivuje, pokud je volána jiná procedura, takže byste měli `On Error Resume Next` provést příkaz v každé rutině s názvem, pokud chcete v rámci této rutiny zpracovat vložené chyby. `On Error Resume Next`
  
> [!NOTE]
>  Konstrukce může být vhodnější `On Error GoTo` při zpracování chyb generovaných při přístupu k jiným objektům. `On Error Resume Next` Kontrola `Err` po každé interakci s objektem odebere nejednoznačnost o tom, který objekt byl získán pomocí kódu. Můžete si být jisti, který objekt umístil kód chyby v `Err.Number`, a také objekt původně vygeneroval chybu (objekt určený v `Err.Source`).

## <a name="on-error-goto-0"></a>Při chybě GoTo 0
 `On Error GoTo 0`Zakáže zpracování chyb v aktuální proceduře. Nespecifikuje řádek 0 jako začátek kódu pro zpracování chyb, a to i v případě, že procedura obsahuje řádek s číslem 0. `On Error GoTo 0` Bez příkazu je obslužná rutina chyby automaticky zakázána při ukončení procedury.

## <a name="on-error-goto--1"></a>Při chybě GoTo-1
 `On Error GoTo -1`zakáže výjimku v aktuální proceduře. Neurčuje řádek-1 jako začátek kódu pro zpracování chyb, a to i v případě, že procedura obsahuje řádek s číslem 1. `On Error GoTo -1` Bez příkazu je výjimka automaticky zakázána při ukončení procedury.

 Chcete-li zabránit spuštění kódu pro zpracování chyb, pokud nedošlo k žádné chybě `Exit Sub`, `Exit Function`umístěte příkaz `Exit Property` , nebo těsně před rutinu zpracování chyb, jako v následujícím fragmentu:

 [!code-vb[VbVbalrErrorHandling#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#18)]

 Zde je kód `Exit Sub` pro ošetření chyb následován příkazem a předchází `End Sub` příkazu k oddělení od toku procedury. Kód pro zpracování chyb lze umístit kdekoli v proceduře.

## <a name="untrapped-errors"></a>Nepřesahovat chyby
 Nezachycené chyby v objektech se vrátí do řídicí aplikace, když je objekt spuštěn jako spustitelný soubor. V rámci vývojového prostředí se chyby bez přesahů vrátí do řídicí aplikace pouze v případě, že jsou nastaveny správné možnosti. Popis možností nastavení, které by měly být nastaveny během ladění, jak je nastavit a zda může hostitel vytvořit třídy, najdete v dokumentaci hostitelské aplikace.

 Vytvoříte-li objekt, který přistupuje k jiným objektům, měli byste se pokusit zpracovat jakékoli neošetřené chyby, které přejdou zpět. Pokud nemůžete, namapujte kódy chyb `Err.Number` v nástroji na jednu z vašich vlastních chyb a pak je předejte volajícímu objektu. Tuto chybu byste měli zadat tak, že do `VbObjectError` konstanty přidáte kód chyby. Například pokud kód chyby je 1052, přiřaďte ho následujícím způsobem:

 [!code-vb[VbVbalrErrorHandling#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#19)]

> [!CAUTION]
>  Systémové chyby během volání knihoven DLL (Dynamic-Link Library) systému Windows nevyvolávají výjimky a nemohou být zachyceny pomocí Visual Basic soutisku chyb. Při volání funkcí knihoven DLL byste měli kontrolovat každou vrácenou hodnotu pro úspěch nebo neúspěch (podle specifikací rozhraní API) a v případě selhání kontrolovat hodnotu `Err` `LastDLLError` vlastnosti objektu.

## <a name="example"></a>Příklad
 Tento příklad nejprve používá `On Error GoTo` příkaz k určení umístění rutiny zpracování chyb v rámci procedury. V příkladu se při pokusu o dělení nulou vygeneruje chybová zpráva číslo 6. Chyba je zpracována v rutině zpracování chyb a ovládací prvek je poté vrácen do příkazu, který způsobil chybu. `On Error GoTo 0` Příkaz vypne soutisk chyb. `On Error Resume Next` Pak příkaz slouží k odložení soutisku chyb, takže kontext pro chybu vygenerovanou dalším příkazem může být pro některé z nich známý. Všimněte si `Err.Clear` , že se po zpracování `Err` chyby používá k vymazání vlastností objektu.

 [!code-vb[VbVbalrErrorHandling#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#20)]

## <a name="requirements"></a>Požadavky
 **Hosting** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)

 **Shromážděním** Visual Basic Runtime Library (v souboru Microsoft.VisualBasic.dll)

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
