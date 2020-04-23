---
title: 'Postupy: načtení informací o typu a členu pomocí reflexe'
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: 9ffc173bbd0ed12eedea0c191f6d39baf181793a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130206"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a>Postupy: načtení informací o typu a členu pomocí reflexe
<xref:System.Reflection> Obor názvů obsahuje mnoho metod získání informací o typech a jejich členech. Tento článek ukazuje jednu z těchto metod, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>. Další informace najdete v tématu [Přehled reflexe](reflection.md).
  
## <a name="example"></a>Příklad

Následující příklad získá informace o typu a členu pomocí reflexe:

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a>Viz také

- [Program s aplikačními doménami](../app-domains/application-domains.md#programming-with-application-domains)
- [Reflexe](reflection.md)
- [Použití aplikačních domén](../app-domains/use.md)
