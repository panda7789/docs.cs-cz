---
title: "Přizpůsobení Operations: Přehled"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6d3491ccd183224063c435f6b377f60b175d5383
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="customizing-operations-overview"></a>Přizpůsobení Operations: Přehled
Ve výchozím nastavení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje dynamické SQL pro příkaz insert, update a operace odstranění na základě mapování. Nicméně v praxi obvykle chcete přidat vlastní obchodní logiku zajistit pro zabezpečení, ověřování a tak dále.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]techniky pro přizpůsobení tyto operace jsou následující.  
  
## <a name="loading-options"></a>Načítání možnosti  
 V dotazech můžete určit, kolik dat souvisejících s vaší hlavní cíl se načítají, když jste připojení k databázi. Tato funkce je implementována do značné míry pomocí <xref:System.Data.Linq.DataLoadOptions>. Další informace najdete v tématu [odložení versus okamžitou načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
## <a name="partial-methods"></a>Částečné metody  
 V jeho výchozí mapování [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje částečné metody, která vám pomůže implementovat obchodní logiku. Další informace najdete v tématu [přidání obchodní logiku podle pomocí částečné metody](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md).  
  
## <a name="stored-procedures-and-user-defined-functions"></a>Uložené procedury a funkce definované uživatelem  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podporuje použití uložených procedur a uživatelem definované funkce. K úpravě operací se často používají uložené procedury. Další informace najdete v tématu [uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).  
  
## <a name="see-also"></a>Viz také  
 [Přizpůsobení operací vložení, aktualizace a odstranění](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
