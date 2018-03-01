---
title: "Postupy: Vytvoření domény aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cdbab5e43d2af7608c4d8322eb071baf591e18d5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-an-application-domain"></a>Postupy: Vytvoření domény aplikace
Běžné hostitel běhu jazyka automaticky vytvoří aplikační domény v případě potřeby. Můžete však vytvořit vlastní domény aplikace a načíst do nich ty sestavení, které chcete spravovat osobní. Můžete také vytvořit aplikační domény, ze kterých je kód spuštěn.  
  
 Vytvořit novou doménu aplikace pomocí jednoho z přetížené **CreateDomain** metody v <xref:System.AppDomain?displayProperty=nameWithType> třídy. Můžete pojmenujte doménu aplikace a odkaz s tímto názvem.  
  
 Následující příklad vytvoří novou doménu aplikace a přiřadí ji název `MyDomain`a potom zobrazí název domény hostitele a nově vytvořené podřízené domény aplikace do konzoly.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Programování s doménami aplikací](http://msdn.microsoft.com/library/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [Používání domén aplikací](../../../docs/framework/app-domains/use.md)
