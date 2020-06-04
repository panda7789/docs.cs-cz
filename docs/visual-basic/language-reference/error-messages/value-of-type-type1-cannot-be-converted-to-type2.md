---
title: Hodnotu typu 'type1' nelze převést na 'type2'.
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: f19f157bd4c76f481aa3232bc33c2a0c6ac21367
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400276"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a>Hodnotu typu 'type1' nelze převést na 'type2'.
Hodnotu typu typ1 nelze převést na typ typ2. Vlastnost Value lze použít k získání řetězcové hodnoty prvního prvku \<parentElement> .  
  
 Byl proveden pokus o implicitní přetypování literálu XML na konkrétní typ. Literál XML nelze implicitně přetypovat na zadaný typ.  
  
 **ID chyby:** BC31194  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Použijte `Value` vlastnost literálu XML pro odkaz na svou hodnotu jako `String` . Použijte `CType` funkci, jinou funkci konverze typu nebo <xref:System.Convert> třídu pro přetypování hodnoty jako zadaného typu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Convert>
- [Funkce pro převod typů](../functions/type-conversion-functions.md)
- [Literály XML](../xml-literals/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
