---
title: 'Přizpůsobení operací: Přehled'
ms.date: 03/30/2017
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
ms.openlocfilehash: 48116887471709c60c9666f68c7ebdd0e6d128a1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247515"
---
# <a name="customizing-operations-overview"></a>Přizpůsobení operací: Přehled
Ve výchozím nastavení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje dynamické SQL pro operace vložení, aktualizace a odstranění na základě mapování. V praxi však obvykle budete chtít přidat vlastní obchodní logiku pro zajištění zabezpečení, ověřování a tak dále.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]mezi techniky přizpůsobení těchto operací patří následující.  
  
## <a name="loading-options"></a>Možnosti načítání  
 V dotazech můžete určit, kolik dat souvisejících s vaším hlavním cílem bude načteno při připojení k databázi. Tato funkce je implementována převážně pomocí <xref:System.Data.Linq.DataLoadOptions>. Další informace najdete v tématu [odložené porovnání a okamžité načítání](deferred-versus-immediate-loading.md).  
  
## <a name="partial-methods"></a>Částečné metody  
 V jeho výchozím mapování poskytuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] částečné metody, které vám pomůžou s implementací obchodní logiky. Další informace najdete v tématu [Přidání obchodní logiky pomocí částečných metod](adding-business-logic-by-using-partial-methods.md).  
  
## <a name="stored-procedures-and-user-defined-functions"></a>Uložené procedury a uživatelsky definované funkce  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podporuje použití uložených procedur a uživatelsky definovaných funkcí. Uložené procedury se často používají k přizpůsobení operací. Další informace najdete v tématu [uložené procedury](stored-procedures.md).  
  
## <a name="see-also"></a>Viz také:

- [Přizpůsobení operací vložení, aktualizace a odstranění](customizing-insert-update-and-delete-operations.md)
