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
ms.openlocfilehash: b2e32dcca2e29a178af6dc985da536b47f0ebae6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="on-error-statement-visual-basic"></a>On Error – příkaz (Visual Basic)
Umožňuje rutiny zpracování chyb a určuje umístění rutiny v rámci procedury; Můžete také použít zakázat rutiny chyba zpracování.  
  
 Bez zpracování chyb, je chyba, ke kterému dochází při spuštění jakékoli závažné: Zobrazí se chybová zpráva a provádění zastaví.  
  
 Pokud je to možné, doporučujeme použít strukturovaného výjimek zpracování ve vašem kódu, nikoli pomocí nestrukturovaných výjimek a `On Error` příkaz. Další informace najdete v tématu [zkuste... Catch... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  `Error` – Klíčové slovo používá taky v [Error – příkaz](../../../visual-basic/language-reference/statements/error-statement.md), což je podporováno pro zpětnou kompatibilitu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
On Error { GoTo [ line | 0 | -1 ] | Resume Next }  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`GoTo``line`|Umožňuje rutiny zpracování chyb, který začíná na řádku zadaný v požadovaných `line` argument. `line` Argument je jakákoliv popisek čáry nebo číslo řádku. Pokud dojde k chybě spuštění, ovládání přejde k zadaný řádek, aktivace obslužná rutina chyb. Zadaný řádek musí být v stejným způsobem jako `On Error` příkaz nebo chybě kompilace dojde.|  
|`GoTo` 0|Zakáže obslužné rutiny povoleno chyb v aktuální postupu a obnoví jeho `Nothing`.|  
|`GoTo` -1|Zakáže povolené výjimky v aktuální postupu a obnoví jeho `Nothing`.|  
|`Resume Next`|Určuje, že když dojde k chybě spuštění, řízení přejde na příkaz okamžitě následující příkaz, kde došlo k chybě a provádění pokračuje od tohoto okamžiku. Tento formulář použijte místo `On Error GoTo` při přístupu k objektům.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Doporučujeme použít strukturované zpracování výjimek ve vašem kódu, pokud je to možné, nikoli pomocí nestrukturovaných výjimek a `On Error` příkaz. Další informace najdete v tématu [zkuste... Catch... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 "Povoleno" Obslužná rutina je ten, který je ve zapnuta `On Error` příkaz. "Aktivní" Obslužná rutina je povoleno obslužná rutina, která probíhá zpracování chyby.  
  
 Pokud dojde k chybě při zpracování chyb je aktivní (mezi výskyt chyby a `Resume`, `Exit Sub`, `Exit Function`, nebo `Exit Property` příkaz), aktuální procedury obslužnou rutinu chyby nemůže zpracovat chyba. Vrátí ovládací prvek volání procedury.  
  
 Pokud volání procedury má povoleno obslužná rutina, je aktivováno pro zpracování chyby. Pokud obslužnou rutinu chyby volání procedury je také aktivní, prvek předává zpátky pomocí předchozích postupů volání až do nalezení obslužnou rutinu chyb povoleno, ale neaktivní. Pokud se nenajde žádný takový obslužnou rutinu chyby, je v okamžiku, kdy je ve skutečnosti došlo k závažné chyby.  
  
 Pokaždé, když obslužná rutina chyb – ovládací prvek předává zpět do volání procedury, tento postup se změní na aktuální procedury. Po chybě je zpracováván obslužnou rutinou chyba jakékoli řízení, provádění pokračuje v postupu aktuální v okamžiku určené, které `Resume` příkaz.  
  
> [!NOTE]
>  Rutiny zpracování chyby není `Sub` postup nebo `Function` postupu. Je části kódu, které jsou označeny popisek čáry nebo číslo řádku.  
  
## <a name="number-property"></a>Vlastnost počtu  
 Rutiny zpracování chyb závisí na hodnotě v `Number` vlastnost `Err` objekt, který chcete-li určit příčinu chyby. Rutiny by měl testů nebo uložit hodnoty relevantní vlastností v `Err` objektu před jiné chybě může dojít, nebo před procedury, která může způsobit, že je volána k chybě. Vlastnost hodnoty ve `Err` objekt odráží pouze poslední chybu. Chybová zpráva přidružená `Err.Number` je součástí `Err.Description`.  
  
## <a name="throw-statement"></a>Throw – příkaz  
 K chybě, která se vyvolá s `Err.Raise` metoda nastaví `Exception` vlastnosti tak, aby nově vytvořená instance <xref:System.Exception> – třída. Za účelem podpory vyvolání výjimky typy odvozené výjimek `Throw` příkaz je podporován v jazyce. Tato akce trvá jeden parametr, který je instancí výjimka vyvolání. Následující příklad ukazuje, jak tyto funkce lze použít s existující zpracování podpora výjimek:  
  
 [!code-vb[VbVbalrErrorHandling#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_1.vb)]  
  
 Všimněte si, že `On Error GoTo` příkaz traps všechny chyby, bez ohledu na třídy výjimek.  
  
## <a name="on-error-resume-next"></a>On Error Resume Next  
 `On Error Resume Next` způsobí, že provádění pokračujte s příkazem okamžitě následující příkaz, který způsobil chybu spuštění nebo s příkazem hned za nejnovější volání mimo procedury obsahující `On Error Resume Next` příkaz. Tento příkaz umožňuje provádění pokračovat i přes Chyba spuštění. Rutiny zpracování chyb, kde by dojít k chybě spíše než přenášení řízení do jiného umístění v rámci procesu můžete umístit. `On Error Resume Next` Neaktivní při jiné procedura je volána, proto by měl provést `On Error Resume Next` příkaz v každé názvem rutiny, pokud chcete, aby vložené chyba zpracování v rámci této rutiny.  
  
> [!NOTE]
>  `On Error Resume Next` Konstrukce může být vhodnější než `On Error GoTo` při zpracování chyb vygenerovaných během přístupu k jiné objekty. Kontrola `Err` po každé interakci s objektem odebere nejednoznačnosti o tom, které byl objekt přistupují kód. Můžete si být jisti který objekt umístit kód chyby v `Err.Number`, a také objekt, který původně vytvořil chybu (objekt určený v `Err.Source`).  
  
## <a name="on-error-goto-0"></a>Na chyby GoTo 0  
 `On Error GoTo 0` zakáže zpracování chyb v aktuálním procesu. Neurčuje řádku 0 jako začátek kód pro ošetření chyb, i v případě, že procedura obsahuje řádek s číslem 0. Bez `On Error GoTo 0` příkaz obslužná rutina se automaticky zakáže při procedury je byl ukončen.  
  
## <a name="on-error-goto--1"></a>Na GoTo chyby -1  
 `On Error GoTo -1` Zakáže výjimka v aktuálním procesu. Neurčuje řádku -1 jako začátek kód pro ošetření chyb, i v případě, že procedura obsahuje řádek s číslem -1. Bez `On Error GoTo -1` příkaz výjimku se automaticky zakáže při procedury je byl ukončen.  
  
 Chcete-li zabránit spuštěn, když došlo k žádné chybě kód pro ošetření chyb, označte jej `Exit Sub`, `Exit Function`, nebo `Exit Property` bezprostředně před rutiny zpracování chyb, jako v následujícím fragmentu:  
  
 [!code-vb[VbVbalrErrorHandling#18](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_2.vb)]  
  
 Zde následuje kód pro ošetření chyb `Exit Sub` příkaz a předchází `End Sub` příkaz k oddělení od toku postupu. Kód pro ošetření chyb můžete umístit kdekoli v postupu.  
  
## <a name="untrapped-errors"></a>Untrapped chyby  
 Untrapped chyby v objektech se vrátíte na řízení aplikace, když objekt běží jako spustitelný soubor. V rámci vývojového prostředí jsou untrapped chyby vrácené řídící aplikaci pouze v případě, že jsou nastaveny správné možnosti. Popis z nich by měl být možnosti nastavenou během ladění, jak je nastavit a jestli hostitele můžete vytvořit třídy jsou uvedeny v dokumentaci hostitelskou aplikaci.  
  
 Pokud vytvoříte objekt, který přistupuje k jiné objekty, se pokuste zpracovat všechny neošetřené chyby, které se předají zpět. Pokud namapujete nelze, kódy chyb v `Err.Number` jeden z vašich vlastních chyb a pak předejte je zpět do volajícího objektu. Musíte zadat vaše chyba přidáním kódu chyby `VbObjectError` konstantní. Například pokud váš kód chyby je 1052, přiřadíte ho následujícím způsobem:  
  
 [!code-vb[VbVbalrErrorHandling#19](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_3.vb)]  
  
> [!CAUTION]
>  Chyby systému během volání Windows dynamické knihovny (DLL) není vyvolávání výjimek a nemůže být zachycena s chyba soutisku jazyka Visual Basic. Při volání funkcí knihovny DLL, je potřeba zkontrolovat každou návratovou hodnotu úspěch či neúspěch (podle specifikace rozhraní API) a v případě selhání, zkontrolujte hodnotu `Err` objektu `LastDLLError` vlastnost.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá nejdřív `On Error GoTo` příkaz k určení umístění rutiny chyba zpracování v rámci procedury. V příkladu se generuje pokus dělit nulou číslo chyby 6. Zpracovává k chybě v rutině zpracování chyb a řízení je pak vrácen do příkazu, který způsobil chybu. `On Error GoTo 0` Příkaz vypne Chyba soutisku. Pak se `On Error Resume Next` příkaz slouží k odložení Chyba soutisku tak, aby kontext chyby generovaných další příkaz může být pro určité známé. Všimněte si, že `Err.Clear` se používá k uvolnění `Err` vlastností objektu po chyba se zpracovává.  
  
 [!code-vb[VbVbalrErrorHandling#20](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_4.vb)]  
  
## <a name="requirements"></a>Požadavky  
 **Namespace:** [Microsoft.VisualBasic –](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Sestavení:** jazyka Visual Basic Runtime Library (v souboru Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Number%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Description%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>  
 [Příkaz End](../../../visual-basic/language-reference/statements/end-statement.md)  
 [Příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Příkaz Resume](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [Chybové zprávy](../../../visual-basic/language-reference/error-messages/index.md)  
 [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
