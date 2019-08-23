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
ms.openlocfilehash: 7b926214d3be7f5f57783a8599acf1bb1042f956
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944447"
---
# <a name="error-statement"></a>Error – příkaz
Simuluje výskyt chyby.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a>Součásti  
 `errornumber`  
 Povinný parametr. Může to být jakékoli platné číslo chyby.  
  
## <a name="remarks"></a>Poznámky  
 `Error` Příkaz se podporuje kvůli zpětné kompatibilitě. V novém kódu, zejména při vytváření objektů, použijte `Err` `Raise` metodu objektu pro generování běhových chyb.  
  
 Pokud `errornumber` je definován `Error` , příkaz zavolá obslužnou rutinu chyby `Err` poté, co jsou vlastnosti objektu přiřazeny následující výchozí hodnoty:  
  
|Vlastnost|Value|  
|--------------|-----------|  
|`Number`|Hodnota zadaná jako argument `Error` into příkazu Může to být jakékoli platné číslo chyby.|  
|`Source`|Název aktuálního projektu Visual Basic.|  
|`Description`|Řetězcový výraz odpovídající vrácené hodnotě `Error` funkce pro zadanou `Number`hodnotu, pokud tento řetězec existuje. Pokud řetězec neexistuje, `Description` obsahuje řetězec s nulovou délkou ("").|  
|`HelpFile`|Plně kvalifikovaná jednotka, cesta a název souboru pro příslušný soubor s Visual Basic Help.|  
|`HelpContext`|Příslušné ID kontextového souboru Help Visual Basic pro chybu odpovídající `Number` vlastnosti.|  
|`LastDLLError`|Vynulujte.|  
  
 Pokud neexistují žádné obslužné rutiny chyb nebo pokud není žádná povolená, vytvoří se chybová zpráva, která `Err` se zobrazí z vlastností objektu.  
  
> [!NOTE]
> Některé hostitelské aplikace Visual Basic nemůžou vytvářet objekty. Informace o tom, zda může vytvořit třídy a objekty, naleznete v dokumentaci hostitelské aplikace.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se `Error` pomocí příkazu vygeneruje chybová zpráva číslo 11.  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>Požadavky  
 **Hosting** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Shromážděním** Visual Basic Runtime Library (v souboru Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [Příkaz On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [Příkaz Resume](../../../visual-basic/language-reference/statements/resume-statement.md)
- [Chybové zprávy](../../../visual-basic/language-reference/error-messages/index.md)
