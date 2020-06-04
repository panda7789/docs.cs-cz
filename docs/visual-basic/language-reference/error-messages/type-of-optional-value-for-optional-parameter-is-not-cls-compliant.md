---
title: Typ nepovinné hodnoty pro volitelný parametr <parametername> není kompatibilní se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords:
- BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
ms.openlocfilehash: 8e53d036ead114d828d9035cef76cee72bf6b1db
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400289"
---
# <a name="type-of-optional-value-for-optional-parameter-parametername-is-not-cls-compliant"></a>Typ nepovinné hodnoty pro volitelný parametr \<parametername> není kompatibilní se specifikací CLS.
Procedura je označena jako, `<CLSCompliant(True)>` ale deklaruje [nepovinný](../modifiers/optional.md) parametr s výchozí hodnotou nekompatibilního typu.  
  
 Aby byl postup kompatibilní s [nezávislostí jazyka a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), musí používat pouze typy kompatibilní se specifikací CLS. To platí pro typy parametrů, návratový typ a typy všech místních proměnných. Vztahuje se také na výchozí hodnoty nepovinných parametrů.  
  
 Následující Visual Basic datové typy nejsou kompatibilní se specifikací CLS:  
  
- [SByte – datový typ](../data-types/sbyte-data-type.md)  
  
- [UInteger – datový typ](../data-types/uinteger-data-type.md)  
  
- [ULong – datový typ](../data-types/ulong-data-type.md)  
  
- [UShort – datový typ](../data-types/ushort-data-type.md)  
  
 Použijete-li <xref:System.CLSCompliantAttribute> atribut na programovací prvek, nastavíte `isCompliant` parametr atributu na hodnotu `True` nebo `False` k označení dodržování předpisů nebo nedodržení předpisů. Pro tento parametr neexistuje výchozí hodnota a je třeba uvést hodnotu.  
  
 Pokud neplatíte <xref:System.CLSCompliantAttribute> pro prvek, je považován za nekompatibilní.  
  
 Ve výchozím nastavení je tato zpráva upozornění. Informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40042  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud volitelný parametr musí mít výchozí hodnotu tohoto konkrétního typu, odeberte <xref:System.CLSCompliantAttribute> . Procedura nemůže být kompatibilní se specifikací CLS.  
  
- Pokud procedura musí být kompatibilní se specifikací CLS, změňte typ této výchozí hodnoty na nejbližší typ kompatibilní se specifikací CLS. Například, `UInteger` `Integer` Pokud nepotřebujete rozsah hodnoty nad 2 147 483 647, můžete použít třeba místo. Pokud budete potřebovat Rozšířený rozsah, můžete nahradit `UInteger` `Long` .  
  
- Pokud procházíte s objekty automatizace nebo COM, pamatujte, že některé typy mají odlišnou šířku dat než v .NET Framework. Například `int` obvykle je 16 bitů v jiných prostředích. Pokud přijímáte 16bitové celé číslo z takové komponenty, deklarujte ho `Short` místo `Integer` ve spravovaném kódu Visual Basic.
