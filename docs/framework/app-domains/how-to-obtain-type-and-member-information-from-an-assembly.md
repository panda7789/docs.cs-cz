---
title: 'Postupy: Získávání informací o typu a členu ze sestavení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- obtaining assembly information
- assemblies [.NET Framework], obtaining information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f9d01715a9635b276ca87d94082bb4d3820084e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675426"
---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a>Postupy: Získávání informací o typu a členu ze sestavení
<xref:System.Reflection> Obor názvů obsahuje mnoho metod pro získání informací ze sestavení. Tato část ukazuje jednu z těchto metod. Další informace najdete v tématu [Přehled reflexe](../../../docs/framework/reflection-and-codedom/reflection.md).  
  
 Následující příklad získá informace o typu a členu ze sestavení.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a>Viz také:

- [Programování pomocí domén aplikace](./application-domains.md#programming-with-application-domains)
- [Reflexe](../../../docs/framework/reflection-and-codedom/reflection.md)
- [Používání domén aplikací](../../../docs/framework/app-domains/use.md)
