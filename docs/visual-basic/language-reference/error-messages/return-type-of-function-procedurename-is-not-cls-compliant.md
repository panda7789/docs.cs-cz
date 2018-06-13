---
title: Návratový typ funkce &#39; &lt;procedurename&gt; &#39; není kompatibilní se specifikací CLS
ms.date: 07/20/2015
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
ms.openlocfilehash: b7704ee63031c38f708a2243e84b880c25fcf819
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595001"
---
# <a name="return-type-of-function-39ltprocedurenamegt39-is-not-cls-compliant"></a>Návratový typ funkce &#39; &lt;procedurename&gt; &#39; není kompatibilní se specifikací CLS
A `Function` postup je označena jako `<CLSCompliant(True)>` , ale vrací typ, který je označen jako `<CLSCompliant(False)>`, není označena nebo nelze vyřešit, protože je typu nesplňujících požadavky.  
  
 Pro proceduru splňovat [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), musí používat pouze typy kompatibilní se specifikací CLS. To platí pro typy parametrů, návratový typ a typy všechny místní proměnné.  
  
 Následující typy dat jazyka Visual Basic nejsou kompatibilní se specifikací CLS:  
  
-   [Datový typ SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Datový typ UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [Datový typ ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [Datový typ UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Pokud použijete <xref:System.CLSCompliantAttribute> programovací element, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` indikující dodržování předpisů nebo nesplňujících požadavky. Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.  
  
 Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, je považován za nedodržuje předpisy.  
  
 Ve výchozím nastavení je tato zpráva upozornění. Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40027  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud `Function` postupu musí vrátit tento konkrétní typ, odeberte <xref:System.CLSCompliantAttribute>. Postup nemůže být kompatibilní se specifikací CLS.  
  
-   Pokud `Function` postupu musí být kompatibilní se specifikací CLS, změnit návratový typ na nejbližší typ kompatibilní se specifikací CLS. Například v místě z `UInteger` je možné použít `Integer` Pokud nepotřebujete rozsah hodnot výše 2 147 483 647. Pokud potřebujete rozšířené rozsahu, můžete nahradit `UInteger` s `Long`.  
  
-   Pokud se propojení s objekty automatizace nebo COM, mějte na paměti, že některé typy mají různé datové šířek než [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Například `int` je často 16 bitů v jiných prostředích. Pokud k takové součásti jsou vrácení 16bitové celé číslo, deklarujte ji jako `Short` místo `Integer` v spravovaného kódu jazyka Visual Basic.