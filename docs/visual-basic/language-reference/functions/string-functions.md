---
title: Funkce řetězce
ms.date: 07/20/2015
helpviewer_keywords:
- string functions
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
ms.openlocfilehash: 2608159e28ee63a0fdb10c82054fd65efe79ac62
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349984"
---
# <a name="string-functions-visual-basic"></a>Funkce řetězce (Visual Basic)

V následující tabulce jsou uvedeny funkce, které Visual Basic poskytuje ve třídě <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType> k hledání a manipulaci s řetězci. Je možné je považovat za Visual Basic vnitřních funkcí; To znamená, že je nemusíte volat jako explicitní členy třídy, jak je znázorněno v příkladu. Další metody a v některých případech doplňkové metody jsou k dispozici ve třídě <xref:System.String?displayProperty=nameWithType>.

|.NET Framework – metoda|Popis|
|---------------------------|-----------------|
|<xref:Microsoft.VisualBasic.Strings.Asc%2A><xref:Microsoft.VisualBasic.Strings.AscW%2A>|Vrací hodnotu `Integer` reprezentující kód znaku odpovídající znaku.|
|<xref:Microsoft.VisualBasic.Strings.Chr%2A><xref:Microsoft.VisualBasic.Strings.ChrW%2A>|Vrátí znak přiřazený k určenému kódu znaku.|
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|Vrací pole s nulovým základem obsahující podmnožinu `String` pole na základě zadaných kritérií filtru.|
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|Vrátí řetězec formátovaný podle pokynů obsažených ve formátu `String` výrazu.|
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|Vrací výraz formátovaný jako hodnota měny pomocí symbolu měny definovaného na ovládacím panelu systému.|
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|Vrátí řetězcový výraz představující hodnotu data a času.|
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|Vrátí výraz formátovaný jako číslo.|
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|Vrátí výraz formátovaný jako procento (vynásobený 100) s koncovým znakem%.|
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|Vrací celé číslo určující počáteční pozici prvního výskytu jednoho řetězce v rámci druhého.|
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|Vrátí pozici prvního výskytu jednoho řetězce v rámci druhého počínaje od pravé strany řetězce.|
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|Vrátí řetězec vytvořený spojením několika podřetězců obsažených v poli.|
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|Vrátí řetězec nebo znak převedený na malá písmena.|
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|Vrátí řetězec obsahující zadaný počet znaků od levé strany řetězce.|
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|Vrátí celé číslo, které obsahuje počet znaků v řetězci.|
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|Vrátí řetězec zarovnaný doleva obsahující zadaný řetězec upravený na zadanou délku.|
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|Vrátí řetězec obsahující kopii zadaného řetězce bez počátečních mezer.|
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|Vrátí řetězec obsahující zadaný počet znaků z řetězce.|
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|Vrátí řetězec, ve kterém byl zadaný dílčí řetězec nahrazen jiným dílčím řetězcem, který je určený počtem opakování.|
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|Vrátí řetězec obsahující zadaný počet znaků z pravé strany řetězce.|
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|Vrátí řetězec zarovnaný doprava obsahující zadaný řetězec upravený na zadanou délku.|
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|Vrátí řetězec obsahující kopii zadaného řetězce bez koncových mezer.|
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|Vrátí řetězec sestávající z určeného počtu mezer.|
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|Vrací jednorozměrné pole s nulovým základem obsahující určený počet podřetězců.|
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|Vrátí hodnotu-1, 0 nebo 1 na základě výsledku porovnání řetězců.|
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|Vrátí řetězec převedený podle zadání.|
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|Vrátí řetězec nebo objekt skládající se ze zadaného znaku, který se opakuje po zadaném počtu opakování.|
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|Vrátí řetězec, ve kterém je obráceno pořadí znaků zadaného řetězce.|
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|Vrátí řetězec obsahující kopii zadaného řetězce bez mezer na začátku nebo na konci.|
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|Vrátí řetězec nebo znak obsahující určený řetězec převedený na velká písmena.|

Pomocí příkazu [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) můžete nastavit, zda jsou řetězce porovnány pomocí pořadí řazení textu bez rozlišení velkých a malých písmen určených národním prostředím systému (`Text`) nebo vnitřními binárními reprezentacemi znaků (`Binary`). Výchozí metoda porovnání textu je `Binary`.

## <a name="example-ucase"></a>Příklad: UCase

V tomto příkladu se pomocí funkce `UCase` vrátí velká a malá verze řetězce.
[!code-vb[VbVbalrStrings#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#31)]

## <a name="example-ltrim"></a>Příklad: LTrim

V tomto příkladu se používá funkce `LTrim` k obložení úvodních mezer a funkce `RTrim` k obložení koncových mezer z řetězcové proměnné. Používá funkci `Trim` k odstranění obou typů mezer.

[!code-vb[VbVbalrStrings#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#25)]

## <a name="example-mid"></a>Příklad: Mid

Tento příklad používá funkci `Mid` k vrácení zadaného počtu znaků z řetězce.

[!code-vb[VbVbalrStrings#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#17)]

## <a name="example-len"></a>Příklad: len

V tomto příkladu se používá `Len` k vrácení počtu znaků v řetězci.

[!code-vb[VbVbalrStrings#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#33)]

## <a name="example-instr"></a>Příklad: InStr

V tomto příkladu se používá funkce `InStr` pro vrácení pozice prvního výskytu jednoho řetězce v jiném.

[!code-vb[VbVbalrStrings#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#8)]

## <a name="example-format"></a>Příklad: formát

Tento příklad ukazuje různá použití funkce `Format` k formátování hodnot pomocí formátů `String` a uživatelsky definovaných formátů. V případě oddělovače data (`/`), oddělovače času (`:`) a indikátory AM/PM (`t` a `tt`) je skutečný formátovaný výstup zobrazený systémem závislý na nastavení národního prostředí, které kód používá. Když jsou časy a kalendářní data zobrazeny ve vývojovém prostředí, je použit krátký formát času a formát krátkého data národního prostředí kódu.

> [!NOTE]
> Pro národní prostředí, která používají 24hodinové hodiny, se indikátory AM/PM (`t` a `tt`) nezobrazí nic.

[!code-vb[VbVbalrStrings#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#27)]

## <a name="see-also"></a>Viz také:

- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
- [Členové knihovny modulu runtime jazyka Visual Basic](../../../visual-basic/language-reference/runtime-library-members.md)
- [Souhrn manipulace s řetězci](../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)
- [Metody třídy System. String](xref:System.String#methods)
