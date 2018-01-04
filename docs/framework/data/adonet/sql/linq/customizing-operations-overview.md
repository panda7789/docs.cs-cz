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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 9776daa28b0a7ffcd3b721f004f5b9a44dd09f48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
