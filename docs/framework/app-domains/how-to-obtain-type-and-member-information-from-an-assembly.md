---
title: "Postupy: Získávání informací o typu a členu ze sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- obtaining assembly information
- assemblies [.NET Framework], obtaining information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1c3112b7484e4d03eaacd218ff8e8ac34e77745b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a>Postupy: Získávání informací o typu a členu ze sestavení
<xref:System.Reflection> Obor názvů obsahuje mnoho metody pro získání informací ze sestavení. V této části ukážeme jednu z těchto metod. Další informace najdete v tématu [Přehled reflexe](../../../docs/framework/reflection-and-codedom/reflection.md).  
  
 Následující příklad získává informace typu a členu ze sestavení.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a>Viz také  
 [Programování s doménami aplikací](http://msdn.microsoft.com/library/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [Reflexe](../../../docs/framework/reflection-and-codedom/reflection.md)  
 [Používání domén aplikací](../../../docs/framework/app-domains/use.md)
