---
title: "Přizpůsobení operace pomocí uložené procedury výhradně"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b379f6eec503f5dffc5a01dd8f5cbc79e19b8c40
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a>Přizpůsobení operace pomocí uložené procedury výhradně
Přístup k datům s použitím pouze uložené procedury je běžný scénář.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Můžete upravit v příkladu v [přizpůsobení Operations podle pomocí uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) nahrazením i první dotaz, (což způsobí, že dynamické provedení SQL) volání metody, která zabalí uložené procedury.  
  
 Předpokládejme `CustomersByCity` je metoda, jako v následujícím příkladu.  
  
### <a name="code"></a>Kód  
 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 Následující kód spustí bez žádné dynamické SQL.  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Viz také  
 [Odpovědnosti vývojáře při přepisu výchozího chování](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
