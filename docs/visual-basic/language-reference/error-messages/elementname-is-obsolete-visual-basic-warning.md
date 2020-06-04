---
title: Element '<elementname>' je zastaralý (upozornění jazyka Visual Basic).
ms.date: 07/20/2015
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
ms.openlocfilehash: 7914bc859966e17f3da41c9a13a01573b31baf91
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409670"
---
# <a name="elementname-is-obsolete-visual-basic-warning"></a>Element '\<elementname>' je zastaralý (upozornění jazyka Visual Basic).
Příkaz se pokusí o přístup k programovacímu prvku, který byl označen <xref:System.ObsoleteAttribute> atributem a direktivou, aby byl považován za upozornění.  
  
 Můžete označit libovolný prvek programování, který se už nepoužívá, a to tak, že <xref:System.ObsoleteAttribute> se na něj aplikuje. Pokud to uděláte, můžete vlastnost atributu nastavit <xref:System.ObsoleteAttribute.IsError%2A> na buď `True` nebo `False` . Nastavíte-li na `True` , kompilátor považuje pokus o použití prvku jako chyby. Nastavíte-li na `False` nebo jako výchozí `False` , kompilátor vydá upozornění, pokud dojde k pokusu o použití prvku.  
  
 Ve výchozím nastavení je tato zpráva upozornění, protože <xref:System.ObsoleteAttribute.IsError%2A> vlastnost <xref:System.ObsoleteAttribute> je `False` . Další informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40008  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Zajistěte, aby měl odkaz na zdrojový kód pravopis názvu elementu správně.  
  
## <a name="see-also"></a>Viz také

- [Přehled atributů](../../programming-guide/concepts/attributes/index.md)
