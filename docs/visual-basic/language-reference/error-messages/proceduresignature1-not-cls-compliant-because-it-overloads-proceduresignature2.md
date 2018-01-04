---
title: "&lt;proceduresignature1&gt; není kompatibilní se specifikací CLS, protože ho přetížení &lt;proceduresignature2&gt; který se liší od jeho pouze pole typů parametr pole nebo pořadí typy pole parametrů"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords: BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d361759471a8edfa97437bd2503cfaa661fb9678
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ltproceduresignature1gt-is-not-cls-compliant-because-it-overloads-ltproceduresignature2gt-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>&lt;proceduresignature1&gt; není kompatibilní se specifikací CLS, protože ho přetížení &lt;proceduresignature2&gt; který se liší od jeho pouze pole typů parametr pole nebo pořadí typy pole parametrů
Procedura nebo vlastnosti je označena jako `<CLSCompliant(True)>` při přepíše jiný postup nebo vlastnost a je jediným rozdílem mezi seznamy jejich parametrů úroveň vnoření Vícenásobná pole nebo pole pořadí.  
  
 V následující deklarace druhý a třetí deklarace generovat tuto chybu.  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 Druhý deklaraci změní parametr původní jednorozměrné `arrayParam` do pole polí. Třetí změny deklarace `arrayParam` dvourozměrné pole (pořadí 2). Přestože jazyka Visual Basic umožňuje přetížení pro liší pouze jednu z těchto změn, takové přetížení není kompatibilní s [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS).  
  
 Pokud použijete <xref:System.CLSCompliantAttribute> programovací element, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` indikující dodržování předpisů nebo nesplňujících požadavky. Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.  
  
 Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, je považován za nedodržuje předpisy.  
  
 Ve výchozím nastavení je tato zpráva upozornění. Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40035  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud budete potřebovat souladu se specifikací CLS, definujte vaše přetížení pro více způsoby než pouze změny, které jsou uvedené na této stránce nápovědy se liší od sebe navzájem.  
  
-   Pokud požadujete, aby přetížení liší pouze změnami citovalo na této nápovědy stránky, odeberte <xref:System.CLSCompliantAttribute> z jejich definice nebo označit je jako `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Viz také  
   
 [Přetížení procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)
