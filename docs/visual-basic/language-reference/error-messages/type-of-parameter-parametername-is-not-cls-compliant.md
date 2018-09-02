---
title: Typ parametru &#39; &lt;parametername&gt; &#39; není kompatibilní se Specifikací CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords:
- BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
ms.openlocfilehash: 13a4e35cd27ed5aa135cec77c4415f223cba70f2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43403033"
---
# <a name="type-of-parameter-39ltparameternamegt39-is-not-cls-compliant"></a>Typ parametru &#39; &lt;parametername&gt; &#39; není kompatibilní se Specifikací CLS
Postup je označen jako `<CLSCompliant(True)>` ale deklaruje parametr s typem, který je označen jako `<CLSCompliant(False)>`, není označena nebo nesplňuje, protože se jedná o nekompatibilní typ.  
  
 Postup, který má být zajištěn soulad [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), musí používat jenom typy kompatibilní se Specifikací CLS. To platí pro typy parametrů, návratový typ a typy všech místních proměnných.  
  
 Následující datové typy jazyka Visual Basic nejsou kompatibilní se Specifikací CLS:  
  
-   [Datový typ SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Datový typ UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [Datový typ ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [Datový typ UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Pokud použijete <xref:System.CLSCompliantAttribute> na programovací prvek, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` k označení dodržování předpisů nebo při nedodržení předpisů. Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.  
  
 Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, se považuje za jako nevyhovující.  
  
 Ve výchozím nastavení tato zpráva je upozornění. Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40028  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud proces musí přijmout parametr tohoto konkrétního typu, odeberte <xref:System.CLSCompliantAttribute>. Procedura nemůže být kompatibilní se Specifikací CLS.  
  
-   Pokud procedura musí být kompatibilní se Specifikací CLS, změňte typ tohoto parametru na nejbližší typ. kompatibilní se Specifikací CLS. Například místo hodnoty `UInteger` je možné použít `Integer` Pokud nepotřebujete rozsah hodnot nad 2 147 483 647. Pokud budete potřebovat delší rozsah, můžete nahradit `UInteger` s `Long`.  
  
-   Při vzájemném propojování s objekty automatizace nebo COM, mějte na paměti, že některé typy mají různou šířkou dat než [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Například `int` je často 16 bitů v jiných prostředích. Pokud přijímáte 16bitové celé číslo z takové součásti, deklarujte ho jako `Short` místo `Integer` v spravovaného kódu jazyka Visual Basic.