---
title: "Chyba při načítání knihovny DLL (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cc557dcc6709178b6519adb56f31debcbd1d1c39
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
 [Declare – příkaz](../../../visual-basic/language-reference/statements/declare-statement.md)
