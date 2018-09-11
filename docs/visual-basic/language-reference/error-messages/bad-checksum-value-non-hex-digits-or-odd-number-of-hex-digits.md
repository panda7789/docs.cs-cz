---
title: Nesprávná hodnota kontrolního součtu. Číslice nejsou v šestnáctkové soustavě nebo je zadán lichý počet číslic v šestnáctkové soustavě.
ms.date: 07/20/2015
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
ms.openlocfilehash: e682c2c23dd6fe80aee87d2a86b3df2dae66b802
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44276458"
---
# <a name="bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a>Nesprávná hodnota kontrolního součtu. Číslice nejsou v šestnáctkové soustavě nebo je zadán lichý počet číslic v šestnáctkové soustavě.
Hodnota kontrolního součtu obsahuje neplatné hexadecimální číslice nebo má lichý počet číslic.  
  
 Když ASP.NET generuje zdrojový soubor jazyka Visual Basic (.vb rozšíření), vypočítá kontrolní součet a umístí jej do skryté zdrojový soubor identifikovaný `#externalchecksum`. Je možné pro uživatele, generuje se soubor .vb k tomu taky, ale tento proces je nejlepší doleva na interní použití.  
  
 Ve výchozím nastavení tato zpráva je upozornění. Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42033  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Pokud technologie ASP.NET generuje zdrojový soubor jazyka Visual Basic, restartujte sestavení projektu.  
  
2.  Pokud toto upozornění zobrazuje i po restartování, přeinstalujte technologie ASP.NET a zkuste sestavení znovu.  
  
3.  Pokud se nepovede upozornění, nebo pokud nejsou pomocí technologie ASP.NET, shromážděte informace o okolnostech a upozorňovat Microsoft Product Support Services.  
  
## <a name="see-also"></a>Viz také:

- [ASP.NET: Přehled](/aspnet/overview)  
- [Kontaktujte nás](/visualstudio/ide/talk-to-us)
