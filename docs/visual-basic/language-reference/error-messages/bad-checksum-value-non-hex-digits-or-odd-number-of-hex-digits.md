---
title: Nesprávná hodnota kontrolního součtu. Číslice nejsou v šestnáctkové soustavě nebo je zadán lichý počet číslic v šestnáctkové soustavě.
ms.date: 07/20/2015
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
ms.openlocfilehash: 1ae4113505ca63df9b20e6e71aa0b418da4ef924
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197345"
---
# <a name="bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a>Nesprávná hodnota kontrolního součtu. Číslice nejsou v šestnáctkové soustavě nebo je zadán lichý počet číslic v šestnáctkové soustavě.
Hodnota kontrolního součtu obsahuje neplatné hexadecimální číslice nebo má lichý počet číslic.  
  
 Když ASP.NET vygeneruje zdrojový soubor Visual Basic (přípona. vb), vypočítá kontrolní součet a umístí ho do skrytého zdrojového souboru identifikovaného `#externalchecksum`. Je možné, že uživatel vygeneruje soubor. vb k tomu, ale tento postup je nejvhodnější pro interní použití.  
  
 Ve výchozím nastavení je tato zpráva upozornění. Informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42033  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Pokud ASP.NET generuje zdrojový soubor Visual Basic, restartujte sestavení projektu.  
  
2. Pokud toto upozornění přetrvává po restartování, přeinstalujte ASP.NET a zkuste sestavení znovu.  
  
3. Pokud upozornění stále přetrvává nebo pokud nepoužíváte ASP.NET, shromážděte informace o okolnostech a upozorněte služby Microsoft Product Support Services.  
  
## <a name="see-also"></a>Viz také:

- [ASP.NET – přehled](/aspnet/overview)
- [Kontaktujte nás](/visualstudio/ide/feedback-options)
