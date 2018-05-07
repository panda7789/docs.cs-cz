---
title: Základy transakce
ms.date: 03/30/2017
ms.assetid: 353f4ee2-e6bf-4b1c-b1c8-385fc8a486c0
ms.openlocfilehash: 1189556c74c45dc7475dd872c01c1ec5eaeba111
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="transaction-fundamentals"></a>Základy transakce
Transakce vazby společně více úloh. Představte si například, že aplikace provede dvě úlohy. Nejprve vytvoří nové tabulky v databázi. Dále volá specializovanou objekt ke sběru, formátování a data vložit do nové tabulky. Tyto dvě úlohy jsou související a dokonce i vzájemně závislé, tak, že chcete se vyhnout, vytvářet nové tabulky, není-li vyplní jej s daty. Provádění oba úkoly v rámci jedné transakce vynucuje mezi nimi spojení. Pokud jako druhý krok nezdaří, prvního úkolu je vrátit zpět do bodu předtím, než byla vytvořena nová tabulka.  
  
 Aby bylo zajištěno předvídatelný chování, musí mít všechny transakce základní vlastnosti ACID (atomické, konzistentní, izolované a trvalý). Tyto vlastnosti posílit úlohu důležitými podnikovými transakce jako all-or-none tvrzení. Další informace o kyseliny, najdete v tématu [kyseliny vlastnosti](http://go.microsoft.com/fwlink/?LinkId=98791). V souhrnu kyselina zaručuje, že sadu související úlohy úspěch nebo neúspěch jako jednotku. V transakci buď zpracování terminologie, transakce potvrzení nebo přerušení. Pro určitou transakci potvrdit musí všichni účastníci zaručit, že změny dat bude trvalé. Změny musíte zachovat navzdory zhroucení systému nebo jiné nepředvídatelné události. Pokud ještě jeden účastník neprovede této záruky, celá transakce nezdaří. Všechny změny dat v rámci oboru transakce jsou vrácena zpět do určitého bodu sady.  
  
 Transakce mohou být omezeny na jednoho datového zdroje, například určitého fronty databáze nebo zprávy. V tomto případě místní transakce je spravován transakce správcem poskytované <xref:System.Transactions> , který generuje zvýšení výkonu. Řídí zdrojů dat, jsou tyto transakce efektivní a snadno spravovat.  
  
 Transakce mohou zasahovat do více zdrojů dat. Distribuované transakce udělit oprávnění začlenit několika distinct operací, k nimž došlo v různých systémech v jednom průchodu nebo neúspěch akce. V tomto případě jsou transakce koordinovaný podle Microsoft distribuované transakce koordinátor (MSDTC) který se nachází v každém systému.  
  
 Pokud vyvíjíte transakční aplikace pomocí tříd poskytovaných <xref:System.Transactions>, není nutné starat o jaký typ transakcí, které potřebujete, nebo jejich zapojení správce transakcí. <xref:System.Transactions> Infrastruktury automaticky spravuje tyto pro vás.  
  
 Při vytváření transakcí, můžete určit úroveň izolace, která se použije pro transakce. Úroveň izolace, definované <xref:System.Transactions.IsolationLevel> výčtu, určuje úroveň přístupu dalších transakcí nebude mít k datům vliv na vaše transakce.  
  
 Můžete vytvořit pomocí ADO.NET, transakce <xref:System.EnterpriseServices>, nebo transakční programovací model poskytované <xref:System.Transactions> oboru názvů. [Funkce poskytované službou System.Transactions –](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md) téma popisuje funkce, které můžete použít k zápisu, transakční aplikace pomocí <xref:System.Transactions> oboru názvů.  
  
## <a name="see-also"></a>Viz také  
 [Funkce poskytované přes System.Transactions](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md)
