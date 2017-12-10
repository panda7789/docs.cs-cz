---
title: "Typ volitelné hodnoty pro volitelný parametr &lt;parametername&gt; není kompatibilní se specifikací CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords: BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 72ec027c397be2a57be5c22b55f6dcce9a5c5f5a
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="type-of-optional-value-for-optional-parameter-ltparameternamegt-is-not-cls-compliant"></a>Typ volitelné hodnoty pro volitelný parametr &lt;parametername&gt; není kompatibilní se specifikací CLS
Postup je označena jako `<CLSCompliant(True)>` deklaruje, ale [volitelné](../../../visual-basic/language-reference/modifiers/optional.md) parametr s hodnotou výchozí nekompatibilních typu.  
  
 Pro proceduru splňovat [jazyková nezávislost a jazykově nezávislé komponenty](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), musí používat pouze typy kompatibilní se specifikací CLS. To platí pro typy parametrů, návratový typ a typy všechny místní proměnné. Platí také pro výchozí hodnoty volitelné parametry.  
  
 Následující [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] datové typy nejsou kompatibilní se specifikací CLS:  
  
-   [SByte – datový typ](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Uinteger – datový typ](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [Ulong – datový typ](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [Ushort – datový typ](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Pokud použijete <xref:System.CLSCompliantAttribute> atribut programovací element, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` indikující dodržování předpisů nebo nesplňujících požadavky. Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.  
  
 Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, je považován za nedodržuje předpisy.  
  
 Ve výchozím nastavení je tato zpráva upozornění. Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40042  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud volitelný parametr musí mít výchozí hodnotu tohoto konkrétního typu, odeberte <xref:System.CLSCompliantAttribute>. Postup nemůže být kompatibilní se specifikací CLS.  
  
-   Pokud postup musí být kompatibilní se specifikací CLS, změňte typ této výchozí hodnoty na typ nejbližší kompatibilní se specifikací CLS. Například v místě z `UInteger` je možné použít `Integer` Pokud nepotřebujete rozsah hodnot výše 2 147 483 647. Pokud potřebujete rozšířené rozsahu, můžete nahradit `UInteger` s `Long`.  
  
-   Pokud se propojení s objekty automatizace nebo COM, mějte na paměti, že některé typy mají různé datové šířek než [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Například `int` je často 16 bitů v jiných prostředích. Pokud je přijímáte 16bitové celé číslo z těchto součástí, deklarujte ji jako `Short` místo `Integer` ve vaší spravované [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kódu.  
  
## <a name="see-also"></a>Viz také  
 [\<PAVE přes > zápis kompatibilní se specifikací CLS kódu](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
