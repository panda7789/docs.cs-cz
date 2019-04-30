---
title: <proceduresignature1> není kompatibilní se Specifikací CLS, protože přetěžuje <proceduresignature2> které se od ní liší jenom polem typů parametrů nebo rozměrem typů parametru pole
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 0bda4ad6a4d5368d93e2ca603b78bf9db6aca858
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920910"
---
# <a name="proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>\<proceduresignature1 > není kompatibilní se Specifikací CLS, protože přetěžuje \<proceduresignature2 > které se od ní liší jenom polem typů parametrů nebo rozměrem typů parametru pole
Procedura nebo vlastnost je označena jako `<CLSCompliant(True)>` když přepíše jiný postup nebo vlastnost a jediným rozdílem mezi seznamy parametrů je úroveň vnoření vícenásobného pole nebo počet rozměrů pole.  
  
 V následující deklarace generovat deklarace druhý a třetí k této chybě.  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 Druhý deklarace změní původní jednorozměrné parametr `arrayParam` do pole polí. Třetí deklarace změny `arrayParam` dvourozměrné pole (řazení 2). Přestože Visual Basic umožňuje přetížení se liší pouze jednou z těchto změn, tato přetížení není kompatibilní s [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS).  
  
 Pokud použijete <xref:System.CLSCompliantAttribute> na programovací prvek, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` k označení dodržování předpisů nebo při nedodržení předpisů. Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.  
  
 Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, se považuje za jako nevyhovující.  
  
 Ve výchozím nastavení tato zpráva je upozornění. Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40035  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud budete vyžadovat dodržování specifikace CLS, definujte vaši přetížení se liší od sebe navzájem více způsoby než pouze změny, které jsou uvedené na této stránce nápovědy.  
  
- Pokud budete vyžadovat, aby přetížení se liší pouze provedené změny uvedené v této nápovědě stránce, odeberte <xref:System.CLSCompliantAttribute> z jejich definice nebo označit je jako `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Viz také:

- [Přetížení procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)
