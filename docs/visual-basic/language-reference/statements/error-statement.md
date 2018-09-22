---
title: Error – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
ms.openlocfilehash: 84fce92183228cbfa5554a3ba45770a86e83bff5
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46579781"
---
# <a name="error-statement"></a>Error – příkaz
Simuluje výskyt chyby.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a>Součásti  
 `errornumber`  
 Požadováno. Může být libovolné platné číslo chyby.  
  
## <a name="remarks"></a>Poznámky  
 `Error` Příkaz je podporován z důvodu zpětné kompatibility. V novém kódu, zejména při vytváření objektů, použijte `Err` objektu `Raise` metoda vygeneruje chyby za běhu.  
  
 Pokud `errornumber` je definován `Error` příkaz volá obslužná rutina chyb po vlastnosti `Err` objektu jsou přiřazeny následující výchozí hodnoty:  
  
|Vlastnost|Hodnota|  
|--------------|-----------|  
|`Number`|Hodnota zadaná jako argument `Error` příkaz. Může být libovolné platné číslo chyby.|  
|`Source`|Název aktuálního projektu jazyka Visual Basic.|  
|`Description`|Výraz odpovídající návratovou hodnotu z řetězce `Error` funkce pro zadaný rozbočovač `Number`, pokud existuje tento řetězec. Pokud řetězec neexistuje, `Description` obsahuje řetězec nulové délky ("").|  
|`HelpFile`|Plně kvalifikovaný jednotky, cestu a název souboru odpovídající souboru nápovědy jazyka Visual Basic.|  
|`HelpContext`|Odpovídající Nápověda jazyka Visual Basic ID kontextu pro příslušné chyby do souboru `Number` vlastnost.|  
|`LastDLLError`|Nula.|  
  
 Pokud neexistuje žádná obslužná rutina chyby, nebo pokud je zapnuta žádná chybová zpráva se vytvoří a zobrazí z `Err` vlastností objektu.  
  
> [!NOTE]
>  Některé hostování aplikací Visual Basic nelze vytvořit objekty. V dokumentaci k hostitelské aplikace k určení, zda je možné vytvořit tříd a objektů.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `Error` příkaz k vygenerování číslo chyby 11.  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>Požadavky  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Sestavení:** knihovny prostředí Runtime jazyka Visual Basic (v souboru Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>  
 [Příkaz On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [Příkaz Resume](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [Chybové zprávy](../../../visual-basic/language-reference/error-messages/index.md)
