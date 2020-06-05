---
title: Ve vloženém kódu v prostředí ASP.NET nejsou podporovány literály XML a vlastnosti XML.
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: bda92b4244631f66142499a94be562854b35437e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406466"
---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a>Ve vloženém kódu v prostředí ASP.NET nejsou podporovány literály XML a vlastnosti XML.
Ve vloženém kódu v rámci ASP.NET nejsou podporovány literály XML a vlastnosti XML. Chcete-li používat funkce XML, přesuňte kód do kódu na pozadí.  
  
 Literál XML nebo vlastnost osy XML jsou definovány v rámci vloženého kódu ( `<%= =>` ) v souboru ASP.NET.  
  
 **ID chyby:** BC31200  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přesuňte kód, který obsahuje literál XML nebo vlastnost osy XML do souboru kódu na pozadí ASP.NET.  
  
## <a name="see-also"></a>Viz také

- [Literály XML](../xml-literals/index.md)
- [Vlastnosti osy XML](../xml-axis/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
