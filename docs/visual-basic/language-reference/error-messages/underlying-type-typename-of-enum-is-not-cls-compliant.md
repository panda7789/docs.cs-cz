---
title: Základní typ &lt;typename&gt; Enum není kompatibilní se Specifikací CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
ms.openlocfilehash: 876a59d1441c1ba4c5057556d5ef2fb2ecb43af6
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37959676"
---
# <a name="underlying-type-lttypenamegt-of-enum-is-not-cls-compliant"></a>Základní typ &lt;typename&gt; Enum není kompatibilní se Specifikací CLS
Datový typ zadaný pro tento výčet není součástí [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS). Toto není k chybě v komponentě, protože [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] a Visual Basic podporují tento datový typ. Jiné součásti, které jsou napsané v striktně kompatibilní se Specifikací CLS kódu však nemusí podporovat tento typ dat. Takové součásti nemusí být úspěšně komunikovat s vaší komponentě.  
  
 Následující datové typy jazyka Visual Basic nejsou kompatibilní se Specifikací CLS:  
  
-   [Datový typ SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Datový typ UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [Datový typ ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [Datový typ UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Ve výchozím nastavení tato zpráva je upozornění. Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40032  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud vaše komponenta rozhraní pouze s jinými [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] komponenty, nebo nemá není rozhraní s ostatními součástmi, nemusíte nic měnit.  
  
-   Pokud při vzájemném propojování součástí, které nejsou napsané pro [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], může být schopní určit, buď prostřednictvím reflexe nebo dokumentaci ke službě, jestli podporuje tento typ dat. Pokud ano, není potřeba nic měnit.  
  
-   Při vzájemném propojování součástí, která nepodporuje tento typ dat, musíte jej nahradit s typem nejbližší kompatibilní se Specifikací CLS. Například místo hodnoty `UInteger` je možné použít `Integer` Pokud nepotřebujete rozsah hodnot nad 2 147 483 647. Pokud budete potřebovat delší rozsah, můžete nahradit `UInteger` s `Long`.  
  
-   Při vzájemném propojování s objekty automatizace nebo COM, mějte na paměti, že některé typy mají různou šířkou dat než [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Například `uint` je často 16 bitů v jiných prostředích. Pokud takové součásti předáváte 16bitový argument, deklarujte ho jako `UShort` místo `UInteger` v spravovaného kódu jazyka Visual Basic.  
  
## <a name="see-also"></a>Viz také  
 [Reflexe (Visual Basic)](../../programming-guide/concepts/reflection.md)  
 [Reflexe](../../../framework/reflection-and-codedom/reflection.md)  
 
