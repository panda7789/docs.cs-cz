---
title: Chyba při načítání knihovny DLL (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: ac21c4d52b248025ee26bac3e511bb5b0a0b668e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="error-in-loading-dll-visual-basic"></a>Chyba při načítání knihovny DLL (Visual Basic)
Dynamická knihovna (DLL) je zadána v knihovna `Lib` klauzuli `Declare` příkaz. Možné příčiny této chyby patří:  
  
-   Soubor není spustitelný soubor knihovny DLL.  
  
-   Soubor není knihovny DLL Microsoft Windows.  
  
-   Knihovny DLL odkazuje na jiné knihovny DLL, která není k dispozici.  
  
-   Knihovny DLL nebo odkazované DLL není v adresáři zadaném v cestě.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud je soubor zdroj textového souboru a proto není spustitelný soubor knihovny DLL, musí být zkompilovány a propojené s formuláři DLL-spustitelný soubor.  
  
-   Pokud není soubor knihovny DLL Microsoft Windows, získejte ekvivalentní Microsoft Windows.  
  
-   Pokud knihovnu DLL odkazuje na jiné knihovny DLL, která není k dispozici, získat odkazované DLL a zpřístupnit jej.  
  
-   Pokud knihovnu DLL nebo odkazované DLL není v zadané cestě adresáře, přesuňte knihovnu DLL odkazované adresáře.  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
