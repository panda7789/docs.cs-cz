---
title: Základní typ &lt;typename&gt; výčtu není kompatibilní se specifikací CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
ms.openlocfilehash: 876a59d1441c1ba4c5057556d5ef2fb2ecb43af6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596616"
---
# <a name="underlying-type-lttypenamegt-of-enum-is-not-cls-compliant"></a>Základní typ &lt;typename&gt; výčtu není kompatibilní se specifikací CLS
Datový typ zadaný pro tento výčet není součástí [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS). Toto není chybu v rámci komponenty, protože [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] a tento typ dat jazyka Visual Basic podporován. Jiné komponenty, které jsou zapsané ve výhradně kompatibilní se specifikací CLS kódu však nemusí podporovat tento datový typ. Tyto součásti nemusí být možné úspěšně komunikovat s příslušné součásti.  
  
 Následující typy dat jazyka Visual Basic nejsou kompatibilní se specifikací CLS:  
  
-   [Datový typ SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Datový typ UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [Datový typ ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [Datový typ UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Ve výchozím nastavení je tato zpráva upozornění. Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40032  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud příslušné součásti rozhraní pouze s jinými [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] součástí, nebo nemá není rozhraní s ostatními součástmi, není potřeba nic nezmění.  
  
-   Pokud se propojení s nejsou určeny pro součásti [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], je možné určit, buď pomocí reflexe nebo z dokumentace, jestli podporuje tento datový typ. Pokud ano, není potřeba nic nezmění.  
  
-   Pokud se propojení s komponenty, která nepodporuje tento typ dat, musíte jej nahradit s typem nejbližší kompatibilní se specifikací CLS. Například v místě z `UInteger` je možné použít `Integer` Pokud nepotřebujete rozsah hodnot výše 2 147 483 647. Pokud potřebujete rozšířené rozsahu, můžete nahradit `UInteger` s `Long`.  
  
-   Pokud se propojení s objekty automatizace nebo COM, mějte na paměti, že některé typy mají různé datové šířek než [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Například `uint` je často 16 bitů v jiných prostředích. Argument 16bitové předáte pro tyto součásti, deklarujte ji jako `UShort` místo `UInteger` v spravovaného kódu jazyka Visual Basic.  
  
## <a name="see-also"></a>Viz také  
 [Reflexe (Visual Basic)](../../programming-guide/concepts/reflection.md)  
 [Reflexe](../../../framework/reflection-and-codedom/reflection.md)  
 
