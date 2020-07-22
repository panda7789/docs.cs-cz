---
title: 'Postupy: Získání informací o typech a členech pomocí reflexe'
description: Naučte se, jak získat informace o typu a členu pomocí reflexe pomocí oboru názvů System. Reflection.
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: fa7af39c0addb328944a03236c26982301caf722
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865317"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a>Postupy: Získání informací o typech a členech pomocí reflexe
<xref:System.Reflection>Obor názvů obsahuje mnoho metod získání informací o typech a jejich členech. Tento článek ukazuje jednu z těchto metod, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> . Další informace najdete v tématu [Přehled reflexe](reflection.md).
  
## <a name="example"></a>Příklad

Následující příklad získá informace o typu a členu pomocí reflexe:

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a>Viz také

- [Program s aplikačními doménami](../app-domains/application-domains.md#programming-with-application-domains)
- [Reflexe](reflection.md)
- [Použití aplikačních domén](../app-domains/use.md)
