---
title: Modely transakcí
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 9efe8c6994cc80957b707bbae0885a3c5896f70a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499021"
---
# <a name="transaction-models"></a>Modely transakcí
Toto téma popisuje vztah mezi programovací modely transakcí a součásti infrastruktury, které společnost Microsoft poskytuje.  
  
 Při použití transakce ve Windows Communication Foundation (WCF), je důležité si uvědomit, že jsou nevyberete mezi různými modely transakcí, ale spíš operační v různých úrovní integrované a konzistentní model.  
  
 Následující části popisují komponenty tři primární transakce.  
  
## <a name="windows-communication-foundation-transactions"></a>Windows Communication Foundation transakce  
 Podpora transakcí v WCF umožňuje že zápis transakční služeb. Kromě toho s podporou pro protokol WS-AtomicTransaction (WS-AT), může aplikace tok transakcí webové služby vytvořené pomocí WCF nebo technologie třetích stran.  
  
 Funkce transakce WCF na službu WCF nebo v aplikaci zadejte atributy a konfigurace pro deklarativně určení jak a kdy infrastruktury by měl vytvářet, toku a synchronizovat transakce.  
  
## <a name="systemtransactions-transactions"></a>System.Transactions – transakce  
 <xref:System.Transactions> Obor názvů obsahuje oba explicitní programovací model na základě <xref:System.Transactions.Transaction> třídy, jakož i k implicitní programování pomocí modelu <xref:System.Transactions.TransactionScope> třída, ve kterém infrastruktury automaticky spravuje transakce.  
  
 Další informace o tom, jak vytvořit transakční aplikace pro použití těchto dvou modelů najdete v tématu [zápis transakční aplikace](http://go.microsoft.com/fwlink/?LinkId=94947).  
  
 V aplikaci, nebo službu WCF <xref:System.Transactions> poskytuje programovací model pro vytváření transakcí v rámci klientské aplikace a explicitně interakci s transakci, pokud jsou povinné, v rámci služby.  
  
## <a name="msdtc-transactions"></a>Služba MSDTC transakce  
 Microsoft koordinátora pro distribuované transakce (MSDTC) je správce transakcí, která poskytuje podporu pro distribuované transakce.  
  
 Další informace najdete v tématu [referenční informace pro programátory DTC](http://go.microsoft.com/fwlink/?LinkId=94948).  
  
 Služba MSDTC na službu WCF nebo v aplikaci poskytuje infrastrukturu pro koordinaci transakce vytvořené v rámci klienta nebo služby.
