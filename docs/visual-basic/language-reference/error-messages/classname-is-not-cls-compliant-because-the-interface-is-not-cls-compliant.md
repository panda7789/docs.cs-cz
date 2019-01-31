---
title: Název třídy '<classname> není kompatibilní se specifikací CLS, protože rozhraní '<interfacename>', které implementuje, není kompatibilní se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
ms.openlocfilehash: 6743a0decebb9711a4e44d09b03fe32f88ff2f72
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283475"
---
# <a name="classname-is-not-cls-compliant-because-the-interface-interfacename-it-implements-is-not-cls-compliant"></a>"\<classname >' není kompatibilní se Specifikací CLS, protože rozhraní"\<interfacename > "ji implementuje, není kompatibilní se Specifikací CLS
Třídy nebo rozhraní je označen jako `<CLSCompliant(True)>` , pokud je odvozena od nebo implementuje typ, který je označen jako `<CLSCompliant(False)>` nebo není označen.  
  
 Pro třídu nebo rozhraní, které má být zajištěn soulad [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), její hierarchie dědění celý musí splňovat předpisy. To znamená, že každý typ, ze kterého se dědí, přímo nebo nepřímo, musí být kompatibilní. Podobně pokud třída implementuje jednu nebo více rozhraní, se musí být všechny předpisy v rámci své hierarchie dědičnosti.  
  
 Pokud použijete <xref:System.CLSCompliantAttribute> na programovací prvek, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` k označení dodržování předpisů nebo při nedodržení předpisů. Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.  
  
 Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, se považuje za jako nevyhovující.  
  
 Ve výchozím nastavení tato zpráva je upozornění. Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40029  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud budete vyžadovat dodržování specifikace CLS, definujte schéma hierarchie nebo k provádění různých dědičnosti tohoto typu.  
  
-   Pokud budete vyžadovat, že tento typ větší než doporučovaných její aktuální schéma hierarchie nebo implementace dědičnosti, odeberte <xref:System.CLSCompliantAttribute> z jeho definice nebo označte ji jako `<CLSCompliant(False)>`.  
  
 
