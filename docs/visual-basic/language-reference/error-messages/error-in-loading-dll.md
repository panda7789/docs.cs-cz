---
title: Chyba při načítání knihovny DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: fd2e425f2dd3f4127cd777d4a1f7ab9809de9d45
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409621"
---
# <a name="error-in-loading-dll-visual-basic"></a>Chyba při načítání knihovny DLL (Visual Basic)
Knihovna DLL (Dynamic-Link Library) je knihovna zadaná v `Lib` klauzuli `Declare` příkazu. Mezi možné příčiny této chyby patří:  
  
- Soubor není spustitelný soubor DLL.  
  
- Soubor není knihovna DLL systému Microsoft Windows.  
  
- Knihovna DLL odkazuje na jinou knihovnu DLL, která není k dispozici.  
  
- Knihovna DLL nebo odkazovaná knihovna DLL nejsou v adresáři zadaném v cestě.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud se jedná o zdrojový textový soubor, a proto ne spustitelný soubor DLL, musí být zkompilován a propojen s formulářem spustitelného souboru DLL.  
  
- Pokud soubor není knihovna DLL systému Microsoft Windows, Získejte ekvivalent systému Microsoft Windows.  
  
- Pokud knihovna DLL odkazuje na jinou knihovnu DLL, která není k dispozici, Získejte odkazovanou knihovnu DLL a zpřístupněte ji.  
  
- Pokud knihovna DLL nebo odkazovaná knihovna DLL není v adresáři určeném cestou, přesuňte knihovnu DLL do odkazovaného adresáře.  
  
## <a name="see-also"></a>Viz také

- [Declare – příkaz](../statements/declare-statement.md)
