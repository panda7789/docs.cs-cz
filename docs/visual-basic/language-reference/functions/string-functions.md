---
title: Funkce řetězce (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- string functions
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
ms.openlocfilehash: f6c7f28cee03c2d5ac258cf1e2c8956225334f7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604143"
---
# <a name="string-functions-visual-basic"></a>Funkce řetězce (Visual Basic)
Následující tabulka uvádí funkce, které Visual Basic poskytuje k vyhledávání a manipulaci s řetězci.  
  
|Rozhraní .NET framework – metoda|Popis|  
|---------------------------|-----------------|  
|<xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>|Vrátí `Integer` hodnotu představující kód odpovídající znaku.|  
|<xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>|Vrací znak přiřazený k určenému kódu znaku.|  
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|Vrátí pole s nulovým základem obsahující dílčí sadu `String` pole podle zadaných kritérií filtru.|  
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|Vrací řetězec formátovaný podle pokynů obsažených ve formátu `String` výraz.|  
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|Vrací výraz formátovaný jako hodnota měny pomocí symbolu měny definovaného v Ovládacích panelech systému.|  
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|Vrací výraz řetězce představující hodnotu data a času.|  
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|Vrací výraz formátovaný jako číslo.|  
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|Vrací výraz formátovaný jako procento (tj, násobenou 100) s znakem %.|  
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|Vrátí celé číslo určující počáteční pozici prvního výskytu jednoho řetězce v jiném.|  
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|Vrátí pozici prvního výskytu jednoho řetězce v rámci druhého, počínaje z pravé strany řetězce.|  
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|Vrací řetězec vytvořený sloučením několika dílčích řetězců obsažených v poli.|  
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|Vrací řetězec nebo znak převedený na malá písmena.|  
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|Vrací řetězec obsahující určený počet znaků z řetězce levé strany.|  
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|Vrátí celé číslo, které obsahuje počet znaků v řetězci.|  
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|Vrací vlevo zarovnaný řetězec obsahující určený řetězec přizpůsobený na určenou délku.|  
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|Vrací řetězec obsahující kopii určeného řetězce bez mezer na začátku.|  
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|Vrací řetězec obsahující určený počet znaků z řetězce.|  
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|Vrátí řetězec, ve kterém je určený dílčí řetězec má nahrazen jiným dílčím řetězcem zadaného počtu opakování.|  
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|Vrací řetězec obsahující určený počet znaků z pravé strany řetězce.|  
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|Vrací vpravo zarovnaný řetězec obsahující určený řetězec přizpůsobený na určenou délku.|  
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|Vrací řetězec obsahující kopii určeného řetězce koncové mezery.|  
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|Vrací řetězec sestávající z určeného počtu mezer.|  
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|Vrátí nule jednorozměrné pole obsahující určený počet dílčích řetězců.|  
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|Vrátí hodnotu -1, 0 nebo 1, na základě výsledku porovnání řetězců.|  
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|Vrací řetězec převedený podle určení.|  
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|Vrátí řetězec nebo objekt sestávající z určeného znaku opakuje zadaného počtu opakování.|  
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|Vrátí řetězec, ve kterém je pořadí znaků z určeného řetězce obrácený.|  
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|Vrací řetězec obsahující kopii určeného řetězce bez mezer na začátku nebo na konci.|  
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|Vrací řetězec nebo znak obsahující určený řetězec převedený na velká písmena.|  
  
 Můžete použít [možnost porovnat](../../../visual-basic/language-reference/statements/option-compare-statement.md) pořadí dáno národního prostředí vašeho systému řazení příkaz, který má-li nastavit, jestli jsou porovnány pomocí velká a malá písmena textového řetězce (`Text`) nebo interní binární reprezentace (znaků `Binary`). Výchozí metoda porovnání textu je `Binary`.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `UCase` funkci vrátíte verzi řetězec s velkými písmeny.  
  
 [!code-vb[VbVbalrStrings#31](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_1.vb)]  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `LTrim` funkce oddělit úvodní mezery a `RTrim` funkce oddělit koncové mezery z proměnné řetězce. Použije `Trim` funkce pro odstranění obou typů prostory.  
  
 [!code-vb[VbVbalrStrings#25](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_2.vb)]  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `Mid` funkce vrací zadaný počet znaků z řetězce.  
  
 [!code-vb[VbVbalrStrings#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_3.vb)]  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `Len` k vrátí počet znaků v řetězci.  
  
 [!code-vb[VbVbalrStrings#33](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_4.vb)]  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `InStr` funkce vrací pozici prvního výskytu jednoho řetězce v jiném.  
  
 [!code-vb[VbVbalrStrings#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_5.vb)]  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje použití různých `Format` funkce, která má formát hodnoty pomocí obou `String` formátů a uživatelem definované formátů. Pro oddělovač data (`/`), oddělovač času (`:`) a indikátory dop. / odp (`t` a `tt`), aktuální formátovaný výstup zobrazí systém závisí na nastavení národního prostředí je pomocí kódu. Když časy a data se zobrazují ve vývojovém prostředí, používají formát krátkého času a formát krátkého data kód národního prostředí.  
  
> [!NOTE]
>  Pro národní prostředí, které používají 24hodinovém formátu indikátory dop. / odp (`t` a `tt`) zobrazit prázdnou.  
  
 [!code-vb[VbVbalrStrings#27](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_6.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)  
 [Členové knihovny modulu runtime jazyka Visual Basic](../../../visual-basic/language-reference/runtime-library-members.md)  
 [Souhrn manipulace s řetězci](../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)
