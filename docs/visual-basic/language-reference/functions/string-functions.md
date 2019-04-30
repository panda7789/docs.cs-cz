---
title: Funkce řetězce (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- string functions
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
ms.openlocfilehash: 645d19219481d22ade90f44aaecb62471eb915d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801989"
---
# <a name="string-functions-visual-basic"></a>Funkce řetězce (Visual Basic)
V následující tabulce jsou uvedeny funkce, které Visual Basic poskytuje pro vyhledávání a manipulaci s řetězci.  
  
|Rozhraní .NET framework – metoda|Popis|  
|---------------------------|-----------------|  
|<xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>|Vrátí `Integer` hodnotu představující kód odpovídající znaku.|  
|<xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>|Vrátí znak spojený se zadaným kódem znaku.|  
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|Vrátí pole s nulovým základem obsahující dílčí sadu `String` pole podle zadaných kritérií filtru.|  
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|Vrátí řetězec formátovaný podle pokynů obsažených ve formátu `String` výrazu.|  
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|Vrací výraz formátovaný jako hodnota měny pomocí symbolu měny definovaného na ovládacím panelu systému.|  
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|Vrátí řetězcový výraz představující hodnotu data a času.|  
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|Vrací výraz formátovaný jako číslo.|  
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|Vrací výraz formátovaný jako procentuální údaj (tj. vynásobený číslem 100) s zakončený znakem %.|  
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|Vrátí celé číslo určující počáteční pozici prvního výskytu jednoho řetězce v jiném.|  
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|Vrátí pozici prvního výskytu jednoho řetězce v jiném počínaje od pravé strany řetězce.|  
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|Vrátí řetězec vytvořený spojením řady dílčích řetězců obsažených v poli.|  
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|Vrací řetězec nebo znak převedený na malá písmena.|  
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|Vrátí řetězec obsahující zadaný počet znaků z levé strany řetězce.|  
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|Vrátí celé číslo obsahující počet znaků v řetězci.|  
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|Vrací vlevo zarovnaný řetězec obsahující určený řetězec přizpůsobený na určenou délku.|  
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|Vrátí řetězec obsahující kopii zadaného řetězce bez počátečních mezer.|  
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|Vrátí řetězec obsahující zadaný počet znaků z řetězce.|  
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|Vrátí řetězec, ve kterém je určený dílčí řetězec má nahrazen jiným dílčím řetězcem zadaného počtu opakování.|  
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|Vrátí řetězec obsahující zadaný počet znaků od pravé strany řetězce.|  
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|Vrací vpravo zarovnaný řetězec obsahující určený řetězec přizpůsobený na určenou délku.|  
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|Vrátí řetězec obsahující kopii zadaného řetězce bez koncových mezer.|  
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|Vrátí řetězec sestávající ze zadaného počtu mezer.|  
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|Vrátí založený na nule, jednorozměrné pole obsahující zadaný počet podřetězců.|  
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|Vrátí hodnotu -1, 0 nebo 1 na základě výsledku porovnání řetězců.|  
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|Vrátí řetězec převedený podle určení.|  
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|Vrátí řetězec nebo objekt tvořený zadaným znakem zadaný počet pokusů o opakování.|  
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|Vrátí řetězec, ve kterém je obrácené pořadí znaků ze zadaného řetězce.|  
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|Vrátí řetězec obsahující kopii zadaného řetězce bez počátečních a koncových mezer.|  
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|Vrátí řetězec nebo znak obsahující určený řetězec převedený na velká písmena.|  
  
 Můžete použít [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) řazení příkazu pro nastavení, zda jsou řetězce porovnány pomocí nerozlišujícího velikost písmen textu podle národního prostředí systému (`Text`) nebo vnitřní binární reprezentace znaků ( `Binary`). Výchozí metoda porovnání textu je `Binary`.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `UCase` funkce vrací verzi řetězce s velkými písmeny.  
  
 [!code-vb[VbVbalrStrings#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#31)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `LTrim` funkce pro odstranění úvodních mezer a `RTrim` funkce pro odstranění koncových mezer z proměnné řetězce. Používá `Trim` funkce pro odstranění obou typů mezer.  
  
 [!code-vb[VbVbalrStrings#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#25)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `Mid` funkce vrací zadaný počet znaků z řetězce.  
  
 [!code-vb[VbVbalrStrings#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#17)]  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `Len` k vrácení počtu znaků v řetězci.  
  
 [!code-vb[VbVbalrStrings#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#33)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `InStr` funkce vrací pozici prvního výskytu jednoho řetězce v jiném.  
  
 [!code-vb[VbVbalrStrings#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#8)]  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje různé možnosti použití `Format` funkce pro formátování hodnot pomocí obou `String` formátů a formátů definovaný uživatelem. Pro oddělovač data (`/`), oddělovač času (`:`) a indikátory dop/odp (`t` a `tt`), skutečný formátovaný výstup zobrazený v systému, závisí na nastavení národního prostředí, které kód používá. Když časy a data zobrazí ve vývojovém prostředí, používají se krátký formát času a krátký formát data národního prostředí kódu.  
  
> [!NOTE]
>  Pro národní prostředí používající 24hodinový formát indikátory dop/odp (`t` a `tt`) nezobrazí.  
  
 [!code-vb[VbVbalrStrings#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#27)]  
  
## <a name="see-also"></a>Viz také:

- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
- [Členové knihovny modulu runtime jazyka Visual Basic](../../../visual-basic/language-reference/runtime-library-members.md)
- [Souhrn manipulace s řetězci](../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)
