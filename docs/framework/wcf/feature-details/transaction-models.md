---
title: Modely transakcí
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 8731b72d0657aa420dbb020e216c3af059916ce9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517780"
---
# <a name="transaction-models"></a>Modely transakcí
Toto téma popisuje vztah mezi programovací modely transakcí a komponent infrastruktury, které společnost Microsoft poskytuje.  
  
 Při použití transakcí ve Windows Communication Foundation (WCF), je důležité pochopit, že se zrušením výběru možnosti mezi různými modely transakcí, ale místo toho provoz na různých úrovních integrované a konzistentní model.  
  
 Následující části popisují tři komponenty primární transakce.  
  
## <a name="windows-communication-foundation-transactions"></a>Windows Communication Foundation transakce  
 Podpora transakcí v WCF umožňuje že zápis transakční služeb. Kromě toho s jeho podporu protokolu WS-AtomicTransaction (WS-AT), můžete aplikace tok transakcí, které webové služby vytvořené pomocí WCF nebo technologii jiného výrobce.  
  
 Ve službě WCF nebo aplikace poskytují funkce transakce WCF atributy a konfigurace pro deklarativně určení jak a kdy by měl vytvořit infrastrukturu, flow a synchronizovat transakce.  
  
## <a name="systemtransactions-transactions"></a>Transakce System.Transactions  
 <xref:System.Transactions> Obor názvů obsahuje oba explicitní programovací model na základě <xref:System.Transactions.Transaction> třídy, jakož i jazyka implicitní programování pomocí modelu <xref:System.Transactions.TransactionScope> třídy, ve kterém infrastruktury automaticky spravuje transakce.  
  
 Další informace o tom, jak vytvořit transakční aplikaci pomocí těchto dvou modelech naleznete v tématu [zápis transakční aplikace](https://go.microsoft.com/fwlink/?LinkId=94947).  
  
 Ve službě WCF nebo aplikace <xref:System.Transactions> poskytuje programovací model pro vytváření transakcí v rámci klientské aplikace a explicitně interakci s transakcí, pokud jsou povinné, v rámci služby.  
  
## <a name="msdtc-transactions"></a>Služba MSDTC transakcí  
 Microsoft distribuované transakce koordinátor MSDTC () je správce transakcí, která poskytuje podporu pro distribuované transakce.  
  
 Další informace najdete v tématu [DTC programátora](https://go.microsoft.com/fwlink/?LinkId=94948).  
  
 Ve službě WCF nebo aplikace služby MSDTC poskytuje infrastrukturu pro koordinaci transakce vytvořené v rámci klienta nebo služby.
