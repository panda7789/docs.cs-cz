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
ms.openlocfilehash: c7b2adfe7f6b6ff5e89598cb318a90c51595ff6f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583383"
---
# <a name="error-statement"></a>Error – příkaz
Simuluje výskyt chyby.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a>Součásti  
 `errornumber`  
 Požadováno. Může to být jakékoli platné číslo chyby.  
  
## <a name="remarks"></a>Poznámky  
 Příkaz `Error` je podporován z důvodu zpětné kompatibility. V novém kódu, zejména při vytváření objektů, použijte metodu `Raise` `Err`ho objektu k vygenerování běhových chyb.  
  
 Je-li definována `errornumber`, příkaz `Error` volá obslužnou rutinu chyby poté, co jsou vlastnosti objektu `Err` přiřazeny následující výchozí hodnoty:  
  
|Vlastnost|Hodnota|  
|--------------|-----------|  
|`Number`|Hodnota zadaná jako argument pro příkaz `Error`. Může to být jakékoli platné číslo chyby.|  
|`Source`|Název aktuálního projektu Visual Basic.|  
|`Description`|Řetězcový výraz odpovídající hodnotě vrácené funkce `Error` pro zadaný `Number`, pokud tento řetězec existuje. Pokud řetězec neexistuje, `Description` obsahuje řetězec s nulovou délkou ("").|  
|`HelpFile`|Plně kvalifikovaná jednotka, cesta a název souboru pro příslušný soubor s Visual Basic Help.|  
|`HelpContext`|Příslušné ID kontextového souboru Help Visual Basic pro chybu odpovídající vlastnosti `Number`.|  
|`LastDLLError`|Vynulujte.|  
  
 Pokud neexistují žádné obslužné rutiny chyb nebo pokud není žádná povolená, vytvoří se chybová zpráva, která se zobrazí z vlastností objektu `Err`.  
  
> [!NOTE]
> Některé hostitelské aplikace Visual Basic nemůžou vytvářet objekty. Informace o tom, zda může vytvořit třídy a objekty, naleznete v dokumentaci hostitelské aplikace.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se k vygenerování čísla chyby 11 používá příkaz `Error`.  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>Požadavky  
 **Obor názvů:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Sestavení:** Knihovna Visual Basic runtime (v souboru Microsoft. VisualBasic. dll)  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [Příkaz On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [Příkaz Resume](../../../visual-basic/language-reference/statements/resume-statement.md)
- [Chybové zprávy](../../../visual-basic/language-reference/error-messages/index.md)
