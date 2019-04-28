---
title: Název třídy '<classname> není kompatibilní se specifikací CLS, protože rozhraní '<interfacename>', které implementuje, není kompatibilní se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
ms.openlocfilehash: 063c42249abbfb506fd15311659599b4777d397f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649878"
---
# <a name="classname-is-not-cls-compliant-because-the-interface-interfacename-it-implements-is-not-cls-compliant"></a>"\<classname >' není kompatibilní se Specifikací CLS, protože rozhraní"\<interfacename > "ji implementuje, není kompatibilní se Specifikací CLS
Třídy nebo rozhraní je označen jako `<CLSCompliant(True)>` , pokud je odvozena od nebo implementuje typ, který je označen jako `<CLSCompliant(False)>` nebo není označen.  
  
 Pro třídu nebo rozhraní, které má být zajištěn soulad [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), její hierarchie dědění celý musí splňovat předpisy. To znamená, že každý typ, ze kterého se dědí, přímo nebo nepřímo, musí být kompatibilní. Podobně pokud třída implementuje jednu nebo více rozhraní, se musí být všechny předpisy v rámci své hierarchie dědičnosti.  
  
 Pokud použijete <xref:System.CLSCompliantAttribute> na programovací prvek, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` k označení dodržování předpisů nebo při nedodržení předpisů. Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.  
  
 Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, se považuje za jako nevyhovující.  
  
 Ve výchozím nastavení tato zpráva je upozornění. Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40029  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud budete vyžadovat dodržování specifikace CLS, definujte schéma hierarchie nebo k provádění různých dědičnosti tohoto typu.  
  
- Pokud budete vyžadovat, že tento typ větší než doporučovaných její aktuální schéma hierarchie nebo implementace dědičnosti, odeberte <xref:System.CLSCompliantAttribute> z jeho definice nebo označte ji jako `<CLSCompliant(False)>`.  
