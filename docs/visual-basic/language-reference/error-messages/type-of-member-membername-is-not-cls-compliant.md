---
title: Typ člena '<membername>' není kompatibilní se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
ms.openlocfilehash: 030cb31b8f1ba0e8eaa82eeb8e37153411a53404
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400302"
---
# <a name="type-of-member-membername-is-not-cls-compliant"></a>Typ člena '\<membername>' není kompatibilní se specifikací CLS.
Datový typ zadaný pro tento člen není součástí nezávislého [jazyka a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS). Nejedná se o chybu v rámci vaší komponenty, protože .NET Framework a Visual Basic podporují tento datový typ. Nicméně jiná komponenta napsaná v striktně kódu kompatibilním se specifikací CLS nemusí tento datový typ podporovat. Taková součást nemusí být schopná úspěšně pracovat s vaší komponentou.  
  
 Následující Visual Basic datové typy nejsou kompatibilní se specifikací CLS:  
  
- [SByte – datový typ](../data-types/sbyte-data-type.md)  
  
- [UInteger – datový typ](../data-types/uinteger-data-type.md)  
  
- [ULong – datový typ](../data-types/ulong-data-type.md)  
  
- [UShort – datový typ](../data-types/ushort-data-type.md)  
  
 Ve výchozím nastavení je tato zpráva upozornění. Další informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40025  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud vaše rozhraní komponenty pouze k jiným .NET Framework komponentám nebo není rozhraním žádné jiné součásti, nemusíte nic měnit.  
  
- Pokud procházíte s komponentou, která není zapsána pro .NET Framework, může být možné určit, buď pomocí reflexe, nebo z dokumentace, zda podporuje tento datový typ. V takovém případě není nutné měnit žádné změny.  
  
- Pokud procházejíte s komponentou, která nepodporuje tento datový typ, je nutné ji nahradit nejbližším typem odpovídajícím specifikaci CLS. Například, `UInteger` `Integer` Pokud nepotřebujete rozsah hodnoty nad 2 147 483 647, můžete použít třeba místo. Pokud budete potřebovat Rozšířený rozsah, můžete nahradit `UInteger` `Long` .  
  
- Pokud procházíte s objekty automatizace nebo COM, pamatujte, že některé typy mají odlišnou šířku dat než v .NET Framework. Například `uint` obvykle je 16 bitů v jiných prostředích. Pokud předáváte pro takovou součást 16bitový argument, deklarujte ji jako `UShort` místo `UInteger` ve spravovaném kódu Visual Basic.  
  
## <a name="see-also"></a>Viz také

- [Reflexe](../../../framework/reflection-and-codedom/reflection.md)
