---
title: <proceduresignature1> není kompatibilní se specifikací CLS, protože přetěžuje <proceduresignature2>, které se liší pouze polem typů parametrů pole nebo řazením typů parametrů pole.
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 6143ebfbe7f131b0e196e531ed4282c8333be4ea
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250171"
---
# <a name="proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>\<proceduresignature1 > není kompatibilní se specifikací CLS, protože přetěžuje > \<proceduresignature2, které se liší pouze polem typů parametrů pole nebo řazením typů parametrů pole.

Procedura nebo vlastnost je označena jako `<CLSCompliant(True)>`, Pokud Přepisuje jinou proceduru nebo vlastnost a jediným rozdílem mezi jejich seznamy parametrů je vnořená úroveň vícenásobného pole nebo rozměru pole.
  
 V následujících deklaracích generuje druhá a třetí deklarace tuto chybu:
  
 `Overloads Sub ProcessArray(arrayParam() As Integer)`  
  
 `Overloads Sub ProcessArray(arrayParam()() As Integer)`  
  
 `Overloads Sub ProcessArray(arrayParam(,) As Integer)`  
  
 Druhá deklarace změní původní jednorozměrné parametr `arrayParam` na pole polí. Třetí deklarace mění `arrayParam` do dvojrozměrného pole (Rank 2). I když Visual Basic umožňuje, aby se přetížení lišila pouze jednou z těchto změn, takové přetížení není kompatibilní s [nezávislostí jazyka a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS).  
  
 Použijete-li <xref:System.CLSCompliantAttribute> na programovací prvek, nastavíte parametr `isCompliant` atributu na hodnotu `True` nebo `False` k označení dodržování předpisů nebo nedodržení předpisů. Pro tento parametr neexistuje výchozí hodnota a je třeba uvést hodnotu.  
  
 Pokud nepoužijete <xref:System.CLSCompliantAttribute> na prvek, považuje se za nevyhovující.  
  
 Ve výchozím nastavení je tato zpráva upozornění. Informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40035  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud požadujete kompatibilitu se specifikací CLS, definujte přetížení tak, aby se vzájemně lišily více způsoby, než jenom změny citované na této stránce s touto stránkou help.
- Pokud vyžadujete, aby se přetížení lišila pouze změnami citovanými na této stránce Nápověda, odeberte <xref:System.CLSCompliantAttribute> ze svých definic nebo je označte jako `<CLSCompliant(False)>`.
  
## <a name="see-also"></a>Související témata

- [Přetížení procedury](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [Přetížení](../modifiers/overloads.md)
