---
title: Chyba při načítání knihovny DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 36452cc6ff03042939cd4066aef76129b5bb8f0a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329556"
---
# <a name="error-in-loading-dll-visual-basic"></a>Chyba při načítání knihovny DLL (Visual Basic)
Knihovna DLL (Dynamic-Link Library) je knihovna určená v klauzuli `Lib` příkazu `Declare`. Mezi možné příčiny této chyby patří:  
  
- Soubor není spustitelný soubor DLL.  
  
- Soubor není knihovna DLL systému Microsoft Windows.  
  
- Knihovna DLL odkazuje na jinou knihovnu DLL, která není k dispozici.  
  
- Knihovna DLL nebo odkazovaná knihovna DLL nejsou v adresáři zadaném v cestě.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud se jedná o zdrojový textový soubor, a proto ne spustitelný soubor DLL, musí být zkompilován a propojen s formulářem spustitelného souboru DLL.  
  
- Pokud soubor není knihovna DLL systému Microsoft Windows, Získejte ekvivalent systému Microsoft Windows.  
  
- Pokud knihovna DLL odkazuje na jinou knihovnu DLL, která není k dispozici, Získejte odkazovanou knihovnu DLL a zpřístupněte ji.  
  
- Pokud knihovna DLL nebo odkazovaná knihovna DLL není v adresáři určeném cestou, přesuňte knihovnu DLL do odkazovaného adresáře.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
