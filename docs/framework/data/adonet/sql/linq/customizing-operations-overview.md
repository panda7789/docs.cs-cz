---
title: 'Přizpůsobení operací: Přehled'
ms.date: 03/30/2017
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
ms.openlocfilehash: 4f13bed76ad2814d669f487b57ae9acbdc08eb74
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735458"
---
# <a name="customizing-operations-overview"></a>Přizpůsobení operací: Přehled
Ve výchozím nastavení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje dynamické SQL pro vložení, aktualizace nebo odstranění operace založené na mapování. Nicméně v praxi obvykle chcete přidat vlastní obchodní logikou poskytnout zabezpečení, ověřování a tak dále.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] techniky pro přizpůsobení tyto operace patří.  
  
## <a name="loading-options"></a>Možnosti načítání  
 V dotazech můžete určit, kolik data související s hlavním cílem je načten při připojení k databázi. Tato funkce je implementována do značné míry pomocí <xref:System.Data.Linq.DataLoadOptions>. Další informace najdete v tématu [odložené versus okamžité načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
## <a name="partial-methods"></a>Částečné metody  
 V jeho výchozí mapování [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje částečným metodám, aby vám pomohly implementovat obchodní logiku. Další informace najdete v tématu [přidání obchodní logiky pomocí částečné metody](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md).  
  
## <a name="stored-procedures-and-user-defined-functions"></a>Uložených procedur a uživatelem definovaných funkcí  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje použití uložených procedur a uživatelem definované funkce. Uložené procedury se často používají k přizpůsobení operací. Další informace najdete v tématu [uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).  
  
## <a name="see-also"></a>Viz také:
- [Přizpůsobení operací vložení, aktualizace a odstranění](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
