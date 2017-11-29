---
title: "Základní typ &lt;typename&gt; výčtu není kompatibilní se specifikací CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords: BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68b57dc82737b72463b7fcf1a3e50934e1562c31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="underlying-type-lttypenamegt-of-enum-is-not-cls-compliant"></a>Základní typ &lt;typename&gt; výčtu není kompatibilní se specifikací CLS
Datový typ zadaný pro tento výčet není součástí [jazyková nezávislost a jazykově nezávislé komponenty](https://msdn.microsoft.com/library/12a7a7h3) (CLS). Toto není chybu v rámci komponenty, protože [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] podporují tento datový typ. Jiné komponenty, které jsou zapsané ve výhradně kompatibilní se specifikací CLS kódu však nemusí podporovat tento datový typ. Tyto součásti nemusí být možné úspěšně komunikovat s příslušné součásti.  
  
 Následující [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] datové typy nejsou kompatibilní se specifikací CLS:  
  
-   [SByte – datový typ](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Uinteger – datový typ](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [Ulong – datový typ](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [Ushort – datový typ](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Ve výchozím nastavení je tato zpráva upozornění. Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40032  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud příslušné součásti rozhraní pouze s jinými [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] součástí, nebo nemá není rozhraní s ostatními součástmi, není potřeba nic nezmění.  
  
-   Pokud se propojení s nejsou určeny pro součásti [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], je možné určit, buď pomocí reflexe nebo z dokumentace, jestli podporuje tento datový typ. Pokud ano, není potřeba nic nezmění.  
  
-   Pokud se propojení s komponenty, která nepodporuje tento typ dat, musíte jej nahradit s typem nejbližší kompatibilní se specifikací CLS. Například v místě z `UInteger` je možné použít `Integer` Pokud nepotřebujete rozsah hodnot výše 2 147 483 647. Pokud potřebujete rozšířené rozsahu, můžete nahradit `UInteger` s `Long`.  
  
-   Pokud se propojení s objekty automatizace nebo COM, mějte na paměti, že některé typy mají různé datové šířek než [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Například `uint` je často 16 bitů v jiných prostředích. Argument 16bitové předáte pro tyto součásti, deklarujte ji jako `UShort` místo `UInteger` ve vaší spravované [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kódu.  
  
## <a name="see-also"></a>Viz také  
 [Reflexe](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26)  
 [Reflexe](../../../framework/reflection-and-codedom/reflection.md)  
 [\<PAVE přes > zápis kompatibilní se specifikací CLS kódu](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
