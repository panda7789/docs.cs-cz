---
title: Typ parametru '<parametername>' není kompatibilní se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords:
- BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
ms.openlocfilehash: edbcadf271c4ccafc11e5b64eb103a0290976179
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413011"
---
# <a name="type-of-parameter-parametername-is-not-cls-compliant"></a>Typ parametru '\<parametername>' není kompatibilní se specifikací CLS.
Procedura je označena jako `<CLSCompliant(True)>` , ale deklaruje parametr s typem, který je označen jako `<CLSCompliant(False)>` , není označen nebo nesplňuje, protože se jedná o nekompatibilní typ.  
  
 Aby byl postup kompatibilní s [nezávislostí jazyka a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), musí používat pouze typy kompatibilní se specifikací CLS. To platí pro typy parametrů, návratový typ a typy všech místních proměnných.  
  
 Následující Visual Basic datové typy nejsou kompatibilní se specifikací CLS:  
  
- [SByte – datový typ](../data-types/sbyte-data-type.md)  
  
- [UInteger – datový typ](../data-types/uinteger-data-type.md)  
  
- [ULong – datový typ](../data-types/ulong-data-type.md)  
  
- [UShort – datový typ](../data-types/ushort-data-type.md)  
  
 Použijete-li na <xref:System.CLSCompliantAttribute> programovací prvek, nastavíte `isCompliant` parametr atributu na hodnotu `True` nebo `False` k označení dodržování předpisů nebo nedodržení předpisů. Pro tento parametr neexistuje výchozí hodnota a je třeba uvést hodnotu.  
  
 Pokud na prvek nepoužijete <xref:System.CLSCompliantAttribute> , bude považován za nekompatibilní.  
  
 Ve výchozím nastavení je tato zpráva upozornění. Informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40028  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud procedura musí přijmout parametr tohoto konkrétního typu, odeberte <xref:System.CLSCompliantAttribute> . Procedura nemůže být kompatibilní se specifikací CLS.  
  
- Pokud procedura musí být kompatibilní se specifikací CLS, změňte typ tohoto parametru na nejbližší typ kompatibilní se specifikací CLS. Například, `UInteger` `Integer` Pokud nepotřebujete rozsah hodnoty nad 2 147 483 647, můžete použít třeba místo. Pokud budete potřebovat Rozšířený rozsah, můžete nahradit `UInteger` `Long` .  
  
- Pokud procházíte s objekty automatizace nebo COM, pamatujte, že některé typy mají odlišnou šířku dat než v .NET Framework. Například `int` obvykle je 16 bitů v jiných prostředích. Pokud přijímáte 16bitové celé číslo z takové komponenty, deklarujte ho `Short` místo `Integer` ve spravovaném kódu Visual Basic.
