---
title: 'Postupy: Získání informací o typu a členu pomocí reflexe'
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
author: rpetrusha
ms.author: ronpet
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: da71845ea276267220636cfd661465ea02b2b50d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972919"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a>Postupy: Získání informací o typu a členu pomocí reflexe
<xref:System.Reflection> Obor názvů obsahuje mnoho metod získání informací o typech a jejich členech. Tento článek ukazuje jednu z těchto metod, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>. Další informace najdete v tématu [Přehled reflexe](reflection.md).
  
## <a name="example"></a>Příklad

Následující příklad získá informace o typu a členu pomocí reflexe:

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a>Viz také:

- [Program s aplikačními doménami](../app-domains/application-domains.md#programming-with-application-domains)
- [Reflexe](reflection.md)
- [Použití aplikačních domén](../app-domains/use.md)
