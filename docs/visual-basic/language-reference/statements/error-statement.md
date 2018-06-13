---
title: Error – příkaz
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
ms.openlocfilehash: 3ecfe18392de15dc937d90565b49641415dd7e0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603883"
---
# <a name="error-statement"></a>Error – příkaz
Simuluje došlo k chybě.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a>Součásti  
 `errornumber`  
 Požadováno. Může být jakékoli platné číslo chyby.  
  
## <a name="remarks"></a>Poznámky  
 `Error` Příkaz je podporován z důvodu zpětné kompatibility. V nový kód, zejména při vytváření objektů, použijte `Err` objektu `Raise` metoda ke generování chyb spuštění.  
  
 Pokud `errornumber` je definována `Error` příkaz volá obslužnou rutinu chyby po vlastnosti `Err` objekt jsou přiřazeny následující výchozí hodnoty:  
  
|Vlastnost|Hodnota|  
|--------------|-----------|  
|`Number`|Hodnota zadaná jako argument `Error` příkaz. Může být jakékoli platné číslo chyby.|  
|`Source`|Název aktuálního projektu jazyka Visual Basic.|  
|`Description`|Řetězcový výraz odpovídající vrácenou hodnotu `Error` funkce pro zadaný `Number`, pokud existuje tento řetězec. Pokud řetězec neexistuje, `Description` obsahuje řetězec nulové délky ("").|  
|`HelpFile`|Plně kvalifikovaný jednotky, cesta a název souboru příslušné souboru nápovědy prostředí Visual Basic.|  
|`HelpContext`|Odpovídající Nápověda Visual Basic kontextu ID pro příslušné chyby do souboru `Number` vlastnost.|  
|`LastDLLError`|Nula.|  
  
 Pokud žádná obslužná rutina chyby existuje, nebo pokud je zapnuta žádná chybová zpráva se vytvoří a zobrazí z `Err` vlastnosti objektu.  
  
> [!NOTE]
>  Některé hostování aplikací Visual Basic nelze vytvořit objekty. Naleznete v dokumentaci k hostitelskou aplikaci k určení, zda může vytvořit tříd a objektů.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `Error` příkaz ke generování číslo chyby 11.  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>Požadavky  
 **Namespace:** [Microsoft.VisualBasic –](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Sestavení:** jazyka Visual Basic Runtime Library (v souboru Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>  
 [Příkaz On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [Příkaz Resume](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [Chybové zprávy](../../../visual-basic/language-reference/error-messages/index.md)
