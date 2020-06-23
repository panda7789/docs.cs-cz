---
title: Zpracování transakcí
description: Kontrola zpracování transakcí v .NET. Transakce zajistí, že se prostředky orientované na data nebudou trvale aktualizovat, dokud nebudou všechny operace úspěšně dokončeny.
ms.date: 03/30/2017
ms.assetid: effdc8e6-accf-41eb-98a5-431603ba218b
ms.openlocfilehash: 30d69c55d968865cc80b8633bdbc2442f6d216de
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141911"
---
# <a name="transaction-processing"></a>Zpracování transakcí
V případě zakoupení knihy online knihkupectví výměny se peníze (ve formě platební) pro knihy. Pokud váš kredit je dobré použít, řadu souvisejících operací zajišťuje, že získat knihy a knihkupectví získá vaše peníze. Nicméně pokud jedné operace v řadě dojde během serveru exchange, celý exchange se nezdaří. Nelze získat knihy a knihkupectví nebude mít k dispozici vaše peníze.  
  
 Technologie odpovědné za výměnu vyváženého a předvídatelný se nazývá zpracování transakcí. Transakce zajistit, aby objektově orientované prostředky nejsou trvale aktualizována, není-li úspěšně dokončit všechny operace v rámci transakční jednotky. Kombinováním sadu souvisejících operací do jednotky, který je buď zcela úspěšná nebo zcela selže, můžete zjednodušit chyba obnovení a spolehlivost vaší aplikace.  
  
 Systémy zpracování transakce se skládá z počítačového hardwaru a softwaru, který je hostitelem aplikace orientované transakce, která provede rutinní transakcí, které jsou nezbytné k podnikání. Příklady: systémy, které spravují prodejní objednávky položku, rezervace letenek, mezd, záznamy zaměstnanců, výrobní a příjemce.  
  
 Tato část poskytuje obecné informace o zpracování transakcí a konkrétní informace o tom, jak napsat Transakční aplikace a správci prostředků pomocí rozhraní Microsoft .NET Framework.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Principy transakcí](transaction-fundamentals.md)  
 Představuje základní transakce zpracování podmínky a konceptů.  
  
 [Funkce poskytované přes System.Transactions](features-provided-by-system-transactions.md)  
 Popisuje, jak používat funkce v System.Transactions psát svůj vlastní transakční aplikace.  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.Transactions>  
 Poskytuje třídy, které umožňují váš kód k účasti v transakcích. Třídy podporu transakcí s více distribuované účastníky, několik fáze oznámení a trvalý zařazení.
