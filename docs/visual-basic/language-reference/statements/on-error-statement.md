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
ms.openlocfilehash: 0a5a5261e6b71178adce02a5635c1f91a1469f3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784069"
---
# <a name="on-error-statement-visual-basic"></a>On Error – příkaz (Visual Basic)
Umožňuje rutiny zpracování chyb a určuje umístění rutinu v rámci procedury; je také možné zakázat rutiny zpracování chyb.  
  
 Bez zpracování chyb, je všechny běhové chyby, ke které dochází závažná: zobrazí chybovou zprávu a zastaví provádění.  
  
 Kdykoli je to možné, doporučujeme používat strukturované výjimky zpracování ve svém kódu místo používání zpracování výjimek nestrukturovaných a `On Error` příkazu. Další informace najdete v tématu [zkuste... Catch... Příkaz finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  `Error` – Klíčové slovo se používá také v [Error – příkaz](../../../visual-basic/language-reference/statements/error-statement.md), který je podporován z důvodu zpětné kompatibility.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
On Error { GoTo [ line | 0 | -1 ] | Resume Next }  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`GoTo``line`|Umožňuje zpracování chyb rutiny, která začíná na řádku zadaném v požadovaném `line` argument. `line` Argumentem je libovolný popisku řádku nebo číslo řádku. Pokud dojde k chybě za běhu, řídit větví na určený řádek aktivace obslužnou rutinu chyb. Zadaný řádek musí být ve stejné proceduře jako `On Error` nebo chybu kompilace dojde.|  
|`GoTo` 0|Zakáže povolenou obslužnou rutinu chyb v aktuální proceduře a vynuluje ji do `Nothing`.|  
|`GoTo` -1|Zakáže povolenou výjimku v aktuální proceduře a vynuluje ji do `Nothing`.|  
|`Resume Next`|Určuje, že pokud dojde k chybě za běhu, ovládací prvek přejde na příkaz okamžitě následující příkaz, kde došlo k chybě, a pokračuje od tohoto okamžiku. Pomocí tohoto formuláře spíše než `On Error GoTo` při přístupu k objektům.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Doporučujeme používat strukturované zpracování výjimek ve vašem kódu, kdykoli je to možné, spíš než nestrukturované zpracování výjimek a `On Error` příkazu. Další informace najdete v tématu [zkuste... Catch... Příkaz finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Obslužná rutina chyby "povoleno" je ten, který je zapnutá `On Error` příkazu. Obslužná rutina chyby "aktivní" je povoleno obslužnou rutinu, která se právě zpracování chyby.  
  
 Pokud dojde k chybě obslužná rutina chyby je aktivní (mezi výskytu chyby a `Resume`, `Exit Sub`, `Exit Function`, nebo `Exit Property` příkaz), aktuální proceduru obslužná rutina chyb nelze chybu zpracovat. Ovládací prvek se vrátí do volající procedury.  
  
 Pokud má volající procedury povolenou obslužnou rutinu chyb, se aktivuje chybu zpracovat. Pokud obslužná rutina chyb volání procedury je také aktivní, řízení se předá zpět do předchozího volání procedury dokud nebude nalezen obslužnou rutinu chyb povoleno, ale neaktivní. Pokud se nenajde žádný takový obslužná rutina chyb, se v okamžiku, kdy ho skutečně došlo k závažné chyby.  
  
 Pokaždé, když chyba obslužná rutina předá řízení zpět do volání procedury, tento postup se změní aktuální proceduře. Po chybě zařizuje služba obslužná rutina chyby v všechny procedury, provádění pokračuje v aktuální proceduře v místě určeném `Resume` příkazu.  
  
> [!NOTE]
>  Rutiny zpracování chyb není `Sub` procedury nebo `Function` postup. To je část kódu označeného řádku popisek nebo číslo řádku.  
  
## <a name="number-property"></a>Number – vlastnost  
 Rutiny zpracování chyb závisí na hodnotě `Number` vlastnost `Err` objektu určit příčinu chyby. Rutiny byste testování nebo uložit hodnoty příslušných vlastností v `Err` objektu před další chyba může nastat, nebo před procedury, která může způsobit, že je volána k chybě. Vlastnost hodnoty v `Err` objekt odrážejí pouze poslední chybu. Chybové zprávy přidružené k `Err.Number` je součástí `Err.Description`.  
  
## <a name="throw-statement"></a>Throw – příkaz  
 K chybě, která je vyvolána s `Err.Raise` metody nastaví `Exception` vlastnost nově vytvořená instance <xref:System.Exception> třídy. Aby bylo možné podporovat vyvolání výjimky, které typy odvozené výjimek, `Throw` příkaz je podporován v jazyce. Tato akce trvá jeden parametr, který je instance výjimky, která je vyvolána. Následující příklad ukazuje, jak lze tyto funkce s výjimkou existující podpory obsluhy výjimek:  
  
 [!code-vb[VbVbalrErrorHandling#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#17)]  
  
 Všimněte si, že `On Error GoTo` příkaz zachycuje všechny chyby, bez ohledu na třídě výjimky.  
  
## <a name="on-error-resume-next"></a>On Error Resume Next  
 `On Error Resume Next` způsobí, že v provádění pokračovat s příkazem bezprostředně následující příkaz, který způsobil chybu za běhu, nebo pomocí příkazu hned za poslední volat z procedury obsahující `On Error Resume Next` příkazu. Tento příkaz umožňuje provádění pokračovat bez ohledu na chyb za běhu. Rutiny zpracování chyb, ve kterém by k této chybě dojít spíše než přenos řízení na jiné místo v rámci postupu můžete umístit. `On Error Resume Next` Příkaz změní na neaktivní při volání jiného režimu, proto by měl provést `On Error Resume Next` příkaz v každém volána rutina, pokud chcete v rámci této rutiny pro zpracování chyb vložené.  
  
> [!NOTE]
>  `On Error Resume Next` Konstruktor může být vhodnější `On Error GoTo` při zpracování chyb generovaných při přístupu k jiným objektům. Kontrola `Err` po každé interakci s objektem odebere nejednoznačnost o tom, která se použila objekt v kódu. Můžete si být jisti objektu umístěn kód chyby v `Err.Number`, stejně jako objekt, který původně vytvořil chybu (objekt určený v `Err.Source`).  
  
## <a name="on-error-goto-0"></a>Na Error GoTo 0  
 `On Error GoTo 0` zakáže zpracování chyb v aktuální proceduře. Ji neurčuje linky 0 jako počáteční kód pro zpracování chyb, i v případě, že postup obsahuje řádek s číslem 0. Bez `On Error GoTo 0` prohlášení, obslužná rutina chyby se automaticky zakáže při procedury je byl ukončen.  
  
## <a name="on-error-goto--1"></a>Na Error GoTo -1  
 `On Error GoTo -1` Zakáže výjimku v aktuální proceduře. Neurčuje řádku -1 jako počáteční kód pro zpracování chyb, i v případě, že postup obsahuje jeden řádek číslované -1. Bez `On Error GoTo -1` příkaz výjimky se automaticky zakáže při procedury je byl ukončen.  
  
 Pokud chcete zabránit spuštění, když nedojde k žádné chybě kód pro zpracování chyb, umístěte `Exit Sub`, `Exit Function`, nebo `Exit Property` příkaz bezprostředně před rutina zpracování chyb, stejně jako v následujícím fragmentu:  
  
 [!code-vb[VbVbalrErrorHandling#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#18)]  
  
 Kód pro zpracování chyb následuje `Exit Sub` příkazu a předchází `End Sub` příkaz k oddělení od toku procedury. Kód pro zpracování chyb můžete umístit kdekoli v postupu.  
  
## <a name="untrapped-errors"></a>Untrapped chyby  
 Untrapped chyby v objektech se vrátí k řídicí aplikaci při objektu je spuštěn jako spustitelný soubor. V rámci vývojového prostředí jsou vráceny untrapped chyby k řídicí aplikaci pouze v případě, že jsou nastaveny správné možnosti. Popis, z nichž by měl být možnosti sady během ladění, jak je nastavit a zda hostitele můžete vytvořit třídy naleznete v dokumentaci své hostitelské aplikaci.  
  
 Pokud vytvoříte objekt, který přistupuje k jiné objekty, doporučujeme zpracovat všechny neošetřené chyby, které se předají zpět. Pokud nelze mapovat kódy chyb v `Err.Number` do jedné z vlastních chyb a pak je předat zpět do volajícího objektu. Chyby by měl určit tak, že přidáte kód chyby `VbObjectError` konstantní. Například pokud váš kód chyby je 1052, je také přiřadíte tímto způsobem:  
  
 [!code-vb[VbVbalrErrorHandling#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#19)]  
  
> [!CAUTION]
>  Chyby systému během volání Windows dynamické knihovny (DLL) nevyvolávejte výjimky a nemůže být zachycena s chyba soutisku jazyka Visual Basic. Při volání funkcí knihovny DLL, je potřeba zkontrolovat každou návratovou hodnotu pro úspěch nebo neúspěch (podle specifikace rozhraní API) a v případě selhání, zkontrolujte hodnotu `Err` objektu `LastDLLError` vlastnost.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se nejdřív pomocí `On Error GoTo` příkaz a zadejte umístění rutiny zpracování chyb v rámci procedury. V tomto příkladu generuje pokus dělit nulou číslo chyby 6. Je chyba zpracována v rutině zpracování chyb a ovládací prvek se poté vrátí příkazu, který způsobil chybu. `On Error GoTo 0` Příkaz vypne Chyba soutisku. Pak bude `On Error Resume Next` prohlášení se používá k odložení Chyba soutisku tak, aby kontext chyby generované dalšího příkazu můžete pro některé známé. Všimněte si, že `Err.Clear` slouží k vymazání `Err` vlastností objektu po je chyba zpracována.  
  
 [!code-vb[VbVbalrErrorHandling#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#20)]  
  
## <a name="requirements"></a>Požadavky  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Sestavení:** Visual Basic Runtime Library (v souboru Microsoft.VisualBasic.dll)  
  
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
