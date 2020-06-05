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
ms.openlocfilehash: 35ba1f19654d1d23ac1ec73564bc36b0af4f6777
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404742"
---
# <a name="error-statement"></a>Error – příkaz
Simuluje výskyt chyby.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a>Součásti  
 `errornumber`  
 Povinná hodnota. Může to být jakékoli platné číslo chyby.  
  
## <a name="remarks"></a>Poznámky  
 `Error`Příkaz se podporuje kvůli zpětné kompatibilitě. V novém kódu, zejména při vytváření objektů, použijte `Err` `Raise` metodu objektu pro generování běhových chyb.  
  
 Pokud `errornumber` je definován, `Error` příkaz zavolá obslužnou rutinu chyby poté, co `Err` jsou vlastnosti objektu přiřazeny následující výchozí hodnoty:  
  
|Vlastnost|Hodnota|  
|--------------|-----------|  
|`Number`|Hodnota zadaná jako argument `Error` into příkazu Může to být jakékoli platné číslo chyby.|  
|`Source`|Název aktuálního projektu Visual Basic.|  
|`Description`|Řetězcový výraz odpovídající vrácené hodnotě `Error` funkce pro zadanou hodnotu `Number` , pokud tento řetězec existuje. Pokud řetězec neexistuje, `Description` obsahuje řetězec s nulovou délkou ("").|  
|`HelpFile`|Plně kvalifikovaná jednotka, cesta a název souboru pro příslušný soubor s Visual Basic Help.|  
|`HelpContext`|Příslušné ID kontextového souboru Help Visual Basic pro chybu odpovídající `Number` Vlastnosti.|  
|`LastDLLError`|0|  
  
 Pokud neexistují žádné obslužné rutiny chyb nebo pokud není žádná povolená, vytvoří se chybová zpráva, která se zobrazí z `Err` vlastností objektu.  
  
> [!NOTE]
> Některé hostitelské aplikace Visual Basic nemůžou vytvářet objekty. Informace o tom, zda může vytvořit třídy a objekty, naleznete v dokumentaci hostitelské aplikace.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se pomocí `Error` příkazu vygeneruje chybová zpráva číslo 11.  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>Požadavky  
 **Obor názvů:** [Microsoft. VisualBasic](../runtime-library-members.md)  
  
 **Sestavení:** Knihovna Visual Basic runtime (v souboru Microsoft. VisualBasic. dll)  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [On Error – příkaz](on-error-statement.md)
- [Resume – příkaz](resume-statement.md)
- [Chybové zprávy](../error-messages/index.md)
