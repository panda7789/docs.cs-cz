---
title: Typ člena '<membername>' není kompatibilní se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
ms.openlocfilehash: f6f66617774dccff4450cce42904126acf5c3769
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590684"
---
# <a name="type-of-member-membername-is-not-cls-compliant"></a>Typ člena '\<membername >' není kompatibilní se Specifikací CLS
Datový typ zadaný pro tento člen není součástí [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS). Nejedná se k chybě v komponentě, protože tento typ dat nepodporuje rozhraní .NET Framework a jazyka Visual Basic. Jiné součásti, které jsou napsané v striktně kompatibilní se Specifikací CLS kódu však nemusí podporovat tento typ dat. Takové součásti nemusí být úspěšně komunikovat s vaší komponentě.  
  
 Následující datové typy jazyka Visual Basic nejsou kompatibilní se Specifikací CLS:  
  
- [Datový typ SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [Datový typ UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [Datový typ ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [Datový typ UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Ve výchozím nastavení tato zpráva je upozornění. Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40025  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud vaše komponenta rozhraní pouze s jinými součástmi rozhraní .NET Framework, nebo není rozhraní s ostatními součástmi, není potřeba nic měnit.  
  
- Při vzájemném propojování součástí, které nejsou napsané pro rozhraní .NET Framework, je možné prostřednictvím reflexe nebo dokumentaci ke službě, určit, jestli je tento typ dat podporuje. Pokud ano, není potřeba nic měnit.  
  
- Při vzájemném propojování součástí, která nepodporuje tento typ dat, musíte jej nahradit s typem nejbližší kompatibilní se Specifikací CLS. Například místo hodnoty `UInteger` je možné použít `Integer` Pokud nepotřebujete rozsah hodnot nad 2 147 483 647. Pokud budete potřebovat delší rozsah, můžete nahradit `UInteger` s `Long`.  
  
- Při vzájemném propojování s objekty automatizace nebo COM, mějte na paměti, že některé typy mají různou šířkou dat než v rozhraní .NET Framework. Například `uint` je často 16 bitů v jiných prostředích. Pokud takové součásti předáváte 16bitový argument, deklarujte ho jako `UShort` místo `UInteger` v spravovaného kódu jazyka Visual Basic.  
  
## <a name="see-also"></a>Viz také:

- [Reflexe](../../../framework/reflection-and-codedom/reflection.md)
